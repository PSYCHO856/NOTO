把目录下所有的文本文件输出到txt



1. 把以下代码保存为 .py 格式
2. 修改indir目录为代码所在目录
3. 修改outfilePath为输出文件

```python
# _*_ coding:utf-8 _*_
import os

def list_files_to_txt(indir, outfile, wildcards, recursion):
    exts = wildcards.split(" ")
    filelist = os.listdir(indir)
    for name in filelist:
        fullname = os.path.join(indir, name)
        if os.path.isdir(fullname) & recursion:
            list_files_to_txt(fullname, outfile, wildcards, recursion)
        else:
            for ext in exts:
                if name.endswith(ext):
                    with open(fullname, encoding='UTF-8') as infile:
                        code = infile.read()
                        outfile.write(code + "\n")
                        break


def RW():
    indir = r"C:\Users\Yzngo\Documents\Projects\Feamber\MiniGame2021\Park\Park\Assets\Park Master\Game\Scripts"
    outfilePath = r"C:\Users\admin\Desktop\park.txt"
    wildcards = ".cs"
    outfile = open(outfilePath, "w", encoding='UTF-8')
    if not outfile:
        print("cannot open output file")
    list_files_to_txt(indir, outfile, wildcards, 1)
    outfile.close()

RW()

```



Bug：

1. `UnicodeEncodeError: 'gbk' codec can't encode character '\ufeff' in position 0: illegal multibyte sequence`

    打开输入文件和输出文件时都要加上 `encoding='UTF-8'`

![image-20211130161825127](C:\Users\xian\AppData\Roaming\Typora\typora-user-images\image-20211130161825127.png)

