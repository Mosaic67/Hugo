---
date: "2020-11-07T04:08:54+08:00" 
title: "去除WinRaR广告"
draft: false
tags: ['Windwos','WinRAR','去除广告']
description: "去除每次打开压缩文件弹出的广告"
postMetaInFooter: true
comments: true
---

#### :open_file_folder:准备工作

    *<u>**[工具下载](https://spook.vercel.app/WinRAR/WinRAR去除广告.rar)**</u>*

1. 解压`WinRAR去除广告.rar`，双击`WinRAR.KeyGen.exe`，点击`Save Licenses`，选择WinRaR存储目录。  

2. 安装`reshacker_setup.exe`  。  

> Resourcehacker是一个反编译器，支持查看和编辑可执行文件（\*.exe; \*.dll; \*.scr; 等）和编译的资源库（\*.res，\*.mui）。  

3. 使用Resourcehacker工具打开`winrar.exe` 。  

![image](/WinRAR/1.png)

![](/WinRAR/2.png)

#### :ballot_box_with_check: 反编译程序，去除广告

4. 找到字符串表下ID 为1272[^1]为广告弹窗文本 。 

[^1]: 后续版本ID可能会发生变化，ID后内容一般不会变。

5. **展开**String Table 字符串表下的*80:2052* 文件，打开文件，编辑区即文本内容。此处可以找到ID 为*1272* 的文本，`winrar.exe`程序即通过读取其文本来弹出广告弹框。

![](/WinRAR/3.png)

![](/WinRAR/4.png)

```
STRINGTABLE
LANGUAGE LANG_CHINESE, SUBLANG_CHINESE_SIMPLIFIED
{
  1265,     "当前文件夹"
  1266,     "本地硬盘驱动器"
  1270,     "http://www.winrar.com.cn"
  1271,     "http://www.buysoftware.cn"
  1272,     ""
  1273,     "https://www.rarlab.com/themes.htm"
}
```

7. **点击绿色三角按钮**重新编译WinRaR.exe，然后`Ctrl`+`S`保存。  

![](/WinRAR/5.png)

8. 重新打开winrar.exe 此时广告弹出已经不会被加载了，世界是美好的。
