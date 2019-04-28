# 顺序读写 #
## 介绍 ##
&emsp;&emsp;顺序读写是基于应用层面的加快IO速度的方法，是说在应用层读或者写一个文件的时候，按照文件读写
指针顺序读写一个文件，能够大大加快文件读写的速度。
## 原因 ##
&emsp;&emsp;由于底层硬件的不同，它的表现形式也是不同的，顺序读写这种应用层技巧，在当底层是机械硬盘的时
候，收益最大。
&emsp;&emsp;机械硬盘读取一个扇区，需要做三步，第一步是寻道，第二步是旋转磁盘到合适的扇区，第三部是读写
数据，顺序读写本质上是减少了寻道和旋转，即寻找扇区的时间，并且可以利用磁盘的预读功能，所以会比较快，收益
大。  
&emsp;&emsp;当然，文件有可能不是占用连续的内存空间（比如原有文件新增数据，造成文件不能占用连续磁盘空间），
但大多数情况下，文件还是会一块一块的存储到磁盘内，所以顺序读写能够加快磁盘IO速度。在写入的时候为了防止
断续的磁盘空间分配，会使用预分配磁盘空间，让磁盘预留连续的磁盘空间。  
&emsp;&emsp;关于SSD硬盘，由于寻道时间+磁盘旋转时间为0，顺序读写主要的收益来源点是预读，也会比随机读写
快。

## 工程映射 ##
&emsp;&emsp;kafka在存储消息的时候利用了磁盘顺序读写的原理。  
&emsp;&emsp;大部分lsm树结构的数据库也是利用了磁盘顺序读写的原理，比如写入，比如scan操作。