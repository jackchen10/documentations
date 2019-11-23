# Linux常用命令

## 1 查看Linux内核版本命令（两种方法）
  * cat /proc/version
  * uname -a

## 2 cp命令
  * cp就是拷贝，最简单的使用方式就是：
		cp oldfile newfile
  * 但这样只能拷贝文件，不能拷贝目录，所以通常用：
		cp -r old/ new/
		那就会把old目录整个拷贝到new目录下。
		注意，不是把old目录里面的文件拷贝到new目录，而是把old直接拷贝到new下面，结果是：
		[root@dc5 test]# ll new/
		total 4
		drwxr-xr-x 2 root root 4096 Dec 15 11:55 old
  * 那如果要保持源文件的所有权限，可以这样：
		cp -rp old/ new/
		-p参数，可以保持权限、宿主、时间栈，还可能包括link等；
  * 还有更简单的，就是用：
		cp -a old/new/
		-a参数，就等于-dpR
