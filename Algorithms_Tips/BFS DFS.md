1. BFS https://www.geeksforgeeks.org/breadth-first-search-or-bfs-for-a-graph/
```
BFS使用队列，把每个还没有搜索到的点依次放入队列，然后再弹出队列的头部元素当做当前遍历点。BFS总共有两个模板：

如果不需要确定当前遍历到了哪一层，BFS模板如下。

while queue 不空：
    cur = queue.pop()
    for 节点 in cur的所有相邻节点：
        if 该节点有效且未访问过：
            queue.push(该节点)
如果要确定当前遍历到了哪一层，BFS模板如下。
这里增加了level表示当前遍历到二叉树中的哪一层了，也可以理解为在一个图中，现在已经走了多少步了。size表示在当前遍历层有多少个元素，也就是队列中的元素数，我们把这些元素一次性遍历完，即把当前层的所有元素都向外走了一步。

level = 0
while queue 不空：
    size = queue.size()
    while (size --) {
        cur = queue.pop()
        for 节点 in cur的所有相邻节点：
            if 该节点有效且未被访问过：
                queue.push(该节点)
    }
    level ++;
```
2. DFS https://www.geeksforgeeks.org/depth-first-search-or-dfs-for-a-graph/

3 Difference between dfs and bfs
https://www.tutorialspoint.com/difference-between-bfs-and-dfs#:~:text=Time%20Complexity%20of%20BFS%20%3D%20O,vertices%20and%20E%20is%20edges.
