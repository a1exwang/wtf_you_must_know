## socat (SOcket CAT)

用于在 Linux 连接两个, stdin, stdout, 文件, socket...许多东西

- 基本语法
  - socat [options] file1 file2
  - 默认情况下是双向连接, 会将 file1 的输入与 file2 的输出连接, file2 的输入与 file1 的输出连接

- 文件地址的一些用法
  - -: stdin, stdout
  - stdin, stdout
    - 顾名思义
  - /home/alexwang/wtf.txt
    - 文件系统路径
  - tcp:localhost:1234, tcp-listen:localhost:1234
    - TCP Socket, 带 listen 的是指服务端 Socket
  - system:"bash"
    - 执行一个 Shell 命令
  - tun:192.168.123.1/24
    - Linux tun 设备, 可以用来快速起一个 VPN
  - pipe:/tmp/a
    - Linux named pipe



- 一些例子, 例子上面的注释是等价写法

```bash
  # cat 
  socat - - 

  # VPN
  # On server
  sudo socat tun:192.168.32.1/24,up tcp:vpn_server:1234
  # On client
  sudo socat tun:192.168.32.2/24,up tcp-listen:1234
  # then use iptables, ip route to configure NAT and routing tables.



```
