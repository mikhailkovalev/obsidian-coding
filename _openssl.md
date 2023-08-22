#openssl #encrypt 
```bash
# encrypt file
openssl enc -aes-256-cbc -md sha512 -pbkdf2 -iter 100000 -salt -in foo.txt -out foo.txt.enc  

# decrypt file
openssl enc -d -aes-256-cbc -md sha512 -pbkdf2 -iter 100000 -salt -in foo.txt.enc  

# encrypt pipe
echo "hello world" | openssl enc -aes-256-cbc -md sha512 -pbkdf2 -iter 100000 -salt -out foo.txt.enc  

# decrypt pipe
cat foo.txt.enc | openssl enc -d -aes-256-cbc -md sha512 -pbkdf2 -iter 100000 -salt
```

Задать пароль через файл
[Source](https://stackoverflow.com/questions/6321353/securely-passing-password-to-openssl-via-stdin)
```bash
openssl aes-256-cbc -a -salt -in twitterpost.txt -out foo.enc -pass file:passfile
```

через переменную окружения:
```
-pass env:ENVVAR
```
