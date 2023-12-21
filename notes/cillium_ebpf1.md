# 学习cillium ebpf 

https://barryx.cn/cilium_ebpf/

https://ebpf-go.dev/guides/getting-started/

## env 

虚拟机：anolis881 

```bash
Welcome to Anolis OS 8

Last login: Sat Nov 18 08:37:02 2023 from 192.168.31.220
[root@anolis881 ~]# uname -a 
Linux anolis881 5.10.134-13.an8.x86_64 #1 SMP Mon Jan 9 10:39:46 CST 2023 x86_64 x86_64 x86_64 GNU/Linux
[root@anolis881 ~]# ip r
default via 192.168.31.1 dev ens3 proto dhcp src 192.168.31.10 metric 100 
default via 192.168.122.1 dev YGSF proto dhcp src 192.168.122.12 metric 425 
172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1 linkdown 
192.168.31.0/24 dev ens3 proto kernel scope link src 192.168.31.10 metric 100 
192.168.122.0/24 dev YGSF proto kernel scope link src 192.168.122.12 metric 425 

```

1. yum install -y clang llvm libbpf-devel 

2. 安装golang 



3.  [root@anolis881 hello-ebpf]# go generate 
Compiled /root/hello-ebpf/counter_bpfeb.o
Stripped /root/hello-ebpf/counter_bpfeb.o
Wrote /root/hello-ebpf/counter_bpfeb.go
Compiled /root/hello-ebpf/counter_bpfel.o
Stripped /root/hello-ebpf/counter_bpfel.o
Wrote /root/hello-ebpf/counter_bpfel.go




[root@anolis881 hello-ebpf]# go generate 
/root/hello-ebpf/counter.c:5:10: fatal error: 'bpf/bpf_helpers.h' file not found
#include <bpf/bpf_helpers.h>
         ^~~~~~~~~~~~~~~~~~~
1 error generated.
Error: can't execute clang: exit status 1
exit status 1
gen.go:3: running "go": exit status 1

