DNSPod-DynamicIP
================

DNSPod.cn域名IP（A记录）定期（30秒）更新Python脚本。

使用说明
--------

在DNSPod.cn创建需要更新的域名的A记录，并通过下面的方法查询domian_id以及对应的record_id

Windows & Linux: 

> python ddnspod.py

Linux (Ubuntu) 自动启动服务:

将ddnsdaemon放置到/ect/init.d/，并给予可运行权限，然后

> sudo update-rc.d ddnsdaemon defaults 


ddnspod.py
----------

替换上你的DNSPod.cn帐号Email，密码，域名ID，记录ID等参数，就可以运行了。 会在后台一直运行，每隔30秒检查一遍IP，如果修改了就更新IP。

获得domain_id可以用curl

> curl -k https://dnsapi.cn/Domain.List -d "login_email=xxx&login_password=xxx"

获得record_id类似 

> curl -k https://dnsapi.cn/Record.List -d "login_email=xxx&login_password=xxx&domain_id=xxx"

代码来源：https://gist.github.com/chuangbo/833369

ddnsdaemon
----------

Linux服务器启动脚本。将ddnspod.py放置到/opt/ddnspod/即可，或者修改指定ddnspod.py访问的路径。

代码来源：https://github.com/iceleaf916/PyDDnsPod/blob/master/ddnspod-daemon

License
-------

GNU Affero General Public License
