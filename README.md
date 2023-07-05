# C-p39-8-
C语言学习笔记 p39指针详解(8)
#include<stdio.h>
#include<string.h>
int main()
{
    //数组名是首元素地址
    //1.sizeof(数组名)-数组名表示整个数组
    //2.&数组名-数组名表示整个数组
    //一维数组
    int a[]={1,2,3,4};
    printf("%d\n",sizeof(a));//计算1数组大小，单位是字节-16
    printf("%d\n",sizeof(a+0));//4/8-数组名这里表示首元素的值，a+0还是首元素地址，地址大小就是4/8字节
    printf("%d\n",sizeof(*a));//4-数组名就是表示首元素地址，*a就是首元素，sizeof(*a)就是4
    printf("%d\n",sizeof(a+1));//4/8-a+1是第二个元素的地址
    printf("%d\n",sizeof(a[1]));//4-第二个元素的大小
    printf("%d\n",sizeof(&a));//4/8-&a取出的是数组的地址，但是数组的地址也是地址，地址的大小就是4/8个字节
    printf("%d\n",sizeof(*&a));//16-&a是数组的地址，数组的地址解引用访问的数组，sizeof计算的就是数组的大小，单位是字节
    printf("%d\n",sizeof(&a+1));//4/8-取出来的地址就是4/8，地址没有高低贵贱之分
    printf("%d\n",sizeof(&a[0]));//4/8 第一个元素的地址
    printf("%d\n",sizeof(&a[0]+1));//4/8 第二个元素的地址
    return 0;
}

int main()
{
    //字符数组
    char arr[]={'a','b','c','d','e','f'};
    printf("%d\n",sizeof(arr));//sizeof计算机的数组大小，6*1=6个字节
    printf("%d\n",sizeof(arr+0));//4/8 arr表示首元素地址，arr+0还是首元素地址 地址大小是4/8个字节
    printf("%d\n",sizeof(*arr));//1 arr是首元素的地址，*arr就是首元素，首元素是字符，大小是一个字节
    printf("%d\n",sizeof(arr[1]));//1
    printf("%d\n",sizeof(&arr));//4/8 虽然是数组的地址，但还是地址，地址的大小是4/8个字节
    printf("%d\n",sizeof(&arr+1));//4/8  &arr+1是跳过整个数组后的地址，地址的大小是4/8个字节
    printf("%d\n",sizeof(&arr[0]+1));//4/8 第二个元素的大小
    return 0;
}


int main()
{
    char arr[]={'a','b','c','d','e','f'};
    printf("%d\n",strlen(arr));//随机值
    printf("%d\n",strlen(arr+0));//随机值
    printf("%d\n",strlen(*arr));//err 这里传值传了个97 不是地址，这是非法访问
    printf("%d\n",strlen(arr[1]));//err 
    printf("%d\n",strlen(&arr));//随机值，与前面两个随机值也是一样的值
    printf("%d\n",strlen(&arr+1));//随机值 比上一个随机值多6
    printf("%d\n",strlen(&arr[0]+1));//随机值 比前面一个随机值少1
    return 0;
}
