# 在 Apple Silicon Mac 上入门汇编语言

2019年，我在GitHub上创建了一个仓库[Assembly-on-macOS](https://github.com/Evian-Zhang/Assembly-on-macOS)。在这个仓库里，我写了十三篇博客，从头开始讲如何在macOS系统上入门汇编语言。3年过去了，我对二进制程序分析、汇编语言有了更深入的认识，文笔也有所长进，与此同时，Apple也在更换Mac的架构，将其从intel的amd64指令集迁移到ARM的aarch64指令集上。因此，我打算重制（也许是remake，也许是remaster，不如叫reforge吧）这个系列，面向使用Apple Silicon Mac的开发者，系统介绍aarch64指令集汇编语言的入门知识。

## 背景

我一直认为，对于一个软件开发者而言，了解一些底层的知识是十分必要的。对于汇编、操作系统、处理器的初步了解，十分有利于在日常软件开发中排除bug、优化性能。

但是，对于手持Apple Silicon Mac（即芯片为M系列的Mac）的开发者而言，入门汇编语言却相对更加困难。

1. 如今国内大部分的中文教材，还是停留在32位甚至16位的处理器上，有些还需要DOS来模拟。
2. 虽然也有一些更现代的书籍、博客会介绍如今主流的64位处理器的汇编语言，但是这些介绍往往是基于Linux和Windows操作系统，在macOS上仍然会有一些差异（如mach-O格式的段、节的名称，命名粉碎机制，系统调用号等）。
3. 就算终于找到了基于macOS的汇编语言入门的文章，也往往都是两三年前所写，仍然基于intel的amd64指令集。而Apple Silicon的Mac则使用ARM的aarch64指令集，两者更是完全不同。

在macOS上使用Docker等虚拟化方案，虽然可以让我们接触amd64指令集的Linux系统，但为什么不用原生的呢？

因此，本系列将针对使用Apple Silicon Mac的开发者，介绍aarch64指令集汇编语言的入门知识。

## 前置知识要求

本系列的前置知识要求并不高，主要包括以下三点：

* 能看懂C语言编写的程序
* 适当了解计算机体系结构知识
* 能够简单使用命令行进行操作

## 参考资料

* [Using `as`](https://sourceware.org/binutils/docs/as/index.html)
* [Armv8-A Instruction Set Architecture](https://developer.arm.com/-/media/Arm%20Developer%20Community/PDF/Learn%20the%20Architecture/Armv8-A%20Instruction%20Set%20Architecture.pdf)
* [ARMv8 Instruction Set Overview](https://class.ece.uw.edu/469/peckol/doc/ARM/ARM_v8_Instruction_Set_Architecture_(Overview).pdf)（不知道为什么，官方网站上不再提供这篇文档）
* [Arm Architecture Reference Manual for A-profile architecture](https://developer.arm.com/documentation/ddi0487/latest)
* [ARM Assembly Language](https://www.oreilly.com/library/view/arm-assembly-language/9781482229851/)