Android-MountDevInfos
=====================

兼容多张sd卡的手机 获取多张sd卡信息 - Compatible with multiple sd card , get multiple sd card information


sdk api里的Environment.getExternalStorageDirectory()只会返回主存储卡
 
vold.fstab就在etc目录下 前面一般都是语法注释 但一般格式都是类似这样：
dev_mount sdcard /storage/sdcard0 auto...
 
其中sdcard 表示设备挂载名称 /storage/sdcard0 是挂载路径 auto是可选参数 表示主存储卡（甚至有发烧友 自己用RE文件管理器修改auto参数 重启后 来做到调换主副存储卡 因为有些手机默认主存储卡空间小 而一般应用数据默认会存到主存储卡）
 
系统启动的时候 init进程会去读这个文件 来挂载存储卡设备 
 
这个文件用java 基本io bufferreader之类的也能直接读 只是自己要去解析下
 
用反射的话 兼容性会更好些 因为不能保证ROM发布者不会修改这文件的语法格式（但目前没发现过）
