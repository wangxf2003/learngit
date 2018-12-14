# 安装python及数据分析相关安装包小结

2017年02月03日 16:04:00 Cherzhoucheer 阅读数：2819 标签： python 数据分析 64位  更多
个人分类： python
版权声明：本文为博主原创文章，未经博主允许不得转载。	https://blog.csdn.net/CherDW/article/details/54847571



由于重装系统以及64位电脑安装了32位python导致数据量导入过大时，出现memoryerror错误，干脆总结安装过程，省得每次安装去找教程和资源。

 

### Python安装



从官方网站下载python，各种版本可供选择：https://www.python.org/downloads/windows/

这里选择的是64位2.7.11，下载地址为：https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64.msi

运行下载的MSI安装包，完成安装，默认会安装到C:\Python27目录下。

打开命令提示符窗口，敲入python后，会得到：
Error:‘python’不是内部或外部命令，也不是可运行的程序或批处理文件。

这是因为Windows会根据一个Path的环境变量设定的路径去查找python.exe，如果没找到，就会报错。解决办法是把python.exe所在的路径C:\Python27添加到Path中。

 

### Pip安装

下载最新的pip安装文件：http://pypi.python.org/pypi/pip#downloads
下载pip-7.1.2.tar.gz (md5, pgp)完成之后，解压到一个文件夹，用CMD控制台进入解压目录，输入：

> python setup.py install 

安装好之后，命令行输入pip，同样会显示'pip'不是内部命令，也不是可运行的程序，同样还是因为没有添加环境变量。解决办法是把C:\Python27\Scripts添加到Path中。




Jupyter Notebook安装
进行下面的步骤，这里可能回提示没有权限打开，这时候需要重启电脑。

> pip install --upgrade pip
> pip install jupyter

数据分析相关包的安装

> pip install numpy
> pip install pandas
> pip install matplotlib
> pip install scipy
> pip install scikit-learn

验证以上是否安装成功，如可以：import numpy,特别使用sklearn时，可能出现scipy\numpy相关错误，这时候需要手动安装这些包。把numpy、scipy、matplotlib、scikit-learn用pipuninstall掉，再去下载最新的whl包重新安装。

具体方案是：

在命令中输入以下指令卸载相应的包：

> pip uninstall numpy
> pip uninstall scipy
> pip uninstall matplotlib
> pip uninstall scikit-learn

在下面的网站中找到对应的包，python2.7就是cp27系列的，电脑是64位的一定下载对应版本：
http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy

http://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy

http://www.lfd.uci.edu/~gohlke/pythonlibs/#matplotlib

http://www.lfd.uci.edu/~gohlke/pythonlibs/#scikit-learn

找到安装Python的目录下的scipyts文件，在这个文件里安装相应的whl包，比如指令为

> cd C：Python27/Scipyts
> pip install D：/xxx/xxx/xxx.whl

如果显示有successful就是完成了。



==================================
pip install 在windows下始终因ascii报错UnicodeDecodeError
petanne petanne 2015-10-22 16:47:42
问题是使用pip install django 或其它时，始终报错：
UnicodeDecodeError: 'ascii' codec can't decode byte 0xb1 inposition 34: ordinal
not in range(128)

原因是windows的cmd环境默认为gbk编码，pip默认用utf8编码。
在Linux和Mac中，terminal环境默认的是utf8编码，所以不会报错。

解决方法：
python目录 Python27\Lib\site-packages 建一个文件sitecustomize.py 
内容为： 
import sys 
sys.setdefaultencoding('gbk') 

python会自动运行这个文件。

参考另一个同样的错误：pip install 出现报asciii码错误的问题

==================================