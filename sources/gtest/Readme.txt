gtest���Կ��ļ�Ŀ¼����Ҫ����gtest-1.6.0�µ�ԭʼ�ļ������ɶ����ͷ�ļ��Ϳ��ļ���
�������ɰ취���£�
1. ���뱾Ŀ¼��

window ����������debug�汾�Ŀ�
visual studio 2012 ��Ҫ�޸�CMakeLists.txt, ��� ������ 
    add_definitions(-D_VARIADIC_MAX=10)
1. mkdir build && cd build
2. cmake .. -G "NMake Makefiles" -Dgtest_force_shared_crt=ON -DCMAKE_BUILD_TYPE=DEBUG -DCMAKE_INSTALL_PREFIX=D:\works\hosting\trunk\library\gtest
2. cmake .. -G "NMake Makefiles" -Dgtest_force_shared_crt=ON -DCMAKE_BUILD_TYPE=DEBUG -DCMAKE_INSTALL_PREFIX=I:\hosting\newcode\thirdparty
3. nmake 
4. nmake install

window ����������Release�汾�Ŀ�
1. mkdir build && cd build
2. cmake .. -G "NMake Makefiles" -Dgtest_force_shared_crt=ON -DCMAKE_BUILD_TYPE=RELEASE -DCMAKE_INSTALL_PREFIX=D:\works\hosting\trunk\library\gtest
3. nmake 
4. nmake install

linux ��װ��
1.mkdir build && cd build
2.cmake -DCMAKE_INSTALL_PREFIX=~/works/library/gtest ..
3.make
4.make install
