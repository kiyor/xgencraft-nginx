xgencraft-nginx
===============

you must change

        /src/core/ngx_conf_file.c:#define NGX_CONF_BUFFER  4096
to

        /src/core/ngx_conf_file.c:#define NGX_CONF_BUFFER  more then 4096

#api docs
更新后开启验证,只有部分权限公开,如查看serverlog.
验证只需添加key=${yourkey}

#for admin
新建普通op用户key

    curl 'manager.xgencraft.com/genkey?key=${yourmasterkey}&user=${newusername}'

删除普通op用户key

    curl 'manager.xgencraft.com/delkey?key=${yourmasterkey}&user=${username}'
    
显示op用户以及key

    user 'manager.xgencraft.com/showuser?key=${yourmasterkey}'
    
    
#for ops
ban单个ip: 1.1.1.1(请勿使用127.x.x.x进行测试)

    curl 'manager.xgencraft.com/banip?key={yourkey}&ip=${ip}'

使用submask表示域

    1.1.1.0 - 1.1.1.255     = 1.1.1.0/24
    1.1.0.0 - 1.1.255.255   = 1.1.0.0/16
    1.0.0.0 - 1.255.255.255 = 1.0.0.0/8 #这个范围太大 勿使用

ban批量ip: 1.1.1.0-255(请勿使用127.x.x.x进行测试)

    curl 'manager.xgencraft.com/banip?key={yourkey}&ip=1.1.1.0/24'

unban

    curl 'manager.xgencraft.com/unbanip?key={yourkey}&ip=${ip}'

显示当前iptables设定

    curl 'manager.xgencraft.com/showip?key={yourkey}'
    
更新ip的country city

    curl 'manager.xgencraft.com/updateip?key={yourkey}&ip={ip}&city={city}&country={country}'
    
其中ip和country可以不填,ip不填默认为指令使用者ip,country不填默认为不修改


#普通权限(无key要求)
显示当前服务器记录500行(不输入数量默认为500行)

    curl manager.xgencraft.com/serverlog

显示当前服务器记录1000行

    curl 'manager.xgencraft.com/serverlog?num=1000'
    
显示当前服务器记录1000行,带有关键字a或关键字b

    curl 'manager.xgencraft.com/serverlog?num=1000&grepor=a,b'
    
显示当前服务器记录1000行,带有关键字a或关键字b并且必须包含关键字c和关键字d

    curl 'manager.xgencraft.com/serverlog?num=1000&grepor=a,b&grepand=c,d'
    
查询ip所在地

    curl 'manager.xgencraft.com/ip=ip{ip}'

以上指令不填写ip则为显示使用者ip所在地


**以上服务器记录指令可以任意组合**

如:

    curl 'manager.xgencraft.com/serverlog?num=100000&grepor=gold,diamond&grepand=someone,8[0-9]%'

#可以直接用浏览器代替curl

比如在浏览器里直接输入

    manager.xgencraft.com/serverlog

颜色将无法在浏览器中显示(也许未来可以添加)
