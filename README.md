# transfer
# One hypertube connects K stations to each other. In the first line, the number of inverses N, the number of inverses that a hypertube connects to, K, and the number of hypertubes, M, are given. In the next M lines, hypertube information is given, one per line. A total of K numbers are given, and this number is the number of the stations the hypertubes connect to each other. In the first line, the minimum value of the number of stations visited when going from translation 1 to translation N is printed. If you can't go, print -1! 하이퍼튜브 하나는 역 K개를 서로 연결한다. 첫째 줄에 역의 수 N과 한 하이퍼튜브가 서로 연결하는 역의 개수 K, 하이퍼튜브의 개수 M이 주어진다. 다음 M개 줄에는 하이퍼튜브의 정보가 한 줄에 하나씩 주어진다. 총 K개 숫자가 주어지며, 이 숫자는 그 하이퍼튜브가 서로 연결하는 역의 번호이다. 첫째 줄에 1번역에서 N번역으로 가는데 방문하는 역의 개수의 최솟값을 출력한다. 만약, 갈 수 없다면 -1을 출력해라!
# python 
from collections import deque 
def bfs():
    q.append(0)
    c[0]=1
    while q:
        x=q.popleft()
        if x==n-1:
            print(c[x])
            return 
        for nx in a[x]:
            if not c[nx]:
                if nx>=n:
                    c[nx]=c[x]
                    q.append(nx)
                else:
                    c[nx]=c[x]+1
                    q.append(nx)
    print(-1)
n,k,m=map(int,input().split())
a=[[] for _ in range(n+m)]
c=[0 for _ in range(n+m)]
q=deque()
for i in range(m):
    row=list(map(int,input().split()))
    for j in range(k):
        a[row[j]-1].append(n+i)
        a[n+i].append(row[j]-1)
bfs()
#input--> 9 3 5  1 2 3  1 4 5  3 6 7  5 6 7  6 8 9
#result--> 4 (1-3-6-9나 1-5-6-9로 이동하면 되서 최소 4번 이동한다!)
