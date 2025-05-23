---
date: 2025-05-22
category:
  -操作系统
tag:
  - 面试题
---


# 说说你对操作系统的理解？核心概念有哪些？

![](https://static.vue-js.com/0f06bf30-008a-11ec-8e64-91fdec0f05a1.png)

## 一、是什么

操作系统（Operating System，缩写：OS）是一组主管并控制计算机操作、运用和运行硬件、软件资源和提供公共服务来组织用户交互的相互关联的系统软件程序，同时也是计算机系统的内核与基石

简单来讲，操作系统就是一种复杂的软件，相当于软件管家

操作系统需要处理如管理与配置内存、决定系统资源供需的优先次序、控制输入与输出设备、操作网络与管理文件系统等基本事务，

操作系统的类型非常多样，不同机器安装的操作系统可从简单到复杂，可从移动电话的嵌入式系统到超级电脑的大型操作系统，在计算机与用户之间起接口的作用，如下图：

 ![](https://static.vue-js.com/0ad1b850-009b-11ec-8e64-91fdec0f05a1.png)

许多操作系统制造者对它涵盖范畴的定义也不尽一致，例如有些操作系统集成了图形用户界面，而有些仅使用命令行界面，将图形用户界面视为一种非必要的应用程序




## 二、核心概念

操作系统的核心概念都是对具体物理硬件的抽象，主要有如下：

- 进程（线程）：进程（线程）是操作系统对CPU的抽象
- 虚拟内存（地址空间）：虚拟内存是操作系统对物理内存的抽象
- 文件：文件是操作系统对物理磁盘的抽象
- shell：它是一个程序，可从键盘获取命令并将其提供给操作系统以执行。
- GUI ：是一种用户界面，允许用户通过图形图标和音频指示符与电子设备进行交互
- 计算机架构(computer architecture)： 在计算机工程中，计算机体系结构是描述计算机系统功能，组织和实现的一组规则和方法。它主要包括指令集、内存管理、I/O 和总线结构
- 多处理系统(Computer multitasking)：是指计算机同时运行多个程序的能力
- 程序计数器(Program counter)：程序计数器 是一个 CPU 中的寄存器，用于指示计算机在其程序序列中的位置
- 多线程(multithreading)：是指从软件或者硬件上实现多个线程并发执行的技术

- CPU 核心(core)：它是 CPU 的大脑，它接收指令，并执行计算或运算以满足这些指令。一个 CPU 可以有多个内核
- 图形处理器(Graphics Processing Unit)：又称显示核心、视觉处理器、显示芯片或绘图芯片
- 缓存命中(cache hit)：当应用程序或软件请求数据时，会首先发生缓存命中

- RAM((Random Access Memory)：随机存取存储器，也叫主存，是与 CPU 直接交换数据的内部存储器

- ROM (Read Only Memory)：只读存储器是一种半导体存储器，其特性是一旦存储数据就无法改变或删除

- 虚拟地址(virtual memory)： 虚拟内存是计算机系统内存管理的一种机制

- 驱动程序(device driver)：设备驱动程序，简称驱动程序（driver），是一个允许高级别电脑软件与硬件交互的程序

- USB(Universal Serial Bus)：是连接计算机系统与外部设备的一种串口总线标准，也是一种输入输出接口的技术规范

- 地址空间(address space)：地址空间是内存中可供程序或进程使用的有效地址范

- 进程间通信(interprocess communication)： 指至少两个进程或线程间传送数据或信号的一些技术或方法

- 目录(directory)： 在计算机或相关设备中，一个目录或文件夹就是一个装有数字文件系统的虚拟容器

- 路径(path name)： 路径是一种电脑文件或目录的名称的通用表现形式，它指向文件系统上的一个唯一位置。
- 根目录(root directory)：根目录指的就是计算机系统中的顶层目录，比如 Windows 中的 C 盘和 D 盘，Linux 中的 /
- 工作目录(Working directory)：它是一个计算机用语。用户在操作系统内所在的目录，用户可在此目录之下，用相对文件名访问文件。
- 文件描述符(file descriptor)： 文件描述符是计算机科学中的一个术语，是一个用于表述指向文件的引用的抽象化概念
- 客户端(clients)：客户端是访问服务器提供的服务的计算机硬件或软件。
- 服务端(servers)： 在计算中，服务器是为其他程序或设备提供功能的计算机程序或设备



## 三、总结

- 操作系统是管理计算机硬件与软件资源的程序，是计算机的基石
- 操作系统本质上是一个运行在计算机上的软件程序 ，用于管理计算机硬件和软件资源
- 操作系统存在屏蔽了硬件层的复杂性。 操作系统就像是硬件使用的负责人，统筹着各种相关事项
- 操作系统的内核（Kernel）是操作系统的核心部分，它负责系统的内存管理，硬件设备的管理，文件系统的管理以及应用程序的管理。 内核是连接应用程序和硬件的桥梁，决定着系统的性能和稳定性



## 参考文献

- https://www.cnblogs.com/cxuanBlog/p/13297199.html
- https://www.cnblogs.com/cxuanblog/p/12607608.html
- https://www.anvilliu.com/2021/03/06/%E8%AE%A1%E7%AE%97%E6%9C%BA%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F%E2%80%94%E2%80%94%E5%9F%BA%E6%9C%AC%E6%A6%82%E5%BF%B5/