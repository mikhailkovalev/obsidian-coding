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