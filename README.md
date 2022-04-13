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
