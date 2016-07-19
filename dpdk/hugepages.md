#Hugepages

## Hugepage的作用
1. 程序中用的都是虚拟地址，CPU需要把虚拟地址转换为物理地址. 
2. CPU将虚拟地址转换为物理地址需要进行两次查表(Tow-level translation), 先查页目录（Page Directory），再查页表（Page Table). 因此需要访问2次内存。
3. CPU为了增加转换速度，引入了TLB（Translation Lookaside Buffer）. TLB是在CPU上的Cache，访问速度远块于内存，但是只能存储有限的映射关系.
4. 为了提高TLB的命中率（TLB hit）, 引入Hugepage，通过提高内存页的大小，提高TLB hit.
5. 使用Hugepage，转换过程（page walk）只需一次查表过程，而且减少了页目录占用的内存空间.

## 设置Hugepage
x86_64结构支持两种大小的Huge page: 2MB、1GB，分别对应的cpuinfo标志是PSE、PDPE1GB. 
### 设置2MB Hugepages
Ubuntu 12.04 LTS
1. 通过pse标志，判断CPU是否支持2MB的Huge page
```
$grep pse /proc/cpuinfo
```
2. 打开/etc/sysctl.conf文件
```
$sudo vim /etc/sysctl.conf

```
3. 把hugepage的数量配置写入/etc/sysctl.conf文件中
```
# Allocate 16 * 2MB huge pages
$vm.nr_hugepages = 16
```
4. 重新启动Ubuntu
```
$sudo reboot
```
5. 查看内存中hugepage的数量
```
$sudo cat /proc/meminfo | grep Huge
```

### 设置1GB Hugepages
1. 通过pdpe1gb标志，判断CPU是否支持1GB的Huge page
```
$grep pdpe1gb /proc/cpuinfo
```
2. 打开/etc/sysctl.conf文件
```
$sudo vim /etc/sysctl.conf

```
3. 把hugepage的数量配置写入/etc/sysctl.conf文件中
```
# Allocate 2 * 1GB pages
default_hugepagesz=1GB hugepagesz=1GB hugepages=2
```
4. 重新启动Ubuntu
```
$sudo reboot
```
5. 查看内存中hugepage的数量
```
$hugeadm --pool-list
      Size  Minimum  Current  Maximum  Default
   2097152       16       16       16        *
1073741824        0        0        0         
```

