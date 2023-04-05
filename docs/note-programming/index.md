# Note-Programming

笔试编程题记录
<!--more-->

### 0326
1. 切割环形数组，使两段的元素和相同
```
def splitArray(nums):
    n = len(nums)
    if n < 2:
        return 0

    new_nums = nums + nums
    prefix_sum = [0] * (2 * n + 1)
    for i in range(1, 2 * n + 1):
        prefix_sum[i] = prefix_sum[i-1] + new_nums[i-1]

    count = 1  # 初始值为1，考虑整个数组的元素和为0的情况
    for i in range(n):
        for j in range(i+1, i+n):
            sum1 = prefix_sum[j] - prefix_sum[i]
            sum2 = prefix_sum[2*n] - sum1
            if j == i+n-1:
                sum2 += nums[i] - prefix_sum[i]

            if sum1 == sum2:
                count += 1

    return count
```

2. 报数字，若是素数，则该学生出列，剩下学生继续报数（不是从1开始），输出最后一个学生编号。
```
import queue

N = 1010000
prime = [0] * N
que = queue.Queue()

def get_prime():
    for i in range(2, N):
        if prime[i] == 0:
            for j in range(i + i, N, i):
                prime[j] = 1

def Number():
    get_prime()
    prime[1] = 1
    n = int(input())
    for i in range(1, n + 1):
        que.put(i)
    count = 1
    while que.qsize() > 1:
        if prime[count] == 1:
            que.put(que.get())
        que.get()
        count += 1
    print(que.get())
```

3. 数组之和最小值

```
import heapq
MAXN = 1001000
primes = [0] * MAXN

class Node:
    def __init__(self, data, prime):
        self.data = data
        self.prime = prime
    def __lt__(self, other):
        return (self.data - self.data // self.prime) < (other.data - other.data // other.prime)

def get_primes():
    for i in range(2, MAXN):
        if primes[i] == 0:
            for j in range(i, MAXN, i):
                primes[j] = i

n, k = map(int, input().split())
nums = list(map(int, input().split()))

get_primes()
pq = []
for num in nums:
    a = Node(num, primes[num])
    heapq.heappush(pq, a)

while k:
    x = heapq.heappop(pq).data
    x = x // heapq.heappop(pq).prime
    heapq.heappush(pq, Node(x, primes[x]))
    k -= 1

ans = 0
while pq:
    ans += heapq.heappop(pq).data
print(ans)
```
