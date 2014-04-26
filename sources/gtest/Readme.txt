gtest测试库文件目录，需要根据gtest-1.6.0下的原始文件，生成对象的头文件和库文件。
具体生成办法如下：
1. 进入本目录。

window 环境下生成debug版本的库
visual studio 2012 需要修改CMakeLists.txt, 添加 如下行 
    add_definitions(-D_VARIADIC_MAX=10)
1. mkdir build && cd build
2. cmake .. -G "NMake Makefiles" -Dgtest_force_shared_crt=ON -DCMAKE_BUILD_TYPE=DEBUG -DCMAKE_INSTALL_PREFIX=D:\works\hosting\trunk\library\gtest
2. cmake .. -G "NMake Makefiles" -Dgtest_force_shared_crt=ON -DCMAKE_BUILD_TYPE=DEBUG -DCMAKE_INSTALL_PREFIX=I:\hosting\newcode\thirdparty
3. nmake 
4. nmake install

window 环境下生成Release版本的库
1. mkdir build && cd build
2. cmake .. -G "NMake Makefiles" -Dgtest_force_shared_crt=ON -DCMAKE_BUILD_TYPE=RELEASE -DCMAKE_INSTALL_PREFIX=D:\works\hosting\trunk\library\gtest
3. nmake 
4. nmake install

linux 安装：
1.mkdir build && cd build
2.cmake -DCMAKE_INSTALL_PREFIX=~/works/library/gtest ..
3.make
4.make install
