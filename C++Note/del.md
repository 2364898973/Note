>main():相当于int main()  
>int main():int是main()函数的返回类型。这表明main()函数返回的值是整数且授受任何数量的参数。  
>void main():void为空型。这表明main()函数无返回值且接受任何数量的参数。  
>int main(void):main()函数不接受任何参数且返回的值是整数。  
#### 另外请注意：
>main()为老式的写法。返回类型int在新型的编泽器通不可以省略，否则会有警告：  
>void main()为老式的写法。  
>int main()和int main(void)为新的写法。  
>在C/C++中声明主函数要么写成int main()，要么写成int main(void)。main()、void main()和void main(void)这三种写法尽量放弃。
             
1.本题要求实现一个计m~n（m<n）之间所有整数的和的简单函数。
```
#include <stdio.h>
int sum(int m, int n);
int main()
{    
    int m, n;
    scanf("%d %d", &m, &n);
    printf("sum = %d\n", sum(m, n));
    return 0;
}
/* 你的代码将被嵌在这里 */
int sum(int m,int n){
    int fact=0;
    for(m;m<=n;m++){
        fact+=m;
    }
    return fact;
}
```
2.判断素数
```
#include <stdio.h>
int main()
{
	int x;
	scanf("%d",&x);
	if(x==1) printf("%d不是素数\n",x),return 0;
	for(i=2;i<=sqrt(x);i++){
		if(x%i==0){
			printf("%d不是素数\n",x);
                        return 0;
		}
	}
	printf("%d是素数\n",x);
	return 0;
}
```
3.输入2个正整数lower和upper（lower≤upper≤100），请输出一张取值范围为[lower，upper]、且每次增加2华氏度的华氏-摄氏温度转换表。     
温度转换的计算公式：C=5×(F−32)/9，其中：C表示摄氏温度，F表示华氏温度。   
```
#include <stdio.h>
int main(void)
{
    int fahr,lower,upper;
    double celsius;
    scanf("%d%d",&lower,&upper);
    if(lower<=upper&&upper<=100){
        printf("fahr celsius\n");
        for(fahr=lower;fahr<=upper;fahr+=2){
            celsius=5.0*(fahr-32)/9.0;
            printf("%d%6.1f\n",fahr,celsius);}
        } else{
    printf("Invalid.");
    }
    return 0;
}
```
4.本题要求编写程序，计算序列 1 + 1/2 + 1/3 + ... 的前N项之和。
```
#include <stdio.h>
int main(void)
{
    int i,n,denominator;
    double item,sum;
scanf("%d",&n);(在PTA中不要写关于提示输入的信息）：
printf(“enter n:”);这是wrong/invalid
    denominator=1;
    item=1;
    sum=0;
    for(i=1;i<=n;i++){
        sum+=item;
        denominator++;
        item=1.0/denominator;
    }
    printf("sum = %f\n",sum);
    return 0;
}
```
5.输入一个非负整数n，生成一张3的乘方表，输出3 0~3 n的值。可调用幂函数计算3的乘方。
```
#include <stdio.h>
#include <math.h>
int main(void)
{
    int i,n;
    scanf("%d",&n);
    for(i=0;i<=n;i++){
        printf("pow(3,%d) = %.0f\n",i,pow(3,i));
    }
    return 0;
}
```
**调用的数学函数都是double类型**  
6.本题要求编写程序，计算交错序列 1-2/3+3/5-4/7+5/9-6/11+... 的前N项之和。
```
#include <stdio.h>
int main(void)
{
    int i,n,fact,denominator;
    double item,sum;
    scanf("%d",&n);
    fact=1;
    denominator=1;
    item=1;
    sum=0;
    for(i=1;i<=n;i++){
        sum+=item;
        fact=-fact;
        denominator+=2;
        item=fact*1.0*(i+1)/denominator;
    }
    printf("%.3f\n",sum);
    return 0;
}  正确
#include <stdio.h>
int main(void)
{
    int i,n,fact,denominator;
    double item,sum;
    scanf("%d",&n);
    fact=1;
    denominator=1;
    item=1;
    sum=0;
    for(i=1;i<=n;i++){
        sum+=item;
        fact=-fact*(i+1);
        denominator+=2;
        item=fact*1.0/denominator;
    }
    printf("%.3f\n",sum);
    return 0;
} 错误
```
7.输出21世纪中截止某个年份以来的所有闰年年份。注意：闰年的判别条件是该年年份能被4整除但不能被100整除、或者能被400整除。
>输入格式:  
>输入在一行中给出21世纪的某个截止年份。  
>输出格式:  
>逐行输出满足条件的所有闰年年份，即每个年份占一行。输入若非21世纪的年份则输出"Invalid year!"。若不存在任何闰年，则输出“None”。  
```
#include<stdio.h>
int main(){
    int n,a,b,flag=0;
    scanf("%d",&n);
    if (n < 2001||n > 2100){
        printf("Invalid year!\n");
        return 0;}
    else
        for (int i = 2000;i <= n;i += 4){
            if ((i % 4 == 0&&i % 100 != 0)||i % 400 == 0)
                if (i != 2000){
                printf("%d\n",i);
                flag = 1;
        }
        }
    if (flag == 0)
        printf("None");
    return 0;
}
#include <stdio.h>
int main(void)
{
    int i ,year;
    scanf("%d",&year);
    if(year<=2000||year>=2100)
    {
        printf("Invalid year!\n");
    } else if(year>2000&&year<2004){
                printf("None\n");}
        else{
        for(i=2001;i<=year;i++){
            if(i%4==0)
            {
                printf("%d\n",i);} 
			}
        }
    return 0;
}
```
8.本题要求将输入的任意3个整数从小到大输出。
>输入格式:   
>输入在一行中给出3个整数，其间以空格分隔。   
>输出格式:   
>在一行中将3个整数从小到大输出，其间以“->”相连。       
>输入样例:     
>4 2 8     
>输出样例:   
>2->4->8   
```
#include <stdio.h>
int main(void)
{
    int a,b,c;
    scanf("%d%d%d",&a,&b,&c);
    if(a==b&&b==c){
        printf("%d->%d->%d",a,b,c);
    }
    if(a>b&&b>c){
        printf("%d->%d_>%d",c,b,a);
    }
    if(a>b&&b<c&&a>c){
        printf("%d->%d->%d",b,c,a);
    }
    if(a>b&&b<c&&a<c){
        printf("%d->%d->%d",b,a,c);
    }
    if(b>a&&a>c){
        printf("%d->%d->%d",c,a,b);
    }
    if(b>a&&a<c&&b>c){
        printf("%d->%d->%d",a,c,b);
    }
    if(b>a&&a<c&&b<c){
        printf("%d->%d->%d",a,b,c);
    }
    return 0;
} 错误
#include<stdio.h>
int main()
{
  int x,y,z,min;
  scanf("%d %d %d",&x,&y,&z);
  //将x位置存放xy中最小的那个 
  if(x>y)
  {
  	min = x;
  	x = y;
  	y = min;  	
  }
  //将x位置存放xz中最小的那个
  if(x>z)
  {
  	min = x;
  	x = z;
  	z = min;
  }
  //经过以上两步，x位置已经是三个数中最小的了，现在仅需将yz中小的那个放到y位置即可 
  if(y>z) 
  {
  	min = y;
  	y = z;
  	z = min;
  }
   printf("%d->%d->%d",x,y,z);
  return 0;
}
//如果第一个if判断不成立，则直接进行下面x与z的比较 
//如果二个if判断仍不成立，则直接进行下面y与z的比较 
//如果三个if判断仍不成立，则直接输出
正确
```
9.按照规定，在高速公路上行使的机动车，达到或超出本车道限速的10%则处200元罚款；若达到或超出50%，就要吊销驾驶证。请编写程序根据车速和限速自动判别对该机动车的处理。
>输入格式:   
>输入在一行中给出2个正整数，分别对应车速和限速，其间以空格分隔。   
>输出格式:    
>在一行中输出处理意见：若属于正常行驶，则输出“OK”；若应处罚款，则输出“Exceed x%. Ticket 200”；若应吊销驾驶证，则输出“Exceed x%. License Revoked”。其中x是超速的百 
>分比，精确到整数。   
```
#include<stdio.h>
int main()  
{  
    int a,b;  
    int exceed;  
    scanf("%d %d",&a,&b);  
    exceed=(double)(a-b)/b*100+0.5;*四舍五入的方法
    if(exceed<10){  
        printf("OK\n");  
}
else if(exceed<50)
{  
        printf("Exceed %d%%. Ticket 200\n", exceed);  
}
else
{  
        printf("Exceed %d%%. License Revoked\n", exceed);  
    }  
    return 0;  
}
```
10.统计整数位数
```
#include <stdio.h>
int main(void)
{
	int count,number,t_number;
	count=0;
	printf("Enter a number:");
	scanf("%d",&number);
	t_number=number;/*保护输入数据number的值不被改变*/
	if(number<0){
		t_number=-t_number;
	}
	do{
		count++;
		t_number=t_number/10;
	} while(t_number!=0);
	printf("It contains %d digits.\n",count);
	return 0;
}
```
11.自然常数e可以用级数1+1/1!+1/2!+⋯+1/n!+⋯来近似计算。本题要求对给定的非负整数n，求该级数的前n+1项和。
```
#include <stdio.h>
int main(void)
{
    int i,j,n,denominator;
    double item,sum;
    i=1;
    j=1;
    denominator=1;
    item=1.0;
    sum=0;
    scanf("%d",&n);
    if(n<=1000&&n>0){
        for(i=1;i<=n;i++){
            for(j=1;j<=i;j++){
            denominator=denominator*j;    
            }
            item=1.0/denominator;
            sum=sum+item;
        }
    }
    sum=sum+1.0;
    printf("%.8f\n",sum);
    return 0;
}(n>10,为什么会出现问题)
```
12.判断的优化(第一个为假，后面的不再执行)。   
13.%在C中是格式控制符，用于字符串中，比如%d表示这里是一个整数，而%%表示这里就是一个“%”符，让程序不要理解成格式符。   
14.查找指定字符     
本题要求编写程序，从给定字符串中查找某指定的字符。     
>输入格式：输入的第一行是一个待查找的字符。第二行是一个以回车结束的非空字符串（不超过80个字符）。   
>输出格式：如果找到，在一行内按照格式“index = 下标”输出该字符在字符串中所对应的最大下标（下标从0开始）；否则输出"Not Found"。   
>输入样例1：  
>m   
>Programming   
>输出样例1：     
>index = 7   
>输入样例2：   
>a   
>1234   
>输出样例2：   
>Not Found   
```
#include <stdio.h>  
#include <string.h>  
#define MAX 100  
int main(void){  
    char ch,s[MAX];
    scanf("%c",&ch);
    getchar();       //有一个换行，一定要去掉
    //gets(s);       //法一
    scanf("%[^\n]s",s);//法二
    int length=strlen(s),max=-1;  
    for(int i=0;i<length;i++){  
        if(s[i]==ch){  
            max=i;  
        }  
    }  
    if(max==-1){  
        printf("Not Found\n");  
    } else{  
        printf("index = %d\n",max);  
    }  
    return 0;  
}
```
15.关于输入scanf（）详解：     
[%2d，%02d](https://cloud.tencent.com/developer/article/2186323)   
16.ceil():向上取整 floor():向下取整&emsp;round():四舍五入取整    
17.  
1. cin>>：   
>用法1：输入一个数字或字符。   
>用法2：接收一个字符串，遇“空格”、“TAB”、“回车”就结束。   
2. cin.getline()：用法:接收一个字符串，可以接收空格并输出。延伸：   
>cin.getline()实际上有三个参数，cin.getline(接收字符串的变量,接收字符个数,结束字符)   
>当第三个参数省略时，系统默认为'\0'   
如果将例子中cin.getline()改为cin.getline(m,5,'a');当输入jlkjkljkl时输出jklj，输入jkaljkljkl时，输出jk。     
3. getline()：用法：接收一个字符串，可以接收空格并输出，需包含“#include<string>” 。    
**注意的问题：**   
>cin.getline()属于istream流，而getline()属于string流，是不一样的两个函数   
>当同时使用cin>>,getline()时，需要注意的是，在cin>>输入流完成之后，getline()之前，需要通过str="\n";getline(cin,str);的方式将回车符作为输入流cin以清除缓存，如果不>这样做的话，在控制台上就不会出现getline()的输入提示，而直接跳过，因为程序默认地将之前的变量作为输入流。
   
18.C++编程语言中重载运算符（operator）：   
```
bool operator==(const vector<PII>a,const vector<PII>b){
        return a[0]==b[0]&&a[1]==b[1];
    }
```
19.C++中stoi()、atoi()、to_string()使用技巧   
**stoi()、atoi()、to_string()这三个函数都是对字符串处理的函数，前两者是将字符串转化为十进制 int 类型，最后一个是将十进制类型 int、double 等转化为string。**
**头文件都是：#include \<cstring>**
1. stoi()和atoi()  
>这两个功能虽然都是将字符串转化为 int 类型，但是还是有区别的，  
>stoi 的参数是 const string* 类型   
>atoi 的参数是 const char* 类型   
>stoi() 会对转化后的数进行检查，判断是否会超出 int 范围，如果超出范围就会报错；   
>atoi() 不会对转化后的数进行检查，超出上界，输出上界，超出下界，输出下界；
 
还有一点，如果使用 atoi()对字符串 string进行转化的话，就需要c_str() 函数将const string/*类型转化为cons char/*类型    

```
#include<iostream>
#include<cstring>
using namespace std;

int main() {
	string s = "12345";
	int num1 = stoi(s);
	int num2 = atoi(s.c_str());// 转化为const char* 
	cout << num1 << endl << num2 << endl;
	return 0;
}
```
2. to_string()
>功能：将数字常量（int,double,long等）转换为字符串（string），返回转换好的字符串
```
#include<iostream>
#include<cstring>
using namespace std;

int main() {
	int num = 123456789;
	string s = to_string(num);
	cout << s << endl;
	return 0;
}
```
