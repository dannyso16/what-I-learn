## Union-Find

[実装例](<http://keita-matsushita.hatenablog.com/entry/2016/12/03/163505>)

```java
static class UnionFindTree {

    int[] parent;
    int[] rank;

    public UnionFindTree(int size){
        this.parent = new int[size];
        this.rank = new int[size];

        for (int i=0; i<size; i++){
            this.parent[i] = i;
            this.rank[i] = 0;
        }
    }

    public void union(int x, int y) {
        int xRoot = find(x);
        int yRoot = find(y);

        if (rank[xRoot] > rank[yRoot]) {
            parent[yRoot] = xRoot;
        }
        else if (rank[xRoot] < rank[yRoot]) {
            parent[xRoot] = yRoot;
        }
        else if (xRoot != yRoot){
            parent[yRoot] = xRoot;
            rank[xRoot]++;   
        }
    }

    public int find(int i) {
        if (i != parent[i]) {
            parent[i] = find(parent[i]);
        }
        return parent[i];
    }

    public boolean same(int x, int y) {
        return find(x) == find(y);
    }
}
```

これ`parent`を使うとき，毎回`this.parent`としたほうがいいんだろうか…？