## 以太坊客户端

> 以太坊客户端是实现以太坊规范并通过对等网络与其他以太坊客户端进行通信的软件应用程序。

以太坊是一个_open source_项目，这也意味着以太坊由一个开放的志愿者社区开发，任何人都可以修改。由名为“黄皮书”的正式规范定义,不同的以太坊客户端如果符合参考规范和标准化通信协议，就可以互操作，虽然这些不同的客户端由不同的团队和不同的编程语言实现.

## 以太坊网络

存在各种基于以太坊的网络，这些网络很大程度上符合以太坊“黄皮书”中定义的正式规范，但它们可能或不能互操作。

在这些以太坊网络中有：Ethereum，Ethereum Classic，Ella，Expanse，Ubiq，Musicoin等等。虽然大多数在协议级别上兼容，但这些网络通常具需要以太坊客户端软件维护人员进行微小更改以支持每个网络的功能或属性。因此，并非以太坊客户端软件的每个版本都可以在每个以太坊区块链上运行。

区块链的健康，弹性和抗审查取决于拥有有多少独立运营和地理上分散的完整节点。每个完整节点都可以帮助其他新节点获取块数据以引导其操作，并为运营商提供对所有交易和合约的权威和独立验证。

## 基于以太坊的区块链首次同步

通常，在同步以太坊区块链时，你的客户端将下载并验证自创世区块以来的每个区块和每个交易。大多数以太坊客户端包括一个选项，可以执行“快速”同步，跳过交易的完整验证，同步到区块链的顶端后，再恢复完整验证。

## JSON-RPC接口

以太坊客户端提供应用程序编程接口（API）和一组远程过程调用（RPC）命令，这些命令被编码为JavaScript对象表示法（JSON）。这被称为_JSON-RPC API_。本质上，JSON-RPC API是一个接口，允许我们将使用以太坊客户端的程序作为_gateway_编写到以太坊网络和区块链中。

通常，RPC接口作为端口+8545+上的HTTP服务提供。出于安全原因，默认情况下，它仅受限于从本地主机（你自己的计算机的IP地址为+127.0.0.1+）接受连接。

要访问JSON-RPC API，可以使用专门的库，用你选择的编程语言编写，它提供与每个可用的RPC命令相对应的“桩（stub）”函数调用。或者，你可以手动构建HTTP请求并发送/接收JSON编码的请求。你甚至可以使用通用命令行HTTP客户端（如 curl ）来调用RPC接口。

[JSON-RPC 2.0规范格式化]( http://www.jsonrpc.org/specification)