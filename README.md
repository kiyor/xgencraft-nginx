xgencraft-nginx
===============

api docs

ban单个ip: 1.1.1.1
curl manager.xgencraft.com/banip=1.1.1.1

ban批量ip: 1.1.1.0-255
curl manager.xgencraft.com/banip=1.1.1.0/24

unban
curl manager.xgencraft.com/unbanip=1.1.1.1
curl manager.xgencraft.com/unbanip=1.1.1.0/24

显示当前iptables设定
curl manager.xgencraft.com/showip

显示当前服务器记录500行
curl manager.xgencraft.com/serverlog

显示当前服务器记录1000行
curl manager.xgencraft.com/serverlog=1000

可以直接用浏览器代替curl
比如在浏览器里直接输入manager.xgencraft.com/banip=1.1.1.1
会下载一个文件,可以直接用记事本打开查看是否成运行成功
