*Project16: implement sm2 2P decrypt with real network communication

202100460134
在SM2.cs内封装了SM2的加解密和签名及验签。
分别实现了客户端和服务端，服务端将发送用客户端提供的公钥加密的消息，最后由客户端解密。

如果不能（估计多半没有编译环境）编译C#源代码(codes.rar)，请直接使用提供的EXE文件(SM2_2P_Server/Client.rar)，该文件就是代码的生成可执行文件。
理论上在Windows X64环境下可以独立运行（Linux也许可以，作者没有测试但被声明可以运行），直接打开EXE即可。

操作流程：

先打开SM_2P_Server.exe再打开SM_2P_Client.exe。
启动后，客户端会向服务端直接发送公钥。
收到客户端发来的公钥后在服务端输入任意信息，然后回车发送。
服务端将使用收到的公钥加密信息再发送给客户端。
客户端解密密文还原信息再打印出来。
