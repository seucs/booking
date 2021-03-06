##非功能性需求
####User interface and human factors
用户界面简洁易懂，做到用户不需要训练即可上手使用系统，在用户执行错误操作时提示错误并提醒修正，否则操作不能执行


####Documentation
提供网站操作的说明书以方便用户的操作，提供网站安全性相关文件让用户放心使用


####Hardware considerations
需要善于进行多线程处理的服务器以及较大的硬盘存储数据库中的内容，需要在多个地区进行镜像网站以保证各地区的连接速度和使用体验


####Performance characteristics
系统速度需要得到保证，要能在短时间内对用户做出的操作进行应答，使用户几乎不需等待即可进行下一步操作，数据大小有限制


####Error handling and extreme conditions
系统需要对错误能够做出及时的反应，防止数据丢失等严重问题发生


####System interfacing
系统的输入可以来自系统外部，输出可以到达系统外部，但都需要按照一定的格式需求


####Quality issues
要求系统的稳定性有保障，及时更新数据，遭遇错误时能在短时间内解决并恢复

####System Modifications
>系统易变性需求
1.设计的整个系统应该具有良好的可维护性和拓展性，功能之间耦合度较低
2.设计过程中采用前后端分离方式，保证前端的修改不影响后端服务变更
3.可变需求控制在前端页面和前后端数据传送方面，严格控制数据库结构不可变更

####Physical Environment
>物理环境需求
1.服务器选用宿舍闲置的电脑，操作系统为ubuntu1.4
2.异常情况状态概述：服务器发热温度过高，服务器连接外网网络异常，停电等状况
3.服务器使用云服务器进行热备


####Security Issues
>安全性问题
1.需要对用户的各类输入进行检测，避免非法数据和缓冲区溢出
2.数据库绑定本机ip，通过服务程序设置入口
3.用户登录设置安全cookie，并且限制cookie作用域，防止跨域访问
4.对请求响应的ip进行记录，限制访问次数
5.服务器端关闭各类无关的对外服务，避免服务攻击


####Resources and Management Issues 
>资源和管理问题
1.服务器数据进行定时备份，数据库视数据量而定，暂定备份时间为3到7天一次
2.配置备用服务器
3.数据备份记录备份时间，备份数据区域，和备份人员
4.服务器配置修改应该记录修改时间，修改内容，修改人员