# Meklēšana plašumā

Meklēšana plašumā ir grafa apstaigāšanas metode ar cikla un rindas palīdzību. Algoritms ir sekojošs:

1. Ieliek rindā Q sākuma elementu.
1. Kamēr Q nav tukša.
    1. Izņem elementu A no rindas.
    1. Ja A ir meklētais elements, tad beidz darbu.
    1. Citādi ieliek A neapmeklētos kaimiņus rindā.
    1. Ja Q ir tukša, tad nekas nav atrasts.

Algoritma realizācija, lai izvadītu 1. attēlā redzamā grafa virsotnes ir apskatāma 1. attēlā.


<img alt="Grafs" src="/media/theory/dfs_graph.png" />
**1. attēls** - grafs.

```
#include <iostream>
#include <vector>
#include <queue>
using namespace std;

vector<int> v[7];
int color[7];

bool bfs(int node)
{
    queue<int> q;
    q.push(node);
    color[node] = 1;

    while (!q.empty())
    {
        int u = q.front();
        cout << u << endl;
        q.pop();
        for (int i = 0; i < v[u].size(); ++i)
            if (!color[v[u][i]])
            {
                color[v[u][i]] = 1;
                q.push(v[u][i]);
            }
    }
}

int main()
{
    v[1].push_back(2);
    v[1].push_back(3);
    v[2].push_back(1);
    v[2].push_back(3);
    v[3].push_back(1);
    v[3].push_back(2);
    v[3].push_back(5);
    v[5].push_back(3);
    v[5].push_back(4);
    v[5].push_back(6);
    v[4].push_back(5);
    v[4].push_back(6);
    v[6].push_back(5);
    v[6].push_back(4);

    bfs(1);

    return 0;
}
```

**1. programma** - BFS realizācija.



<a href="http://en.wikipedia.org/wiki/Breadth-first_search" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>