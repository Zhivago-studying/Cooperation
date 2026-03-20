# CMake Note

## 语法特性

> + 基本语法 ```指令（参数 变量 ...）```  
  参数间只能用空格或分号隔开；  
  指令大小写无关；参数大小写相关；  
  变量用${}取值，IF 语句中直接使用变量名；  

## 指令

> + 指定最小版本  
> ```cmake_minimum_required(VERSION 3.0)``` # 指定最低版本为3.0  

> + 定义工程名称  
> ```project(HELLOWORLD)```  #可选语言  工程名为HELLOWORLD  

> + 显式的定义变量  
> ```set(SRC sayhello.cpp hello.cpp)```  # 定义SRC变量，值为sayhello.cpp hello.cpp

> + 向工程添加多个特定头文件搜索路径  
> ```include_directories(dir1 dir2)``` # 可添加多个路径  

> + 向工程添加多个特定库搜索路径  
> ```link_directories(dir1 dir2)``` # 可添加多个路径  

> + 生成库文件
> ```add_library(libname [STATIC|SHARED|MULDABLE] ${SRC})``` # 通过SRC变量生成libname库文件  

> + 添加编译参数
> ```add_definitions(<参数1> <参数2> ...)``` # 添加编译参数  

> + 生成可执行文件  
> ```add_executable(exe_name ${SRC})``` # 通过SRC变量（或直接用CPP文件）生成exe_name可执行文件  

> + 为target添加需要链接的共享库  
> ```target_link_libraries(可执行文件 lib1 lib2 ...)``` # 将lib1 lib2 ...链接到可执行文件  

> + 向当前工程添加存放源文件的子目录，并可指定中间二进制和目标二进制存放位置  
> ```add_subdirectory(src)``` # 添加src子目录,src中必须含有CMakeLists.txt  

> + 发现一个目录下的所有源文件并将列表储存在变量中，这个指令临时被用来自动构建源文件列表  
> ```aux_source_directory(dir src)``` # 将dir（.表当前目录）目录下的所有源文件列表储存在src变量中  
> 然后就可以用add_executable(exe_name ${src})来生成可执行文件了  

## 变量

+ ```CMAKE_C_FLAGES``` gcc编译选项
+ ```CMAKE_CXX_FLAGS``` g++编译选项
+ ```CMAKE_BUILD_TYPE``` 编译类型（debug/release）
+ ```XXX_FOUND  ```      代表库是否查找成功  
+ ```XXX_INCLUDE_DIRS ```   代表头文件的路径  
+ ```XXX_LIBRARIES```    代表库文件的名称

## CMake 编译工程

### 采用外部构建

+ 创建工程目录下创建build目录  
+ 进入build目录  
+ 执行cmake ..  生成Makefile  
+ 执行make，生成可执行文件  
