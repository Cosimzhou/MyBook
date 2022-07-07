信息安全笔记
============

# RSA算法

RSA算法涉及三个参数，$n,e_1,e_2$。

其中，$n$是两个大质数$p,q$的积，$n$的二进制表示时所占用的位数，就是所谓的密钥长度。

$e_1$和$e_2$是一对相关的值，$e_1$可以任意取，但要求$e_1$与$(p-1)(q-1)$互质；再选择$e_2$，要求$(e_2\times e_1)\equiv (\mod(p-1)\times(q-1))$。

$(n,e_1),(n,e_2)$就是密钥对。其中$(n,e_1)$为公钥，$(n，e_2)$为私钥。

RSA加解密的算法完全相同，设$A$为明文，$B$为密文，则：$A\equiv B^e2( mod n)$；$B\equiv A^e1 (mod n)$；（公钥加密体制中，一般用公钥加密，私钥解密）

$e_1$和$e_2$可以互换使用，即：

$A\equiv B^{e_1} (\mod n)\quad B\equiv A^{e_2}(\mod n);$

例如，$p=11,q=23,n=253$；可以取$e_1=13,e_2=17$，这时$(253,13)$为公钥，$(253,17)$为私钥。

比如数据为100，加密过程为：$100^{17}(\mod 253)\equiv 243$，即密文为243；

解密过程为：$243^{17}(\mod 253)\equiv 100$，即解密得的明文为100。


# 椭圆曲线算法

在椭圆曲线加密（ECC）中，利用了某种特殊形式的椭圆曲线，即定义在有限域上的椭圆曲线。其方程如下：

$y^2=x^3+ax+b(\mod p)$

这里$p$是素数，$a$和$b$为两个小于$p$的非负整数，它们满足：

$4a^3+27b^2(\mod p)\neq 0$ 其中，$x,y,a,b\in F_p$，则满足式(2)的点$(x,y)$和一个无穷点O就组成了椭圆曲线$E$。

椭圆曲线离散对数问题ECDLP定义如下：给定素数$p$和椭圆曲线$E$，对 $Q=kP$,在已知$P,Q$的情况下求出小于$p$的正整数$k$。可以证明，已知$k$和$P$计算$Q$比较容易，而由$Q$和$P$计算$k$则比较困难，至今没有有效的方法来解决这个问题，这就是椭圆曲线加密算法原理之所在。


# 常见的数字证书格式

|           | 二进制 | 支持证书 | 保存私钥 | 密码保护 | 应用场景 | 详情命令 |
| --------- | ------ | -------- | -------- | -------- | -------- | -------- |
| .der/.cer |   是   |     是   |     否   |     否   | Java和Windows环境 | `openssl x509 -inform der -text -noout -in x.der` |
| .crt      |   可   |     是   |     否   |     否   | 同pem | 同pem或der|
| .pfx/.p12 |   是   |     是   |     是   |     是   | IIS服务器 | `openssl pkcs12 -in for-iis.pfx` |
| .p7b      |   是   |     是   |     是   |     是   | | |
| .jks      |   是   |     是   |     是   |     是   | Tomcat服务器 | |
| .pem      |   否   |     是   |     可   |     可   | Apache或Nginx服务器 | `openssl x509 -text -noout -in x.pem` |
| .crl      |   是   |     否   |     否   |     否   | 证书吊销列表 | |
| .csr      |   否   |     -    |     -    |     -    | 证书签署申请| |


# 常见的证书规范
| 选项     | 含义          |
| -------- | ------------- |
| x500     | 是一套已经被国际标准化组织（ISO）接受的目录服务系统标准，它定义了一个机构如何在全局范围内共享其名字和与之相关的对象 |
| x509     | 公钥证书，只有公钥。 |
| pkcs7    | 签名或加密。可以往里面塞x509，同时没有签名或加密内容。 |
| pkcs8    | 描述私有密钥信息格式，该信息包括公开密钥算法的私有密钥以及可选的属性集等。 |
| pkcs12   | 含有私钥，同时可以有公钥，有口令保护。 |
| pkcs1    | 定义RSA公开密钥算法加密和签名机制，主要用于组织PKCS#7中所描述的数字签名和数字信封。|
| pkcs3    | 定义Diffie-Hellman密钥交换协议。|
| pkcs5    | 描述一种利用从口令派生出来的安全密钥加密字符串的方法。使用MD2或MD5 从口令中派生密钥，并采用DES-CBC模式加密。主要用于加密从一个计算机传送到另一个计算机的私人密钥，不能用于加密消息。|
| pkcs6    | 描述了公钥证书的标准语法，主要描述X.509证书的扩展格式。|
| pkcs7    | 定义一种通用的消息语法，包括数字签名和加密等用于增强的加密机制，PKCS#7与PEM兼容，所以不需其他密码操作，就可以将加密的消息转换成PEM消息。|
| pkcs8    | 描述私有密钥信息格式，该信息包括公开密钥算法的私有密钥以及可选的属性集等。|
| pkcs9    | 定义一些用于PKCS#6证书扩展、PKCS#7数字签名和PKCS#8私钥加密信息的属性类型。|
| pkcs10   | 描述证书请求语法。|
| pkcs11   | 称为Cyptoki，定义了一套独立于技术的程序设计接口，用于智能卡和PCMCIA卡之类的加密设备。|
| pkcs12   | 描述个人信息交换语法标准。描述了将用户公钥、私钥、证书和其他相关信息打包的语法。|
| pkcs13   | 椭圆曲线密码体制标准。|
| pkcs14   | 伪随机数生成标准。|
| pkcs15   | 密码令牌信息格式标准。|


# openssl

# 证书查看：
openssl x509    -in x.der -text -noout -inform der
openssl x509    -in x.pem -text -noout
openssl pkcs12  -in x.pfx
openssl rsa     -in x.pem -text -noout


# 证书互转：
openssl x509   -in cert.crt -out Cert.pem -outform pem -inform der
openssl x509   -in cert.crt -out Cert.der -outform der
openssl pkcs12 -in cert.pfx -out Cert.pem -nodes


# 创建证书请求CSR：
openssl req -new -out ca-req.csr -key ca-key.pem [-config openssl.cnf]

# CSR认证：
openssl x509 -req -in cert.csr       -out Cert.crt        -signkey private.key    -days 1800
openssl x509 -req -in server-req.csr -out server-cert.pem -signkey server-key.pem -days 365 -CA ca-cert.pem -CAkey ca-key.pem -CAcreateserial #CA认证证书



```bash
# RSA加解密实例
# 生成一个密钥：
openssl genrsa -out test.key 1024

# 提取公钥：
openssl rsa -in test.key -pubout -out test_pub.key

# 公钥加密：
openssl rsautl -encrypt -in hello.txt -inkey test_pub.key -pubin -out hello.en
#-in指定要加密的文件，-inkey指定密钥，-pubin表明是用纯公钥文件加密，-out为加密后的文件。

# 私钥解密：
openssl rsautl -decrypt -in hello.en -inkey test.key -out hello.de
```
