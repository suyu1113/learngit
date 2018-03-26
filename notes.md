技术相关
========

Yes ilike

20180326 1024

解析优先级
----------

浏览器缓存\--》本地host解析\--》网络dns解析

注意：在访问过生产环境的浏览器上做提交类压测时，需要注意清空浏览器缓存，以防因上面的现象导致测试数据提交生产

F12
---

查看错误

从生产获取json构造数据：

【20171130 数据魔方
测试数据构造dayline】通过network抓取请求（关键词"dailyLine"），将数据获取json链接（http://three.cninfo.com.cn/data/cube/dailyLine?stockCode=000031）复制出来\-\--粘贴在ie浏览器，提示保存为json文件\--在原网页设置断点\--刷新页面\--赋值（将保存到的json文件的字符值赋给断点定义的变量）\--执行下一步\--查看效果

快捷键
------

Alt键调整出浏览器的菜单栏 {#alt键调整出浏览器的菜单栏 .ListParagraph}
-------------------------

F5-强刷

Ctrl+shift+delete 快速调出清楚缓存窗口

**应用程序需要以管理员权限运行时**
----------------------------------

[[https://jingyan.baidu.com/article/0bc808fc68f3c11bd485b9b3.html]{.underline}](https://jingyan.baidu.com/article/0bc808fc68f3c11bd485b9b3.html)

超级棒的使用方法**-**loadrunner多个场景执行顺序
-----------------------------------------------

20171215 该应用为亮点可推广 遇到的问题：

-   设定想要的基础数据\--合适的场景（常用的模式是
    顺序压完单场景后执行组合场景，估第一个场景为顺序执行的场景，第二个为混合场景）

-   Controller需要管理员权限而有的是普通用户\--参考（四），属性-勾选"以管理员权限运行"-应用-确定

-   启动Controller后有弹窗提示\--点击查看详情-更改级别

-   结果第二个场景覆盖第一个场景\--为每个场景设定result
    setting为自动生成新的文件，并给默认结果名称设定为对应场景的名称

    至此，实验成功。

-   遗留问题\-\-\--顺序执行的脚本场景的结果是一份，如果要求每个脚本的图形该怎么办？

http://blog.csdn.net/he\_jian1/article/details/41722427

**应用场景**\
假设有3个不同的测试场景，分别为并发登录、核心业务、可靠性测试，3个场景有先后执行顺序。由于白天测试机器另有用处，只能在晚上进行性能测试，这时我们的期望是能否把测试场景都设定好之后晚上自动运行，第二天我们回来看测试结果呢？\
答案是肯定的，可以有两种方式实现。

**第一种，相对简单\
**充分利用LR Controller里面Group的功能。\
新建一个场景把3个脚本都添加进来，在Edit Schedule中选择"Schedule by
Group"的方式，在StartTime中设置3个脚本的运行顺序为"Start when Group xxx
finished"，并在"Scenario Start
Time"中设定场景在晚上的运行启动时间。设定完定时执行场景后，点击StartScenario按钮，会出现一个倒计时窗口，这样在固定的某个时间上，测试场景中的3个脚本将乖乖的按照设定的先后顺序进行测试。注意，如果没有点击StartScenario按钮激活测试，是不会真正进行测试的。（感谢Athenst朋友的提醒，\^\_\^）

**第二种，比较灵活\
**我们把应用场景稍微扩展一下，假设其中1、3场景只有一个测试脚本，而核心业务场景由数据录入、数据查询、数据上报3个脚本组成，同样的，3个场景仍需按顺序进行测试。这时如果采用第一种方式，由于第2个场景有3个脚本，所以第三个脚本的启动时间就是一个问题了。由于Controller中每个脚本都对应一个Group，而且GroupName不能重复，这时第三个场景的StartTime中"Start
when group
finished"则只能是选择第二个场景中的某个Group，而并非是第二个场景的3个脚本都完成之后再进行，无法达到我们的初衷。\
这时，可以通过命令行的方式来进行。\
首先创建并设置好3个测试场景，再创建一个一个批处理程序按先后顺序调用这3个场景进行测试，最后通过Windows的定时任务设定批处理的执行时间。\
**批处理**示例如下：\
cls\
SET M\_ROOT=\"D:\\Program Files\\MI\\Mercury LoadRunner\\bin\\\"\
%M\_ROOT%\\wlrun.exe -TestPath \"D:\\Program Files\\MI\\Mercury
LoadRunner\\scenario\\Test\\TestScen\_1.lrs\" -Run\
%M\_ROOT%\\wlrun.exe -TestPath \"D:\\Program Files\\MI\\Mercury
LoadRunner\\scenario\\Test\\TestScen\_2.lrs\" -Run\
%M\_ROOT%\\wlrun.exe -TestPath \"D:\\Program Files\\MI\\Mercury
LoadRunner\\scenario\\Test\\TestScen\_3.lrs\" -Run\
这种方式比较灵活，但需要注意在Result　Settings中设置"Automatically
create a results directory for each scenario
execution"，以免后面的测试结果覆盖了前面的。

另外补充一下，如果想对某个脚本进行50、100、150\...等用户数递增的测试，也可以用以上方法实现，但需要注意的是将事务名称区分开以便进行分析。

 {#section .ListParagraph}

Linux 高并发命令 ab命令
-----------------------

ab（apache bench）是apache下的一个工具，主要用于对web站点做压力测试，\
\
基础用法：ab -c 500 -n 1000
[[http://www.baidu.com]{.underline}](http://www.baidu.com) \
其中-c选项为一次发送的请求数量，及并发量。\
-n选项为请求次数。

![](media/image1.png){width="4.675in" height="5.543055555555555in"}

接口数据
--------

自动化测试
----------

### RobotFrame RIDE

#### 常用快捷键：

ctrl+alt+空格 自动带出相关关键字

F5 查询关键字

F8 运行脚本

Ctrl+鼠标悬浮 关键字相关用法

性能测试相关
------------

出入参，数据量-基础数据和使用数据，性能指标

2.  ### Jconsole \-\--Java 自带性能监控工具

3.  ### Jvisualvm

JDK
自带的jvisualvm监控工具能有效的帮助我们监控Java应用程序运行过程中占用消耗的CPU

### Jvm

JVM 堆内存划分为**年轻代**和**年老代**，JVM
年老代与年轻代的比例（**XX:NewRatio**)为
**2**，这个比例并不适合所有情况，特别是当你的应用里局部变量远远大于全局变量，而且大量局部变量生命周期都很短的时候。如何根据应用实时的运行运行情况合理配置年轻代(Young
Generation，即 Eden 区和两个 Survivor 区之和)和年老代(Old Generation，即
Tenured 区)的比例 XX:NewRatio 值？

附注：JVM
堆内存平均分成了三份，年老大占用了两份，而年轻代占用一份。参考资料 Sun
Java System Application Server Enterprise Edition 8.2 Performance Tuning
Guide

### LR

#### 使用记录

##### 参数化支持20w数据：

【20171221】发现unique+each itea+abort user是个冒险的活\
会自动将   20w数据/并发用户数 为块 分配给 虚拟用户   如我设定1000的并发  vuser就只有1-200（200000/1000）vusr2就是201-400\
所以如果并发用户是梯形上升  很可能1000并发没加载完就已经报错abort了

修改参数化可见大小在vugen.ini中修改

##### 添加oracle监控

-   前提

    在Controller所在的机器上安装Oracle客户端，然后配置好服务名（tns路径，一般在%ORACLE\_HOME%\\network\\admin\\tnsnames.ora），用sqlplus确认可以连接Oracle\--需要知道oracle
    ip、端口、severname、用户名、密码（需要什么权限的用户）

-   监控指数：

自定义增加指数:在安装路径的Mercury
LoadRunner\\dat\\monitors找到vmon.cfg文件

![](media/image2.png){width="5.767361111111111in"
height="6.457638888888889in"}

（详见http://blog.csdn.net/zouxiongqqq/article/details/50113777）

-   常用监控指标

在监视Oracle服务器（从V\$ SYSSTAT表）时，最常使用下列度量：

  --------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **度量**                                      **描述**
  **CPU used by this session**                  这是在用户调用开始和结束之间会话所占用的 CPU 时间（以 10 毫秒为单位）。一些用户调用在 10 毫秒之内即可完成，因此用户调用的开始和结束时间可以是相同的。在这种情况下，统计值为 0 毫秒。操作系统报告中可能有类似的问题，尤其是在经历许多上下文切换的系统中。
  **Bytes received via SQL\*Net from client**   通过 Net8 从客户端接收的总字节数。
  **Logons current**                            当前的登录总数。
  **Opens of replaced files**                   由于已经不在进程文件缓存中，所以需要重新打开的文件总数。
  **User calls**                                在每次登录、解析或执行时， Oracle 会分配资源（Call State 对象）以记录相关的用户调用数据结构。在确定活动时，用户调用与 RPI 调用的比说明了因用户发往 Oracle 的请求类型而生成的内部工作量。
  **SQL\*Net roundtrips to/from client**        发送到客户端和从客户端接收的 Net8 消息的总数。
  **Bytes sent via SQL\*Net to client**         从前台进程中发送到客户端的总字节数。
  **Opened cursors current**                    当前打开的光标总数。
  **DB block changes**                          由于与一致更改的关系非常密切，此统计数据计算对SGA 中所有块执行的、作为更新或删除操作一部分的更改总数。这些更改将生成重做日志项，如果事务被提交，将是对数据库的永久性更改。此统计数据是一个全部数据库作业的粗略指示，并且指出（可能在每事务级上）弄脏缓冲区的速率。
  **Total file opens**                          由实例执行的文件打开总数。每个进程需要许多文件（控制文件、日志文件、数据库文件）以便针对数据库进行工作。
  --------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

#####  操作oracle

-   使用webservise协议

操作：[[https://www.cnblogs.com/sinozhou/archive/2013/03/05/2944373.html]{.underline}](https://www.cnblogs.com/sinozhou/archive/2013/03/05/2944373.html)

脚本说明：结合web协议将慢sql写入文本中

常见两个错误及解决办法： http://doc.okbase.net/qyxa/archive/15076.html

在Loadrunner中也提供了C对数据库操作的相关功能函数，以下这些数据库功能函数只能用于**Web
Services协议。**

  ----------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------
  [lr\_db\_connect](mk:@MSITStore:C:\\Documents and Settings\\Administrator\\Desktop\\vuser_utils_FuncRef.chm::/lr_db_connect.html)                           连接数据库
  [lr\_db\_disconnect](mk:@MSITStore:C:\\Documents and Settings\\Administrator\\Desktop\\vuser_utils_FuncRef.chm::/lr_db_disconnect.html)                     断开数据库的连接
  [lr\_db\_executeSQLStatement](mk:@MSITStore:C:\\Documents and Settings\\Administrator\\Desktop\\vuser_utils_FuncRef.chm::/lr_db_executeSQLStatement.html)   执行SQL语句
  [lr\_db\_dataset\_action](mk:@MSITStore:C:\\Documents and Settings\\Administrator\\Desktop\\vuser_utils_FuncRef.chm::/lr_db_dataset_action.html)            对数据库执行操作
  [lr\_db\_getValue](mk:@MSITStore:C:\\Documents and Settings\\Administrator\\Desktop\\vuser_utils_FuncRef.chm::/lr_db_getValue.html)                         从数据集中检索值
  ----------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------

各函数语法如下：

lr\_db\_connect(\"StepName\",
\"ConnectionString=\<connection\_string\>\",
\"ConnectionName=\<connection\_name\>\",
\"ConnectionType=\<connection\_type\>\", LAST);

lr\_db\_disconnect(\"StepName=\<step\_name\>\",
\"ConnectionName=\<connection\_name\>\", LAST);

lr\_db\_executeSQLStatement(\"StepName=\<step\_name\>\",
\"ConnectionName=\<connection\_name\>\", \"SQLStatement=\<statement\>\",
\[\"DatasetName=\<dataset\_name\>\",\] LAST);

lr\_db\_dataset\_action(\"StepName=\<step\_name\>\",
\"DatasetName=\<dataset\_name\>\", \"Action=\<action\>\", LAST);

lr\_db\_getValue(\"StepName=\<step\_name\>\",
\"DatasetName=\<dataset\_name\>\", \"Column=\<column\>\",
\"Row=\<row\>\", \"OutParam=\<output\_parm\>\", LAST);

 

#####  使用atof函数

使用的时候不先在脚本中先定义声明的话，返回的浮点数与正确的字符转译的浮点数会不同。

不声明前无论什么字符转译都是0，声明后浮点数转换正确

同理
atol函数也需要先显性声明才能使用，在lr的函数帮助文档中有说明"不返回整数的函数，需要在脚本中显性声明才能使用"

因为float，[double]{.underline}型在不同的平台下长度不一样，所以在loadrunner中调用[atof]{.underline}需要显式的声明这个函数。

如下：

doubleatof (const char \*string);

#### 常见错误

##### Error -27796

Failed to connect to server \"10.2.9.147:80\":
\[10048\]（服务器ip和端口）

[[https://jingyan.baidu.com/article/60ccbceb42720264cab197fa.html]{.underline}](https://jingyan.baidu.com/article/60ccbceb42720264cab197fa.html)

#####  LoadRunner**性能测试问题集锦**

[[http://blog.csdn.net/rachel\_luo/article/details/7913114]{.underline}](http://blog.csdn.net/rachel_luo/article/details/7913114)

1】执行性能测试过程中，LR报错： Action.c(6):Error -27796: Failed to
connect to server \"xxx.xxx.xxx.xxx:xx\":\[10060\] connetion time out

服务端防火墙限制流量导致：iptables接受的流量为304bytes，多余的都抛弃；

1.调整服务端防火墙限制；

2.关闭服务端防火墙进行测试；

2】LoadRunner不能使用IE浏览器进行web脚本录制     

a）LR 8.1不能使用IE进行web脚本录制

原因：

1.在IE7上，安装补丁："K2618444  Internet Explorer
累积安全更新"后，LR8.1就无法录制web脚本；

2.IE8及以上版本的浏览器与LR 8.1的兼容性不好，不能录制脚本；

解决方法：

回退到IE6，或使用IE7时卸载对应的补丁。

b）LR11不能使用IE进行web脚本录制

IE设置的问题，打开"工具\--internet选项\--高级"，取消"启用第三方浏览扩展"。

3】执行性能测试过程中，LR报错： Action.c(3):Error -27796: Failed to
connect to server \"xxx.xxx.xxx.xxx:xx\":\[10048\] Address already in
use

1\. 可能与本地机器有关：Try changing the registry value：

HKEY\_LOCAL\_MACHINE\\System\\CurrentControlSet\\Services\\tcpip\\Parameters\\TcpTimedWaitDelayto
30

andHKEY\_LOCAL\_MACHINE\\System\\CurrentControlSet\\Services\\tcpip\\Parameters\\MaxUserPortto
65534

and rebooting the machine；

2.可能与服务器链接数有关：

a）查看服务器最大连接数（linux）：ulimit -n；

如果连接数不够(默认为1024)，修改：

vim /etc/security/limits.conf

增加以下配置：

\* soft noproc 65536

\* hard noproc 65536

\* soft nofile 65536

\* hardnofile 65536

保存退出后，退出客户端使之生效。

b）应用或应用服务器对最大请求数的限制调整：

web容器：例如tomcat，调整8080端口对应的一些连接配置；

java应用：咨询开发需要修改连接数的配置文件。

4】执行性能测试过程中，LR报错：13874,Error:missing newline in
E:\\sky2.0\\sky2\_merSearchLists\\search.dat

参数化类型未：file时，保存参数值的文件末尾需要一行空行。缺少空行就会报此错。

5】LR中在winsocket下，报10053错误（Software caused connection
abort，10053 error）

10053
错误：原因是超时或协议错误，说明LR在执行套接字操作时，发生通信超时、网络中断或其它异常，主动将Socket连接断开。

分析业务场景：重复登录会踢掉第一次登录的用户，从而断开对应的Socket连接，那么基于之前连接所发生的请求和响应都会失败。

问题：为什么会重复登录，是因为做用户名参数化的时候，使用的是方式是随机分配用户名，导致偶尔出现用户名重复。

解决方法：修改用户名参数化的方式为唯一（file + unique）。

 

6】机器资源不够，使用多台机器作为Load Generators的情况：

      
问题：机器内存2G，vuser=5000（短连接），对服务端进行并发测试，机器很卡；需求是：10000个并发数对服务端进行性能测试，设置vuser至少是10000，在进行压力测试时，机器内存不够，直接死机。

       解决方法：多找几台装有LoadRunner的机器作为Load
Generators，来分担这10000个vuser；

       注意：1.其他作为Load Generators的机器只需开启LoadRunner  Agent
 Service；

                  
2.保证每台机器上LoadRunner支持的最大Vuser数足够（最大可支持65000个Vuser的License：golba65000:
AEACFSJIYJKJKJJKEJIJDBCLBR）；

                 
 3.在做性能测试的机器上，在LR的controller中，添加其他Load
Generators，具体操作：Scenario\--》Load
Generators，点击界面中的Add按钮，填写其他机器的IP，点击connect进行连接；还需要点击details按钮，设置Vuser
limits的最大值（默认是1000）；

                   4.在controller的Scennario
Groups中，添加步骤3中已成功建立连接的Load Generators及对应的脚本。

7】http协议的脚本，执行性能测试过程中报错：Action.c(3): Error -27791:
Server  has shut down the connection prematurely

测试对象是通过nginx做请求分发的一个java程序。

解决方案：测试过程中，服务器java应用的压力并未上去，且应用未死掉。跟踪nginx日志，发现nginx将多余的请求丢弃，需要修改 worker\_connections（派发nginx于后端连接数，文件名：/安装目录/nginx/conf/nginx.conf），默认是1024，改成4096，问题解决。

 附带网上相关情景的解决方案：\
1、应用服务器死掉。小用户时程序上的问题，程序上处理数据库的问题

2、应用服务没有死。应用服务参数设置问题。例如：在许多客户端weblogic应用服务器被拒绝，而在服务器端没有错误显示，则有可能是weblogic中的server元素的acceptbacklog属性值设得过低。如果连接时收到connection
refused消息，说明应提高该值，每次增加25%。我们用的是Tomcat，
然后我自己优化了tomcat配置，初始好像是maxThreads=\"500\"
minSpareThreads=\"400\" maxSpareThreads=\"450\"。

3、数据库的连接

在应用服务的性能参数可能太小了数据库启动的最大连接数（跟硬件的内存有关）

4、有时关闭卡巴斯基也会解决如上问题

 8】执行场景时，LR报错：Error -27796: Failed to connect to server
\"xxx.xxx.xxx.xxx:xx\": \[10060\] Connection timed out.

场景执行原本没有问题，中途修改ip地址由动态获取为静态指定，报了上述错误，将ip地址改回为动态获取，该错误解决。（使用的是公司网络）

9】执行场景时，Vuser数量最大运行数为1000。

解决方案：Controller\--》Scenario\--》Load
Generator\--》details\--》Vuser
Limits，修改第2,3项的1000到你期望的数值即可。（LR这两项默认值为1000）当然前提是你的license支持Vuser的数量要大。

10】执行场景时，所有Vuser都从Down到Pending状态，无法进入运行状态。

解决方案：Controller\--》Scenario\--》Load
Generator\--》details\--》Vuser Limits，应勾选GUI/WINRunner和Other
Vuser两项。Other Vuser忘记勾选导致上述问题。

##### 常见问题 如中文乱码，ie浏览器打不开等问题

http://www.docin.com/p-1549614416.html

#### 混发场景运行僵尸

20180117 0830-1830

直接退出 ctroller \--res.lrr打开报错"......Stop\_time is 0"

\|\|

百度该错误\--无果

\|\|

重新跑场景，再次遇见-试图修改res.lrr文件

\|\|

对比正确的结果，主要查找Stop关键词\--原先存在的文件也有问题，无该关键字

请教同事\--使用谷歌搜索，找到Stop关键词\--按照该文件增加Stop\_time(使用了站长之家-换算-转换时间戳)\--打开到90%报错"......算术溢出错误"

\|\|

将Stop\_time改小，再次尝试打开\--仍旧报算术溢出错误

"......算术溢出错误"\--谷歌对于该错误无解决方案

\|\|

重新跑场景，勾选自动分析结果 auto load
analysis（保证再次controller无法正常停止的时候关闭controller，增加可以手动打开res.lrr概率）\--实验失败

\|\|

晚上重新跑场景再次遇到\--未做处理

20180118 0830-1100

第二日来看正常停止，多运行了30min上\--将所有脚本的step\_out
time等设置从999改为180\--尝试再次失败，1个vuser一直等待超过5min没处理

\|\|

查看机器cpu，使用率为0，查看运行进程有mmdrv.exe,想到主动结束生成vuser的进程，在网上求证该进程是否正确，手动结束，controller
vuser exiting数量从1到了0，error数量从0到1

\|\|

打开res.lrr\--正常打开

robotframe测试相关
------------------

-   安装pywin32和AutoItLibrary后，导入AutoItLibrary显示红色，如下：
    ---------------------------------------------------------------

![](media/image4.png){width="5.761111111111111in" height="1.1388888888888888in"} {#section-1 .ListParagraph}
--------------------------------------------------------------------------------

解决办法：

需要安装AutoIt，且在安装过程中需要选择与系统位数相同的，如64位电脑需要选择（如下），成功安装后，可以看到红色字体已经ok。

-   **Get Current Date中参数格式为see'data formats'时（这时估计都很困惑），就是在userguide中查看，最终访问到页面https://docs.python.org/2/library/datetime.html\#strftime-strptime-behavior**
    -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

![](media/image5.png){width="5.760416666666667in"
height="2.627083333333333in"}

-   **自动导入库：tool-preference**
    -------------------------------

业务相关：
==========

1.  交易日

截止日期=当期系统日期-1个交易日，该值应获取"【当期日期-1】的日期向前最近的交易日"，而不是"当期日期的上一个交易日"，差别在
正常周日的截止日期 理论上应返回
周五的日期，如果根据"当期日期的上一个交易日"则会返回 周四的日期

2.  股票简称：

深圳-目前最长为四个汉字，后期可能拓展为8个汉字

3.  财务报表

4.  公司年报

其他
====

测试点
------

1.  下载次数限制：

<!-- -->

1.  需确认**限制维度**，如ip\*下载文件类型 or ip\*文件类型\*语言 or
    ip\*文件类型\*语言\*股票代码

2.  限制维度越多，过滤拦截数越小\-\--如防止"**数据爬取**"则不能江**维度、颗粒**设置太细
    （一般限制次数，我们都是基于考虑对**系统频繁请求**攻击服务器，在金融领域还需考虑数据爬取，所以需要将限制颗粒设的相对粗一些）

<!-- -->

2.  实现一个**需求必须基于意义**，而不是所有个人想法去实现（20171115）

3.  查询、输入项：

    输入法全角半角

> 防止css攻击：转译特殊字符
>
> 防止sql注入：将**sql关键词进行全角转译**

4.  下载：

    下载次数\--见第一点

    Pdf支持图像，excel不支持

    表格某条记录跨页\--字体高度为3px，如果表格高度是4px，就会出现重叠等现象\--可以设置为6px、9px（最完美）等

    下载文件大小、页数是否有限制\--需求是否要求最多2页

    下载各类型文件-字段值的格式，一般pdf会和页面一样（屏幕拍照），但是excel需要写模板，一般样式会与页面不一致

    页面头尾说明、页码、免责说明、页面上下页签设置

5.  小数位数：

    策略：向上取整，向下取整，四舍五入

    取整处理后为0的情况

    负数四舍五入

6.  常识 1G=10亿=1\*10\^9 1M=100万=1\*10\^6

7.  附件

    文本编码考虑

    文本编辑对原文本是否有影响

    附件名称带括号或者-、/号的支持

8.  月初和年初 问题最多\--表未建

9.  链接新开窗口:点击n次只开一个窗口pk点击n次新开n个窗口 （n\>1）
    > \_Blank \_blank

10. 任何**递归函数**都存在**栈溢出**的问题

    https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/001431756044276a15558a759ec43de8e30eb0ed169fb11000

11. 

概念拓展
--------

### 图形生成插件

Higncharts \--魔方数据生成

Echarts \--常用 http://echarts.baidu.com/examples.html

### 数据库元数据

20171201

### **平台搭建网站**

> **使用了 TRS内容协作平台(TRS WCM) als基金会**
>
> **内容和样式及排序附件等均在后台配置**
>
> **站点\--栏目\--子栏目\--模板\--文档**

### **Excel单元格内容超出长度后显示......，鼠标放上去显示全部内容**

> **参考http://help.finereport.com/doc-view-1832.html**
