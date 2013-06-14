xgencraft-nginx
===============

#api docs

#ban单个ip: 1.1.1.1(请勿使用127.x.x.x进行测试)

    curl manager.xgencraft.com/banip=1.1.1.1

#使用submask表示域

    1.1.1.0 - 1.1.1.255     = 1.1.1.0/24
    1.1.0.0 - 1.1.255.255   = 1.1.0.0/16
    1.0.0.0 - 1.255.255.255 = 1.0.0.0/8 #这个范围太大 勿使用

#ban批量ip: 1.1.1.0-255(请勿使用127.x.x.x进行测试)

    curl manager.xgencraft.com/banip=1.1.1.0/24

#unban

    curl manager.xgencraft.com/unbanip=1.1.1.1
    curl manager.xgencraft.com/unbanip=1.1.1.0/24

#显示当前iptables设定

    curl manager.xgencraft.com/showip

#显示当前服务器记录500行(不输入数量默认为500行)

    curl manager.xgencraft.com/serverlog

#显示当前服务器记录1000行

    curl manager.xgencraft.com/serverlog=1000


#可以直接用浏览器代替curl

比如在浏览器里直接输入

    manager.xgencraft.com/banip=1.1.1.1

会下载一个文件
可以直接用记事本打开查看是否成运行成功
