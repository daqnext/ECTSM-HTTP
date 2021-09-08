## ECTSM

### 'elliptic curve & time security message protocol'
##### this is another secured communication protocal over http

![alt tag](https://github.com/daqnext/ECTSM/blob/main/concept_v1.0.0.png)


### server must provide 
 
```javascript
//http api 
'/etcminfo'
//with the following json response
{
    servertime: server-unix-time-stamp-seconds
    publickey: server's public key
}
```


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
#### 3.encrypted-content-header encrypted by client's symmetric key
##### 3.1 client side unix-time stamp in seconds  int64
##### 3.2 client's user token [optional]

#### 4. encrypted-content-body [optional]
###### ``` body is whatever you like ```


### server side time check
```
server should check 'client side unix-time' , this should be within +/- 30 seconds
to prevent replay attack
```

### server side user token check [optional]

### server side optimization 
####  server can cache a map of  [ signature => symmetric key ] to accelerate the decoding process





