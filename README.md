### 目的
哈囉，我現在要開始學C++和準備APCS。由於實際寫過發現自己 bug 太多，因此決定在這裡放對我來說有代表性的題（例如用新東西）和主要 debug 次數（之後有機會隱藏？）請大家強烈公審我的 debug 次數以督促我好好寫並練習。
- 我後來 debug 都只放主要的，像加;那種就沒算，所以第一題次數應該比較不準（？
- 後面有在程式內加 // 寫 debug 原因提醒我注意。
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
        r=1; //做完一組後記得 r 變為非 0，避免第一組做完後 r=0 影響下一組小 while 判斷。 
        while(r){
            r=a%b;
            a=b;
            b=r;
        }
        cout<<a<<'\n';
    }
}
```
[TOJ 8](https://toj.tfcis.org/oj/pro/8/)（debug: 2）

- getline &`while(cin>>n)`
```
#include<bits/stdc++.h>
using namespace std;
int main(){
    ios::sync_with_stdio(false), cin.tie(nullptr);
    int n;
    while(cin>>n){
        string s;
        cin.ignore();
        getline(cin,s);
        for(int i=0;i<n;i++) for(int j=0;j<s.length()/n;j++) cout<<s[j*n+i];
        cout<<'\n';
    }
}
```
[TOJ 485](https://toj.tfcis.org/oj/pro/485/)（debug: 2）

- 就是覺得比較難 然後`while j!=e`的想法我覺得還不錯（？
```
#include<bits/stdc++.h>
using namespace std;
int main(){
    ios::sync_with_stdio(false), cin.tie(nullptr);
    int n,e=0,j=1;
    string a,s;
    cin>>n>>s;
    while(j!=e){
        j=e;
        for(int i=0;i<s.length()/2;i++){ //記得 s 長度會變，不能用 n
            if(s[i]!=s[s.length()-1-i]){
                e+=1;
                a=s[e-1];
                s.insert(n,a); //不能 (n,s[e-1])（idk why）or (n,"s[e-1]")（直接插入字）
                break;
            }
        }
    }
    cout<<e<<'\n';
}
```
[TOJ 501](https://toj.tfcis.org/oj/pro/501/)（debug: 2）

- 比較難
```
#include<bits/stdc++.h>
using namespace std;
int main(){
    ios::sync_with_stdio(false), cin.tie(nullptr);
    int n,s,l=0,j=0;
    cin>>n;
    int m[2*n+1];
    for(int i=0;i<n;i++){
        cin>>m[i];
        m[i+n]=m[i];
    }
    m[2*n]=0;
    while(l<n && j<n){
        s=0;
        for(int i=j;i<2*n;i++){
            if(m[i]>=i-j+1) s++;
            else break;
        }
        l=max(s,l);
        j+=s-m[j+s]+1;
    }
    cout<<min(n,l)<<'\n';
}
```
[Zero Judge-f168.](https://zerojudge.tw/ShowProblem?problemid=f168)

- 枚舉 用遞迴
```
#include<bits/stdc++.h>
using namespace std;
int n;
vector<int> v,sum,three;
void func(int idx,int s3){
    if(idx==0){
        sum.push_back(0);
        sum.push_back(v[0]);
        if(v[0]==s3) three.push_back(1);
    }
    else{
        func(idx-1,s3);
        int sz=sum.size();
        for(int i=0;i<sz;i++){
            sum.push_back(sum[i]+v[idx]);
            if(sum[i]+v[idx]==s3) three.push_back(sum.size()-1);
        }
    }
}
int main(){
    ios::sync_with_stdio(0),cin.tie(0);
    int a,s=0,s3;
    cin>>n;
    for(int i=0;i<n;i++){
        cin>>a;
        v.push_back(a);
        s+=v[i];
    }
    if(s%3) cout<<"NO\n";
    else{
        s3=s/3;
        func(n-1,s3);
        for(int i=0;i<three.size();i++){
            for(int j=i+1;j<three.size();j++){
                if(!(three[i] & three[j])){
                    cout<<"YES\n";
                    return 0;
                }
            }
        }
        cout<<"NO\n";
    }
}
```
[Zero Judge-b938.](https://zerojudge.tw/ShowProblem?problemid=b938)

- wonderhoi 教的聰明方法
```
#include<bits/stdc++.h>
using namespace std;
int main(){
    ios::sync_with_stdio(0),cin.tie(0);
    int n,m,k,tr;
    cin>>n>>m;
    vector<int> v(n+2);
    for(int i=1;i<=n+1;i++) v[i]=i;
    for(int i=0;i<m;i++){
        cin>>k;
        if(v[k+1]==n+1 || v[k]!=k) cout<<"0u0 ...... ?\n";
        else{
            cout<<v[k+1]<<'\n';
            tr=v[k+1]+1;
            v[v[k+1]]=v[tr];
            v[k+1]=v[tr];
        }
    }
}
```
[Zero Judge-a010.](https://zerojudge.tw/ShowProblem?problemid=a010)

- 線性質數篩 + 壓時間空間複雜度
```
#include<bits/stdc++.h>
using namespace std;
int main(){
    ios::sync_with_stdio(0),cin.tie(0);
    int n,idx2=0;
    cin>>n;
    vector<int> b(int(sqrt(n))+1,0),prime; //（以下所有sqrt(n)）若不用，時間、vector記憶體炸
    for(int i=2;i<=int(sqrt(n));i++){
        if(!b[i]){
            int idx=1,ep=0;
            for(int j=0;j<prime.size();j++){
                if(i*prime[j]<=int(sqrt(n))) b[i*prime[j]]=1;
                if(!(i%prime[j])) idx=0;
            }
            if(idx){
                prime.push_back(i);
                while(!(n%i)){
                    ep++;
                    n/=i;   //把n壓下來
                }
                if(ep){
                    if(idx2) cout<<" * ";
                    idx2=1;
                    cout<<i;
                    if(ep>1) cout<<'^'<<ep;
                }
            }
        }
    }
    if(n!=1){   //可能有>sort(n)的質數
        if(idx2) cout<<" * ";
        cout<<n;
    }
}
```
