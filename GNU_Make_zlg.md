#### Sweet Tips

##### Tip One
Make's compilation idea is very simple. If the source program changes and you need to rebuild the program or other output files, make first check the __timestamps__ and change them, and rebuild these files as required, without wasting time rebuilding other files.

##### Tip Two
When you type the make command on the terminal, the make tool will be called. Make will look for the Makefile in the current directory according to the file name order, followed by: GNUmakefile, makefile, __Makefile__. If you find any of them, read it and follow the rules in it, otherwise you will get an error.

##### Tip Three
If you are not favorate of the names, like GNUmake, makefile, Makefile, you are free to name your Makefile file. For instance, `rockchipapp.mk`. But remember, you must enter the command `make -f rockchipapp.mk` , if you try to compile your code.

##### Tip Four
When you use Makefile to build your source code or gemerate your system image, you should think about the execution time. For example, the latter operation use the result A generates by the previous operation. For this case, you should pay attention to how much time it would cost to generate the result A.

##### Tip Five

###### make options table

| Options | Descriptions                                                 | Remarks |
| ------- | ------------------------------------------------------------ | ------- |
| -C dir  | 指定 make 开始运行之后的工作目录为指定目录,不用-C 指定默认为当前目录 |         |
| -d      | 打印除一般处理信息之外的调试信息,例如进行比较的文件的时间,尝试的规则等 |         |
| -e      | 不允许在 makefile 中对环境变量赋新值,即丢弃与环境变量同名的自定义变量 |         |
| -f file | 使用指定文件为 makefile                                      |         |
| -i      | 忽略 makefile 运行时命令产生的错误,不退出 make               |         |
| -I dir  | 指定 makefile 运行时的包含目录,多个包含目录用空格分隔        |         |
| -S      | 执行 makefile 时遇到错误即退出。这是 make 的默认工作方式,无需指定 |         |
| -v      | 打印 make 版本号                                             |         |
|         |                                                              |         |





For example

```

#Build u-boot
cd u-boot
make rk3399_box_defconfig
./mkv8.sh

sleep 2

#Building kernel
cd kernel
make rockchip_defconfig
make rk3399-rock960-model-ab.img -j4
cd ..

sleep 2

#Building AOSP
source build/envsetup.sh
lunch rk3399_box-userdebug
make -j4

sleep 2

#Generate images
if
	ln -s RKTools/linux/Linux_Pack_Firmware/rockdev/ rockdev

./mkimage.sh

sleep 2

#Pack all partitions into one image
cd rockdev

if
	ln -s Image-rk3399_box Image

./mkupdate.sh

if update.img exists
	echo "update.img is ready."


```


