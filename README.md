# Fisco-Bcos & WeBASE-Front
作者: 深职院-符博<br>
本文内容: 通过WeBASE-Front中间件部署合约 并调用其自带接口WeBASE-Front/trans/handle发送交易


---------------------------------------
# Fisco-Bcos简介: <br>
FISCO BCOS是由国内企业主导研发、对外开源、安全可控的企业级金融联盟链底层平台，由金链盟开源工作组协作打造，并于2017年正式对外开源。
社区以开源链接多方，截止2020年5月，汇聚了超1000家企业及机构、逾万名社区成员参与共建共治，发展成为最大最活跃的国产开源联盟链生态圈。底层平台可用性经广泛应用实践检验，数百个应用项目基于FISCO BCOS底层平台研发，超80个已在生产环境中稳定运行，覆盖文化版权、司法服务、政务服务、物联网、金融、智慧社区等领域。<br>
官方网址：https://fisco-bcos-documentation.readthedocs.io/zh_CN/latest/docs/introduction.html

# WeBASE简介: <br>
WeBASE（WeBank Blockchain Application Software Extension） 是在区块链应用和FISCO-BCOS节点之间搭建的一套通用组件。围绕交易、合约、密钥管理，数据，可视化管理来设计各个模块，开发者可以根据业务所需，选择子系统进行部署。WeBASE屏蔽了区块链底层的复杂度，降低开发者的门槛，大幅提高区块链应用的开发效率，包含节点前置、节点管理、交易链路，数据导出，Web管理平台等子系统。<br>
官方网址: https://webasedoc.readthedocs.io/zh_CN/latest/docs/WeBASE/introduction.html

# WeBASE-Front简介: <br>
WeBASE-Front是和FISCO-BCOS节点配合使用的一个子系统。此分支支持FISCO-BCOS 2.0以上版本，集成web3sdk，对接口进行了封装，可通过HTTP请求和节点进行通信。另外，具备可视化控制台，可以在控制台上开发智能合约，部署合约和发送交易，并查看交易和区块详情。还可以管理私钥，对节点健康度进行监控和统计。<br>
官方网址: https://webasedoc.readthedocs.io/zh_CN/latest/docs/WeBASE-Front/README.html

# 使用说明
需提前在本地搭建一条4节点的FISCO-BCOS链 <br>官方文档教程: https://fisco-bcos-documentation.readthedocs.io/zh_CN/latest/docs/installation.html<br>
需提前搭建好WeBASE-Front中间件 <br> 官方文档教程: https://webasedoc.readthedocs.io/zh_CN/latest/docs/WeBASE-Front/install.html


# 1, 做好上述准备后,在浏览器中访问 WeBASE-Front
![image](https://user-images.githubusercontent.com/103564714/163139344-af2beea2-31c8-45ef-8d92-1966b0240cc1.png)

# 2, 编写智能合约，本文将用简单的领养宠物合约作为案例
![image](https://user-images.githubusercontent.com/103564714/163139750-94cb1cd5-5d4b-462f-98b4-425c671ec472.png)
![image](https://user-images.githubusercontent.com/103564714/163139781-7d914126-aaf2-4309-b282-38dd6695d225.png)

# 3, 保存编译部署合约成功后 会生成合约地址,合约名称，合约ABI等，在后续都将会用到(部署合约前，需在测试用户中创建用户)
![image](https://user-images.githubusercontent.com/103564714/163151209-f4375aae-8d10-4061-9000-bfef53be56be.png)

# 4, 在windows端打开IDEA并创建一个新的springboot项目 在pom.xml中导入hutool工具包
![image](https://user-images.githubusercontent.com/103564714/163153688-b2cd45b0-808c-446e-932a-489aa5067fee.png)
![image](https://user-images.githubusercontent.com/103564714/163153713-9a133b60-f18b-4129-bb94-95bd803f3e2e.png)

# 5, 在写后端接口前，先熟悉一下调用WeBASE-Front自带接口WeBASE-Front/trans/handle发送交易时所需的参数要求
![image](https://user-images.githubusercontent.com/103564714/163154396-8a02cdd3-b0d9-4982-85e3-5254c8db72af.png)
![image](https://user-images.githubusercontent.com/103564714/163154417-610a982d-4353-4b9b-bad4-c57263f0fd84.png)<br>
官方文档说明: https://webasedoc.readthedocs.io/zh_CN/latest/docs/WeBASE-Front/interface.html#id392

# 6, 根据合约内容去写后端调用的逻辑(这里只简单的测试两个登录和注册的功能)






