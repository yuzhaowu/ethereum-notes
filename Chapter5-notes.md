## 密钥，地址

### 简介

> EOAs中以太的所有权通过 *数字密钥* *digital keys*，*以太坊地址_和_数字签名* 建立 。数字密钥实际上并不存储在区块链中或在以太坊网络上传输，而是由用户创建并存储在文件或称为_钱包_的简单数据库中。用户钱包中的数字密钥完全独立于以太坊协议，可以由用户的钱包软件生成和管理，无需参考区块链或访问互联网。
>
> 以太坊交易需要将有效的数字签名包含在区块链中，该签名只能使用密钥生成；因此，任何拥有该密钥副本的人都可以控制ether。以太坊交易中的数字签名证明了资金的真正所有者。

### 私钥

> 生成密钥的第一步也是最重要的一步是找到一个安全的熵源或随机源。创建以太坊私钥基本上与“选择1到2256之间的数字”相同。只要不可预测和不可重复，用于选择该数字的确切方法并不重要。
>
> 在以太坊中，私钥可以是+1+和+n-1+之间的任何数字，其中n是定义为使用的椭圆曲线的阶数的常数（n = 1.158*1077，略小于2256）（参见[椭圆曲线密码学解释](https://github.com/inoutcode/ethereum_book/blob/master/第五章.asciidoc#elliptic_curve)）。为了创建这样的密钥，我们随机选择一个256位数字并检查它是否小于+n-1+。在编程方面，这通常是通过将从密码学安全的随机源收集的更大的随机比特串提供给256位哈希算法（如Keccak-256或SHA256）（参见 [[cryptographic_hash_algorithm\]](https://github.com/inoutcode/ethereum_book/blob/master/第五章.asciidoc#cryptographic_hash_algorithm)），产生一个256位数字。
>
> Tip:
>
> 不要编写自己的代码来创建随机数或使用你的编程语言提供的“简单”随机数发生器。使用密码学安全的伪随机数字发生器（CSPRNG）和来自足够熵源的种子。

### 公钥

> 以太坊公钥是一个椭圆曲线上的_点_ *point*，意思是它是一组满足椭圆曲线方程的X和Y坐标。简单来说，以太坊公钥是两个数字，并联在一起。这些数字是通过一次单向的计算从私钥生成的。
>
> Tip:
>
> 椭圆曲线乘法是密码学家称之为“单向”函数的一种函数：在一个方向（乘法）很容易完成，而在相反方向（除法）不可能完成。私钥的所有者可以很容易地创建公钥，然后与世界共享，因为知道没有人能够反转该函数并从公钥计算私钥。这种数学技巧成为证明以太坊资金所有权和合同控制权的不可伪造和安全数字签名的基础。

### 加密哈希函数

> 哈希函数是可用于将任意大小的数据映射到固定大小的数据的函数
>
> 加密哈希函数有五个主要属性 ([Source: Wikipedia/Cryptographic Hash Function](https://en.wikipedia.org/wiki/Cryptographic_hash_function)):
>
> - 确定性
>
>   任何输入消息总是产生相同的哈希摘要。
>
> - 可验证性
>
>   计算消息的哈希是有效的（线性性能）。
>
> - 不相关
>
>   对消息的小改动（例如，一位改变）会大幅改变哈希输出，以致它不能与原始消息的哈希相关联。
>
> - 不可逆性
>
>   从哈希计算消息是不可行的，相当于通过可能的消息进行蛮力搜索。
>
> - 碰撞保护
>
>   计算两个不同的消息产生相同的哈希输出应该是不可行的。

### 以太坊地址

> *唯一标识符* *unique identifiers*，它们是使用单向哈希函数（Keccak-256）从公钥或合约派生的。
>
> #### 格式
>
> > 以太坊地址是十六进制数字，从公钥的Keccak-256哈希的最后20个字节导出的标识符。以原始十六进制形式呈现，没有任何校验和。该决定背后的基本原理是，以太坊地址最终会隐藏在系统高层的抽象（如名称服务）之后，并且必要时应在较高层添加校验和。

