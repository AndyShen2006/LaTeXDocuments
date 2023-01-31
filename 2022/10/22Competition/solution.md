# 提高组试题题解

## T1 桃花源的道路(By AndyShen)

这题极为简单，本来想开subtask，想想看算了。

解题思路：考虑到当前字符串中$3n+1$位置中如果不是`X`，那么这个位置就一定要移动，只要推算一下不符合条件的`X`数就行了。

理论上直接用string全文读入会爆，应该用`getchar()`一位位读，但是因为技术问题还是不了了之了。

### std:
```cpp
#include <bits/stdc++.h>

using namespace std;

int main()
{
    int ans = 0;
    char c;
    int cur = 0;
    while ((c = getchar()) != EOF) {
        if (!(cur % 3)) {
            if (c != 'X') {
                ans++;
            }
        }
        cur++;
    }
    cout << ans << endl;
}
```

## T2 扣篮比赛(By Quidrem)

说在前头：本题要开 $\text{long long}$，不知道有没有人死在这。

显然最小的消耗肯定是选择的最高篮筐高度的两倍与选择篮筐消耗和之和。

### 20pts

将篮筐按高度由低到高排序，暴力枚举所有的选择扣的篮筐方案，因为先选择高的篮筐再选择低的篮筐与先选低的再选高的是等价的（前面解释了为什么这是成立的），所以每次只需从上一次选择的篮筐往后选，总时间复杂度大概是 $O(n!)$。

### 60pts

这题仔细想想就可以发现是没有贪心思想的（可能有，反正我没想到）。此时我们就可以考虑用 dp 来做。先按高度从小到大排序，记 $f_{i,j}$ 为前 $i$ 个篮筐（必选第 $i$ 个）扣 $j$ 个的最小消耗，转移方程 $f_{i,j}=min\{f_{k,j-1}+h_i-h_k\}$，其中 $i\le j\le n$，$0\le k< j$。有一些细节，自己随便调一调就好了。

注：因为算的是往返的总距离，所以高度都先乘 $2$ 处理掉。

```cpp
memset(f,0x3f,sizeof(f));
f[0][0]=0;
for(ll i=1;i<=n;i++){
	for(ll j=i;j<=n;j++){
		for(ll k=0;k<j;k++){
			f[i][j]=min(f[i][j],f[i-1][k]+p[j].h-p[k].h);
		}
		f[i][j]+=p[j].s;
	}
}
```

输出的时候 $O(n^2)$ 算一下选 $j$ 个的所有情况下的最小值。

```cpp
for(ll i=1;i<=n;i++){
	ans=inf;
	for(ll j=1;j<=n;j++){
		ans=min(ans,f[i][j]);
	}
	printf("%lld\n",ans);
}
```

### 80pts

揣摩一下上面那个方程，发现转移到 $f_{i,j}$ 的那些值同样会转移给 $f_{i+x,j},x\in N_+$。所以我们用一个数组 $min$ 来记录第 $i$ 层的最小值即可，时间复杂度优化到 $O(n^2)$。

注：因为要开两个 $n^2$ 的数组，所以只能开到 $4000^2$，否则会 $\text{MLE}$。（负责人注：实际比赛时内存有512M，所以不一定会MLE）

```cpp
memset(mn,0x3f,sizeof(mn));
memset(mn[0],0,sizeof(mn[0]));
for(ll i=1;i<=n;i++){
	for(ll j=1;j<=n;j++){
		f[i][j]=mn[i-1][j-1]+p[j].h+p[j].s;
		mn[i][j]=min(mn[i][j-1],f[i][j]-p[j].h);
	}
}
```

### 100pts

当我们使用 $min$ 的第 $i+2$ 层时，第 $i$ 层就没用了，所以可以使用一个 $2\times n$ 的数组和一个反复 $0,1$ 变换的变量 $tag$ 来优化内存。

```cpp
memset(mn[tg],0,sizeof(mn[tg]));
for(ll i=1;i<=n;i++){
	memset(mn[tg^1],0x3f,sizeof(mn[tg^1]));
	for(ll j=1;j<=n;j++){
		f[i][j]=mn[tg][j-1]+p[j].h+p[j].s;
		mn[tg^1][j]=min(mn[tg^1][j-1],f[i][j]-p[j].h);
	}
	tg^=1;
}
```
### std:
```cpp
#include<bits/stdc++.h>
#define ll long long
#define lnf 0x3f3f3f3f3f3f3f3f
#define N 5010
using namespace std;
inline ll rl(){
	char c=getchar();ll ans=0,f=1;
	while(c<'0'||c>'9'){if(c=='-')f=-1;c=getchar();}
	while(c>='0'&&c<='9')ans=(ans<<3)+(ans<<1)+c-'0',c=getchar();
	return ans*f;
}
struct node{
	ll a,s;
}p[N];
bool cmp(node a,node b){
	return a.s<b.s;
}
ll n,f[N][N],ans,mx[2][N],tg;
signed main(){
	n=rl();
	for(ll i=1;i<=n;i++){
		p[i].s=rl()<<1;
	}
	for(ll i=1;i<=n;i++){
		p[i].a=rl();
	}
	sort(p+1,p+n+1,cmp);
	memset(mx[tg],0,sizeof(mx[tg]));
	for(ll i=1;i<=n;i++){
		memset(mx[tg^1],0x3f,sizeof(mx[tg^1]));
		for(ll j=1;j<=n;j++){
			f[i][j]=mx[tg][j-1]+p[j].s+p[j].a;
			mx[tg^1][j]=min(mx[tg^1][j-1],f[i][j]-p[j].s);
		}
		tg^=1;
	}
	for(ll i=1;i<=n;i++){
		ans=lnf;
		for(ll j=1;j<=n;j++){
			ans=min(ans,f[i][j]);
		}
		printf("%lld\n",ans);
	}
	return 0;
}

```

## T3 花园(By AndyShen)

这道题目的思想来源自[P5123](https://www.luogu.com.cn/problem/P5123)，这道题使用了bitset压位，所以这题也出成了bitset压位

首先，我们用一个映射表（map）存情况，键表示美观点，值用bitset表示有这个美观点的花的情况。这个bitset怎么存呢？第j位表示第j朵花是否具有这个美观点，有为1，无为0。（当然，实际操作过程中是从高位向低位放的）

将样例这么表示后就是这样的：
| 键 | 值 |
| -----------: | -----------: |
| 1 | 1100 |
| 2 | 1111 |
| 3 | 0111 |
| 4 | 1010 |
| 5 | 0001 |

然后我们考虑对于每一朵花，有多少朵花与其有偶数个共同美观点。很简单，以这朵花的每一个美观点作为键取出对应的值，如果相同为1的有偶数个，则-1，否则+1。什么运算有偶数个1与奇数个1算出来相反的呢？很简单，异或运算即可，所以最后成型算法思路就是：

1、对于每个美观点，以这个美观点为键在map里面放一个关于这个美观点拥有情况的一个压位值。

2、按顺序取出这些花，对于每一朵花，考虑它的美观点对应的压位值，将这些值异或，然后统计0和1的个数。

这个地方有两个细节要注意一下，我一开始也写错了。第一个就是，自己和自己之间造成的美观值。如果美观点个数是奇数个，以花1为例，它对应异或之后的值就变成了`1001`,但是第一位这个1，是自己与自己异或出来的，是不应该计入统计的，所以这里要减去这种情况。另外就是双边的问题，A对B，B对A只算一种，所以答案要除二。

### std:
```cpp
#include <bits/stdc++.h>

using namespace std;

map<int, bitset<50001> > type;

struct cow {
    int a[11];
} cows[50001];

int main()
{
    int m, n;
    cin >> m >> n;
    for (int i = 0; i < m; i++) {
        for (int j = 1; j <= n; j++) {
            cin >> cows[i].a[j];
            type[cows[i].a[j]].set(i, true);
        }
    }
    int del = 0, add = 0;
    bitset<50001> check;
    for (int i = 0; i < m; i++) {
        check.reset();
        for (int j = 1; j <= n; j++) {
            check ^= type[cows[i].a[j]];
            // cout << type[cows[i].a[j]] << endl;
        }
        // cout << check << endl;
        del += m - 1 - check.count();
        add += check.count();
        if (n % 2 == 1) {
            del++;
    	}
        // cout << add << ' ' << del << endl;
    }
    cout << (add - del) /2 << endl;
    return 0;
}

```

## T4 条件(By AndyShen)

如果我们将这些条件都看做单向边（如a -> b看做是a到b有一条有向边），那么这题就转换成了图论题。

前面15个点分数很好拿，直接上Floyd传递闭包即可，复杂度$O(n^3)$。第16-20个点稍微麻烦一点，题目的特殊说明里说有至少100个点与其成充分必要关系，换言之，就是对于每个点，都有至少100个点和它在同一个强连通分量内，那么可以先Tarjan缩点（复杂度$O(n)$），在同一个强连通分量内的直接输出<->，剩下的看对应强连通分量的关系即可，总复杂度$O(n+(n/100)^3)$

### std:
```cpp
#include <bits/stdc++.h>

using namespace std;

constexpr int MAX_N = 5e4 + 10;
vector<int> G[MAX_N];
set<int> scc[MAX_N];
int sccno[MAX_N], scccnt;
int dfn[MAX_N], low[MAX_N], cnt;
stack<int> st;
bool ins[MAX_N];

int nG[510][510];

void tarjan(int x)
{
    dfn[x] = low[x] = ++cnt;
    st.push(x);
    ins[x] = true;
    for (auto it : G[x]) {
        if (!dfn[it]) {
            tarjan(it);
            low[x] = min(low[x], low[it]);
        } else if (ins[it]) {
            low[x] = min(low[x], dfn[it]);
        }
    }
    if (low[x] == dfn[x]) {
        int tmp;
        scccnt++;
        while (true) {
            tmp = st.top();
            st.pop();
            ins[tmp] = false;
            scc[scccnt].insert(tmp);
            sccno[tmp] = scccnt;
            if (tmp == x) {
                break;
            }
        }
    }
}

int main()
{
    int n, m, q;
    cin >> n >> m >> q;
    int a, b;
    string type;
    for (int i = 1; i <= m; i++) {
        cin >> a >> type >> b;
        if (type == "->") {
            G[a].push_back(b);
        } else if (type == "<-") {
            G[b].push_back(a);
        } else if (type == "<->") {
            G[a].push_back(b);
            G[b].push_back(a);
        }
    }
    // Tarjan's Algorithm
    for (int i = 1; i <= n; i++) {
        if (!dfn[i]) {
            tarjan(i);
        }
    }
    // cout << scccnt << endl;
    // Generate a new graph
    for (int i = 1; i <= n; i++) {
        for (auto it : G[i]) {
            nG[sccno[i]][sccno[it]] = 1;
        }
    }
    // Floyd Algorithm
    for (int i = 1; i <= scccnt; i++) {
        for (int j = 1; j <= scccnt; j++) {
            for (int k = 1; k <= scccnt; k++) {
                nG[i][j] |= nG[i][k] & nG[k][j];
            }
        }
    }
    for (int i = 1; i <= q; i++) {
        cin >> a >> b;
        if (sccno[a] == sccno[b]) {
            cout << a << " <-> " << b << endl;
        } else if (nG[sccno[a]][sccno[b]]) {
            cout << a << " -> " << b << endl;
        } else if (nG[sccno[b]][sccno[a]]) {
            cout << a << " <- " << b << endl;
        } else {
            cout << "Fail" << endl;
        }
    }
    return 0;
}
```