# cillium ebpf 




实际上是ebpf-go 

https://ebpf-go.dev/guides/getting-started/#building-and-running-the-go-application


eunomia-bpf 的bpf程序可以参见[21-xdp](../src/21-xdp/xdp.bpf.c)


## 

1. 在anolis881 build的go程序

```bash
[root@anolis881 hello-ebpf]# vim main.go 
[root@anolis881 hello-ebpf]# vim main.go 
[root@anolis881 hello-ebpf]# ./01-build.sh 
Compiled /root/bpf-developer-tutorial/hello-ebpf/counter_bpfel.o
Stripped /root/bpf-developer-tutorial/hello-ebpf/counter_bpfel.o
Wrote /root/bpf-developer-tutorial/hello-ebpf/counter_bpfel.go
Compiled /root/bpf-developer-tutorial/hello-ebpf/counter_bpfeb.o
Stripped /root/bpf-developer-tutorial/hello-ebpf/counter_bpfeb.o
Wrote /root/bpf-developer-tutorial/hello-ebpf/counter_bpfeb.go
[root@anolis881 hello-ebpf]# ls
01-build.sh  99-clean.sh       counter_bpfeb.o   counter_bpfel.o  gen.go  go.sum      main.go
02-run.sh    counter_bpfeb.go  counter_bpfel.go  counter.c        go.mod  hello-ebpf  Readme.md
[root@anolis881 hello-ebpf]# ./hello-ebpf 
2023/12/22 06:40:34 Usage:./hello-ebpf interface
[root@anolis881 hello-ebpf]# 
[root@anolis881 hello-ebpf]# ls
01-build.sh  99-clean.sh       counter_bpfeb.o   counter_bpfel.o  gen.go  go.sum      main.go
02-run.sh    counter_bpfeb.go  counter_bpfel.go  counter.c        go.mod  hello-ebpf  Readme.md
```



2. 拷贝到另外一个os中

```bash
[root@anolis881 hello-ebpf]# scp hello-ebpf   192.168.31.108:~/
The authenticity of host '192.168.31.108 (192.168.31.108)' can't be established.
ECDSA key fingerprint is SHA256:bVum4noPPkqQtg4eh2Wr2HDWKwzXkSriW20pYES6qH0.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '192.168.31.108' (ECDSA) to the list of known hosts.
root@192.168.31.108's password: 
hello-ebpf  
```

3. 直接跑，发现能正常run起来， 实现了ebpf一次编写，一次build,到处可run的效果。

```bash
root@debian12:~# ./hello-ebpf 
2023/12/22 06:41:06 Usage:./hello-ebpf interface
root@debian12:~# ./hello-ebpf ens36
2023/12/22 06:41:12 Counting incoming packets on ens36..
2023/12/22 06:41:13 Received 124 packets
2023/12/22 06:41:14 Received 166 packets
2023/12/22 06:41:15 Received 212 packets
^C2023/12/22 06:41:16 Received signal, exiting..

root@debian12:~# uname -a 
Linux debian12 6.1.0-9-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.1.27-1 (2023-05-08) x86_64 GNU/Linux

```

## issue: git clone 之后hello-ebpf 没有了go.mod 文件

git clone 之后hello-ebpf 没有了go.mod 文件，是怎么回事？ 



# coolbpf 


https://gitee.com/anolis/surftrace

surftrace是一个ftrace封装器和开发编译平台，既能让用户基于libbpf快速构建工程进行开发，也能作为ftrace的封装器进行trace命令编写。项目包含surftrace工具集和pylcc、glcc(python or generic C language for libbpf Compiler Collection)，提供远程和本地eBPF的编译能力。


## 特点


## 本地编译

https://gitee.com/anolis/coolbpf/blob/master/docs/localcompile.md


