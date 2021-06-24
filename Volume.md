# Volumes
- **FAT32** - é a mais comum em periféricos e FAT64 é a nova versão.
- **NTFS** - é o sistema de arquivo mais comum pra windows tanto que ele só pode ser instalado em NTFS
- **EXT4** - Versão 4 do sistema de arquivo EXT.
## Comandos
- **fdisk** - Criar partições
- **mkfs.ext4 /dev/sdb2** - Formatar partição como ext4 
- **mount /dev/sda1 /media/particao** - Monta partição 
- **df** - Ve as partições e etc
## FSTAB
- **/etc/fstab** - é o arquivo que o linux usa pra fazer a montagem das partições