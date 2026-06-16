# ZJ-f312. 1.人力分配
正式準備APCS後第一次寫ZJ考古題。
## 聲明
由於實際寫過發現自己第一版 bug 太多，因此目前會把寫過的題目設成公開並放上 debug 次數（之後有機會隱藏？）請大家督促我練習並強烈譴責我的 debug 次數。\
[Zero Judge-f312. 1.人力分配](https://zerojudge.tw/ShowProblem?problemid=f312)

- 嘗試只用 if/else (debug: 5)
```
#include<bits/stdc++.h>
using namespace std;
int main(){
    int a1,b1,c1,a2,b2,c2,n,a,b,c;
    cin>>a1>>b1>>c1>>a2>>b2>>c2>>n;
    a=a1+a2;
    b=b1-2*n*a2-b2;
    c=c1+n*n*a2+n*b2+c2;
    double d=(-1.0)*b/(2*a);
    if(a>=0){
        if(d<=n/2.0){
            cout<<a*n*n+b*n+c<<'\n';
        }
        else{
            cout<<c<<'\n';
        }
    }
    else{
        if(d<=0){
            cout<<c<<'\n';
        }
        else if(d>=n){
            cout<<a*n*n+b*n+c<<'\n';
        }
        else if(d-int(d)<=0.5){
            cout<<a*int(d)*int(d)+b*int(d)+c<<'\n';
        }
        else{
            cout<<a*int(d+1)*int(d+1)+b*int(d+1)+c<<'\n';
        }
    }
}
```
- 用 max/min (debug: 4)
```
#include<bits/stdc++.h>
using namespace std;
int main(){
    int a1,b1,c1,a2,b2,c2,n,a,b,c;
    cin>>a1>>b1>>c1>>a2>>b2>>c2>>n;
    a=a1+a2;
    b=b1-2*n*a2-b2;
    c=c1+n*n*a2+n*b2+c2;
    double d=(-1.0)*b/(2*a);
    if(a>=0){
        if(d<=n/2.0){
            cout<<a*n*n+b*n+c<<'\n';
        }
        else{
            cout<<c<<'\n';
        }
    }
    else{
        if(d<=0){
            cout<<c<<'\n';
        }
        else if(d>=n){
            cout<<a*n*n+b*n+c<<'\n';
        }
        else if(d-int(d)<=0.5){
            cout<<a*int(d)*int(d)+b*int(d)+c<<'\n';
        }
        else{
            cout<<a*int(d+1)*int(d+1)+b*int(d+1)+c<<'\n';
        }
    }
}
```
