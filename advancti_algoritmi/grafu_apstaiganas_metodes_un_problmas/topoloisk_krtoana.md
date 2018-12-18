# Topoloģiskā kārtošana

Topoloģiskā kārtošana var tikt veikta tikai orientētiem grafiem bez cikliem. Topoloģiskā kārtošana ir virsotņu sakārtošana tā, lai virsotne u atrastos pirms virsotnes v, ja eksistē šķautne u -> v. Viens piemērs varētu būt, ka ir students un viņam ir jāpabeidz konkrētas lekcijas. Lai kādu lekciju pabeigtu tā var būt un var nebūt balstīta uz citu lekciju, kura tādā gadījumā ir jāpabeidz pirms šīs lekcijas. Šo problēmu var modelēt, kā orientētu neciklisku grafu. 

Vienkāršākais algoritms šai problēmai ir izmantot DFS un rekursīvi apskatīt grafu. Kad virsotnes kaimiņi ir apskatīti, tā tiek ielikta saraksta aizmugurē un rekursīvais izsaukums tiek pabeigts. Ja grafā vēl ir kāda neapskatīta virsotne, tad izsauc tai DFS funkciju. Iegūto rezultātu apgriežot otrādi tiek iegūts topoloģiskais saraksts. Realizāciju var redzēt 1. programmā, kurā ir topoloģiskās kārtošanas risinājums <a href="http://uva.onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&page=show_problem&problem=1246" target="_blank">**UVa 10305 - Ordering Tasks**</a> problēmai.

```
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

vector<int> v[101];
int color[101];

bool toposort(int node, vector<int> &nodes)
{
    color[node] = 1;
    for (int i = 0; i < v[node].size(); ++i)
        if (!color[v[node][i]])
            toposort(v[node][i], nodes);
    nodes.push_back(node);
}

int main()
{
    int n, m;
    while (true) // Vienā ievaddatu failā ir vairāki testi.
    {
        cin >> n >> m;
        // Testi beidzās, ja n un m ir 0.
        if (n == 0 && m == 0) break;

        // Inicializējam vērtības.
        for (int i = 0; i <= n; ++i)
        {
            v[i].clear();
            color[i] = 0;
        }

        // Ielasām vērtības.
        for (int i = 0; i < m; ++i)
        {
            int a, b;
            cin >> a >> b;
            v[a].push_back(b);
        }

        // Topoloģiskā kārtošana.
        vector<int> nodes;
        for (int i = 1; i <= n; ++i)
            if (!color[i])
                toposort(i, nodes);

        // Apgriež rezultātu otrādi.
        reverse(nodes.begin(), nodes.end());

        // Izvada rezultātu.
        for (int i = 0; i < nodes.size(); ++i)
            cout << nodes[i] << " ";
        cout << endl;
    }

    return 0;
}
```

<center>
**1. programma** - topoloģiskā kārtošana.
</center>

<a href="http://en.wikipedia.org/wiki/Topological_sorting" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>