# kern_hook_demo

Bpftrace scripts that study Linux kernel hook points.

相关笔记直接记录在脚本中

## env

install bpftrace 
doc: https://github.com/iovisor/bpftrace/blob/master/INSTALL.md

## usage

```shell
#need root
bpftrace kern_hook_demo.bt
```

## Hook point

> 支持 `15` 种 Hook，涵盖除网络方面的大部分安全审计检测需求，目前输出字段主要为进程主要信息及函数参数，主要参考hades

<details><summary> eBPF Hook point 详情 </summary>
<p>

| Hook                                       | Status                |
| :----------------------------------------- | :------------------------------------ |
| tracepoint/syscalls/sys_enter_execve       | ON                                     |
| tracepoint/syscalls/sys_enter_execveat     | ON                                     |
| tracepoint/syscalls/sys_enter_memfd_create | ON                                     |
| tracepoint/syscalls/sys_enter_prctl        | ON                                       |
| tracepoint/syscalls/sys_enter_ptrace       | ON                                       |
| kprobe/security_socket_connect             | OFF                                    |
| kprobe/security_socket_bind                | OFF                                     |
| kprobe/commit_creds                        | ON                                     |
| k(ret)probe/udp_recvmsg                    | OFF              |
| kprobe/do_init_module                      | ON                                     |
| kprobe/security_kernel_read_file           | ON                                     |
| kprobe/security_inode_create               | ON                                     |
| kprobe/security_sb_mount                   | ON                                     |
| kprobe/call_usermodehelper                 | ON                                     |
| kprobe/security_inode_rename               | ON                                     |
| kprobe/security_inode_link                 | ON                                     |
| kprobe/security_file_permission            | OFF                                     |
| kprobe/security_bpf                        | ON                                     |

</p></details>
