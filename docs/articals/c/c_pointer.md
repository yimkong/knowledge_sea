## 基本使用
?> 在c语言里，指针是一个宏大而又复杂的话题，值得好好学习与思考

通常使用步骤为： 
1. 定义一个指针变量，`int *ip;`，声明的时候在变量名字前加个*代表这个是指针，指针变量是用来存放内存地址的变量
2. 把变量地址赋值给指针，`ip = &var;`，在变量名字前加个&就是拿地址，例如`&z[0]`就是拿数组的第一格地址
3. 访问指针变量中可用地址的值,`*ip = 0; // var is now 0`，给指针指向的变量赋值的时候在变量名字前加个*

疑问：对于指针来说，不管什么类型的数据都是一样的内存地址，为什么要区分类型？

指针例子：
```C
#include <stdio.h>

main(){
    int x = 1, y = 2, z[10];
    int *ip; //define pointer
    ip = &x; // ip point to x now
    printf(*ip);
    y = *ip; // y is now 1
    *ip = 0; // x is now 0
    ip = &z[0]; // ip now points to z[0]
}
```
