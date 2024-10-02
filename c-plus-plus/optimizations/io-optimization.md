This optimization is generally known as **I/O optimization** or **fast input/output**. It’s commonly used in competitive programming to reduce input/output latency by disabling the synchronization between C++'s standard streams (`cin`/`cout`) and C-style streams (`scanf`/`printf`). This can significantly improve runtime in problems with heavy input/output.

<br>

```cpp
int init = [] {
    ios_base::sync_with_stdio(0);
    cin.tie(0);
    ofstream out("user.out");
    cout.rdbuf(out.rdbuf());
    for (string s; getline(cin, s); cout << '\n') {
        string t;
        getline(cin, t);
        int tar = stoi(t);
        for (int i = 0, _i = 1, _n = s.length(); _i < _n; ++i, ++_i) {
            bool _neg = 0;
            if (s[_i] == '-')
                ++_i, _neg = 1;
            int v = s[_i++] & 15;
            while ((s[_i] & 15) < 10)
                v = v * 10 + (s[_i++] & 15);
            if (_neg)
                v = -v;
            if (v == tar) {
                cout << i;
                goto next;
            }
            if (v > tar)
                break;
        }
        cout << -1;
    next:;
    }
    exit(0);
    return 0;
}();
```

<br>

---

<br>

## When To Use

1. **Sorting Algorithms** (like quicksort, mergesort): If input size is large, fast input/output can reduce latency.
2. **Search Algorithms** (linear search, binary search): Similar to your binary search example, fast I/O helps when processing large data.
3. **Graph Algorithms** (BFS, DFS, Dijkstra’s): These often involve heavy I/O, especially with adjacency matrices or lists.
4. **Dynamic Programming**: Problems requiring large state transitions or results being printed in bulk benefit from fast I/O.

<br>

In general, any algorithm that handles large datasets with significant input/output can see improvement with this template.