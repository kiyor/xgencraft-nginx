xgencraft-nginx
===============

#api docs
更新后开启验证,只有部分权限公开,如查看serverlog.
验证只需添加key=${yourkey}

#for admin
新建普通op用户key

    curl manager.xgencraft.com/genkey?key=${yourmasterkey}&user=${newusername}

删除普通op用户key

    curl manager.xgencraft.com/delkey?key=${yourmasterkey}&user=${username}
    
#for ops
ban单个ip: 1.1.1.1(请勿使用127.x.x.x进行测试)

    curl manager.xgencraft.com/banip?key={yourkey}&ip=${ip}

使用submask表示域

    1.1.1.0 - 1.1.1.255     = 1.1.1.0/24
    1.1.0.0 - 1.1.255.255   = 1.1.0.0/16
    1.0.0.0 - 1.255.255.255 = 1.0.0.0/8 #这个范围太大 勿使用

ban批量ip: 1.1.1.0-255(请勿使用127.x.x.x进行测试)

    curl manager.xgencraft.com/banip?key={yourkey}&ip=1.1.1.0/24

unban

    curl manager.xgencraft.com/unbanip?key={yourkey}&ip=${ip}

显示当前iptables设定

    curl manager.xgencraft.com/showip?key={yourkey}

#普通权限(无key要求)
显示当前服务器记录500行(不输入数量默认为500行)

    curl manager.xgencraft.com/serverlog

显示当前服务器记录1000行

    curl manager.xgencraft.com/serverlog?num=1000


#可以直接用浏览器代替curl

比如在浏览器里直接输入

    manager.xgencraft.com/serverlog

[0;33;22m这类乱码是颜色代码,可以无视,也可以复制粘贴去notepad++,软件会无视

