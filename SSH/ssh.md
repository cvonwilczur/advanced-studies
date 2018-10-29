#Secure Shell - ssh

SSH is a protocol, or language through which machines communicate with each other. Examples of this include HTTP, FTP, HTTPS etc.

The shell, unlike the browser, allows you to interact with the computer directly. SSH will allow you to communicate directly with another computer, and SSH does so securely.

For example, you can ssh into a server hosted on Digital Ocean and make changes to that server.

ssh {user}@{host}

You may need to SSH into your computer remotely, or SSH into a server to make changes to your application.


##SSH - How it Works

###Symmetrical Encryption

ComputerA <-> ComputerB
Uses one secret key for encryption and decryption. ComputerA and ComputerB will have the same key, which encrypts and decrypts the message.

A Key Exchange Algorithm manages the Key, with the two computers sharing public data that corresponds to the key. The Key Exchange Algorithm relies on Asymmetrical Encryption.

###Asymmetrical Encryption
Assymetrical Encryption uses two separate keys, Public Keys and Private Keys. The Public Key shares a link to its corresponding Private Key. The Private Key can only mathematically compute its own Public Key.

The strength of the entire idea is that the Private Key is never shared. During an SSH connection, both parties create public and private keys and exchange them.

###Hashing
One-way hash functions are never meant to decrypt anything. The function will run through the input and convert it into gibberish. The gibberish will be sent along with information related to the transmission, and the receiving machine will run the same function and compare the values to determine if they match.