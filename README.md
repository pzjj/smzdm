# smzdm
My first repository on GitHub copy by mengshouer 
#第一个小玩意，完全照抄的mengshouer雪狐大佬的，只是单独拿出来自用，谢谢大佬分享。
以下来自大佬的指导说明，有问题别问我，问就是不知道。
什么值得买网页每日签到
因为登录获取到的cookies时间比较长，就没写自动登录了

使用方法
Github Actions版本
1.点击项目右上角的Fork，Fork此项目
2.到自己Fork的项目点击Setting→Secrets→New secrets
3.Name填写cookie_smzdm，Value填写 获取到的cookie
4.在"Actions"中的"run"下点击"Run workflow"即可手动执行签到，后续运行按照schedule，默认在每天凌晨0:30自动签到，可自行修改
5.(可选)New secrets，Name填写SCKEY，Value填写 Server酱推送SCKEY 报错提醒用

腾讯云函数SCF的版本
1.下载requirements.zip所需库，到层里面新建一个层
2.到函数服务里面新建一个函数，输入名字，运行环境选择python3.6，选择空白模板，下一步
3.修改执行方法为smzdm_pc，修改index.py文件，把SCF版py文件内容覆盖掉里面的函数，删除config.json
4.高级设置，添加多个环境变量key内输入：1.cookie_smzdm 2.SCKEY(选填)
value内输入：1.获取到的cookie 2.Server酱推送SCKEY,报错提醒
5.层配置，添加层，选择刚才新建的层。最后点完成
6.进入函数→触发管理→新建触发器，按自己需求定时启动

Cookie获取方法
浏览器打开需要签到的网站并登录，F12打开检查
在 Chrome 浏览器下方的开发工具中单击 Network 标签页(其他浏览器大同小异)
F5刷新当前网站，随便选一个Name里面的网页，在右侧Headers内找到Cookie: xxxxxx，复制xxxx的东西，一般很长一大串
Headers如果没有Cookie就换另一个Name里面的网页，实在看不懂就自行baidu吧.jpg
Cookie过期就必须手动更换，再重复一次获取流程，然后Github到secrets里更新，腾讯云函数就到函数配置中修改环境变量的值
