# 《C++ 程序设计语言*第四版》 中文勘误

---

* P122：把补码改成反码

译文：一个8位的字节所能容纳的256个值既可以被看成0~255，也能被看成-127~127。注意：不是像你想象的-128～127。因为C++标准支持使用补码的硬件设备，而补码会排除掉一个值，所以如果我们使用-128的话代码就不容易移植了。


原文：the C++ standard leaves open the possibility of one's complement （反码）hardware and that eliminates one value; thus, a use of –128 is nonportable. 

---

* P123:代码错误

``` C++
// 译文
singed char sc = -160
//原文
singed char sc = -140
P166：Map类函数声明形参错误
template <class K,class V>
class Map{
    public:
        V& operator[](const K& k);//返回与键值k对应的值
}
```

---

* P180：函数错误

``` C++
ostream& operator<<(ostream& os, Point p)
{
     //中文翻译版错误如下
     //return os << '{' << p[i].x << ',' << p[i].y << '}';
     //英文原文是正确的
     return os << '{' << p.x << ',' << p.y << '}';
}
```

---

* P217：变量名字错误

``` C++
default:
    if (isalpha(ch)) {
        //string_value = ch; 错误的版本
        ct.string_value = ch;//正确的版本
        while (ip->get(ch) && isalnum(ch))
            ct.string_value += ch;
        ip->putback(ch);
        return ct = {Kind::name};
    }
```

---

* P223：多打了一个加号

译文（错误）：a++++1 的意思是 (a++)+1 

原文：a+++1 means (a ++) + 1

---
* P310：struct类不完整
```c++
template<typename F>
struct Final_action {
      Final_action(F f): clean{f} {}
      ~Final_action() { clean(); }
      F clean;
      Final_action(const Final_action&) =delete;       // not meant to be copied (§3.3.4, §17.6.4)
      Final_action& operator=(const Final_action&) =delete;
};
```

---
* P340：函数调用中参数太少

```c++
namespace Parser {
	double expr(bool);
	double term(bool);
	double prim(bool);
}

double val = Parser::expr(true);

double Parser::expr(bool b)
{
	//...
}

```

* P343：缺少分号

```c++
namespace N {
	struct S { int i; };
	void g(S);
	void f(S);
	void h(int);
}
```

* P367：头文件中不该包含以下内容，无名名字空间代码错误

|内容|代码|
|:---:|:---:|
|无名名字空间|namespace{/**/}|
