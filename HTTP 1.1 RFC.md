# RFC HTTP1.1
- **Connection:** Uma camada de transporte virtual entre 2 programas.
- **Message:** A unidade basica do HTTP que é uma sequencia de octetos(talvez 8 bits?) que seguem a sintaxe do HTTP
- **Resource:** Um objeto de informação de rede que pode ser identificado por uma URI
- **Entity:** Uma informação transferida como um payload que consiste de metainformação(tipo o header) e o conteudo.
- **Representação:** Uma entity com uma response que é sujeito a uma negociação de conteudo
- **Origin server: ** O servidor em que o resource reside

## **Augmented BNF*
- **name = definition** sem <> e 
- **"literal"** Literal  e case-insensitive
- **rule1 | rule2** Alternativas
- **(rule1 rule2)** Um unico elemento com regras sequenciais
- **\*rule** Repetição de pelo menos uma vez
- **[rule]** Mesma coisa que **1(rule)**
- **N rule** É n vezes o rule
- **; comment** Comentário

## Regras básicas
- **OCTET** = 8 bits
- **CHAR** = ASCII-US 0 a 127
- **UPALPHA** = A..Z
- **LOALPHA** = a..z
- **ALPHA** = UPALPHA | LOALPHA
- **DIGIT** = 0..9
- **CTL** = 0 a 31 e DEL (127)
- **CR** CARRIAGE RETURN 13
- **LF** LINE FEADER 10
- **SP** SPACE 
- **HT** HORIZONTAL-TAB 9
- <\"> 
- **CRLF** = "\r\n"
- **LWS** = \[CRLF\] 1* (SP|HT)
- **TEXT** = Qualquer OCTET que não seja CTLs
- **HEX** = A..F | a..f | DIGIT
- **HTTP-Version**  = "HTTP" "/" 1\*DIGIT "." 1\*DIGIT

## Uniform resource identifiers
**URIs** = Scheme seguido de ":" 
**http_URL** = "http:" "//" host \[":" port\] \[abs_pth \["?" query\]\]
Se a port não é especificada a porta 80 é assumida.

## Comparação de URI
Para comparar 2 URI o client **DEVE** usar uma analise case-sentisitive octeto por octeto das URIs

## Formato de datas 
Sun, 06 Nov 1994 08:49:37 GMT

- ** HTTP-date **   = [rfc1123](https://datatracker.ietf.org/doc/html/rfc1123)\-date | [rfc850](https://datatracker.ietf.org/doc/html/rfc850)\-date | asctime-date
 - **[rfc1123](https://datatracker.ietf.org/doc/html/rfc1123)\-date** = wkday "," SP date1 SP time SP "GMT"
 
 - **[rfc850](https://datatracker.ietf.org/doc/html/rfc850)\-date**  = weekday "," SP date2 SP time SP "GMT"
 
 - **asctime-date** = wkday SP date3 SP time SP 4DIGIT
 
 -  **date1**        = 2DIGIT SP month SP 4DIGIT
 
 - **date2**        = 2DIGIT "-" month "-" 2DIGIT
 
-  **date3**        = month SP ( 2DIGIT | ( SP 1DIGIT ))

 - **time**         = 2DIGIT ":" 2DIGIT ":" 2DIGIT
 
 -  **wkday**        = "Mon" | "Tue" | "Wed" | "Thu" | "Fri" | "Sat" | "Sun"
 
-  **weekday**      = "Monday" | "Tuesday" | "Wednesday" | "Thursday" | "Friday" | "Saturday" | "Sunday"

-  **month**  = "Jan" | "Feb" | "Mar" | "Apr" | "May" | "Jun" | "Jul" | "Aug | "Sep" | "Oct" | "Nov" | "Dec"
