# DPDK 优化

## 硬件和内存
1. 使用Intel Xeon系列服务器CPU.


2. 内存的Channel越多越好，内存Channel对DPDK的性能有最直接影响的因素之一(one of the most direct effects on performace)，每个内存Channel至少有一个DIMM插槽。测试机器有两个内存Channel,每个Channel有12个DIMM插槽。
``` dmidecode -t memory | grep Locator ```

3. 内存的频率越高越好。测试机器的CPU频率是1333MHz.
``` dmidecode -t memory | grep Speed ```

## 网卡

1. 使用DPDK支持的高性能网卡。测试机器使用的是Intel I350.

2. 使用PCIe第三代插槽，例如Gen3 x8 或 Gen3 x16插槽。Gen2的插槽不能给2个10GbE网口提供足够的带宽。使用下面的命令可以查看PCIe插槽的状态：
``` lspci -s 03:00.1 -vv | grep LnkSta ```

3. 使用多CPU的机器，要把所有网卡连到同一个CPU上。

4. 每个网卡只使用一个网口，因为网卡上的所有网口会共享PCIe总线的带宽。

## BIOS

1. 关掉一切省电模式

2. 在CPU电源管理和性能管理的选项中，选择性能的最大化

3. 关闭Turbo Boost ???

4. 把CPU的频率设置为所支持的最高频率，不要用Auto选项

5. 关闭所有的虚拟化选项。

## Linux启动命令

1. 预留1GB的大内存页， 例如，保留8个1GB的大内存页
``` default_hugepagesz=1G hugepagesz=1G hugepages=8 ```

2. 孤立CPU的核(Isolate CPU cores), 例如：?????
``` isolcpus=2,3,4,5,6,7,8 ```

## DPDK设置

1. 查看CPU的核, 使用``` tools/cpu_layout.py```或者```lscpu```

2. 检查网卡的ID和网卡相关CPU的Socket

2.1 查看网卡的PCI地址和设备ID
```
#List all the NICs with PCI address and device IDs
lspci -nn |  grep Eth
```

2.2 查看PCI设备对应的CPU(numa_node)
``` cat /sys/bus/pci/devices/0000\:xx\:00.x/numa_node ```

2.3 将网卡绑定到对应CPU的核上(根据numa_node), 每个网口要绑定到不同核的逻辑核上。一个CPU核会分出多个逻辑核(logical cores)。

2.4 每个网口使用两个queue pairs, 每个queue pairs需要一个独立的CPU核
