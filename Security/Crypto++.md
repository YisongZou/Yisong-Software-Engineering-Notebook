### 1
```
linux环境下crypto++动态库生成与使用

cpp Crypto++ 库官方wiki:
https://www.cryptopp.com/wiki/Advanced_Encryption_Standard

cbc mode:
https://www.cryptopp.com/wiki/CBC_Mode

sha2:
https://www.cryptopp.com/wiki/Sha2

安装步骤：
下载cryptopp820.zip:
https://www.cryptopp.com/release820.html

解压后安装：（从make and install开始往下）
https://www.cryptopp.com/wiki/Linux

Makefile记得加：
g++  -g -o $@ $< -L/usr/local/lib/ -lcryptopp

```
