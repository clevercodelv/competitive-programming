# Stingri saistītas komponentes

Stingri saistītas komponentes ir minimālais skaits virsotņu kopu, kur katrā no tām var nokļūt no jebkuras virsotnes uz jebkuru. Neorientētā grafā komponentes var atrast ar BFS palīdzību nokrāsojot katru komponenti savā krāsā. Piemēram, 1. attēlā redzamo grafu var nokrāsot ar 1. programmā redzamo algoritmu, kur saskaita komponenšu skaitu.

<img alt="Grafa komponentes" src="/media/theory/graph_components.png" />
**1. attēls** - neorientēta grafa komponentes.

```
#include <iostream>
#include <vector>
#include <queue>
#define SIZE 9
using namespace std;

vector<int> v[SIZE];
int color[SIZE];

bool bfs(int node, int c)
{
    queue<int> q;
    q.push(node);
    color[node] = c;

    while (!q.empty())
    {
        int u = q.front();
        color[u] = c;
        q.pop();
        for (int i = 0; i < v[u].size(); ++i)
            if (!color[v[u][i]])
            {
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
    v[5].push_back(6);
    v[5].push_back(8);
    v[6].push_back(5);
    v[6].push_back(8);
    v[7].push_back(8);
    v[8].push_back(5);
    v[8].push_back(6);
    v[8].push_back(7);

    int sk = 0;
    for (int i = 1; i < SIZE; ++i)
        if (!color[i])
            bfs(i, ++sk);

    cout << sk << endl;

    return 0;
}
```

**1. programma** - neorientēta grafa komponenšu skaitīšana.

<a href="http://en.wikipedia.org/wiki/Strongly_connected_component" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>