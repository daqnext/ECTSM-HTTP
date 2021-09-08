## ECTSM

### 'elliptic curve & time security message protocol'
##### this is another secured communication protocal over http

![alt tag](https://github.com/daqnext/ECTSM/blob/main/concept_v1.0.0.png)


### server must provide 
#### 1. http interface '/server_publickey'
#### 2. http interface '/server_unixtime'


### check time before communication
```
before the communication the client must check server time ['/server_unixtime'] 
to make sure the local time is within +/- 15 seconds compared with server
if not , please stop and adjust client side clock
```

### message format:

#### 1.signature 
##### ``` signature : server-publickey(symmetric-key) and can be decoded from server side  ```
##### ``` public-private-key using elliptic curve secp256k1 ```
#### 2.encrypted-content
##### ``` encrypted content:  symmetric-key(raw content) can be decoded from server side ```
##### ``` AES (Advanced Encryption Standard) used for symmetric encryption/decryption ```
#### 3.encrypted-content-header
##### 3.1 client side unix-time stamp in seconds [64 bits] '32bits is too small after year 2038 '
##### 3.2 message version definition 16 bytes [ascii string ]
###### ``` message version like 'meson.1.3.2'  ```
#### 4. encrypted-content-body 
###### ``` body is whatever you like ```


### server side time check
```
server should check 'client side unix-time' , this should be within +/- 30 seconds
to prevent replay attack
```





