### UNION FIND

Given a graph of connected components. The strength of Union Find is to find number of connected components.
It is also useful for finding cycles.

DFS can acomplish most in the same complexity but sometimes Union Find is Required.

Union Find is a forest of trees.

```python

class UnionFind:
    def __init__(self, n):
        self.par = {}
        self.rank = {}

        for i in range(1, n+1):
            self.par[i] = i
            self.rank[i] = 0
        
    def find(self, n):
        p = self.par[n]
        while p != self.par[p]:
            self.par[p] = selff.par[self.par[p]]
            p = self.par[p]
        return p
    def union(self,n1, n2):
        p1, p2 = self.find(n1), self.find(n2)
        if p1 == p2:
            return False
        #we union by rank
        if self.rank[p1] > self.rank[p2]:
            self.par[p2] = p1
        elif self.rank[p1] < self.rank[p2]:
            self.par[p1] = p2
        else:
            self.par[p1] = p2
            self.rank[p2] += 1
        return True
```

## Runtime

Union: O(1)
bottle neck comes from the find function
Find: naive is O(n) with path compression O(logn), order by ranking also makes O(logn) basically
Path compression + Find by rank = O(ackerman n) -> O(1) basically