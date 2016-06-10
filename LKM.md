# Loadable Kernel Module
可动态加载的内核模块，顾名思义，不需要重新编译Linux内核，在Linux运行时可以自动加载到Kernel里的模块。

1. 显示系统中的内核模块: 
``` lsmod ```

2. 显示内核模块的文件名列表:
```
modprobe --list
# for those who don't have the `--list' or `-l' option, use the command below:
# find /lib/modules/`uname -r` -type f -name "*.ko"
```

3. 装载一个内核模块
``` modprobe module_name ```

4. 卸载一个内核模块
``` rmmod module_name ```

5. 显示一个内核模块的信息
``` modinfo module_name ```

6. 内核模块的黑名单，阻止系统自动加载该内核模块
``` vim /etc/modprobe.d/blacklist ```
修改完blacklist文件，需要更新驱动缓存
``` sudo update-initramfs -u ```

