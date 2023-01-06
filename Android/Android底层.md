# 系统架构


# repo

1. Andoird的代码管理使用git，使用Gerrit进行代码审核。repo对git进行封装，管理多个git仓库

# 系统启动流程

linux内核启动（）：
`start_kernel`(common/arch/arm/kernel/head-common.S)
->`start_kernel(void)`(common/init/main.c 同下)  
->`rest_init(void)`  

->`kernel_init(void *unused)`:找init进程  
->`run_init_process(void *unused)`  
->`kernel_execve()`:内核空间调用用户空间的应用程序

>init进程
>1.分析启动init.rc脚本文件。
>2.为应用程序访问设备驱动生成设备节点文件。
>3.子进程的创建与终止。
>4.提供property service属性服务，进行Android系统的属性管理。
