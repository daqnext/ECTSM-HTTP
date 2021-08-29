## ECTSM
### elliptic curve &amp; time security message protocol

### check time before communication
```
before the communication the client must check server time 
to make sure the local time is within +/- 15 seconds
```


### message format:

#### 1.signature 
##### ``` signature : server-publickey(symmetric-key) and can be decoded from server side  ```
#### 2.encrypted content
##### ``` encrypted content:  symmetric-key(raw content) can be decoded from server side ```
#### 3.encrypted content header
##### 3.1 client side unix-time stamp in seconds [64 bits] '32bits is too small after year 2038 '
##### 3.2 message version definition 16 bytes [ascii string ]
###### ``` message version like 'meson.1.3.2'  ```
#### 4. content 
###### ``` content is whatever you like ```





