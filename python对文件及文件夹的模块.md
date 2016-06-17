#模块的常用命令
<pre>
python中对文件、文件夹(文件操作函数)的操作需要涉及到os模块和shutil模块
</pre>
##一、Python的os模块
<pre>
1.	os.name() --判断现在正在使用的平台，Windows返回'nt';Linux返回'posix'
2.	os.getcwd() --得到当前工作的目录
3.	os.remove() --函数用来删除一个文件
4.	os.listdir() --返回指定目录下的所以文件和目录名
5.	os.path.isfile() --检验给出的路径是否是一个文件
6.	os.path.isdir()  --检验给出的路径是否是一个目录
7.	os.path.isabs()  --判断是否是绝对路径
8.	os.path.exists() --检验给出的路径是否真的存在
9.	os.path.split()  --返回一个路径的目录和文件名
10.	os.path.splitext() --分离扩展名
11.	os.path.dirname() --获取路径名
12.	os.path.basename() --获取文件名
13.	os.system()    --运行shell命令
14.	os.getenv()与os.putenv()
15.	os.linesep --给出当前平台使用的行终止符window使用'\r\n',linux使用'\n'而Mac使用'\r'
16.	os.rename(old,new) --重命名
17.	os.makedirs(r"c:\python\test")  --创建多级目录
18.	os.mkdir("test") --创建单个目录
19.	os.stat(file)  --获取文件属性
20.	os.chmod(file) --修改文件权限与时间戳
21.	os.path.ggetsize(filename) --获取文件大小(获取的是byte)byte/1024=kb
</pre>

##二、文件操作
<pre>
1. os.mknod("test.txt")  --创建空文件
2. fp = open("test.txt",w) --直接打开一个文件，如果文件不存在则创建文件，如果存在，则清空
关于open模式：
w   --以写方式打开
a   --以追加模式打开(从EOF开始，必要时创建新文件)
r+  --以读写模式打开
w+  --以读写模式打开(参见w)
a+  --以读写模式打开(参见a)a+可以修改几行之间的内容
rb  --以二进制读模式打开
wb  --以二进制写模式打开（参见w）

3. fp.read([size])  --size为读取长度，以byte为单位
4. fp.readline([size])  --读一行，如果定义了size，有可能返回只有一行的一部分
5. fp.readlines([size])   --把文件每一行作为一个list的成员，并返回这个list，其他的内部是通过循环调用readline()来实现的，如果提供size参数，size是表示读取内容的总长，也就是说可能只读到文件的一部分
6. fp.write(str) --把str写到文件中，write()并不会再str后加上一个换行符
7. fp.writelines(seq) --把seq的内容全部写到文件中(多行一次性写入)，这个函数也只是忠实的写入，不会再每行后面加上任何东西
8. fp.close()   --关闭文件。Python会在一个文件不用后自动关闭文件，不过这一功能没有保证，最好还是养成自己关闭习惯，如果一个文件在关闭后还对其进行操作会产生ValueError 
9. fp.flush()  --把缓冲区的内容写入硬盘
10. fp.fileno()  --返回一个长整型"文件标签"
11. fp.isatty()  --文件是否是一个终端文件
12. fp.tell()    --返回文件操作标记的当前位置，以文件的开头为原点
13. fp.next()   --返回下一行，并将文件操作标记位移到下一行
14. fp.truncate([size]) 把文件裁成规定的大小，默认的是裁到当前文件操作标记的位置。

</pre>

##三、目录操作
<pre>
1. os.mkdir("file")    --创建目录

复制文件
2. shutil.copyfile("old","new")  --复制文件 old和new都只能是文件
3. shutil.copy("old","new")    --复制文件 old只能是文件夹，new可以是文件也可以是目录

复制目录
4. shutil.copytree("olddir","newdir") olddir和newdir都只能是目录，且newdir必须不存在

重命名目录（文件）
5. os.rename("oldname","newname") 文件或目录都是使用这条命令

移动文件（目录）
6. shutil.move("oldpos","newpos")

删除文件
7. os.remove("file")

删除目录
8. os.rmdir("dir") 只能删除空目录
9. shutil.rmtree("dir")  空目录、有内容的目录都可以删除

转换目录
10. os.chdir("path") 换路径
</pre>


<pre>
1. seek(offset,where) where=0 从起始位置移动，1从当前位置移动，2从结束位置移动，当有换行时，会被换行截断，seek()无返回值，故值为None

2. tell() 文件的当前位置，即tell是获取文件指针位置，受seek,readline,read,readlines影响，不受truncate影响
3. truncate(n):从文件的首行首字符开始截断，截断文件为n个字符；无n表示从当前位置起截断；截断之后n后面的所以字符被删除。
4. readline(n)  读入若干行，n表示读入的最长字节数。其中读取的位置为tell()+1 ,当n为空时，默认只读当前行的内容
</pre>
