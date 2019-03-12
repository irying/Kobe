









作者：dawnmist

链接：https://www.zhihu.com/question/32087709/answer/54936403

来源：知乎

著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

个人经验，C++ primer 第一次可以跳着看。关键是要尽快用起来，在使用中熟练，而不是在细节中迷失。
以C++ Primer第五版为例，第一遍读的时候：
Part1也就是前七章，除了6.6，6.7节，都要通读。尤其是第三章初步介绍了vector和string，简直就是新手福音，搞定这两个容器就能写一些简单的程序。
Part2基本就是数据结构和算法，如果有基础读起来很轻松。
9，11两章介绍的容器，以及12.1节的智能指针要通读。多用智能指针和容器，远离segment fault. 第10章里的泛型算法可以慢慢读，读完以后可以写出高逼格的函数式风格C++。12.2节讲了怎么用new和delete分配空间，题主作为新手，知道这种写法就行，写程序时尽量用容器代替原始数组，尤其是代码里最好不要有delete。
Part3是块硬骨头，标题就是Tools for Class Authors. 作为一个"class user"，有些部分第一次是可以略过的。
13章很重要，要细读。初始化，复制，赋值，右值引用是C++里很微妙很重要的部分，别的语言对于这些概念很少有区分得这么细的。这一章不但要精读，还要完全掌握。
14章的操作符重载第一次可以观其大略；14.9节第一次可以跳过。
15章讲OOP，重要性不言而喻。如果之前一点概念都没有，学起来会觉得比较抽象。网上关于OOP有很多通俗有趣的文章，可以一起看看。
16章讲泛型编程，第一次读16.1节，掌握最基本的函数模板和类模板就行了。
Part4就更高档了，很多内容第一次就算啃下来，长久不用又忘了。第一次读推荐把18.2节读懂，命名空间简单易用效果好。别的内容可以观其大略，用时再看。17.1节的tuple是个有趣的东东，可以读一读。17.3节的正则表达式和17.4节的随机数也许有用，也可以读一读。如果需要读写文件，要读一下17.5.2节的raw I/O和17.5.3节的random I/O。

最后给题主的建议是，写C++，要尽量避免C的写法。用static_cast而不是括号转换符；用vector而不是C里面的数组；用string而不是char *；用智能指针而不是原始指针。当然I/O是个例外，printf()还是比cout好用的；转换数字和字符串时sprintf()也比stringstream快



![](https://ws1.sinaimg.cn/large/e5b38bb8gy1g0wfggx47bj216c0y4qgb.jpg)





https://blog.csdn.net/u011675745/article/details/51939108



首先，endl是一个操作符（Manipulators），但我们必须知道endl是一个什么类型的变量。endl是跟在”<<“运算符后面，故endl应该是一个参数。其实endl是一个函数名，它是一个"<<"运算符重载函数中的参数，参数类型为函数指针。下面我们看下内部函数实现。

```
ostream& ostream::operator << ( ostream& (*op) (ostream&))
{
// call the function passed as parameter with this stream   as the argument
return (*op) (*this);
}

std::ostream& std::endl (std::ostream& strm)
{
    // write newline
    strm.put('\n');
    // flush the output buffer
    strm.flush();
    // return strm to allow chaining
    return strm;
}
```

可以看出，运算符重载函数中的函数参数为一个函数指针，其指向一个输入输出均为ostream类引用的函数。而endl正是这样一个函数。所以我们在运行"cout<<endl;"语句时，<u>**endl是一个函数参数，类型为函数指针。然后会执行”return (*endl) (*this);“语句，即执行endl函数。endl函数输出一个换行符，并刷新输出缓冲区。</u>**



![](https://ws1.sinaimg.cn/large/e5b38bb8gy1g0wfr48obyj216m0d8ae4.jpg)





![image-20190309163339722](/Users/xiangyu.liu/Library/Application Support/typora-user-images/image-20190309163339722.png)





![image-20190309173209510](/Users/xiangyu.liu/Library/Application Support/typora-user-images/image-20190309173209510.png)

![image-20190309212451226](/Users/xiangyu.liu/Library/Application Support/typora-user-images/image-20190309212451226.png)





![image-20190309213051477](/Users/xiangyu.liu/Library/Application Support/typora-user-images/image-20190309213051477.png)





![image-20190309232412767](/Users/xiangyu.liu/Library/Application Support/typora-user-images/image-20190309232412767.png)





![image-20190310112854276](/Users/xiangyu.liu/Library/Application Support/typora-user-images/image-20190310112854276.png)







![image-20190310112935474](/Users/xiangyu.liu/Library/Application Support/typora-user-images/image-20190310112935474.png)









![image-20190310134651354](/Users/xiangyu.liu/Library/Application Support/typora-user-images/image-20190310134651354.png)







![image-20190310135320416](/Users/xiangyu.liu/Library/Application Support/typora-user-images/image-20190310135320416.png)



![image-20190310135557631](/Users/xiangyu.liu/Library/Application Support/typora-user-images/image-20190310135557631.png)





![image-20190310155614700](/Users/xiangyu.liu/Library/Application Support/typora-user-images/image-20190310155614700.png)



![image-20190310161918094](/Users/xiangyu.liu/Library/Application Support/typora-user-images/image-20190310161918094.png)





![image-20190310162813871](/Users/xiangyu.liu/Library/Application Support/typora-user-images/image-20190310162813871.png)



![image-20190310163632414](/Users/xiangyu.liu/Library/Application Support/typora-user-images/image-20190310163632414.png)



![image-20190310164042562](/Users/xiangyu.liu/Library/Application Support/typora-user-images/image-20190310164042562.png)





![image-20190310165202727](/Users/xiangyu.liu/Library/Application Support/typora-user-images/image-20190310165202727.png)





![image-20190310165254109](/Users/xiangyu.liu/Library/Application Support/typora-user-images/image-20190310165254109.png)



![image-20190310174801574](/Users/xiangyu.liu/Library/Application Support/typora-user-images/image-20190310174801574.png)



![image-20190310180220670](/Users/xiangyu.liu/Library/Application Support/typora-user-images/image-20190310180220670.png)





![image-20190310182046579](/Users/xiangyu.liu/Library/Application Support/typora-user-images/image-20190310182046579.png)



![image-20190310184111530](/Users/xiangyu.liu/Library/Application Support/typora-user-images/image-20190310184111530.png)





