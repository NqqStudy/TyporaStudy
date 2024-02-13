# 0 基础算法_模板

## 1 快速排序
[Acwing 785.快速排序](https://www.acwing.com/problem/content/787/)
```cpp
void quick_sort(int q[], int l, int r)
{
    if (l >= r) return;

    int i = l - 1, j = r + 1, x = q[l + r >> 1];
    while (i < j)
    {
        do i ++ ; while (q[i] < x);
        do j -- ; while (q[j] > x);
        if (i < j) swap(q[i], q[j]);
    }
    quick_sort(q, l, j), quick_sort(q, j + 1, r);
}
```
## 2 归并排序
[Acwing 787.归并排序](https://www.acwing.com/problem/content/789/)
```cpp
void merge_sort(int q[], int l, int r)
{
    if (l >= r) return;

    int mid = l + r >> 1;
    merge_sort(q, l, mid);
    merge_sort(q, mid + 1, r);

    int k = 0, i = l, j = mid + 1;
    while (i <= mid && j <= r)
        if (q[i] <= q[j]) tmp[k ++ ] = q[i ++ ];
        else tmp[k ++ ] = q[j ++ ];

    while (i <= mid) tmp[k ++ ] = q[i ++ ];
    while (j <= r) tmp[k ++ ] = q[j ++ ];

    for (i = l, j = 0; i <= r; i ++, j ++ ) q[i] = tmp[j];
}
```
## 3 整数二分

[Acwing 789.数的范围](https://www.acwing.com/problem/content/791/)
```cpp
bool check(int x) {/* ... */} // 检查x是否满足某种性质

// 区间[l, r]被划分成[l, mid]和[mid + 1, r]时使用：
int bsearch_1(int l, int r)
{
    while (l < r)
    {
        int mid = l + r >> 1;
        if (check(mid)) r = mid;    // check()判断mid是否满足性质
        else l = mid + 1;
    }
    return l;
}
// 区间[l, r]被划分成[l, mid - 1]和[mid, r]时使用：
int bsearch_2(int l, int r)
{
    while (l < r)
    {
        int mid = l + r + 1 >> 1;
        if (check(mid)) l = mid;
        else r = mid - 1;
    }
    return l;
}
```
## 4 浮点数二分
[Acwing 790.数的三次方根](https://www.acwing.com/problem/content/792/)
```cpp
bool check(double x) {/* ... */} // 检查x是否满足某种性质

double bsearch_3(double l, double r)
{
    const double eps = 1e-6;   // eps 表示精度，取决于题目对精度的要求
    while (r - l > eps)
    {
        double mid = (l + r) / 2;
        if (check(mid)) r = mid;
        else l = mid;
    }
    return l;
}
```
## 5 高精度加法
[Acwing 791.高精度加法](https://www.acwing.com/problem/content/793/)
```cpp
// C = A + B, A >= 0, B >= 0
vector<int> add(vector<int> &A, vector<int> &B)
{
    if (A.size() < B.size()) return add(B, A);

    vector<int> C;
    int t = 0;
    for (int i = 0; i < A.size(); i ++ )
    {
        t += A[i];
        if (i < B.size()) t += B[i];
        C.push_back(t % 10);
        t /= 10;
    }

    if (t) C.push_back(t);
    return C;
}
```
## 6 高精度减法
[Acwing 792.高精度减法](https://www.acwing.com/problem/content/794/)
```cpp
// C = A - B, 满足A >= B, A >= 0, B >= 0
vector<int> sub(vector<int> &A, vector<int> &B)
{
    vector<int> C;
    for (int i = 0, t = 0; i < A.size(); i ++ )
    {
        t = A[i] - t;
        if (i < B.size()) t -= B[i];
        C.push_back((t + 10) % 10);
        if (t < 0) t = 1;
        else t = 0;
    }
    while (C.size() > 1 && C.back() == 0) C.pop_back();
    return C;
}
```
## 7 高精度乘低精度
[Acwing 793.高精度乘法](https://www.acwing.com/problem/content/795/)
```cpp
// C = A * b, A >= 0, b >= 0
vector<int> mul(vector<int> &A, int b)
{
    vector<int> C;

    int t = 0;
    for (int i = 0; i < A.size() || t; i ++ )
    {
        if (i < A.size()) t += A[i] * b;
        C.push_back(t % 10);
        t /= 10;
    }
    while (C.size() > 1 && C.back() == 0) C.pop_back();
    return C;
}
```
## 8 高精度除以低精度
[Acwing 794.高精度除法](https://www.acwing.com/problem/content/796/)
```cpp
// A / b = C ... r, A >= 0, b > 0
vector<int> div(vector<int> &A, int b, int &r)
{
    vector<int> C;
    r = 0;
    for (int i = A.size() - 1; i >= 0; i -- )
    {
        r = r * 10 + A[i];
        C.push_back(r / b);
        r %= b;
    }
    reverse(C.begin(), C.end());
    while (C.size() > 1 && C.back() == 0) C.pop_back();
    return C;
}
```
## 9 一维前缀和
[Acwing 795.前缀和](https://www.acwing.com/problem/content/797/)

```cpp
S[i] = a[1] + a[2] + ... a[i]
a[l] + ... + a[r] = S[r] - S[l - 1]
```
## 10 二维前缀和
[Acwing 796.子矩阵的和](https://www.acwing.com/problem/content/798/)

```cpp
S[i, j] = 第i行j列格子左上部分所有元素的和
以(x1, y1)为左上角，(x2, y2)为右下角的子矩阵的和为：
S[x2, y2] - S[x1 - 1, y2] - S[x2, y1 - 1] + S[x1 - 1, y1 - 1]
```
## 11 一维差分
[Acwing 797.差分](https://www.acwing.com/problem/content/799/)
```cpp
给区间[l, r]中的每个数加上c：B[l] += c, B[r + 1] -= c
```
## 12 二维差分
[Acwing 798.差分矩阵](https://www.acwing.com/problem/content/800/)

```cpp
给以(x1, y1)为左上角，(x2, y2)为右下角的子矩阵中的所有元素加上c：
S[x1, y1] += c, S[x2 + 1, y1] -= c, S[x1, y2 + 1] -= c, S[x2 + 1, y2 + 1] += c
```
## 13 位运算
[Acwing 801.二进制中1的个数](https://www.acwing.com/problem/content/803/)

```cpp
求n的第k位数字: n >> k & 1
返回n的最后一位1：lowbit(n) = n & -n
```
## 14 双指针算法
[Acwing 799.最长连续不重复子列](https://www.acwing.com/problem/content/801/)
[Acwing 800.数组元素的目标和](https://www.acwing.com/problem/content/802/)
```cpp
for (int i = 0, j = 0; i < n; i ++ )
{
    while (j < i && check(i, j)) j ++ ;

    // 具体问题的逻辑
}
常见问题分类：
    (1) 对于一个序列，用两个指针维护一段区间
    (2) 对于两个序列，维护某种次序，比如归并排序中合并两个有序序列的操作
```
## 15 离散化
[Acwing 802.区间和](https://www.acwing.com/problem/content/804/)

```cpp
vector<int> alls; // 存储所有待离散化的值
sort(alls.begin(), alls.end()); // 将所有值排序
alls.erase(unique(alls.begin(), alls.end()), alls.end());   // 去掉重复元素

// 二分求出x对应的离散化的值
int find(int x) // 找到第一个大于等于x的位置
{
    int l = 0, r = alls.size() - 1;
    while (l < r)
    {
        int mid = l + r >> 1;
        if (alls[mid] >= x) r = mid;
        else l = mid + 1;
    }
    return r + 1; // 映射到1, 2, ...n
}
```
## 16 区间合并
[Acwing 803.区间合并](https://www.acwing.com/problem/content/805/)
```cpp
// 将所有存在交集的区间合并
void merge(vector<PII> &segs)
{
    vector<PII> res;

    sort(segs.begin(), segs.end());

    int st = -2e9, ed = -2e9;
    for (auto seg : segs)
        if (ed < seg.first)
        {
            if (st != -2e9) res.push_back({st, ed});
            st = seg.first, ed = seg.second;
        }
        else ed = max(ed, seg.second);

    if (st != -2e9) res.push_back({st, ed});

    segs = res;
}
```

# 1 基础算法_快排/归排/二分查找/高精度

理解思想，默写代码模板，写出来调试通过，同一个题可以写3-5次

## 1 排序
### 1.1 快速排序(难在划分)
- 快速排序的核心是**分治思想**：假设我们的目标依然是按从小到大的顺序排列，我们找到数组中的一个分割值，**把比分割值小的数都放在数组的左边**，**把比分割值大的数都放在数组的右边**，这样分割值的位置就被确定。数组一分为二，我们**只需排前一半数组和后一半数组**，复杂度直接减半。采用这种思想，**不断的进行递归**，最终分割得只剩下一个元素时，整个序列自然就是有序的

![在这里插入图片描述](https://img-blog.csdnimg.cn/bcf3033cf7f747a0871c47818361730f.png)



- **左边指针 i 不满足小于分界值就停下来，然后右边指针j移动，遇到不满足大于分界值就停下来，接着交换指针 i 和指针 j 互相所指的值，交换完之后，指针 i 和 j 均移动一位**

- 用指针 j 来划分，左边是小于等于分界值，右边大于等于分界值。就是 i 指针左边的数一定小于等于分界值，j 指针右边的数一定大于等于分界值

![在这里插入图片描述](https://img-blog.csdnimg.cn/2bda4adfb0c84dc790fb8046ff302fe5.png)
#### 1.1.1 模板
 - i + r >> 1：i + r 的值右移1位，相当 i + r 的值除以2取整，int是向下取整的函数
[i + r >> 1解释](https://blog.csdn.net/m0_49824320/article/details/120819675)
 - 模板1：quick_sort(q, l, j)，x = q[l]或者q[l + r >> 1]
 - 当下面递归取 j 时，x 不能取 x = q[r]作为边界
```cpp
void quick_sort(int q[], int l, int r)// l 是左指针， r是右指针
{
    if (l >= r) return 0;// 左指针 > 右指针时，返回

	// 当x = q[l]里面是左边界l, 则quick_sort(q,l,j)最后必须是j
	// quick_sort(q, l, j)时，x = q[l]或者q[l + r >> 1]均是可以的
    int i = l - 1, j = r + 1, x = q[l + r >> 1];// 右移1位，相当于i + r的值除以2取整
    while (i < j)
    {
        do i ++ ; while (q[i] < x);// 一直做i++,直到找到大于等于x的值，然后再进行j--
        do j -- ; while (q[j] > x);// 做完i++,才做j--,直到找到小于等于x的值
        if (i < j) swap(q[i], q[j]);// 找到之后，进行交换
    }
    quick_sort(q, l, j);// 左半部分递归排序
    quick_sort(q, j + 1, r);// 右半部分递归排序
    // quick_sort(q, l, i - 1) 写成i - 1是可以的,同时必须修改x = q[l] 为 int x = q[(l + r + 1) / 2]，否则出现边界问题
    // quick_sort(q, i, r);
}
```
- 模板2：quick_sort(q, l, i - 1)，x = q[l]或者q[l + r >> 1]
- 当下面递归取 i 时，x 不能取 x = q[l]作为边界

```cpp
void quick_sort(int q[], int l, int r)// l 是左指针， r是右指针
{
    if (l >= r) return;// 左指针 > 右指针时，返回
    
	// 当x = q[r]里面是右边界r时, 则quick_sort(q,l,i-1)
	// quick_sort(q, l, i - 1)时，x = q[l]或者q[l + r >> 1]均是可以的
	int x = q[(l + r + 1) / 2], i = l - 1, j = r + 1;
    while (i < j)
    {
        do i ++ ; while (q[i] < x);// 一直做i++,知道找到大于等于x的值，然后再进行j++
        do j -- ; while (q[j] > x);// 做完i++,才做j++,直到找到小于等于x的值
        if (i < j) swap(q[i], q[j]);// 找到之后，进行交换
    }
    quick_sort(q, l, i - 1);
    quick_sort(q, i, r);
}
```

#### 1.1.2 习题1 — 785.快速排序
[Acwing 785.快速排序](https://www.acwing.com/problem/content/description/787/)

```cpp
#include<iostream>
using namespace std;
const int N = 1e6 + 10;

int n;
int q[N];

void quick_sort(int q[], int l, int r)
{
    if(l >= r) return 0;
    
    // int x = q[l + r >> 1] 也可以
    int x = q[(l + r) / 2], i = l - 1, j = r + 1;// 数据加强了，x不能取边界值
    while(i < j)
    {
        do i++; while(q[i] < x);
        do j--; while(q[j] > x);
        if(i < j) swap(q[i],q[j]);
    }
    quick_sort(q, l, j);
    quick_sort(q, j + 1, r);
}

int main()
{
    scanf("%d",&n);
    for(int i = 0;i < n; i++) scanf("%d",&q[i]);
    
    quick_sort(q, 0, n - 1);
    for(int i = 0;i < n; i++) printf("%d ",q[i]);
    
    return 0;
} 
```
#### 1.1.3 习题2 — 786.第k个数(快速选择算法)
[Acwing 786.第k个数](https://www.acwing.com/problem/content/788/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/29987b815e794c628b861e4fd4ffa37b.png)

 - **左半边的左边界是l，右边界是j**
![在这里插入图片描述](https://img-blog.csdnimg.cn/52b5686d6d044f07a5f717beeee0110f.png)
```cpp
#include<iostream>
using namespace std;

const int N = 100010;
int n, k;
int q[N];

int quick_sort(int l, int r, int k)
{
    if(l == r) return q[l];
    int x = q[(l + r)/2], i = l - 1, j = r + 1;// 双指针方式，x是分界点，区分不同的值
    while(i < j)
    {
        while(q[++i] < x);// 找到小于x的坐标值
        while(q[--j] > x);// 找到大于x的坐标值
        if(i < j) swap(q[i],q[j]);
    }
    
    int sl = j - l + 1;// sl部分数的个数
    if(k <= sl) return quick_sort(l, j, k);// k小于s1就在左半区间找
    
    return quick_sort(j + 1, r, k - sl);// 否则返回右半区间
}

int main()
{
    cin >> n >> k;
    for(int i = 0;i < n;i++) cin >> q[i];
    cout << quick_sort(0, n - 1, k) << endl;// 0是左边界，n-1是右边界
    return 0;
}
```

### 1.2 归并排序(难在合并)
![在这里插入图片描述](https://img-blog.csdnimg.cn/278efb61d9bb4c56a40b529678eaafdb.png)
 - 难点在于如何把有序的序列合二为一
![在这里插入图片描述](https://img-blog.csdnimg.cn/207549bfbf9c4a40a5f8aead8a8b7662.png)
 - 举例
![在这里插入图片描述](https://img-blog.csdnimg.cn/aa6f71ff353b4e35bd64ec618576c069.png)
#### 1.2.1 模板
```cpp
void merge_sort(int q[], int l, int r)// q是要排序的数组，l和r使左右闭区间
{
    if (l >= r) return;// 判断当前区间

    int mid = l + r >> 1;// 取区间的中点，相当于i + r的值除以2向下取整
    merge_sort(q, l, mid);// 左边递归排序，已经排好顺序
    merge_sort(q, mid + 1, r);// 右边递归排序，已经排好顺序

	// 归并合二为一
    int k = 0, i = l, j = mid + 1;// k表示tmp中合并数字的个数，i是左指针，j是右指针
    while (i <= mid && j <= r) // 左半边边界和右半边边界
        if (q[i] <= q[j]) tmp[k ++ ] = q[i ++ ];
        else tmp[k ++ ] = q[j ++ ];
        
	// 左右两边有一边没有循环结束的话，接到tmp后面去
    while (i <= mid) tmp[k ++ ] = q[i ++ ];// 如果左边没有循环结束，加入到tmp中
    while (j <= r) tmp[k ++ ] = q[j ++ ];// 右边没有循环结束也加入进去

    for (i = l, j = 0; i <= r; i ++, j ++ ) q[i] = tmp[j];// 把结果从tmp中拿回到q里面
}
```
#### 1.2.2 习题1 — 787.归并排序
[Acwing 787.归并排序](https://www.acwing.com/problem/content/789/)

```cpp
#include<iostream>
using namespace std;

const int N = 1000010;

int n;
int q[N],tmp[N];

void merge_sort(int q[],int l, int r)
{
    if(l >= r) return;
    
    int mid = l + r >> 1;// 就是 L+R 然后除以2
    merge_sort(q, l, mid);
    merge_sort(q, mid + 1, r);
    
    int k = 0, i = l, j = mid + 1;
    while(i <= mid && j <= r)
    {
        if(q[i] <= q[j]) tmp[k++] = q[i++];
        else tmp[k++] = q[j++];
    }
    
    while(i <= mid) tmp[k++] = q[i++];
    while(j <= r) tmp[k++] = q[j++];
    
    for(int i = l,j = 0;i <= r; i++, j++) q[i] = tmp[j];
}

int main()
{
    scanf("%d",&n);
    for(int i = 0;i < n; i++) scanf("%d",&q[i]);
    
    merge_sort(q, 0, n - 1);
    for(int i = 0;i < n; i++) printf("%d ",q[i]);
    
    return 0;
}
```
#### 1.2.3 习题2 — 788.逆序对的数量
[Acwing 788.逆序对的数量](https://www.acwing.com/problem/content/790/)
 - 解题思路
![在这里插入图片描述](https://img-blog.csdnimg.cn/45a0b88301cb420da164d8769fc6317a.png)

```cpp
#include<iostream>
using namespace std;

typedef long long LL;

const int N = 100010;// 数据范围是100000

int q[N], tmp[N];

LL merge_sort(int l, int r)
{
    if(l >= r) return 0;
    
    int mid = l + r >> 1;
    LL res = merge_sort(l, mid) + merge_sort(mid + 1, r);// 这里res的数据类型是LL
    
    // 归并过程
    int k = 0, i = l, j = mid + 1;
    while(i <= mid && j <= r)
    {
        if(q[i] <= q[j]) tmp[k++] = q[i++];// 这里判断条件是小于等于
        else
        {
            tmp[k++] = q[j++];
            res += mid - i + 1;// 根据公式得来的
        }
    }
    
    // 扫尾
    while(i <= mid) tmp[k++] = q[i++];
    while(j <= r) tmp[k++] = q[j++];
    
    // 物归原主
    for(int i = l, j = 0;i <= r;i++, j++) q[i] = tmp[j];// 这里的i是从l开始
    
    return res;
}

int main()
{
    int n;
    cin >> n;
    
    for(int i = 0; i < n; i ++) cin >> q[i];
    
    cout << merge_sort(0, n - 1) << endl;
    
    // for(int i = 0; i < n; i++) cout << q[i] << endl;
    
    return 0;
}
```
## 2 二分查找(已升序/降序排列)
### 2.1 整数二分(使用l<r)
 - 如果遇到相同的数字，**模板1可以求出数字的起始位置，模板2可以求出数字的终止位置**。如果没有遇到数字重复的情况，则模板1和2均可以求出位置所在
 - 确定check(mid)条件，默写模板
 - 最后的结果中 **l = r**，就是说**左右会集合到同一个点**

![在这里插入图片描述](https://img-blog.csdnimg.cn/33273001d3374fa0925fa6320d5213a6.png)
#### 2.1.1 模板1(r = mid, mid = l + r >> 1）
 - 条件是左边**红色区域**，x是初始比较的值，加判断条件**q[mid] >= x**，true的话说明想查找的数字在mid的左边，那么**true为 r = mid**，**否则 l = mid + 1**。可以求出数字的起始位置
![在这里插入图片描述](https://img-blog.csdnimg.cn/e94237129b8641a8882ed1d2a1dfef1d.png)
```cpp
bool check(int x) {/* ... */} // 检查x是否满足某种性质
// 模板1
// 区间[l, r]被划分成[l, mid]和[mid + 1, r]时使用：
int bsearch_1(int l, int r)
{
    while (l < r)
    {
        // check()判断mid是否满足性质
        int mid = l + r >> 1;// int是向下取整
        if (check(mid)) r = mid;//  check条件是q[mid] >= x
        else l = mid + 1;
    }
    return l;
}
```
#### 2.1.2 模板2(l = mid, mid = l + r + 1 >> 1)
 - 条件是**绿色区域**，x是初始比较的值，加入判断条件**q[mid] <= x**，true的话说明x在mid的右边，那么**true为 l = mid**，**否则 r = mid - 1**。可以求出位置的终止位置
![在这里插入图片描述](https://img-blog.csdnimg.cn/1ca6d58b17a64b3eb519ad5d156310eb.png)
```cpp
// 模板2
// 区间[l, r]被划分成[l, mid - 1]和[mid, r]时使用：
int bsearch_2(int l, int r)
{
    while (l < r)
    {
        int mid = l + r + 1 >> 1;
        if (check(mid)) l = mid;// check条件是q[mid] <= x
        else r = mid - 1;
    }
    return l;
}
```
#### 2.1.2 习题1 — 789.数的范围
[Acwing 789.数的范围](https://www.acwing.com/problem/content/791/)
 - 首先定义check(mid)的规则是 **x 右边的数是 >= x，如果q[mid] >= x，表示答案x在左半边**。
![在这里插入图片描述](https://img-blog.csdnimg.cn/b184e6dfa44248dd814b603816e17b6a.png)
 - 然后定义check(mid)的规则是 **x 左边的数是 <= x，如果q[mid] <= x，表示答案x在右半边，x左边的数均满足 <= x**。
![在这里插入图片描述](https://img-blog.csdnimg.cn/8ceef19f4d0a45659e18e08481359ec0.png)
```cpp
#include<iostream>
using namespace std;

const int N = 1e6 + 10;

int n, m;
int q[N];

int main()
{
    scanf("%d%d",&n, &m);// n表示多少个数字，m表示要查询的个数
    for(int i = 0;i < n; i++) scanf("%d",&q[i]);
    
    while(m--)// 有三个数需要查询
    {
        // 本题中 前一个3是用模板1求起始位置，后一个3是用模板2求终止位置
        int x;
        scanf("%d",&x);
        
        // 从前往后找
        int l = 0, r = n - 1;
        while(l < r)
        {
            int mid = l + r >> 1;// (l + r)/2
            if(q[mid] >= x) r = mid;
            else l = mid + 1;
        }
        
        if(q[l]!=x) cout << "-1 -1" << endl;// 这里输出q[l] = q[r]
        else
        {
            cout << l << " ";
            // 从后往前找
            int l = 0, r = n - 1;
            while(l < r)
            {
                int mid = l + r + 1 >> 1;
                if(q[mid] <= x) l = mid;
                else r = mid - 1;
            }
            cout << l << endl;
        }
    }
    return 0;
}
```
### 2.2 浮点数二分
 - 右边界不能小于1
![在这里插入图片描述](https://img-blog.csdnimg.cn/393d6ae5015a40188121c99800f9f2d8.png)

#### 2.2.1 模板
```cpp
bool check(double x) {/* ... */} // 检查x是否满足某种性质

double bsearch_3(double l, double r)
{
    const double eps = 1e-6;   // eps 表示精度，取决于题目对精度的要求
    while (r - l > eps)
    {
        double mid = (l + r) / 2;
        if (check(mid)) r = mid;
        else l = mid;
    }
    return l;// 也可以输出 r
}
```
#### 2.2.2 习题1(开根号)
 - 不用考虑边界问题
![在这里插入图片描述](https://img-blog.csdnimg.cn/7b3882fe82d541fdbde1923948b1f6f0.png)

```cpp
#include<iostream>
using namespace std;
int main()
{
	double x;
	cin >> x;
	
	double l = 0, r = x;
    while (r - l > 1e-8)// 如果结果保留6为小数，则写为e-8，多写两位
    {
        double mid = (l + r) / 2;
        if (mid * mid >= x) r = mid;
        else l = mid;
    }
    printf("%lf",l);// 输出 l和r均可以
    return 0;
}
```
#### 2.2.3 习题2 — 790.数的三次方根
[Acwing 790.数的三次方根](https://www.acwing.com/problem/content/792/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/ca8aed4ae7be4e7ba880b06aebcdcec3.png)

```cpp
#include<iostream>
using namespace std;

int main()
{
    double x;
    cin >> x;
    
    double l = -10000, r = 10000;
    while(r - l > 1e-8)
    {
        double mid = (l + r)/2;
        if(mid * mid * mid >= x) r = mid;
        else l = mid;
    }
    printf("%lf",l);// 输出 l和r均可以
    return 0;
}
```

## 3 高精度
### 3.1 高精度加法
#### 3.1.1 模板

```cpp
// C = A + B, A >= 0, B >= 0
vector<int> add(vector<int> &A, vector<int> &B)
{
    if (A.size() < B.size()) return add(B, A);

    vector<int> C;
    int t = 0;
    for (int i = 0; i < A.size(); i ++ )
    {
        t += A[i];
        if (i < B.size()) t += B[i];
        C.push_back(t % 10);
        t /= 10;
    }

    if (t) C.push_back(t);
    return C;
}
```
#### 3.1.2 习题
[Acwing 791.高精度加法](https://www.acwing.com/problem/content/793/)

```cpp
#include<iostream>
#include<algorithm>
#include<vector>
using namespace std;

// C = A + B
vector<int> add(vector<int> &A, vector<int> &B)
{
    vector<int> C;
    
    int t = 0;
    for(int i = 0;i < A.size()|| i < B.size(); i++)
    {
        if(i < A.size()) t += A[i];
        if(i < B.size()) t += B[i];// t存储Ai + Bi + 上一位的进位
        C.push_back(t%10);// 求余
        t /= 10;// 看是否有下一位的进位
    }
    if(t) C.push_back(1);// 最高位有没有进位
    return C;// 返回的是C的数组
}

int main()
{
    string a, b;
    vector<int>A, B;
    
    cin >> a >> b;// a = "123456", 字符串a可以当作字符数组来处理, 处理后
    // 将a[]中阿拉伯数字字符转换成int数字，需要减去'0'', A 结果是 [6, 5, 4, 3, 2, 1]，最低位是个位数，这种操作叫字符串转整型
    for(int i = a.size() - 1; i >= 0; i--) A.push_back(a[i] - '0');
    for(int i = b.size() - 1; i >= 0; i--) B.push_back(b[i] - '0');
    
    auto c = add(A,B);// auto 是自动推断变量的类型，auto 这里等价于 vector<int>
    // 逆向输出，先输出最高位，因为之前的相加的结果的开头是最低位
    for(int i = c.size() - 1;i >= 0;i --)printf("%d",c[i]);// i从size - 1开始
    return 0;
}
```
### 3.2 高精度减法
![在这里插入图片描述](https://img-blog.csdnimg.cn/b980133070654b6aa6048fb427fdb273.png)
 - 假如给出A < B，则先计算B - A，再在前面加"-"。
 - t 值的求法

![在这里插入图片描述](https://img-blog.csdnimg.cn/53345549f26a4328aea87bb7a47b125d.png)
#### 3.2.1 模板
```cpp
// C = A - B, 满足A >= B, A >= 0, B >= 0
vector<int> sub(vector<int> &A, vector<int> &B)
{
    vector<int> C;
    for (int i = 0, t = 0; i < A.size(); i ++ )
    {
        t = A[i] - t;
        if (i < B.size()) t -= B[i];// 先判断B的位数是否存在
        C.push_back((t + 10) % 10);// 当t>=0时，直接赋值为t，当t<0时，t = t + 10，直接用(t+10)%10来表示这两种情况
        if (t < 0) t = 1;// t < 0，进一位，否则不进位
        else t = 0;
    }

    while (C.size() > 1 && C.back() == 0) C.pop_back();
    return C;
}
```
#### 3.2.2 习题
[Acwing 792.高精度减法](https://www.acwing.com/problem/content/794/)

```cpp
#include<iostream>
#include<algorithm>
#include<vector>
using namespace std;

// 判断是否有A >= B，假定A和B都是正数
bool cmp(vector<int>&A, vector<int>&B)
{
    if(A.size() != B.size()) return A.size() > B.size();// 判断两者的位数，A的位数是否大于B
    for(int i = A.size() - 1; i >= 0; i--)// 从最高位开始比较，最高位在数组的最后的一位
        if(A[i] != B[i])
            return A[i] > B[i];// 返回同一位较大的值
    return true;
}

// C = A - B
vector<int> sub(vector<int> &A, vector<int> &B)
{
    vector<int> C;
    int t = 0;
    for(int i = 0;i < A.size(); i++)
    {
        t = A[i] - t;
        if(i < B.size()) t -= B[i];// 先判断B的位数是否存在
        C.push_back((t + 10)% 10);// 当t >= 0时，直接赋值为t，当t<0时，t = t + 10，直接用(t+10)%10来表示这两种情况
        if(t < 0) t = 1;// t < 0，向前借一位，否则不借位
        else t = 0;
    }
    while(C.size() > 1 && C.back() == 0) C.pop_back();// C.back表示最后一位等于零的话，就弹出来，就是要丢掉前导零，比如123 - 120 = 003，输出的结果C是300，去掉最后的两个零，变成3
    return C;
}

int main()
{
    string a, b;
    vector<int>A, B;
    
    cin >> a >> b;// a = "123456", 字符串a可以当作字符数组来处理, 处理后
    // 将a[]中阿拉伯数字字符转换成int数字，需要减去'0'', A 结果是 [6, 5, 4, 3, 2, 1]，最低位是个位数，这种操作叫字符串转整型
    for(int i = a.size() - 1; i >= 0; i--) A.push_back(a[i] - '0');
    for(int i = b.size() - 1; i >= 0; i--) B.push_back(b[i] - '0');
    
    if(cmp(A,B))// 判断A与B大小关系，在A >= B的情况下，再进行A - B的操作
    {
        auto c = sub(A,B);// auto 是自动推断变量的类型，auto 这里等价于 vector<int>
        // 逆向输出，先输出最高位，因为之前的相加的结果的开头是最低位
        for(int i = c.size() - 1;i >= 0;i --)printf("%d",c[i]);// i 从size - 1开始
    }
    else
    {
        auto c = sub(B,A);
        printf("-");// 当 A < B时，先求B - A，再在前面添加"-"
        for(int i = c.size() - 1;i >= 0;i --)printf("%d",c[i]);// i从size - 1开始
    }
    return 0;
}
```
### 3.3 高精度乘以低精度
![在这里插入图片描述](https://img-blog.csdnimg.cn/5a7ae9f6e3aa44af938917508a375563.png)

#### 3.3.1 模板
```cpp
// C = A * b, A >= 0, b >= 0
vector<int> mul(vector<int> &A, int b)
{
    vector<int> C;

    int t = 0;
    for (int i = 0; i < A.size() || t; i ++ )
    {
        if (i < A.size()) t += A[i] * b;
        C.push_back(t % 10);
        t /= 10;
    }

    while (C.size() > 1 && C.back() == 0) C.pop_back();
    return C;
}
```
#### 3.3.2 习题
[Acwing 793.高精度乘以低精度](https://www.acwing.com/problem/content/795/)

```cpp
#include<iostream>
#include<vector>
using namespace std;

vector<int> mul(vector<int>&A, int b)
{
    vector<int> C;
    
    int t = 0;
    for(int i = 0;i < A.size() || t;i ++)// i没有循环完或者t不为零
    {
        if(i < A.size())t += A[i] * b;// t = A[i] * b + t
        C.push_back(t % 10);
        t /= 10;// t = t / 10
    }
    while(C.size() > 1 && C.back() == 0) C.pop_back();// C.back表示最后一位等于零的话，就弹出来，就是去掉前导零
    return C;
}

int main()
{
    string a;// 长数字用字符串处理，一般小数字用int保存
    int b;
    cin >> a >> b;
    
    vector<int>A;
    for(int i = a.size() - 1;i >= 0;i --) A.push_back(a[i] - '0');
    
    auto C = mul(A,b);// 这里是A，就是处理后的vector数组
    for(int i = C.size() - 1;i >= 0;i --) printf("%d", C[i]);
}
```
### 3.4 高精度除以低精度
![在这里插入图片描述](https://img-blog.csdnimg.cn/89d2321c7e434d9b8cad5fa288e1aba2.png)
#### 3.4.1 模板
```cpp
// A / b = C ... r, A >= 0, b > 0
vector<int> div(vector<int> &A, int b, int &r)
{
    vector<int> C;
    r = 0;
    for (int i = A.size() - 1; i >= 0; i -- )
    {
        r = r * 10 + A[i];
        C.push_back(r / b);
        r %= b;
    }
    reverse(C.begin(), C.end());
    while (C.size() > 1 && C.back() == 0) C.pop_back();
    return C;
}
```

#### 3.4.2 习题

```cpp
#include<iostream>
#include<vector>
#include<algorithm>
using namespace std;

// C = A / B, 商是C，余数是r。除法是从最高位开始计算
vector<int> div(vector<int>&A, int b, int &r)// r位引用
{
   vector<int>C;
   r = 0;// 刚开始余数位0
   for(int i = A.size() - 1;i >= 0;i --)
   {
       r = r * 10 + A[i];// 余数
       C.push_back(r/b);// 求商
       r %= b;
   }
   reverse(C.begin(),C.end());
   while(C.size() > 1 && C.back() == 0) C.pop_back();// 数组最后一位是零的话，会自动弹出来，清除前导零
   return C;
}

int main()
{
    string a;// 长数字用字符串处理，一般小数字用int保存
    int b;
    cin >> a >> b;
    
    vector<int>A;
    for(int i = a.size() - 1;i >= 0;i --) A.push_back(a[i] - '0');
    
    int r = 0;
    auto C = div(A,b,r);// 这里是A，就是处理后的vector数组
    
    for(int i = C.size() - 1;i >= 0;i --) printf("%d", C[i]);// 输出商
    cout << endl;
    cout << r << endl;// 输出余数
}
```

# 2 一二维前缀和/一二维差分

## 1 一维前缀和
![在这里插入图片描述](https://img-blog.csdnimg.cn/4be6d067b64b4e3b856e9220121de542.png)
### 1.1 模板
![在这里插入图片描述](https://img-blog.csdnimg.cn/ba1ab4f898ba4f56b4e256a0f662bad1.png)

```cpp
S[i] = a[1] + a[2] + ... a[i]
a[l] + ... + a[r] = S[r] - S[l - 1]
```
### 1.2 习题 — 795.前缀和
[Acwing 795.前缀和](https://www.acwing.com/problem/content/797/)

```cpp
#include<iostream>
using namespace std;

const int N = 100010;// 防止越界
int n, m;
int a[N], s[N];

int main()
{
    // ios::sync_with_stdio(false);
    scanf("%d%d", &n, &m);// cin >> n >> m;
    for(int i = 1;i <= n;i ++)scanf("%d",&a[i]);// cin >> a[i]
    
    s[0] = 0;// 求前缀和数组s[1],s[2]....
    for(int i = 1;i <= n;i ++) s[i] = s[i - 1] + a[i];// 前缀和的初始化
    
    while(m--)// 输入三次区间
    {
        int l, r;
        scanf("%d%d",&l, &r);// 数据量大的情况下，scanf输入速度比cin大一倍
        printf("%d\n", s[r] - s[l-1]);// 区间和计算
    }
    // 或者用下面的方式
    while(m--)
    {
    	int l, r;
    	cin >> l >> r;
    	cout << s[r] - s[l-1] << endl;
	}
    return 0;
}
```
## 2 二维前缀和
![在这里插入图片描述](https://img-blog.csdnimg.cn/dc68160ff30549ffb7074ac66ef0932e.png)
 - 公式推导
![在这里插入图片描述](https://img-blog.csdnimg.cn/6707d86d0ca7444a89f6b7faa282a8d1.png)
### 2.1 模板
![在这里插入图片描述](https://img-blog.csdnimg.cn/def51ff597164031866135a788d1aa77.png)
- s[i][j]的计算方法
![在这里插入图片描述](https://img-blog.csdnimg.cn/ae92f82e42b24abeb558caff831886f0.png)


```cpp
S[i, j] = 第i行j列格子左上部分所有元素的和
以(x1, y1)为左上角，(x2, y2)为右下角的子矩阵的和为：
S[x2, y2] - S[x1 - 1, y2] - S[x2, y1 - 1] + S[x1 - 1, y1 - 1]
```
### 2.2 习题 — 796.子矩阵的和
[Acwing 796.子矩阵的和](https://www.acwing.com/problem/content/798/)
[图形解释](https://www.acwing.com/solution/content/27301/)
```cpp
#include<iostream>

const int N = 1010;// n要小点
int n, m, q;
int a[N][N], s[N][N];

int main()
{
    scanf("%d%d%d",&n,&m,&q);// scanf读入速度快
    for(int i = 1;i <= n; i++)// i是从1开始
        for(int j = 1;j <= m; j++)
            scanf("%d", &a[i][j]);
    
    // 初始化前缀和数组
    for(int i = 1; i <= n;i++)
        for(int j = 1;j <= m;j++)// 这里s[0][1] = s[1][0] = s[0][0] = 0
            s[i][j] = s[i - 1][j] + s[i][j - 1] - s[i - 1][j - 1] + a[i][j];// 求前缀和
    
    // 询问
    while(q--)
    {
        int x1,y1,x2,y2;
        scanf("%d%d%d%d",&x1,&y1,&x2,&y2);
        printf("%d\n",s[x2][y2] - s[x1 - 1][y2] - s[x2][y1 - 1] + s[x1 - 1][y1 - 1]);// 算部分和
    }
    return 0;
}
```
## 3 一维差分
![在这里插入图片描述](https://img-blog.csdnimg.cn/4faaafd803b24ba18c2d2d5233216bf5.png)
 - **a称为b的前缀和，b称为a的差分**

![在这里插入图片描述](https://img-blog.csdnimg.cn/ade838a9916e4d3bb0ff8b79b6b5c9dc.png)

### 3.1 模板
![在这里插入图片描述](https://img-blog.csdnimg.cn/c8b9f99a9b5f4084bc7f0439828d1a5f.png)

 - 根据上图右边的示意图可知如下
![在这里插入图片描述](https://img-blog.csdnimg.cn/c77fa1c757e24cc78c533ec271f82f6c.png)
```cpp
给区间[l, r]中的每个数加上c：B[l] += c, B[r + 1] -= c
```
### 3.2 习题 — 797.差分
[Acwing 797.差分](https://www.acwing.com/problem/content/799/)

```cpp
#include<iostream>
using namespace std;

const int N = 100010;

int n, m;
int a[N], b[N];// a[N]是原数组，b[N]是差分数组

void insert(int l, int r, int c)
{
    b[l] += c;
    b[r + 1] -= c;
}

int main()
{
    scanf("%d%d",&n, &m);
    for(int i = 1; i <= n; i++) scanf("%d",&a[i]);
    
    // 将输入进来的数组插入到原数组A，为下面的操作做准备
    for(int i = 1; i <= n; i++) insert(i,i,a[i]);
    // 在a[1,1]上添加a[1], a[2,2]上增加a[2]
    
    while(m--)
    {
        int l, r ,c;
        scanf("%d%d%d",&l, &r, &c);
        insert(l, r, c);
    }
    
    // 求前缀和就是b数组
    for(int i = 1; i <= n; i++) b[i] = b[i-1] + b[i];// 相当于在求a[i] = b1 + b2 + bi
    for(int i = 1; i <= n; i++) printf("%d ",b[i]);
	
	// 或者用下面的方式
	// 求前缀和就是a数组
    for(int i = 1; i <= n; i++) a[i] = a[i-1] + b[i];// a[i] - a[i-1] = b[i]
    
    for(int i = 1; i <= n; i++) printf("%d ",a[i]);
    return 0;
}
```
## 4 二维差分
### 4.1 模板
![在这里插入图片描述](https://img-blog.csdnimg.cn/99157407be7948278f474eabf1d0c9c1.png)

```cpp
给以(x1, y1)为左上角，(x2, y2)为右下角的子矩阵中的所有元素加上c：
S[x1, y1] += c, S[x2 + 1, y1] -= c, S[x1, y2 + 1] -= c, S[x2 + 1, y2 + 1] += c
```
### 4.2 习题 — 798.差分矩阵
[Acwing 798.差分矩阵](https://www.acwing.com/problem/content/800/)

```cpp
#include<iostream>
using namespace std;

int n, m, q;
const int N = 1010;
int a[N][N], b[N][N];

void insert(int x1, int y1, int x2, int y2, int c)
{
    b[x1][y1] += c;
    b[x2+1][y1] -= c;
    b[x1][y2+1] -= c;
    b[x2+1][y2+1] += c;
}

int main()
{
    scanf("%d%d%d",&n, &m, &q);
    
    for(int i = 1;i <= n;i++)
        for(int j = 1;j <= m;j++)
            scanf("%d",&a[i][j]);
            
    for(int i = 1;i <= n;i++)
        for(int j = 1; j <= m;j++)
            insert(i,j,i,j,a[i][j]);
            
    while(q--)
    {
        int x1, y1, x2, y2, c;
        cin >> x1 >> y1 >> x2 >> y2 >> c;
        insert(x1,y1,x2,y2,c);
    }
    
    // 求前缀和
    for(int i = 1; i <= n; i++)
        for(int j = 1;j <= m; j++)
            b[i][j] += b[i-1][j] + b[i][j-1] -b[i-1][j-1];
            // a[i][j] = a[i - 1][j] + a[i][j - 1] - a[i - 1][j - 1] + b[i][j]
            
    for(int i = 1; i <= n; i++)
    {
        for(int j = 1;j <= m; j++) printf("%d ",b[i][j]);
        puts("");
    }
    return 0;
}
```

# 3 双指针/位运算/离散化/区间合并

## 1 双指针(滑动窗口)
### 1.1 模板
![在这里插入图片描述](https://img-blog.csdnimg.cn/d190203adad443229ca0619090787d64.png)
```cpp
for (int i = 0, j = 0; i < n; i ++ )
{
    while (j < i && check(i, j)) j ++ ;
    // 具体问题的逻辑
}
常见问题分类：
    (1) 对于一个序列，用两个指针维护一段区间
    (2) 对于两个序列，维护某种次序，比如归并排序中合并两个有序序列的操作
```
### 1.2 习题1 — 799.最长连续不重复序列
[Acwing 799.最长连续不重复子序列](https://www.acwing.com/problem/content/801/)
 - 红色指针和绿色指针中间是没有重复数字的，**绿色指针是 j，红色指针是 i**。判断红绿色指针之间有没有重复数字。红色指针向后移动的话，绿色指针也一定会向后移动，它们之间具有单调性
 - 如果判断之间有重复元素的话，就 j++
![在这里插入图片描述](https://img-blog.csdnimg.cn/85f8ea42da804abcbdef76b48fcc3491.png)
 - 这里应该是**i - j +1**, 不是j - i + 1
![在这里插入图片描述](https://img-blog.csdnimg.cn/9985843f7ee146a0b7116991179101d7.png)
 - 使用**s[N]来保存a[N]所对应数字的数量**，无论是a[i]还是a[j]都会找到相同的对应数字

![在这里插入图片描述](https://img-blog.csdnimg.cn/565cdba97b64449582d7645c9185c3cb.png)
```cpp
#include<iostream>
using namespace std;

const int N = 100010;

int n;
int a[N];// 原来数组
int s[N];// j 到 i之间每个数出现的次数，初始化为0

int main()
{
    cin >> n;
    for(int i = 0;i < n; i++) cin >> a[i];
    
    int res = 0;// 答案
    for(int i = 0, j = 0;i < n;i++)
    {
        s[a[i]]++;// 指针i所指的数字的数量增加1次
        while(s[a[i]] > 1)// 判断哪个数重复了
        {
            s[a[j]] --;// 重复之后，指针j向右移动，所指的数字的数量减少1次，直到a[i]所指的数字的数量降到1为止，表明没有重复
            j ++;//  指针j向右移动1次
        }
        
        res = max(res, i - j + 1);
    }
    cout << res << endl;
    return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/fd2149b0ed9842cfbd8479e7101ae418.png)
### 1.3 习题2 — 800.数组元素的目标和
[Acwing 800.数组元素的目标和](https://www.acwing.com/problem/content/802/)
### 1.4 习题3 — 816.判断子序列
[Acwing 816.判断子序列](https://www.acwing.com/problem/content/2818/)

## 2 位运算
### 2.1 模板
 - 在n的二进制表示中第k位是几
```cpp
求n的第k位数字: n >> k & 1
返回n的最后一位1：lowbit(n) = n & -n
```
#### 2.1.1 求n的第k位数字
![在这里插入图片描述](https://img-blog.csdnimg.cn/5489a9c43f914b56856fd18c00944ba2.png)
#### 2.1.2 返回n的最后一位1(lowbit函数)

```cpp
返回n的最后一位1：lowbit(n) = n & -n，相当于lowbit(n) = n & (~n + 1) 取反+1
```

 - lowbit函数
![在这里插入图片描述](https://img-blog.csdnimg.cn/423c96f801be48ce80cd74b1e50d089d.png)
 - 具体实现步骤
![在这里插入图片描述](https://img-blog.csdnimg.cn/5f55168bc6db4bb9824fc2dfaef30a83.png)
### 2.2 习题1 — 801.二进制中1的个数(lowbit函数)
[Acwing 801.二进制中1的个数](https://www.acwing.com/problem/content/803/)

```cpp
#include<iostream>
using namespace std;

int lowbit(int x)// lowbit函数，返回x的最后一位1。x应该是二进制
{
    return x & -x;// lowbit(n) = n & -n 就是lowbit(n) = n & ~n + 1, 就是取反加1
}

int main()
{
    int n;
    cin >> n;

    while(n--)
    {
        int x;
        cin >> x;
        
        int res = 0;// 最后要置零，否则会叠加
        while(x) x -= lowbit(x), res++;// 每次减去x的最后一个1，这里的x是二进制
        
        cout << res << ' ';
    }
    return 0;
}
```
 - 源码、补码、反码
![在这里插入图片描述](https://img-blog.csdnimg.cn/24fb08b4b0c04e6cb5448fc36795927f.png)
## 3 离散化(重要)
![在这里插入图片描述](https://img-blog.csdnimg.cn/a1becb0d209b4ae09849154eadde36a4.png)
### 3.1 模板
![在这里插入图片描述](https://img-blog.csdnimg.cn/bd9809607976414dbdb99ca62503f67b.png)
 - **erase的地方是重复的元素**
 - **unique函数会返回不重复的前面那段最后数字的下标**

```cpp
vector<int> alls; // 存储所有待离散化的值，这里的alls就是a数组
sort(alls.begin(), alls.end()); // 将所有值排序
alls.erase(unique(alls.begin(), alls.end()), alls.end());   // 去掉重复元素

// 二分求出x对应的离散化的值
int find(int x) // 找到第一个大于等于x的位置
{
    int l = 0, r = alls.size() - 1;
    while (l < r)
    {
        int mid = l + r >> 1;
        if (alls[mid] >= x) r = mid;
        else l = mid + 1;
    }
    return r + 1; // 映射到1, 2, ...n(加1表示从1开始映射，不加1表示从0开始映射)
}
```
### 3.2 习题1 — 802.区间和
[Acwing 802.区间和](https://www.acwing.com/problem/content/804/)

 - 特点是数字非常稀疏，需要用离散化方式做
![在这里插入图片描述](https://img-blog.csdnimg.cn/ace92da0d5d44f52b034815b479f62dc.png)
 - 在x位置加上c，只需要a[x] += c
 - 做n次操作，需要n个下标，m次询问，需要2m个下标。所以总共只需要2m+n个下标
 - 把用到数组下标映射到从1开始的自然数
![在这里插入图片描述](https://img-blog.csdnimg.cn/0a2e699a7d224a02ac463a556f1156c6.png)

```cpp
#include<iostream>
#include<vector>// 使用vector做离散化
#include<algorithm>

using namespace std;

typedef pair<int,int> PII;// 输入n次操作和m次询问，输入对象都是一对int值

const int N = 300010;// 做n次操作，需要n个下标，m次询问，需要2m个下标, 总共只需要2m+n个下标. n好m的范围都是小于100000
int a[N], s[N];

vector<int> alls;// 存入所有需要离散化值的坐标
vector<PII> add, query;// 前面是n次的添加操作，后面是m次的查询操作

// find函数求这个值离散化之后的结果
int find(int x)
{
    int l = 0, r = alls.size() - 1;
    while(l < r)
    {
        int mid = l + r >> 1;
        if(alls[mid] >= x) r = mid;
        else l = mid + 1;
    }
    return r + 1;// 将原来的位置x按照大小映射到1, 2, ...n(加1表示从1开始映射)
}

int main()
{
    // 先读入所有的数据，然后将用到的数据进行离散化处理
    int n, m;
    cin >> n >> m;
    for(int i = 0; i < n; i++)
    {
        int x, c;
        cin >> x >> c;
        add.push_back({x,c});
        
        alls.push_back(x);// 将坐标x加入到离散化的数组里面
    }
    
    for(int i = 0; i < m; i++)
    {
        int l, r;
        cin >> l >> r;
        query.push_back({l, r});
        
        alls.push_back(l);
        alls.push_back(r);// 把所有需要用到的值的下标都放在了alls里面
    }
    
    // alls数组去重，数的下标值有可能有重复(需要用到模板)
    sort(alls.begin(),alls.end());// 先进行排序
    // unique函数是把里面所有的重复元素删掉，把不重复的数组放到前面去，返回的是新数组最后的位置
    alls.erase(unique(alls.begin(),alls.end()),alls.end());
    
    
    // 处理插入
    for(auto item : add)
    {
        int x = find(item.first);// item.first下标位置x, 使用find函数返回位置x映射的值
        a[x] += item.second;// 在位置x进行值的相加c
    }
    
    // 预处理前缀和
    for(int i = 1; i <= alls.size(); i++) s[i] = s[i - 1]+ a[i];// 这里的i可以取到alls.size()
    
    // 处理查询
    for(auto item : query)
    {
        int l = find(item.first), r = find(item.second);// [l, r]分别映射到左右，item.first就是[l,r]的l
        // 前缀和公式，求[l,r]之间的数字和
        cout << s[r] - s[l-1] << endl;
    }
    return 0;
}
```
## 4 区间合并
### 4.1 模板
```cpp
// 将所有存在交集的区间合并
void merge(vector<PII> &segs)
{
    vector<PII> res;

    sort(segs.begin(), segs.end());

    int st = -2e9, ed = -2e9;
    for (auto seg : segs)
        if (ed < seg.first)
        {
            if (st != -2e9) res.push_back({st, ed});
            st = seg.first, ed = seg.second;
        }
        else ed = max(ed, seg.second);

    if (st != -2e9) res.push_back({st, ed});

    segs = res;
}
```
### 4.2 习题1 — 803.区间合并
[Acwing 803.区间合并](https://www.acwing.com/problem/content/805/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/e12d681026df493eb56fa2e41837cad8.png)
 - 三种情况分析
![在这里插入图片描述](https://img-blog.csdnimg.cn/f563c9ed387c42e8b252733f451c5e9d.png)

```cpp
#include<iostream>
#include<vector>
#include<algorithm>

using namespace std;

typedef pair<int, int> PII;// 左边first存区间左端点，右边second存区间右端点

const int N = 100010;

vector<PII> segs;

void merge(vector<PII>&segs)// vector本质上是一个动态数组，
{
    vector<PII> res;// 存合并之后结果
    
    sort(segs.begin(),segs.end());// 把所有区间按照左端点从小到大顺序排列
    
    int st = -2e9, ed = -2e9;// 数据范围是大于-1e9, 这里是设计边界值
    for(auto seg : segs)// 从左往右扫描所有区间线段
    {
        if(ed < seg.first)// 维护的区间右端点ed是严格小于枚举的区间的左端点，没有任何交集
        {
            if(st != -2e9) res.push_back({st, ed});// 判断不是最开始初始区间，就加入到答案里面
            st = seg.first, ed = seg.second;
        }
        else ed = max(ed, seg.second);// 否则的话说明区间有交集，求两区间的并集，将右端点更新为最大值
    }
    
    if(st != -2e9) res.push_back({st, ed});// 防止是空区间，将最后一个区间加到答案里面(有可能最后一段区间和前面都没有交集)
    
    segs = res;// 区间更新为segs
}

int main()
{
    int n;
    cin >> n;// 读入n个区间
    
    for(int i = 0; i < n; i++)
    {
        int l, r;
        cin >> l >> r;// 读入左右端点
        segs.push_back({l, r});
    }
    merge(segs);// 区间合并
    
    cout << segs.size() << endl;// 返回区间合并后的序列长度
    return 0;
}
```

# 4 单链表/双链表/栈/单调栈/队列/单调队列/KMP

## 1 单链表(用数组模拟链表)
 - **单链表用的最多的是存储图和树**
 - e[N]表示当前结点的值，ne[N]表示指向下一个结点。都是整数型数组，空结点的下标用-1表示
 - ne[N] = N + 1记录指向下一个结点
![在这里插入图片描述](https://img-blog.csdnimg.cn/dd25fe401b204eeb81513bdaea45f900.png)
```cpp
// head存储链表头，e[]存储节点的值，ne[]存储节点的next指针，idx表示当前用到了哪个节点
int head, e[N], ne[N], idx;

// 初始化
void init()
{
    head = -1;
    idx = 0;
}

// 在链表头插入一个数a
void insert(int a)
{
    e[idx] = a, ne[idx] = head, head = idx ++ ;
}

// 将头结点删除，需要保证头结点存在
void remove()
{
    head = ne[head];
}
```
### 1.1 模板
 - **ne[ ]存储节点的next指针，就是ne[k]里面存的是k+1，就是ne[k] = k + 1**

```cpp
#include<iostream>
using namespace std;

const int N = 100010;

// head表示头结点的下标
// e[i]表示节点i的值
// ne[i]表示节点i的next指针是多少，就是该点的指针指向
// idx存储当前已经用到了哪个点
int head, e[N], ne[N], idx;

// 初始化
void init()
{
    head = -1;
    idx = 0;
}

// 将x值插到头结点(头插法)
void add_to_head(int x)
{
	// head 表示头结点的下标
    e[idx] = x;// 将x的值存下来
    ne[idx] = head;// 将红色的指针1指向之前head存的，相当于ne[idx] ——> head
    head = idx;// 将head指向红色指针2，相当于 head ——> idx
    idx ++;
}

// 将x插到下标k的点后面
void add(int k, int x)// idx就是插入的点，ne[x]存的是x点下一点坐标值
{
	e[idx] = x;// 先存下x值
	ne[idx] = ne[k];// 红颜色的指针1指向k的下一个点(k点就是点2，k的下一个点是点3)
	ne[k] = idx;// 点k指向idx，就是插入的点
	idx ++;
}

// 将下标为k的点后面的点删除，比如k=1就是要删除2号点
void remove(int k)
{
	ne[k] = ne[ne[k]];// 就是说将下下个指针赋给k的下一个指针,跳过第k+1个点
}
```
#### 1.1.1 头部插入元素模板
- 在**头部插入元素**
![在这里插入图片描述](https://img-blog.csdnimg.cn/759b47a214fb4731a2565e86d9b0d7a8.png)
```cpp
// 将x值插到头结点(头插法)
void add_to_head(int x)// idx表示插入点的下标值，插入的第1个点idx = 0
{
	// head 表示头结点的下标，存储链表头，head的存储的值时0，head——>0
	// ne[ ]存储节点的next指针，就是ne[k]里面存的是k+1，就是ne[k] = k + 1
    e[idx] = x;// 将x的值存下来
    ne[idx] = head;// 红色指针1指向之前head存的，之前是head指向节点0，现在换成ne[idx]指向节点0, 这里的ne[idx]存储的就是idx+1
    head = idx;// 将head指向红色指针2，相当于 head ——> idx，idx = 0
    idx ++;
}
```
#### 1.1.2 第k个位置插入元素模板
- 在**第 k 个位置插入元素**
![在这里插入图片描述](https://img-blog.csdnimg.cn/c49f742fec5043b99eb7b67cbda199cf.png)
```cpp
// 将x插到下标k的点后面，k是从0开始的
void add(int k, int x)// idx就是插入的点，ne[x]存的是x点下一点坐标值
{
	// k=2，表示将点插入到点2的后面，原来ne[2] = 3，现在ne[idx] = 3，ne[2] = idx
	e[idx] = x;// 先存下x值
	ne[idx] = ne[k];// 红颜色的指针1指向k的下一个点(k点就是点2，k的下一个点是点3)
	ne[k] = idx;// 点k指向idx，就是插入的点， 2——>idx
	idx ++;
}
```
#### 1.1.3 删除元素模板
![在这里插入图片描述](https://img-blog.csdnimg.cn/6c2cb7e2309244ac8381286f5386c7d7.png)
```cpp
// 将下标为k的点后面的点删除，比如k = 1就是要删除点2
void remove(int k)
{
	ne[k] = ne[ne[k]];// 就是说将下下个指针赋给k的下一个指针,跳过第k+1个点
}
```
### 1.2 习题1 — 826.单链表
[Acwing 826.单链表](https://www.acwing.com/problem/content/828/)

- 刚开始头结点 head 指向空，第1个点插入点的下标为0，...，第 k 个插入点的下标为 k-1，就是idx的值(idx从0开始)
![在这里插入图片描述](https://img-blog.csdnimg.cn/9100c197c8b64c93a0413f64c92d9aae.png)
- H 9：插入第1个点，下标 idx 为 0，值 e 为 9
![在这里插入图片描述](https://img-blog.csdnimg.cn/5d60ce002d6041d8941ca1554ff93608.png)
- I 1 1：第1个点后面插入新的点，即第2个插入的点，下标 idx = 1，值 e 为 1
![在这里插入图片描述](https://img-blog.csdnimg.cn/c0b5da9b0de046b78b8ca6a640042860.png)
- D 1：删除第1个插入的点的下一个点，就是下标 idx = 1, 值 e 为 1 的点(这张图有问题，应该**删除第2个点**)，保留下标为0，e = 9的点
![在这里插入图片描述](https://img-blog.csdnimg.cn/5181546affdd45769f2d2a15342e796e.png)
- D 0：删除头结点，就是将整个链表删除
- H 6：插入头结点，值 e 为 6，idx = 2;
- I 3 6：第3个插入的点(idx = 2)后面插入点，该点 idx = 3，值为 6
- I 4 5：第4个插入的点(idx = 3)后面插入点，该点 idx = 4，值为 5(第1个插入的点，idx = 0)
- I 4 5：第4个插入的点(idx = 3)后面插入点，该点 idx = 5，值为 5
- I 3 4：第3个插入的点(idx = 2)后面插入点，该点 idx = 6，值为 4
![在这里插入图片描述](https://img-blog.csdnimg.cn/c2db290d6aa949dcba5e83c9ad2408f8.png)
- D 6：删除第6个插入的点的下一个点，就是 idx = 5的点的下一个点，即idx = 4的点(所以这张图也是有问题的，应该删除idx = 4的点)
![在这里插入图片描述](https://img-blog.csdnimg.cn/e3ea4b5c13564b3f9eef51f3496da582.png)

```cpp
#include<iostream>
using namespace std;

const int N = 100010;
// k 表示当前点是第k个插入的点, 从1开始算(由题意可知输入进来的值),
// 代入进来的时候需要 k - 1, 这样也可以从0开始算，第k个插入的点下标就是k-1
// idx 表示新插入的点的下标, 从0开始算

// head表示头结点的下标
// e[i]表示节点i的值
// ne[i]表示节点i的next指针是多少，就是该点的指针指向
// idx存储当前已经用到了哪个点
int head, e[N], ne[N], idx;

// 初始化
void init()
{
    head = -1;// 刚开始head指向空集
    idx = 0;
}

// 将x值插到头结点(头插法)
void add_to_head(int x)
{
	// head 表示头结点的下标
    e[idx] = x;// 将x的值存下来。刚开始插入点，e[0] = x，就是将x值存在e[0]
    ne[idx] = head;// 将红色的指针1指向之前head存的，相当于ne[idx] ——> head。刚开始插入点，ne[0] = -1，第1个点指向空集
    head = idx;// 将head指向红色指针2，相当于 head ——> idx。刚开始插入的第1个点，head = 0
    idx ++;
}

// 将x插到第k个插入的点的后面(和模板不一样，模板的k是第k个位置，这里的k表示第k个插入的点，就是第k-1的位置)
void add(int k, int x)// idx就是插入的点，ne[x]存的是x点下一点坐标值
{
	e[idx] = x;// 先存下x值
	ne[idx] = ne[k];// 红颜色的指针1指向k的下一个点(k点就是点2，k的下一个点是点3), ne[k] = 2，通过赋值操作，nex[idx] = 2(点3)，下标为2，表示第3个插入的点
	ne[k] = idx;// 点k指向idx，就是插入的点
	idx ++;
}

// 将下标为k的点后面的点删除，比如k = 1就是要删除k = 2点
void remove(int k)
{
	ne[k] = ne[ne[k]];// 就是说将下下个指针赋给k的下一个指针,跳过第k+1个点
}

int main()
{
    int m;
    cin >> m;// 一共要进行m次操作
    
    init();// 需要进行初始化
    
    while(m--)
    {
        int k, x;
        char op;
        
        cin >> op;
        if(op == 'H')// 头部插入点的操作
        {
            cin >> x;
            add_to_head(x);
        }
        else if(op == 'D')// 进行删除第k点后面的点的操作
        {
        	// k 表示当前点是第k个插入的点, 从1开始算，第k个插入的点下标就是k-1，算法都是按照下标进行的
            cin >> k;
            if(!k) head = ne[head];// 如果k = 0, 则head指向下下个指针
            remove(k - 1);
        }
        else
        {
            cin >> k >> x;
            add(k - 1, x);
        }
    }
    for(int i = head; i != -1; i = ne[i]) cout << e[i] << ' ';// ne[i]就是不断向前走一步,ne[i]存的是下一个点的下标
    cout << endl;
}
```
## 2 双链表
### 2.1 模板
- 下标0是最左边的点，下标1是最右边的点
- 0是左端点，1是右端点，0号点右边是1号点，1号点的左边是0号点
![在这里插入图片描述](https://img-blog.csdnimg.cn/93497b02f1db4f19ae01dfbfa26625de.png)
```cpp
// e[]表示节点的值，l[]表示节点的左指针，r[]表示节点的右指针，idx表示当前用到了哪个节点
int e[N], l[N], r[N], idx;

// 初始化
void init()
{
    //0是左端点，1是右端点
    l[1] = 0, r[0] = 1;// 1号点的左边是0号点，0号点右边是1号点
    idx = 2;// 0和1已经被占用了，idx从2开始
}

// 在节点a的右边插入一个数x
void insert(int a, int x)
{
    e[idx] = x;
    l[idx] = a, r[idx] = r[a];
    l[r[a]] = idx, r[a] = idx ++ ;
}

// 删除节点a
void remove(int a)
{
    l[r[a]] = l[a];
    r[l[a]] = r[a];
}
```
#### 2.1.1 插入操作
![在这里插入图片描述](https://img-blog.csdnimg.cn/689abd30564e4c23b937da109e693014.png)
- 必须先修改 l[r[k]] = idx 才能进行 l[k] = idx
![在这里插入图片描述](https://img-blog.csdnimg.cn/fab5dbf14c294719b3ea7e0248fe18f2.png)
```cpp
// 先进行初始化
void init()
{
    //0是左端点，1是右端点
    l[1] = 0, r[0] = 1;// 1号点的左边是0号点，0号点右边是1号点
    idx = 2;// 0和1已经被占用了，idx从2开始
}

// 在下标是k的点的右边插入x。如果是在k的左边插入x，则直接调用add(l[k], x)
void add(int k, int x)
{
    e[idx] = x;
    r[idx] = r[k];// k指针的右边赋给idx的右边(右边红色箭头)
    l[idx] = k;// idx指针的左边指向k(左边红色箭头)
    l[r[k]] = idx;// k右边指针再指向idx(必须先进行右边绿色箭头)
    l[k] = idx;// k的左边指向idx(再进行左边绿色箭头)
    idx ++;
}
```
#### 2.1.2 删除操作
- 直接将点的左边等于右边，点的右边等于左边
![在这里插入图片描述](https://img-blog.csdnimg.cn/e1eb191164ed4ee29ec453283a657c8d.png)
```cpp
// 删除第k个结点
void remove(int k)
{
    r[l[k]] = r[k];// k左边的右边直接等于k的右边
    l[r[k]] = l[k];// k右边的左边直接等于k的左边
}
```
### 2.2 习题1 — 827.双链表
[Acwing 827.双链表](https://www.acwing.com/problem/content/829/)

```cpp
#include<iostream>
using namespace std;

const int N = 100010;

int m;
int e[N], l[N], r[N], idx;// e[]表示节点的值，l[]表示节点的左指针，r[]表示节点的右指针，idx表示当前用到了哪个节点

// 初始化
void init()
{
    //0是左端点，1是右端点
    l[1] = 0, r[0] = 1;// 1号点的左边是0号点，0号点右边是1号点
    idx = 2;// 0和1已经被占用了，idx从2开始
}

// 在下标是k的点的右边插入x
void add(int k, int x)
{
    e[idx] = x;
    r[idx] = r[k];// k指针的右边赋给idx的右边
    l[idx] = k;// idx指针的左边指向k
    l[r[k]] = idx;// k右边指针再指向idx
    l[k] = idx;// k的左边指向idx
}

// 删除第k个结点
void remove(int k)
{
    r[l[k]] = r[k];// k左边的右边直接等于k的右边
    l[r[k]] = l[k];// k右边的左边直接等于k的左边
}
```
## 3 栈(用数组模拟栈)
- 栈先进后出，队列先进先出
### 3.1 模板
```cpp
// tt表示栈顶
int stk[N], tt = 0;

// 向栈顶插入一个数
stk[ ++ tt] = x;

// 从栈顶弹出一个数
tt -- ;

// 栈顶的值
stk[tt];

// 判断栈是否为空
if(tt > 0) not empty;
else empty;
```
- 上课代码
```cpp
#include<iostream>
using namespace std;
const int N = 100010;

int stk[N], tt;// stk[N]表示栈，tt表示栈顶，默认tt初始值为0

// 栈顶插入x
stk[++ tt] = x;

// 栈顶弹出x
tt--;// 栈顶下标--即可

// 判断栈是否为空
if(tt > 0) not empty;
else empty;

// 栈顶
stk[tt];
```

### 3.2 习题1 — 828.模拟栈
[Acwing 828.模拟栈](https://www.acwing.com/problem/content/830/)

## 4 单调栈
- 双指针暴力做法，找到距离i最近的比i小的值，j是从i-1的位置开始找起，即找到i的左边第一个比i小的数(离i最近的小的数)
![在这里插入图片描述](https://img-blog.csdnimg.cn/0cd5d6edec0c4a0d9f59097057e53b2f.png)
### 4.1 模板
```cpp
常见模型：找出每个数左边离它最近的比它大/小的数
int tt = 0;
for (int i = 1; i <= n; i ++ )
{
    while (tt && check(stk[tt], i)) tt -- ;
    stk[ ++ tt] = i;
}
```
### 4.2 习题1 — 830.单调栈
[Acwing 830.单调栈](https://www.acwing.com/problem/content/832/)

```cpp
#include<iostream>
using namespace std;

const int N = 100010;
int stk[N], tt = 0;// tt默认初始值为0

int main()
{
	cin.tie(0);
	ios::sync_with_stdio(false);// 提高速度
    int n;// 读入第1行的数
    cin >> n;
    
    for(int i = 0; i < n; i++)
    {
        int x;
        cin >> x;
        while(tt && stk[tt] >= x) tt--;// 栈不为空且栈顶元素大于给的x值，就弹出栈顶元素
        if(tt) cout << stk[tt] << ' ';// 如果栈不为空，则输出距离x最近的比x小的值
        else cout << -1 << ' ';
        
        stk[++ tt] = x;// 把x插入到栈里面，每个元素只能出入栈一次，时间复杂度为2n
    }
    return 0;
}
```
- 使用scanf进行读入，可以提升程序的运行速度
```cpp
int main()
{
    int n;// 读入第1行的数
    scanf("%d",&n);
    
    for(int i = 0; i < n; i++)
    {
        int x;
        scanf("%d",&x);
        while(tt && stk[tt] >= x) tt--;// 栈不为空且栈顶元素大于给的x值，就弹出栈顶元素
        if(tt) printf("%d ",stk[tt]);// 如果栈不为空，则输出距离x最近的比x小的值
        else printf("-1");
        
        stk[++ tt] = x;// 把x插入到栈里面
    }
    return 0;
}
```

## 5 队列
### 5.1 模板
#### 5.1.1 普通队列
- 队头 hh 在左边，队尾 tt 在右边
- 队头弹出一个数据，则 hh++，队尾插入一个数据，则 tt++
![在这里插入图片描述](https://img-blog.csdnimg.cn/44eb84cb34c64e6ab13825e16f8ab6ac.png)
```cpp
// hh 表示队头，tt表示队尾
// 在队尾插入元素，在队头弹出元素
int q[N], hh = 0, tt = -1;

// 向队尾插入一个数
q[ ++ tt] = x;

// 从队头弹出一个数
hh ++ ;

// 队头的值
q[hh];

// 判断队列是否为空
if (hh <= tt)
{
}
```
- 上课代码
```cpp
// hh 表示队头，tt表示队尾
// 在队尾插入元素，在队头弹出元素
int q[N], hh = 0, tt = -1;// tt初始为-1，如果保证队头hh在队尾tt后面的话，hh应该小于tt才对

// 向队尾插入一个数
q[ ++ tt] = x;

// 从队头弹出一个数
hh ++ ;// 如下图所示hh++, 则队头数据弹出

// 取队头元素
q[hh];

// 取队尾元素
q[tt];

// 判断队列是否为空
if (hh <= tt) not empty
else empty;
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/44eb84cb34c64e6ab13825e16f8ab6ac.png)

#### 5.1.2 循环队列
```cpp
// hh 表示队头，tt表示队尾的后一个位置
int q[N], hh = 0, tt = 0;

// 向队尾插入一个数
q[tt ++ ] = x;
if (tt == N) tt = 0;

// 从队头弹出一个数
hh ++ ;
if (hh == N) hh = 0;

// 队头的值
q[hh];

// 判断队列是否为空
if (hh != tt)
{
}
```
### 5.2 习题1 — 829.模拟队列
[Acwing 829.模拟队列](https://www.acwing.com/problem/content/831/)

## 6 单调队列(滑动窗口)

### 6.1 模板
```cpp
常见模型：找出滑动窗口中的最大值/最小值
int hh = 0, tt = -1;// hh表示队头，tt表示队尾。
for (int i = 0; i < n; i ++ )
{
    while (hh <= tt && check_out(q[hh])) hh ++ ;  // 判断队头是否滑出窗口
    while (hh <= tt && check(q[tt], i)) tt -- ;
    q[ ++ tt] = i;
}
```
### 6.2 习题1 — 154.滑动窗口
[Acwing 154.滑动窗口](https://www.acwing.com/problem/content/156/)
- 前面的一个点比后面的一个点大(紧挨着的两个点)，在求最小值时，前面大的点没用的，就会被弹出去。就是出现有前面一个点大于后面一个点这样的逆序对，就把大的点删掉。这样**数列变成严格单调上升的队列**。队头就是最小值
![在这里插入图片描述](https://img-blog.csdnimg.cn/1f75e5c7a9c84adbbd2f465aa23cbd13.png)
- i是枚举的右端点，k是区间的长度，队列q[hh]存的是下标
![在这里插入图片描述](https://img-blog.csdnimg.cn/8b5d5969d8e34ecea32a7c99c9fe5f12.png)
 - 队头是指滑动窗口左边，队尾是滑动窗口右边。每次移动把新元素插到队尾，队头弹出滑出去的元素

```cpp
#include<iostream>
using namespace std;

const int N = 1000010;
int n, k;// n表示数组长度，k表示滑动窗格大小
int q[N], a[N];// 数组a存原来的值，q存单调队列

int main()
{
    scanf("%d%d", &n, &k);
    for(int i = 0; i < n; i++) scanf("%d",&a[i]);// 先把所有字符读进来
    
    // 求最小值
    int hh = 0, tt = -1;// hh表示队头，tt表示队尾(-1表示空)
    for(int i = 0; i < n; i++)
    {
        // 判断队头是否已经滑出窗口(队列里面存的是下标), 下面true的话表示已经滑出
        // 队头小于队尾，且i - k + 1表示窗格队头下标，q[hh](队列)存的是最小值的下标，如果小于就说明上一次的最小值在窗格内
        if (hh <= tt && i - k + 1 > q[hh]) hh ++;
        
        while (hh <= tt && a[q[tt]] >= a[i]) tt --;// q[tt]里面存的是下标，如果队尾的值大于当前值，则弹出队尾值
        
        q[++tt] = i;// 把当前数的下标插入到队列, 因为i有可能是最小值，所以需要先进行添加
        if(i >= k - 1) printf("%d ",a[q[hh]]);// 前k-1个数之后开始输出，如果i>=k-1，才开始输出，队头是最小值
        
        // 输出队列数据，看是否符合预期
        // for(int j = hh; j <= tt;j ++) printf("%d ",a[q[j]]);
        // puts("");
    }
    puts("");// 换行
    
    // 求最大值
    hh = 0, tt = -1;// hh表示队头，tt表示队尾(-1表示空)
    for(int i = 0; i < n; i++)
    {
        // 判断队头是否已经滑出窗口(队列里面存的是下标), 下面true的话表示已经滑出
        // 队头小于队尾，且i - k + 1表示窗格队头下标
        if (hh <= tt && i - k + 1 > q[hh]) hh ++;
        
        while (hh <= tt && a[q[tt]] <= a[i]) tt --;// q[tt]里面存的是下标，如果队尾的值大于当前值，则弹出队尾值
        
        q[++tt] = i;// 把当前数的下标插入到队列, 因为i有可能是最小值，所以需要先进行添加
        if(i >= k - 1) printf("%d ",a[q[hh]]);// 队头是最大值
    }
    puts("");// 换行
    return 0;
}
```
## 7 KMP
- 暴力解法
![在这里插入图片描述](https://img-blog.csdnimg.cn/7ea80d4ce3de41d898849a8fbf39ecf5.png)
- next[i] = j：表示数组p在[1,j]这个区间的值与[i-j+1,i]这个区间的值相等，如图1和图2所示。也就是说红色数组，[1, j]和[i-j+1, i]这两段数组相同。比如j=3,i=5,则[1,3]区间的数和[3,5]区间的数相同。
- next[i]里面存放的是[1,i]这个区间最长公共串的长度。
![在这里插入图片描述](https://img-blog.csdnimg.cn/a8f37f6c6a3c489e9afc5f62fded4099.png)
- 图2
![在这里插入图片描述](https://img-blog.csdnimg.cn/f9b505ebdfbc44db8d5d8e15c2585fab.png)
- 当蓝色在i位置，红色在 j+1 位置不匹配时，绿色是红色的一部分，使得满足红色数组部分p[1, m] = p[j - m + 1, j]两部分相等。就是红绿部分匹配符合next[j] = m式子。
- 绿色的圈是 i，红色的圈是 j。s[i] 不同于 p[j+1]，s[i-1] 相同于 p[j]
![在这里插入图片描述](https://img-blog.csdnimg.cn/d2873bdc6a8448ae9fa7d9b2c9d89d4a.png)
- Si 匹配 Pj+1

### 7.1 模板
```cpp
// s[]是长文本，p[]是模式串，n是s的长度，m是p的长度
求模式串的Next数组：
for (int i = 2, j = 0; i <= m; i ++ )
{
    while (j && p[i] != p[j + 1]) j = ne[j];
    if (p[i] == p[j + 1]) j ++ ;
    ne[i] = j;
}

// 匹配
for (int i = 1, j = 0; i <= n; i ++ )
{
    while (j && s[i] != p[j + 1]) j = ne[j];
    if (s[i] == p[j + 1]) j ++ ;
    if (j == m)
    {
        j = ne[j];
        // 匹配成功后的逻辑
    }
}
```
### 7.2 习题1 — 831.KMP字符串
[Acwing 831.KMP字符串](https://www.acwing.com/problem/content/833/)
[详细解释](https://www.acwing.com/solution/content/14666/)

- 图中绿色圈和红色的圈不能匹配，就是s[i] != p[j+1]
![在这里插入图片描述](https://img-blog.csdnimg.cn/aa9877603e8b4f90a7d5041c50a6fc6e.png)
- 如果不匹配就向后移动一格，ne[j] + 1 = j，在判断ne[j]后面的一个数是否和位置 i的数字相同
![在这里插入图片描述](https://img-blog.csdnimg.cn/db73e46b2a874f7fbaac45fc8b3a2eb9.png)

```cpp
#include<iostream>
using namespace std;

const int N = 100010, M = 1000010;// 大于给定的数

int n, m;// n表示模式串p的长度，m表示字符串S的长度
char p[N], s[M];// 字符串数组
int ne[N];// C++中定义为next会报错

int main()
{
    cin >> n >> p + 1 >> m >> s + 1;// p和s的下标从1开始
    
    // 求next[]数组过程
    for(int i = 2, j = 0; i <= n; i++)// i从2开始，i = 2时，j = 1，next[j = 1] = 0
    {
        while(j && p[i] != p[j + 1]) j = ne[j];// 退而求其次，就是整体向后移动一格
        if(p[i] == p[j + 1]) j ++;// 匹配上的话，j就向后移动一位
        ne[i] = j;// p[1,j] = p[i-j+1, i]
    }
    
    // kmp匹配过程
    for(int i = 1, j = 0;i <= m; i++)
    {
        // j没有退回起点(退回起点需要重新匹配)，且s[i]和p[j+1]不能相匹配(如图所示，与s[i]匹配的是p[j+1]，所以i=1时,j=0)
        while(j && s[i] != p[j + 1]) j = ne[j];// 绿色的圈不能和红色的圈匹配, ne[j]表示是[1,j]这个区间最长公共串的长度(红色)
        if(s[i] == p[j + 1]) j++;// 如果两个已经匹配，则j移动到下一个位置
        if(j == n)// 匹配成功
        {
            printf("%d ", i - n);// 起始位置，题目下标从0开始
            j = ne[j];// 往后退一步
        }
    }
    return 0;
}
```
- j = ne[j]
![在这里插入图片描述](https://img-blog.csdnimg.cn/43dad28289fe4e228fffc40aa7134f08.png)

# 5 Trie树/并查集/堆/哈希表/STL技巧

## 1 Trie树
- 使用Trie树的题目会限制字母的种类和数量，一般是26或者52个
- **高效存储和查找字符串集合的数据结构**
- **字符串最后都会被打上标记，表示以当前这个字母结尾是有个单词**
![在这里插入图片描述](https://img-blog.csdnimg.cn/180e0302a0414afeac597b36a0a8067f.png)
- 比如查找abcd，按照路线可以找到abcd字符串，但是d没有被标记，所以不存在abcd这个字符串
![在这里插入图片描述](https://img-blog.csdnimg.cn/4e56563931494648bf16a4f5c2a50d19.png)
### 1.1 模板
```cpp
int son[N][26], cnt[N], idx;
// 0号点既是根节点，又是空节点
// son[][]存储树中每个节点的子节点
// cnt[]存储以每个节点结尾的单词数量

// 插入一个字符串
void insert(char *str)
{
    int p = 0;
    for (int i = 0; str[i]; i ++ )
    {
        int u = str[i] - 'a';
        if (!son[p][u]) son[p][u] = ++ idx;
        p = son[p][u];
    }
    cnt[p] ++ ;
}

// 查询字符串出现的次数
int query(char *str)
{
    int p = 0;
    for (int i = 0; str[i]; i ++ )
    {
        int u = str[i] - 'a';
        if (!son[p][u]) return 0;
        p = son[p][u];
    }
    return cnt[p];
}
```
- 使用数组模拟指针，下标是x的点，这个节点所有的儿子，son[x]\[0]表示第1个儿子。
```cpp
#include<iostream>
using namespace std;

const int N = 100010;
int son[N][26];// 每个节点的子节点个数最多是26，每个节点最多向外连26条边
int cnt[N];// 以当前点结尾的单词有多少个，存储以每个节点结尾的单词数量
int idx = 0;// 表示当前用到哪个下标(节点)，下标为0的点，既是根节点，又是空节点

// 存储插入
void insert(char str[])
{
    int p = 0;// 从根节点开始，p的范围是0~9999，因为字符串总长度不超过100000
    for(int i = 0; str[i]; i++)// C++字符串结尾是\0, str[]判断是否走到结尾
    {
        int u = str[i] - 'a';// 把字母a~z映射成数字0~25
        if(!son[p][u]) son[p][u] = ++idx;// p这个节点不存在u这个儿子的话，就创建出来
        p = son[p][u];// 走到下一个点，因为son[p][u]的值会一直+1
    }
    cnt[p] ++;// 以这点为结尾的单词数量多了一个
}

// 查询字符串出现多少次
int query(char str[])
{
    int p = 0;
    for(int i = 0; str[i]; i++)
    {
        int u = str[i] - 'a';// 得到当前查询字母子节点的编号
        if(!son[p][u]) return 0;// 如果不存在当前字母，直接return 0
        p = son[p][u];//存在当前字母就走下去
    }
    return cnt[p];//返回以p结尾的单词数量
}
```

### 1.2 习题1 — 835.Trie字符串统计
[Acwing 835.Trie字符串统计](https://www.acwing.com/problem/content/837/)

```cpp
#include<iostream>
using namespace std;

const int N = 100010;
int son[N][26];// 每个节点的子节点个数最多是26，每个节点最多向外连26条边
int cnt[N];// 以当前点结尾的单词有多少个
int idx = 0;// 表示当前用到哪个下标(节点)，下标为0的点，既是根节点，又是空节点
char str[N];// 每次输入的字符串

// 存储插入
void insert(char str[])
{
    int p = 0;// 从根节点开始，p的范围是0~9999，因为字符串总长度不超过100000
    for(int i = 0; str[i]; i++)// C++字符串结尾是\0,str[]判断是否走到结尾
    {
        int u = str[i] - 'a';// 把字母a~z映射成数字0~25
        if(!son[p][u]) son[p][u] = ++idx;// p这个节点不存在u这个儿子的话，就创建出来
        p = son[p][u];//走到下一个点
    }
    cnt[p] ++;// 以这点为结尾的单词数量多了一个
}

// 查询字符串出现多少次
int query(char str[])
{
    int p = 0;
    for(int i = 0; str[i]; i++)
    {
        int u = str[i] - 'a';// 得到当前查询字母子节点的编号
        if(!son[p][u]) return 0;// 如果不存在当前字母，就是son[p][u] == 0, 直接return 0
        p = son[p][u];//存在当前字母就走下去
    }
    return cnt[p];//返回以p结尾的单词数量
}

int main()
{
    int n;// 输入n次
    scanf("%d",&n);
    while(n--)
    {
        char op[2];
        scanf("%s%s",op,str);// 先读入类型，再读入操作的字符串
        if(op[0] == 'I') insert(str);
        else printf("%d\n",query(str));
    }
    return 0;
}
```
### 1.3 习题2 — 143.最大异域对

## 2 并查集(常用)
![在这里插入图片描述](https://img-blog.csdnimg.cn/5dce69660bcd4064a5c6e4ba3bfa6ff9.png)
- 优化问题2，在x向上遍历的过程中，搜过路径的每一个节点最后都指向根节点，可以提升速度
- 优化方法叫：**路径压缩**
![在这里插入图片描述](https://img-blog.csdnimg.cn/c5301af9a4a04e83aa00a42df89e32a3.png)
### 2.1 查询元素
- 作用1：**询问两个元素是否在同一个集合中**
- 根节点的标号就是当前集合的编号，每个点都存储它的父节点是谁。
- 求当前点的编号就不断向上找父节点，直到找到根节点为止，则**当前节点的编号就是根节点的编号**。这样可以快速找到哪个元素属于哪个集合。
![在这里插入图片描述](https://img-blog.csdnimg.cn/5a5585780e294c068c7f9f802107faa5.png)
- p[x]表示当前点x的父节点
- 除了根节点p[x] == x之外，其他的点的父节点p[x]和x都不相等
- 不断往上判断，x = p[x]，父节点赋值给子节点，就是父节点一步一步变成子节点
### 2.2 集合合并
- 作用2：**将两个集合合并**
- px是x的集合编号，py是y的集合编号，p[x] = y，就是直接将x的集合插入到y里面，就是说将y看做是x的父节点
![在这里插入图片描述](https://img-blog.csdnimg.cn/d567ce9570ee403186e11a1cdce889db.png)

### 2.3 模板
- 只要记住例题的find函数模板
#### 2.3.1 朴素并查集
```cpp
	int p[N]; //存储每个点的祖宗节点

    // 返回x的祖宗节点
    int find(int x)
    {
        if (p[x] != x) p[x] = find(p[x]);
        return p[x];
    }

    // 初始化，假定节点编号是1~n
    for (int i = 1; i <= n; i ++ ) p[i] = i;

    // 合并a和b所在的两个集合：
    p[find(a)] = find(b);
```
#### 2.3.2 维护size的并查集
```cpp
	int p[N], size[N];
    //p[]存储每个点的祖宗节点, size[]只有祖宗节点的有意义，表示祖宗节点所在集合中的点的数量

    // 返回x的祖宗节点
    int find(int x)
    {
        if (p[x] != x) p[x] = find(p[x]);
        return p[x];
    }

    // 初始化，假定节点编号是1~n
    for (int i = 1; i <= n; i ++ )
    {
        p[i] = i;
        size[i] = 1;
    }

    // 合并a和b所在的两个集合：
    size[find(b)] += size[find(a)];
    p[find(a)] = find(b);
```
#### 2.3.3 维护到祖宗节点距离的并查集
```cpp
    int p[N], d[N];
    //p[]存储每个点的祖宗节点, d[x]存储x到p[x]的距离

    // 返回x的祖宗节点
    int find(int x)
    {
        if (p[x] != x)
        {
            int u = find(p[x]);
            d[x] += d[p[x]];
            p[x] = u;
        }
        return p[x];
    }

    // 初始化，假定节点编号是1~n
    for (int i = 1; i <= n; i ++ )
    {
        p[i] = i;
        d[i] = 0;
    }

    // 合并a和b所在的两个集合：
    p[find(a)] = find(b);
    d[find(a)] = distance; // 根据具体问题，初始化find(a)的偏移量
```
### 2.4 习题1 — 836.合并集合(模板例题)
[Acwing 836.合并集合](https://www.acwing.com/problem/content/838/)
[并查集总结](https://blog.csdn.net/m0_52361859/article/details/112851102)

 - p[find(a)] = find(b): p[x] = y，find(a)是a的祖宗节点，find(b)是b的祖宗节点。**让a的祖宗节点的父亲等于b的祖宗节点**

![在这里插入图片描述](https://img-blog.csdnimg.cn/3f230be63cfd43f8b2746395636439b5.png)
```cpp
// M 1,2最初1和2分别在两个集合，所以需要将1和2合并到一个集合。M 3,4同理
// 这里先进行合并，再进行查询
#include<iostream>
using namespace std;

const int N = 100010;

int n,m;// 读入数
int p[N];// 每个元素的父节点

//find函数和下面p[i] = i一起看(这段重点)
int find(int x)// 返回x的祖宗节点，就是x所在集合的编号 + 路径压缩优化
{
    if(p[x] != x) p[x] = find(p[x]);// 如果x不是根节点, 让左边的父节点等于右边的祖宗节点。求集合编号x = p[x]
    return p[x];// 返回父节点,p[x]里面已经有被赋的值(p[i] = i)
}

int main()
{
    scanf("%d%d", &n, &m);
    
    // 最开始每个数都是自己单独一个为集合，就是树根都是自己
    for(int i = 0; i < n; i++) p[i] = i;// p[x] == x时候，x就是树根，将所有的p值赋成自己。
    
    while(m--)
    {
        char op[2];// 有M和Q两种指令，sacnf读入字符串(%s)比字符(%c)更好用。无论读字符还是字符串，都用字符串来读
        int a, b;// 表示指令后面的两个数字
        scanf("%s%d%d", op, &a, &b);// 字符串数组名字本身就是数组首地址
        
        // 合并操作，p[x] = y，find(a)是a的祖宗节点，find(b)是b的祖宗节点。让a的祖宗节点的父亲等于b的祖宗节点
        if(op[0] == 'M') p[find(a)] = find(b);
        
        else    // 判断两个节点是不是在一个集合里面，此时op[0] = 'I'
        {
            if(find(a) == find(b)) puts("Yes");
            else puts("No");
        }
    }
    return 0;
}
```

### 2.5 习题2 — 837.连通块中点的数量
[Acwing 837.连通块中点的数量](https://www.acwing.com/problem/content/839/)

 - a, b可能相等，相等就在a上面画一个圈
 - C a b：在点 a 和点 b之间连一条边，a 和 b可能相等；
 - Q1 a b：询问点 a 和点 b 是否在同一个连通块中，a 和 b可能相等
 - Q a b：询问点 a所在连通块中点的数量
![在这里插入图片描述](https://img-blog.csdnimg.cn/4cade7d68e484009928d214554ad552c.png)
- 在两个连通块之间加一条线，就是相当于进行集合合并。a和b之间拉一条线就是进行合并
- 在集合中，只保证根节点的size是有意义的
![在这里插入图片描述](https://img-blog.csdnimg.cn/579b0cebafad491abe21a4e9510d0ae3.png)
- 合并之后，求集合中所有点的size，只需要size(a) + size(b)，a和b都是根节点
![在这里插入图片描述](https://img-blog.csdnimg.cn/60be358ff2864ab7bc664fb6ae49a77e.png)
```cpp
#include<iostream>
using namespace std;

const int N = 100010;

int n, m;
int p[N];


// 查找节点x的祖宗节点
int find(int x)
{
    if(p[x] != x) p[x] = find(p[x]);
    return p[x];
}

int main()
{
    scanf("%d%d",&n, &m);
    
    // size表示每一个集合的大小，就是每个集合里面点的数量。只保证祖宗节点(根节点)的size是有意义的
    int size[N];
    for(int i = 0; i < n; i++) 
    {
        p[i] = i;
        size[i] = 1;// 最开始每个集合数量为1
    }
    
    while(m--)
    {
        char op[5];
        int a, b;
        scanf("%s", op);// 数组首字母就是数组首地址
        
        if(op[0] == 'C') // 第1个操作是进行合并
        {
            scanf("%d%d",&a, &b);
            if(find(a) == find(b)) continue;// 如果a和b已经在同一个集合里，就直接跳过
            size[find(b)] += size[find(a)];// a的根节点合并到b的根节点之后，size就进行相加
            p[find(a)] = find(b);
        }
        else if(op[1] == '1')// 第2个操作是Q1,判断第二个字符是1即可
        {
            scanf("%d%d",&a, &b);
            if(find(a) == find(b)) puts("Yes");
            else puts("No");
        }
        else
        {
            // 求某一个点所在集合中点的数量(连通快中点的数量)
            scanf("%d", &a);
            printf("%d\n",size[find(a)]);// 只需要返回点a的根节点的size
        }
    }
    return 0;
}
```
## 3 堆(完全二叉树)
- STL可以实现前三个操作，STL里面的堆就是优先队列，priority_queue
- 基本操作1：down(x)
- 基本操作2：up(x)
- **heap[size]代表树的最后一个数，heap[1]代表树的第1个数**
- **插入一个数**：**heap[++size] = x; up(size);** 在树的最后插入一个数，将最后一个数size然后不断往上移动
- **求集合中的最小值**：**heap[1];** 根节点是最小值
- **删除最小值**：**heap[1] = heap[size]; size--; down(1);** 把最后一个元素覆盖到堆顶区，再把最后一个元素删除，最后将堆顶元素不断往下down。
![在这里插入图片描述](https://img-blog.csdnimg.cn/3fc8cdc92c684fb4ab8c02329a0e9220.png)
- **删除任意一个元素**：**heap[k] = heap[size]; size--;down[k];up[k];** 用最后一个数覆盖掉需要删除的数，根据大小来判断，是down还是up，只会执行一个
- **修改任意一个元素**：**heap[k] = x; down[k];up[k];**根据大小来判断，是down还是up，只会执行一个
![在这里插入图片描述](https://img-blog.csdnimg.cn/cd8adda66ace41768c2b380db115f8a8.png)
- 小根堆，每个点的左右两个子节点的值都大于父节点，所以小根堆的最小值是根节点
![在这里插入图片描述](https://img-blog.csdnimg.cn/11d5c8447d6942d0bd849c78452e14e0.png)
- 堆状数据结构，就是完全二叉树都用一维数组来存。**第1个位置是根节点，第x个结点的左儿子位置是2x，x的右儿子是2x+1**
![在这里插入图片描述](https://img-blog.csdnimg.cn/7a56801030b64e548cd63efd1f451b1c.png)
### 3.1 模板
```cpp
// h[N]存储堆中的值, h[1]是堆顶，x的左儿子是2x, 右儿子是2x + 1
// ph[k]存储第k个插入的点在堆中的位置
// hp[k]存储堆中下标是k的点是第几个插入的
int h[N], ph[N], hp[N], size;

// 交换两个点，及其映射关系
void heap_swap(int a, int b)
{
    swap(ph[hp[a]],ph[hp[b]]);
    swap(hp[a], hp[b]);
    swap(h[a], h[b]);
}

void down(int u)
{
    int t = u;
    if (u * 2 <= size && h[u * 2] < h[t]) t = u * 2;
    if (u * 2 + 1 <= size && h[u * 2 + 1] < h[t]) t = u * 2 + 1;
    if (u != t)
    {
        heap_swap(u, t);
        down(t);
    }
}

void up(int u)
{
    while (u / 2 && h[u] < h[u / 2])
    {
        heap_swap(u, u / 2);
        u >>= 1;
    }
}

// O(n)建堆
for (int i = n / 2; i; i -- ) down(i);
```
### 3.2 习题1 — 838.堆排序
[Acwing 838.堆排序](https://www.acwing.com/problem/content/840/)
[down 从n/2开始的分析](https://www.acwing.com/solution/content/6362/)
 - 这里只需要操作2和操作3
- **求集合中的最小值**：**heap[1];** 根节点是最小值
- **删除最小值**：**heap[1] = heap[size]; size--; down(1);** 把最后一个元素覆盖到堆顶区，再把最后一个元素删除，最后将堆顶元素不断往下down。
```cpp
// 就是要求最小值，并且不断删除最小值，再求最小值，删除
#include<iostream>
#include<algorithm>// swap函数
using namespace std;

const int N = 100010;
int n, m;
int h[N], mySize;// h就是heap, size表示存在当前heap里面的元素

// down函数
void down(int u)// 求父节点和两个子节点中最小值，u表示数组下标编号
{
    int t = u;// t表示三个点里面的最小值的位置标号
    // 第1个位置是根节点，第u个结点的左儿子位置是2u，右儿子位置是2u+1
    if( u * 2 <= mySize && h[u * 2] < h[t]) t = u * 2;// 判断节点u的左儿子是否比点u大，小的话将最小值位置坐标赋给t
    if( u * 2 + 1 <= mySize && h[u * 2 + 1] < h[t]) t = u * 2 + 1;
    if(u != t)// 表示当前根节点不是最小值
    {
        swap(h[u],h[t]);// 将最小值节点和当前值节点交换
        down(t);// 再将t结点down
    }
}

// up函数
void up(int u)
{
    while(u / 2 > 0 && h[u / 2] > h[u])// u是子节点，u/2表示父节点，h[u/2]表示父节点的值，h[u]表示子节点的值
    swap(h[u/2],h[u]);
    u /= 2;// u = u/2表示将当前的父节点再赋值为子节点，一步一步向上
}

int main()
{
    scanf("%d%d", &n, &m);
    for(int i = 1; i <= n; i++) scanf("%d",&h[i]);
    mySize = n;// 开始size的值就是n
    
    for(int i = n/2; i; i--) down(i);// 首先进行堆排序，序号从1开始
    while(m--)
    {
        printf("%d ",h[1]);// 打印出堆顶元素，就是最小值
        h[1] = h[mySize];// 把最后一个元素赋给堆顶元素
        mySize --;// 这三句话表示删除堆顶元素(最小值)
        down(1);// 把堆顶元素按照大小down下来
    }
    return 0;
}
```

### 3.3 习题2 — 839.模拟堆
[Acwing 839.模拟堆](https://www.acwing.com/problem/content/841/)

 - 难点在于删除第k个插入的数(而不是第k个数)
 - **ph[k]存的是第k个插入的数在堆里面的下标是什么**
 - **hp[k]存的是堆里面第k个点是第几个插入的点**
![在这里插入图片描述](https://img-blog.csdnimg.cn/d1269554dc10448f839492fdfbdada8c.png)
- 两个数交换后
- **ph[j] = k 表示第 j 个插入的数在堆里面的下标是 k**
- **hp[k] = j 表示堆里面下标为 k 的数是第 j 个插入的数**
- 需要从第几个插入的元素找队里的元素，有需要从堆里面的元素确定是第几个插入的
![在这里插入图片描述](https://img-blog.csdnimg.cn/83c5e67be8b544a484f5620710d82d05.png)
```cpp
swap(ph[hp[a]], ph[hp[b]]);// 绿色部分
swap(hp[a],hp[b]);// 红色部分
swap(h[a],h[b]);
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/915e30af5df64e1b92f035b5fb463aa8.png)

```cpp
// 老师讲解中所有的size都不能用，用其他代替
#include<iostream>
#include<algorithm>//  swap函数
#include<cstring>
#include<stdio.h>// C的头文件
using namespace std;

const int N = 100010;
int h[N], asize = 0;// heap[]数组
int ph[N], hp[N];// ph[k]表示第k个插入的数在堆里面的下标是什么，hp[k]表示堆里面第k个点是第几个插入的点

// 交换，进行存储映射(ph[i]和ph[j]所指的数)
void heap_swap(int a, int b)// a和b均表示堆里面元素的下标
{
    // 如上图存在 ph[j] = k, hp[k] = j的映射关系
    // 这里是hp[a] = i, ph[i] = a，hp[b] = j, ph[j] = b，所以交换ph[]所指的方向
    swap(ph[hp[a]], ph[hp[b]]);
    swap(hp[a],hp[b]);
    swap(h[a],h[b]);
}

// down函数
void down(int u)
{
    int t = u;// 先假设父节点为最小值，u表示下标标号
    if(u * 2 <= asize && h[u * 2] < h[t]) t = u * 2;// 左儿子小于父节点，则最小值t为左儿子
    if(u * 2 + 1 <= asize && h[u * 2 + 1] < h[t]) t = u * 2 + 1;
    if(u != t)
    {
        heap_swap(u, t);// 这里u是父节点，t是子节点，不等于的话说明子节点比父节点值小，所以要交换
        down(t);
    }
}

void up(int u)
{
    while(u / 2 && h[u / 2] > h[u])// 父节点大于子节点，就交换
    {
        heap_swap(u / 2, u);
        u = u / 2;
    }
}

int main()
{
    int n, m = 0;// m表示当前第几个插入的数
    scanf("%d",&n);
    while(n --)
    {
        char op[10];
        int x, k;
        scanf("%s", op);
        
        // 操作1: 将输入的数插入到堆的末尾，再进行up操作
        if(!strcmp(op, "I"))// 字符串比较，strcmp(a, b)，比较两个字符串的大小，a < b 返回-1，a == b 返回0，a > b返回1 
        {
           scanf("%d",&x);// 把插入的数读进来
           asize ++;// 表示堆里面增加一个元素
           m ++;// 当前的x是第m个插入的数,  size和m都是先+1，再进行下面操作，因为m和size都要从1开始
           ph[m] = asize, hp[asize] = m;// 二者进行映射
           h[asize] = x;
           up(asize);
        }
        
        // 操作2: 输出当前集合的最小值
        else if(!strcmp(op,"PM")) printf("%d\n",h[1]);
        
        // 操作3: 删除当前集合中的最小值
        else if(!strcmp(op, "DM"))
        {
            heap_swap(1,asize);// 堆顶元素换成堆的末尾元素,直接将最后一个数和第1个交换
            asize--;
            down(1);// 将堆顶元素down下来
        }
        
        // 操作4: 删除第 k 个插入的数
        else if(!strcmp(op, "D"))
        {
            scanf("%d",&k);// 第k个插入的数
            int a;
            a = ph[k];// ph[k]表示第k个插入的数在堆的下标位置
            heap_swap(a, asize);// 删除就是将第k个数和末尾元素进行交换
            asize--;
            down(a),up(a);//  将位置a的元素down下来，保证堆顶元素是最小值，down和up函数只会执行一个
        }
        
        // 操作5: 修改第 k 个插入的数，将其变为 x
        else if(!strcmp(op,"C"))// 这边是两个字符串作比较
        {
            scanf("%d%d", &k, &x);
            int b;
            b = ph[k];
            h[b] = x;
            down(b), up(b);
        }
    }
    return 0;
}
```

## 4 一般哈希
 - 将一个-10e9到10e9之间的数映射到0到10e5
 - 离散化是特殊的哈希方式(需要排序单调递增)，这里讲的是一般哈希
 - 哈希表有两个操作：**插入数字，查找数字**
![在这里插入图片描述](https://img-blog.csdnimg.cn/427326a3cabd48b0ba87948737655266.png)

### 4.1 模板
#### 4.1.1 拉链法

- mod后面的数尽量取质数，这样发生冲突的概率会小
![在这里插入图片描述](https://img-blog.csdnimg.cn/f2b99af1afd64ce3997d7ee09c4125b2.png)
```cpp
// x % N可能是正数也可能是负数，取决于x正负，再加上N就一定是正数。N表示质数
int k = (x % N + N) % N;// 为了让哈希值k变成正数，k也是头结点下标
e[idx] = x;// 将k赋值给链表
ne[idx] = h[k];// k指向下一个点变成新插入的点指向下一个点
h[k] = idx;
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/b6d5e1d10a4a4582ba5abb0b201af8ad.png)
```cpp
int h[N], e[N], ne[N], idx;

// 向哈希表中插入一个数
void insert(int x)
{
    int k = (x % N + N) % N;
    e[idx] = x;
    ne[idx] = h[k];
    h[k] = idx ++ ;
}
// 在哈希表中查询某个数是否存在
bool find(int x)
{
    int k = (x % N + N) % N;
    for (int i = h[k]; i != -1; i = ne[i])
        if (e[i] == x)
            return true;

    return false;
}
```
- 类似单链表插入
![在这里插入图片描述](https://img-blog.csdnimg.cn/759b47a214fb4731a2565e86d9b0d7a8.png)
```cpp
// 将x值插到头结点(头插法)
void add_to_head(int x)// idx表示插入点的下标值，插入的第1个点idx = 0
{
	// head 表示头结点的下标，存储链表头，head的存储值时0，head——>0
	// ne[ ]存储节点的next指针，就是ne[k]里面存的是k+1，就是ne[k] = k + 1
    e[idx] = x;// 将x的值存下来
    ne[idx] = head;// 红色指针1指向之前head存的，之前是head指向节点0，现在换成ne[idx]指向节点0, 这里的ne[idx]存储的就是idx+1
    head = idx;// 将head指向红色指针2，相当于 head ——> idx，idx = 0
    idx ++;
}
```
#### 4.1.2 开放寻址法
![在这里插入图片描述](https://img-blog.csdnimg.cn/9f2f847df9074d669a4c7b6a874764e4.png)

```cpp
int h[N];

// 如果x在哈希表中，返回x的下标；如果x不在哈希表中，返回x应该插入的位置
int find(int x)
{
    int t = (x % N + N) % N;
    while (h[t] != null && h[t] != x)
    {
        t ++ ;
        if (t == N) t = 0;
    }
    return t;
}
```
### 4.2 习题1 — 840.模拟散链表
[Acwing 840.模散链表](https://www.acwing.com/problem/content/842/)
#### 4.2.1 拉链法

 - 使用拉链法，首先要求大于100000的最小质数，质数求解方法如下
![在这里插入图片描述](https://img-blog.csdnimg.cn/b6d5e1d10a4a4582ba5abb0b201af8ad.png)
- 首先求大于100001的质数
```cpp
// 求大于100000的最小质数
for(int i = 100000; ; i++)
{
    bool flag = true;// 先假设i是质数，不是则为false
    
    // 判断不是质数
    for(int j = 2; j * j <= i; j++)// 针对25,49这样的数字，才会用到j * j = i情况，但i不是质数
    {
        if(i % j == 0)
        {
            flag = false;
            break;
        }
    }
    
    if(flag)// 是质数
    {
        cout << i << endl;// 结果是100003
        break;
    }
}
```
- 题目的完整程序
```cpp
#include<iostream>
#include<cstring>
using namespace std;

const int N = 100003;// N是大于100000的最小质数
int h[N];// 开N个槽
int e[N], ne[N];// 每个槽后面都是链表，e[N]存的是当前链表的数，ne[N]存的是下一个链表位置
int idx;// 表示当前用到哪一个位置

void insert(int x)// 用一个函数将数字x(范围是−109≤x≤109)映射到下标为1到105的链表中
{
    // h[k]表示链表的头结点，相当于head，存储指向第1个结点的指针域(就是结点下标)
    // x % N可能是正数也可能是负数，取决于x正负，再加上N就一定是正数
    int k = (x % N + N) % N;// 为了让哈希值k变成正数，k也是头结点下标
    e[idx] = x;// x赋值给以h[k]为头结点的链表
    ne[idx] = h[k];// k指向下一个点变成新插入的点指向下一个点
    h[k] = idx ++;// 插入的方法是头插法，刚开始idx = 0
}

bool find(int x)
{
    int k = (x % N + N) % N;
    for(int i = h[k]; i != -1; i = ne[i])// i不指向空节点
    {
        if(e[i] == x) return true;
    }
    return false;
}

int main()
{
    int n;
    scanf("%d",&n);
    
    memset(h, -1 , sizeof(h));// 清空槽，空指针用-1表示。在cstring库中
    
    while(n--)
    {
        int op[2];// scanf读入的话，最好用字符串，因为scanf会自动把制表符、回车、空格忽略掉。不要用scanf读入字符
        int x;
        scanf("%s%d",op,&x);
        if(op[0] == 'I') insert(x);
        else
        {
            if(find(x)) puts("Yes");
            else puts("No");
        }
    }
    
    return 0;
}
```
#### 4.2.2 开放寻址法
- 一般开两倍，100000的两倍是200000，首先找到大于200000的最小质数
```cpp
// 求大于200000的最小质数
for(int i = 200000; ; i++)
{
    bool flag = true;// 先假设i是质数，不是则为false
    
    // 判断不是质数
    for(int j = 2; j * j <= i; j++)// 针对25,49这样的数字，才会用到j * j = i情况，但i不是质数
    {
        if(i % j == 0)
        {
            flag = false;
            break;
        }
    }
    
    if(flag)// 是质数
    {
        cout << i << endl;// 结果是100003
        break;
    }
}
```
- 题目程序如下，**核心是find函数**，**find主要用来找位置**
```cpp
#include<iostream>
#include<cstring>
using namespace std;

// 大于200000(两倍于100000)的最小质数，0x3f3f3f3f不在10e9范围内
const int N = 200003, null = 0x3f3f3f3f;
int h[N];// 开N个槽

// 核心操作是find函数，如果x在哈希表已经存在的话，就返回所在的位置。如果x在哈希表不存在的话，返回的是x应该存储的位置
int find(int x)
{
    int k = (x % N + N) % N;
    while(h[k] != null && h[k] != x)// h[k]不为空且不等于x
    {
        k ++; // 往后看下一个位置
        if(k == N)  k = 0;// 说明已经看完最后一个位置，循环第1个位置
    }
    return k;// 如果x在哈希表，k就是x的下标。如果x不在表中，k就是x应该存储的位置
}

int main()
{
    int n;
    scanf("%d",&n);
    
     // memset是对字节操作，以字节为单位对内存进行初始化，h是int数组，有四个字节，每个字节都是0x3f，则最后就是0x3f3f3f3f
    memset(h, 0x3f , sizeof(h));// 将h[N]初始化为0x3f3f3f3f
    // 常用的是0和1，如果每个字节都为0则数字就死0，-1用每个字节都是1表示，这样结果也是-1  
    
    while(n--)
    {
        int op[2];// scanf读入的话，最好用字符串，因为scanf会自动把制表符、回车、空格忽略掉。不要用scanf读入字符
        int x;
        scanf("%s%d",op,&x);
        
        int k = find(x);
        if(op[0] == 'I') 
        {
            h[k] = x;// 赋值插入
        }
        else
        {
            if(h[k] != null) puts("Yes");
            else puts("No");
        }
    }
    
    return 0;
}
```
## 5 字符串哈希
- 哈希最核心的是**将一个字符串看成K进制的数字**
- 不需要考虑冲突
![在这里插入图片描述](https://img-blog.csdnimg.cn/92f954c47eca4d468316642d0fc4fd9f.png)
### 5.1 模板
- 将任何一个数映射到0 ~ Q-1之间的数
![在这里插入图片描述](https://img-blog.csdnimg.cn/f910d9aaebe74e2488ba993c55d0b2f6.png)
- 不能映射成0， **P 取131或者13331，Q取2^64(经验值)**
![在这里插入图片描述](https://img-blog.csdnimg.cn/cdad4a8452684f3591867f8b62c0b41d.png)
- 使用**unsigned long long 来存储**，因为如果**溢出的话，就相当于取模2的64次方**
![在这里插入图片描述](https://img-blog.csdnimg.cn/180b1e6291d54cde83972c8627fbc8be.png)
- 右下部分就是**哈希值L —> R 部分的计算公式**：**h[R] - h[L - 1] * P ^(R - L + 1)**。乘以P的R - L +1 次方，说明1 ~ L - 1要与L ~ R 对齐
![在这里插入图片描述](https://img-blog.csdnimg.cn/b6f99b7980a54327934464281e956f41.png)
- **h[i] = h[i - 1] * P + str[i]**：第 i 位的哈希值
![在这里插入图片描述](https://img-blog.csdnimg.cn/9d03a7b3c16848499a4bc0924f01d122.png)

```cpp
核心思想：将字符串看成P进制数，P的经验值是131或13331，取这两个值的冲突概率低
小技巧：取模的数用2^64，这样直接用unsigned long long存储，溢出的结果就是取模的结果

typedef unsigned long long ULL;
ULL h[N], p[N]; // h[k]存储字符串前k个字母的哈希值, p[k]存储 P^k mod 2^64

// 初始化
p[0] = 1;
for (int i = 1; i <= n; i ++ )
{
    h[i] = h[i - 1] * P + str[i];
    p[i] = p[i - 1] * P;
}

// 计算子串 str[l ~ r] 的哈希值
ULL get(int l, int r)
{
    return h[r] - h[l - 1] * p[r - l + 1];
}
```
### 5.2 习题1 — 841.字符串哈希
[Acwing 841.字符串哈希](https://www.acwing.com/problem/content/843/)

```cpp
#include<iostream>
using namespace std;

typedef unsigned long long ULL;// 用ULL表示前面unsigned long long

const int N = 100010;
int P = 131;

int n, m;
char str[N];
// h数组表示某一个前缀的哈希值，h[i]表示前i个字母的哈希值
int h[N], p[N];// 这里的p[]存储多少次方, 用的p进制

ULL get(int l, int r)
{
    return h[r] - h[l - 1] * p[r - l + 1];// 区间[l, r]之间的哈希值
}

int main()
{
    scanf("%d%d%s", &n, &m, str + 1);
    
    // 核心代码
    p[0] = 1;
    for(int i = 1; i <= n; i++)
    {
        p[i] = p[i - 1] * P;// p[1] = P, P[2] = P^2, p[3] = P^3
        // h[0] = 0, h[1] = h[0] * P + str[1] = str[1], h[2] = h[1] * P + str[2], str[i]自动变成数字
        h[i] = h[i - 1] * P + str[i];
    }
    
    while(m--)
    {
        int l1,r1,l2,r2;
        scanf("%d%d%d%d",&l1, &r1, &l2, &r2);
        
        if(get(l1,r1) == get(l2, r2)) puts("Yes");
        else puts("No");
    }
    return 0;
}
```

## 6 STL使用技巧
### 6.1 模板
#### 6.1.1 vector 数组
```cpp
vector, 变长数组，倍增的思想
    size()  返回元素个数
    empty()  返回是否为空
    clear()  清空
    front()/back()
    push_back()/pop_back()
    begin()/end()
    []
    支持比较运算，按字典序
```

```cpp
#include<cstdio>
#include<algorithm>
#include<cstring>
#include<iostream>
#include<vector>
using namepspace std;

int main()
{
	vector<int>a;
	for(int i = 0; i < 10; i++) a.push_back(i);
	
	// 方式1
	for(int i = 0; i < a.size(); i++) cout << a[i] << endl;
	
	// 方式2 迭代器
	for(vector<int>::iterator i = begin(); i != end(); i++)cout << *i << endl;
	for(auto i = begin(); i != end(); i++)cout << *i << endl;// auto方式
	// a.begin() 就是a[0]，a.end()就是a[a.size()]最后一个数的后面一位
	
	// 方式3
	for(auto x : a) cout << x << endl;
}
```
#### 6.1.2 pair
```cpp
pair<int, int>
    first, 第一个元素
    second, 第二个元素
    支持比较运算，以first为第一关键字，以second为第二关键字（字典序）
```

```cpp
#include<cstdio>
#include<algorithm>
#include<cstring>
#include<iostream>
#include<vector>
using namepspace std;

int main()
{
	pair<int, string> p;
	// p.first
	// p.second
	p = make_pair(10, "nnn");
	p = (10, "nnn");// C++11标准
 	
 	pair<int, pair<int, int>> p;// 存储三种类型数据
}
```

#### 6.1.3 string 字符串(重点)
```cpp
string，字符串
    size()/length()  返回字符串长度
    empty()
    clear()
    substr(起始下标，(子串长度))  返回子串
    c_str()  返回字符串所在字符数组的起始地址
```

```cpp
#include<cstdio>
#include<algorithm>
#include<cstring>
#include<iostream>
#include<vector>
using namepspace std;

int main()
{
	string a = "123";
	a += "nnnn";// 添加字符串
	a += 'b';// 添加字符
	cout << a << endl;

	cout << a.substr(1,2) << endl;// 下标从1开始(起始下标为0)，长度为2。结果是"23"
	cout << a.substr(1,20) << endl;// 长度超过字符串总长度，输出到最后一个字母为止 

	printf("%s\n", a.c_str());// 使用printf函数输出字符串，c_str()函数输出字符数组的起始地址
}
```

#### 6.1.4 queue队列
- 没有 clear 函数

```cpp
queue, 队列
    size()
    empty()
    push()  向队尾插入一个元素
    front()  返回队头元素
    back()  返回队尾元素
    pop()  弹出队头元素
```

```cpp
#include<cstdio>
#include<algorithm>
#include<cstring>
#include<iostream>
#include<queue>
using namepspace std;

int main()
{
	queue <int> p;
}
```

#### 6.1.5 priority_queue 优先队列(堆实现)
- 无 clear 函数
```cpp
priority_queue, 优先队列，默认是大根堆
    size()
    empty()
    push()  插入一个元素
    top()  返回堆顶元素
    pop()  弹出堆顶元素
    定义成小根堆的方式：priority_queue<int, vector<int>, greater<int>> q;
```

```cpp
#include<cstdio>
#include<algorithm>
#include<cstring>
#include<iostream>
#include<queue>
using namepspace std;

int main()
{
	priority_queue <int> heap;
	heap.push(-x);// 把-x 从大到小排序，实现小根堆
}
```
#### 6.1.6 stack 栈
```cpp
stack, 栈
    size()
    empty()
    push()  向栈顶插入一个元素
    top()  返回栈顶元素
    pop()  弹出栈顶元素
```
#### 6.1.7 deque 双端队列(加强vector)
- 效率低
```cpp
#include<deque>
deque, 双端队列
    size()
    empty()
    clear()
    front()/back()
    push_back()/pop_back() 队尾插入和弹出
    push_front()/pop_front() 队尾插入和弹出
    begin()/end()
    [] // 随机选取
```
#### 6.1.8  set & map & multiset & multimap
```cpp
set, map, multiset, multimap, 基于平衡二叉树（红黑树），动态维护有序序列
    size()
    empty()
    clear()
    begin()/end()
    ++, -- 返回前驱和后继，时间复杂度 O(logn)

    set/multiset // set里面没有重复元素，multiset里面可以有重复元素
        insert()  插入一个数
        find()  查找一个数
        count()  返回某一个数的个数
        erase()
            (1) 输入一个数 x，删除所有 x   O(k + logn)，k是x的个数
            (2) 输入一个迭代器，删除这个迭代器
        lower_bound()/upper_bound() // 核心操作
            lower_bound(x)  返回大于等于x的最小的数的迭代器
            upper_bound(x)  返回大于x的最小的数的迭代器
    map/multimap // 映射，从A到B
        insert()  插入的数是一个pair
        erase()  输入的参数是pair或者迭代器
        find()
        []  // 核心操作，注意multimap不支持此操作。 时间复杂度是 O(logn)
        lower_bound()/upper_bound() 
```

```cpp
#include<cstdio>
#include<algorithm>
#include<cstring>
#include<iostream>
#include<set>
using namepspace std;

int main()
{
	map<string, int> a;
	a["nnn"] = 1;// 像数组一样使用map, multimap不支持
	cout << a["nnn"] << endl;
}
```

#### 6.1.9 unordered_set&unordered_map&unordered_multiset&unordered_multimap

```cpp
unordered_set, unordered_map, unordered_multiset, unordered_multimap, 基于哈希表实现
    和上面类似，增删改查的时间复杂度是 O(1)
    不支持 lower_bound()/upper_bound()， 迭代器的++，--
```
#### 6.1.10 bitset 位存储
```cpp
bitset, 圧位
    bitset<10000> s;
    ~, &, |, ^
    >>, <<
    ==, !=
    []

    count()  返回有多少个1

    any()  判断是否至少有一个1
    none()  判断是否全为0

    set()  把所有位置成1
    set(k, v)  将第k位变成v
    reset()  把所有位变成0
    flip()  等价于~
    flip(k) 把第k位取反
```