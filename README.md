### 目的
哈囉，我現在要開始學C++和準備APCS。由於實際寫過發現自己 bug 太多，因此決定在這裡放我做過的一些題和 debug 次數（之後有機會隱藏？）請大家強烈公審我的 debug 次數以督促我好好寫並練習。
### 題
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
[TOJ 305](https://toj.tfcis.org/oj/pro/355/)（debug: 1）
```
#include<bits/stdc++.h>
using namespace std;
int main(){
    int n,k,v,f=1,s=1;
    cin>>n>>k;
    for(int i=0;i<n;i++){
        cin>>v;
        if(v>f){
            s=f;
            f=v;
        }
        if(v<f && v>s){
            s=v;
        }
    }
    cout<<s<<'\n';
}
```
