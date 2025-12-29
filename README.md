Compress（Huffman 压缩/解压工具）

这是一个基于 Huffman 编码 的命令行压缩/解压工具，用于将任意文件（按字节读取）压缩为自定义格式的 .huf 文件，并在解压时恢复原始内容与原始扩展名。


功能特性：

Huffman 压缩：统计输入文件字节频率，构建 Huffman 树并生成码表，将数据编码为比特流并按字节写入。

Huffman 解压：读取 .huf 文件头部信息和频率表，重建 Huffman 树，逐比特解码恢复原始数据。

自动恢复扩展名：压缩时记录原文件扩展名（例如 .txt），解压输出文件名为 input + 原扩展名。

二进制模式读写：使用 ios::binary，可处理文本与二进制文件（实现上按字节处理）。 


使用方法

压缩
compress.exe -c input.txt

解压
compress.exe -d input.huf

文件格式（.huf）

magic：4 字节，固定为 "HF01"

orig_size：4 字节 int，原扩展名长度

orig：orig_size 字节，原扩展名字符串

total：4 字节 int，原始数据大小

sz：4 字节 int，频率表大小

freq table

data bytes

有效位

