# SDU_Crypto_Homework_Group_66 

* 杜威完成的任务 

*Project1: implement the naïve birthday attack of reduced SM3

    ** 在实现生日攻击之前，我们需要进行以下几个操作：
            生成随机消息：使用Python的secrets模块和string模块生成随机的ASCII消息。
            计算哈希值：使用gmssl库中的sm3哈希函数计算消息的哈希值。
            验证碰撞：比较两个消息的哈希值是否相同，并确保这两个消息不相同。
    ** 对SM3函数进行了简化
            我直接截取其前32位。只关注SM3函数输出结果的前32位，而忽略了其余部分。
            SM3函数是一种哈希函数，用于将任意长度的输入消息映射为固定长度的哈希值，通常情况下，SM3函数的输出结果是一个256位的哈希值。
            通过截取SM3函数输出结果的前32位，保留了其中的一部分信息。这种简化会导致哈希值的冲突概率增加，因为截取后的哈希值空间较小。
            这也意味着不同的输入消息有可能产生相同的截断哈希值，从而降低了哈希函数的安全性和抗碰撞能力。
    ** 下面是生日攻击的实现步骤：
            Step 1: 引入所需的库和模块：导入random、secrets、string和gmssl的sm3模块，以及time模块。
            Step 2: 生成随机消息：编写generate_random_message()函数，生成随机的ASCII消息。
            Step 3: 计算哈希值：编写hash_message()函数，使用sm3哈希函数计算消息的哈希值。
            Step 4: 验证碰撞：编写verify_collision()函数，比较两个消息的哈希值是否相同，并确保这两个消息不相同。
            Step 5: 实施生日攻击：编写birthday_attack()函数，在一个循环中生成随机消息，并计算其哈希值。如果发现两个具有相同哈希值的不同消息，就验证碰撞并输出结果。
    ** 结果分析
            运行结果，碰撞已经找到了！这意味着在进行生日攻击时，你找到了两个不同的消息，它们经过SM3哈希函数处理后产生了相同的哈希值。
            这种攻击方法强调了哈希函数的抗碰撞能力，并展示了在特定条件下，找到碰撞的概率是多么高。

            
*Project2: implement the Rho method of reduced SM3

    ** 在实现Rho攻击之前，我们需要进行以下几个操作：
            生成随机消息：使用secrets模块和string模块生成随机的ASCII消息。
            计算哈希值：使用gmssl库中的sm3哈希函数计算消息的哈希值。
            验证碰撞：比较两个消息的哈希值是否相同，并确保这两个消息不相同。
    ** 实现步骤：
            引入所需的库和模块：导入secrets、string和gmssl的sm3模块，以及time模块。
            生成随机消息：编写generate_random_message()函数，生成随机的ASCII消息。
            计算哈希值：编写hash_message()函数，使用sm3哈希函数计算消息的哈希值。
            验证碰撞：编写verify_collision()函数，比较两个消息的哈希值是否相同，并确保这两个消息不相同。
            实施Rho攻击：编写rho_attack()函数，在一个循环中生成两个消息并计算它们的哈希值。如果发现两个具有相同哈希值的不同消息，就验证碰撞并输出结果。
    ** 结果分析：
            运行结果，如果发现两个具有相同哈希值的不同消息，说明成功找到了哈希碰撞。这表明在实施Rho攻击时
            通过生成随机消息并利用差分分析的方法，成功找到了具有相同哈希值的两个不同输入。


 *Project5: Impl Merkle Tree following RFC6962
 
     ** Merkle Tree实现的操作如下：
    	    构建Merkle Tree：根据数据块构建Merkle Tree的树状结构。这个过程通常需要对数据块进行哈希计算，并逐层构建树节点。
    	    验证数据完整性：通过计算根哈希并与预期的根哈希进行比较，验证数据集的完整性。
    	    检索被修改的数据块：如果数据集中的数据块被修改，Merkle Tree可以快速定位并检索被修改的数据块。
    ** 实现步骤
    	    定义日志条目（LogEntry）类，用于表示Merkle Tree中的叶节点。每个日志条目包含索引和数据块。
    	    定义哈希函数，用于计算叶节点和节点的哈希值。
    	    实现构建Merkle Tree的函数（construct_merkle_tree）。该函数接受日志条目列表作为输入，并按照RFC 6962的要求构建Merkle Tree的树状结构。
    	    实现验证数据完整性的函数（verify_integrity）。该函数接受日志条目列表和预期的根哈希作为输入，并通过构建Merkle Tree并比较根哈希来验证数据的完整性。
    	    实现检索被修改的数据块的函数（retrieve_modified_data）。该函数接受日志条目列表和根哈希作为输入，然后返回对应的被修改的数据块。
    ** 结果分析
        	通过构建Merkle Tree和实现相应的功能函数，我们可以实现数据完整性验证和检索被修改的数据块。
            在这个示例中，被修改的数据块是在日志条目列表中的第二个条目（索引为1）被修改为'modified block2'。
            通过检索被修改的数据块函数，我们成功地检测到了这个修改，并返回了被修改的数据块。


 *Project9: AES software implementation
 
    ** OFB工作模式:我们在实现过程中加入了OFB工作模式， OFB（Output Feedback）是一种AES工作模式。
            它将前一个加密块的输出作为输入来加密下一个块，并使用一个初始化向量（IV）来启动加密过程。
            它以流密码的方式产生密钥流，然后将密钥流与明文进行异或操作以生成密文。    
    ** 代码实现思路与过程:
            定义明文字符串，并将其转换为适合AES加密算法的字节序列形式。
            实现AES加密算法，包括密钥扩展和轮加密操作。
            实现OFB工作模式，生成初始化向量（IV）和密钥流。
            将密钥流与转换后的明文进行异或操作，生成密文。
            实现AES解密算法，包括密钥扩展和逆轮加密操作。
            使用解密后的密文和生成的密钥流进行异或操作，解密得到明文。
            将解密后的明文再次转换为自定义语言形式，如解码为原始字符串。
    

*Project13: Implement the above ECMH scheme

    ** ECMH方案支持以下操作：	
    	验证数据：使用公钥验证多重集合中的数据和对应的签名是否有效。
    	合并多重集合：参与方可以将自己的多重集合与其他多重集合合并，生成一个新的多重集合。
    	计算多重集合哈希：对多重集合的数据进行哈希计算，生成多重集合的哈希值。
    ** 实现步骤
    	生成私钥和公钥：每个参与方生成自己的私钥和公钥对。
    	添加数据：参与方使用私钥对数据进行签名，并将签名后的数据添加到自己的多重集合中。
    	验证数据：其他参与方可以使用公钥验证多重集合中的数据和对应的签名是否有效。
    	合并多重集合：参与方可以将自己的多重集合与其他多重集合合并，生成一个新的多重集合。
    	计算多重集合哈希：对多重集合的数据进行哈希计算，生成多重集合的哈希值。
    ** 结果分析
    	在实例中，Signature1 is valid: True 和 Signature2 is valid: True 表明添加的数据和对应的签名验证都是有效的，说明签名和验证功能正常。
    	Combined Multiset Hash 是合并后的多重集合的哈希值，它是两个多重集合哈希值的加法运算结果，验证了合并操作的正确性。
    	最后，输出 Homomorphic property is verified. 表示同态性质验证通过，验证了该 ECMH 方案在合并多重集合时保持了同态性质。





*Project17：Imple Google Password concept 

      ** 实现的操作:
              处理数据信息：对data_records中的用户名和密码进行哈希，并生成对应的key-value表和分割的集合。
              用户名和密码检查：当用户输入用户名和密码时，客户端计算其哈希值，并生成临时密钥sk。然后计算key和value。
              查找数据集：根据key在分割的集合中找到对应的数据集。
              用户名和密码检测：计算h^ab和h^b，并检查h^b是否存在于数据集中。
      ** 实现步骤:
              创建一个data_records字典，存放用户名和密码的哈希值。
              生成服务器的私密参数b。
              处理数据信息：对data_records中的用户名和密码进行哈希，生成key-value表和分割的集合。
              客户端输入用户名和密码，生成临时密钥sk，计算key和value。
              查找数据集：根据key在分割的集合中找到对应的数据集。
              计算h^ab和h^a，并检查h^b是否存在于数据集中。
              输出结果，告知用户用户名和密码是否存在于已泄露的数据库中。
      ** 结果分析: 
              设置要验证的用户名和密码，例如 username = "user1" 和 password = "password1"。
              调用 check_username_password(username, password) 函数，传入用户名和密码进行验证。
              返回值为 True，即用户名和密码存在于已泄露的数据库中，则输出 "用户名和密码存在于已泄露的数据库中。"。



 *Project20: ECMH PoC
 
     该实验与project 13 重复，不再赘述

     
李旷达完成的任务如下：
*Project4: do your best to optimize SM3 implementation (software)

*Project11: impl sm2 with RFC6979
   
      complete submission是所有工作量的集合版，由于是分功能实现SM2相关的部件，所以进行的了分块的提交。 
    首先对于SM体系下的椭圆曲线加解密体系，实现了一个ECC—class,椭圆曲线密码类（实现一般椭圆曲线的运算，不局限于SM2）。
    对于SM2-class，则是调用了ECC—class作为底层运算部件，根据RFC6979协议标准实现。该方案进行了基础性的ECDH正确性测试，SM2密钥协商测试，SM2数字签名与验证测试，测试过程均在key-Enc-test文件中可运行。
    最后main_part运行结果，可复现RFC6979，SM2文档中的示例结果（达到要求）
    备注：若要完整运行测试代码还需安装gmssl（pip install gmssl）和pysmx（pip install snowland-smx）。

*Project19: forge a signature to pretend that you are Satoshi
       
       关于Attack_process文件是进行攻击的具体实行，进行签名伪造，伪造自己的身份为Satoshi
       而testing文件则是用于签名伪造结果的验证，检测攻击是否成功
       而ECDSA.py文件则是一个通用的ECC椭圆曲线加密的模型代码
       运行代码之前需要在pycharm中安装ecdsa与hashlib两个库文件进行调用，才能正常运行！

*Project22: research report on MPT  

杨昊（202100460134）：

*Project15: implement sm2 2P sign with real network communication

      可执行文件一并上传了。
      过程：
            利用Bouncy Castle提供的椭圆曲线基本方法和SM2相关参数封装了SM2的加密解密和签名验签，对应SM2.cs文件。
            客户端和服务端则利用.NetFrameWork .NetCore自带的套接字实现。
            1.服务端计算P1=di^(-1)*G并发送给客户端。
            2.客户端收到P1，计算公钥P=d2^(-1)*P1-G
            3.服务端发送的的消息是M，选取Z并计算e=Hash(Z||M)，生成k1并计算Q1=k1*G。发送Q1和e。
            4.客户端计算Q2=k2*G，（x1,y1)=k3*Q1+Q2。生成签名r=x1+e(mod n)(r!=0)，计算s2=d2*k3(mod n)，s3=d2*(r+k2)(mod n)。发送r，s2，s3。
            5.服务端计算s=(d1*k1)*s2+d1*s3-r(mod n)。根据s的结果输出最终签名(r,s)。
      结果：
            CPU 11th Gen Intel(R) Core(TM) i5-11300H @ 3.10GHz
            加密或者解密的运行耗时均不足10ms。
      
*Project16: implement sm2 2P decrypt with real network communication
      
      可执行文件一并上传了。
      过程：
            利用Bouncy Castle提供的椭圆曲线基本方法和SM2相关参数封装了SM2的加密解密和签名验签，对应SM2.cs文件。
            客户端和服务端则利用.NetFrameWork .NetCore自带的套接字实现。
            1.客户端通过套接字向服务端发送自己生成的公钥。
            2.服务端利用套接字接受公钥并用该公钥加密要传递的信息。
            3.客户端收到密文，用自己公钥对应的私钥进行解密得到明文。
      结果：
            CPU 11th Gen Intel(R) Core(TM) i5-11300H @ 3.10GHz
            加密或者解密的运行耗时均不足10ms。
