# Serial em C

Incluir algumas libs em C
```c
#include <stdio.h>   // Standard IO 
#include <string.h>  // Manipulação de Strings

#include <fcntl.h> // Coisas para controlar arquivos
#include <errno.h> // Enum de erros e a função strerror()
#include <termios.h> // Controle de terminal POSIX
#include <unistd.h> // Manipulação de arquivos UNIX
```
Abre o fd correspondente
```c
int serial_port = open("/dev/ttyUSB0", O_RDWR);

// Check por erro
if (serial_port < 0) {
    printf("Error %i from open: %s\n", errno, strerror(errno));
}
```
Criar a estrutura de termios do POSIX e depois usa o FD para pegar info do FD e botar no tty, é necessário se não o comportamento vai ser indefinido
```c
struct termios tty;

if(tcgetattr(serial_port, &tty) != 0) {
    printf("Error %i from tcgetattr: %s\n", errno, strerror(errno));
}
```

Bit de paridade para checagem de erro facil não é usada em comunicações seriais normalmente então é bom limpar 
```c
// Limpa o bit de paridade
tty.c_cflag &= ~PARENB;
// Seta o bit de paridade
tty.c_cflag |= PARENB;
```
CSTOPB define se vai ser usado um ou dois bits de parada. Quando é limpo ele usa só 1
```c
// Limpa o bit de stop ou seja só usa 1
tty.c_cflag &= ~CSTOPB; 
// Seta o bit pra usar 2
tty.c_cflag |= CSTOPB; 
```
Numeros de bits por byte
```c
// Limpa os bits de tamanho então seta os de baixo
tty.c_cflag &= ~CSIZE
// Oito bits por byte
tty.c_cflag |= CS8; 
```
Habilita e desabilita o controle de fluxo RTC/CTS que é um protocolo que provaelmente vamos desabilitar
```c
tty.c_cflag &= ~CRTSCTS; // Desabilita
tty.c_cflag |= CRTSCTS; // Habilita
```
Setar CLOCAL desabilita coisas especificas do modem tipo `carrier detect`. Nesse caso setar o CLOCAL nós habilita a ler  dados
```c
// Liga CREAD e desabilita CLOCAL (1)
tty.c_cflag |= CREAD | CLOCAL; 
```
UNIX da dois tipos de input que é `canonical` que o input é processado quando um `\n` surge e não canonico que 
```c
tty.c_lflag &= ~ICANON; // Desabilita Canonical mode
```
Desligar ECHO (quando um bit é mandado ele é ecoado de volta)
```c
tty.c_lflag &= ~ECHO; // Tira eco
tty.c_lflag &= ~ECHOE;  // Tira erasure
tty.c_lflag &= ~ECHONL; // Tira eco de quebra de linha
```
ISIG deixa INTR, QUIT e SUSP serem interpretados
```c
tty.c_lflag &= ~ISIG; // Dsabilita alguns problemas de char que podem surgir 
```
Desabilita software flow control
```c
tty.c_iflag &= ~(IXON | IXOFF | IXANY); // Turn off s/w flow ctrl
```
Desabilita qualqeur tipo especial de handling de byte
```c
tty.c_iflag &= ~(IGNBRK|BRKINT|PARMRK|ISTRIP|INLCR|IGNCR|ICRNL); // Disable any special handling of received bytes
```
Desabilita interpretação de \\n e outros na saida de dados
```c
tty.c_oflag &= ~OPOST; // Prevent special interpretation of output bytes (e.g. newline chars)
tty.c_oflag &= ~ONLCR; // Prevent conversion of newline to carriage return/line feed
// tty.c_oflag &= ~OXTABS; // Prevent conversion of tabs to spaces (NOT PRESENT IN LINUX)
// tty.c_oflag &= ~ONOEOT; // Prevent removal of C-d chars (0x004) in output (NOT PRESENT IN LINUX)
```

**VMIN = 0, VTIME = 0**: Não bloqueia e retorna imediatamente o que recebeu

**VMIN > 0, VTIME = 0**:  Bloqueia e espera pela quantidade especificada pelo VMIN

**VMIN = 0, VTIME > 0**: Bloqueia até atingir o tempo VTIME.

**VMIN > 0, VTIME > 0**: Bloqueia até o minimo de chars ou quando VTIEM for atingido pelo primeiro char.

```c
tty.c_cc[VTIME] = 10; // Wait for up to 1s (10 deciseconds), returning as soon as any data is received.
tty.c_cc[VMIN] = 0;
```
Seta velocidade de input e saida
```c
cfsetispeed(&tty, B9600);
cfsetospeed(&tty, B9600);
```
Checa configurações do termios
```c
if (tcsetattr(serial_port, TCSANOW, &tty) != 0) {
    printf("Error %i from tcsetattr: %s\n", errno, strerror(errno));
}
```
