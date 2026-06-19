### 目的
哈囉，我現在要開始學C++和準備APCS。由於實際寫過發現自己 bug 太多，因此決定在這裡放對我來說有代表性的題（例如用新東西）和 debug 次數（之後有機會隱藏？）請大家強烈公審我的 debug 次數以督促我好好寫並練習。
### 題
[Zero Judge-f312.](https://zerojudge.tw/ShowProblem?problemid=f312)

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
[TOJ 355](https://toj.tfcis.org/oj/pro/355/)（debug: 1）
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
[TOJ 110](https://toj.tfcis.org/oj/pro/110/)（debug: 3）

- 用用看`while(i--)`（for 應該比較好用）
```
#include<bits/stdc++.h>
using namespace std;
int main(){
    ios::sync_with_stdio(false), cin.tie(nullptr);
    int n,a;
    cin>>n;
    while(n--){
        cin>>a;
        int i=a-3;
        while(i--){
            for(int j=0;j<i+3;j++){
                cout<<" ";
            }
            for(int j=0;j<2*(a-i)-7;j++){
                cout<<"*";
            }
            cout<<'\n';
        }
        for(int j=0;j<2*a-1;j++){
            cout<<"*";
        }
        cout<<'\n'<<" ";
        for(int j=0;j<2*a-3;j++){
            cout<<"*";
        }
        cout<<'\n';
        for(int j=0;j<2*a-1;j++){
            cout<<"*";
        }
        cout<<'\n';
        while(i<a-4){
            for(int j=0;j<i+4;j++){
                cout<<" ";
            }
            for(int j=0;j<2*(a-i)-9;j++){
                cout<<"*";
            }
            cout<<'\n';
            i++;
        }
    }
}
```
[TOJ 114](https://toj.tfcis.org/oj/pro/114/)（前面看錯題目所以 debug 好幾次இωஇ 我的 NTOJ accuracy rate 啊啊啊啊(つД`)ノ）

- 用用看`return 0;`
```
#include<bits/stdc++.h>
using namespace std;
int main(){
    int a[5][6];
    for(int i=0;i<5;i++){
        for(int j=0;j<6;j++) cin>>a[i][j];
    }
    for(int i=0;i<5;i++){
        for(int j=0;j<4;j++){
            if(a[i][j]==a[i][j+1] && a[i][j]==a[i][j+2]){
                cout<<"Yes\n";
                return 0;
            }
        }
    }
    for(int j=0;j<6;j++){
        for(int i=0;i<3;i++){
            if(a[i][j]==a[i+1][j] && a[i][j]==a[i+2][j]){
                cout<<"Yes\n";
                return 0;
            }
        }
    }
    cout<<"No\n";
}
```
[TOJ 3](https://toj.tfcis.org/oj/pro/3/)（debug: 2）

- 最大公因數（大 while 裡）感覺很重要（？
```
#include<bits/stdc++.h>
using namespace std;
int main(){
    int t,a,b,r;
    cin>>t;
    while(t--){
        cin>>a>>b;
        r=1;
        while(r){
            r=a%b;
            a=b;
            b=r;
        }
        cout<<a<<'\n';
    }
}
```
