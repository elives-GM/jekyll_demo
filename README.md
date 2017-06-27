# jekyll_demo


Tmp: 

### 1. rpath
连接器在处理动态库时将链接时路径（Link-time path）和运行时路径（Run-time path）分开,用户可以通过-L指定连接时库的路径，通过-R（或-rpath）指定程序运行时库的路径，大大提高了库应用的灵活性。比如我们做嵌入式 移植时#arm-Linux-gcc $(CFLAGS) –o target –L/work/lib/zlib/ -llibz-1.2.3 (work/lib/zlib下是交叉编译好的zlib库)，将target编译好后我们只要把zlib库拷贝到开发板的系统默认路径下即可。或者通过- rpath（或-R ）

gcc中的rpath用法: -Wl,-rpath,dir
多个dir之间用冒号分隔: -Wl,-rpath,dir1:dir2:...:dirN

对于我们的项目：
LD_RUN_PATH=-Wl,-rpath,$(LOG_LIB_PATH)

${EXE_FILE}: ${OBJ_FILE}
 ${CC} ${CXXFLAGS} $(LD_RUN_PATH) -o ${EXE_FILE}  ${OBJ_FILE}  ${LIBS}

### 2. Xlinker
-Xlinker:
https://www.ibm.com/developerworks/cn/linux/l-cn-linklib/

### 3. 
-L:
-I /home/hello/include表示将/home/hello/include目录作为第一个寻找头文件的目录，寻找的顺序是：/home/hello/include-->/usr/include-->/usr/local/include
-L /home/hello/lib表示将/home/hello/lib目录作为第一个寻找库文件的目录，寻找的顺序是：/home/hello/lib-->/lib-->/usr/lib-->/usr/local/lib
-lworld表示在上面的lib的路径中寻找libworld.so动态库文件（如果gcc编译选项中加入了“-static”表示寻找libworld.a静态库文件）

### 4. 
-lpthread -lgcov -lmockcpp

http://blog.csdn.net/haifengid/article/details/51732438

http://blog.csdn.net/linxuping/article/details/7068213
