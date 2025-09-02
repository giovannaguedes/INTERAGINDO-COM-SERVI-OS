# INTERAGINDO-COM-SERVI-OS
código permite a interação do socket com o ftp server ou seja porta 21.

⚠️ Uso exclusivo para fins educacionais • Desenvolvido por M!ss s3c

📝 Guia: Criando e executando seu primeiro script de interação com FTP

1. Criar o arquivo do script

No terminal, crie o arquivo:

nano script4.7.py

2. Adicionar o código Python

Cole o seguinte código:

#!/usr/bin/python3
# Interação com FTP Server via Socket

import socket

print("Interagindo com FTP Server")

# Solicita o IP do servidor FTP
ip = input("Digite o IP: ")
porta = 21  # porta padrão FTP

# Cria o socket TCP
meusocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
meusocket.settimeout(3)  # evita travamentos longos

# Conecta ao servidor e recebe o banner
meusocket.connect((ip, porta))
banner = meusocket.recv(1024)
print(banner.decode().strip())

# Envia usuário
print("Enviando usuário")
meusocket.send(str.encode('USER ricardo\r\n'))
banner = meusocket.recv(1024)
print(banner.decode().strip())

# Envia senha
print("Enviando senha")
meusocket.send(str.encode("PASS ricardo\r\n"))
banner = meusocket.recv(1024)
print(banner.decode().strip())

# Fecha o socket
meusocket.close()


⚠️ Observação: Este script não deve ser usado em sistemas não autorizados. Serve apenas para aprendizado.

3. Executar o script
python3 script4.7.py

4. Exemplo de execução
Interagindo com FTP Server
Banner recebido: 220 (vsFTPd 3.0.3)
Enviando usuário
Resposta: 331 Please specify the password.
Enviando senha
Resposta: 230 Login successful.

👉 O que você aprendeu aqui

socket.socket() → cria um socket TCP.

connect() → conecta ao servidor FTP.

recv(1024) → recebe a resposta do servidor (banner ou mensagens).

send() → envia comandos para o serviço (USER, PASS).

settimeout() → evita travamentos em servidores lentos ou não responsivos.

Sempre usar close() → libera recursos do socket.
