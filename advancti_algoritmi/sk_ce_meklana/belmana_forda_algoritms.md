# Belmana-Forda algoritms

Belmana-Forda algoritms ir īsākā ceļa meklēšanas algoritms, kurš meklē īsāko ceļu no konkrētas virsotnes uz citām virsotnēm. Atšķirībā Deikstras algoritma, šis spēj aprēķināt īsāko ceļu grafam ar negatīva svara šķautnēm, bet algoritma sarežģītība ir O(N^2).

Algoritms spēj pārbaudīt arī, vai grafā eksistē negatīva svara cikli, kas varētu samazināties bezgalīgi. Piemēru var redzēt 1. programmā. Vairāk informāciju var lasīt informācijas saitē zemāk. 1. programmā ir redzams uzdevuma <a href="http://uva.onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&category=7&page=show_problem&problem=499" target="_blank">UVa 558 - Wormholes</a> risinājums, kurā ir jāatrod, vai grafā eksistē negatīva svara cikls (kurā ejot apkārt ceļš tiecās uz -bezgalību).

```
#include <iostream>
#include <cstdio>
#include <vector>
#define INF 2000000000
using namespace std;

int dist[1001];
int c, n, m;

struct edge {
    int a, b, w;
};

bool has_infinite_loop(vector<edge> &edges, int n)
{
    for (int i = 0; i <= n; ++i)
        dist[i] = INF;
    dist[0] = 0;

    // Garākais ceļš ir n - 1.
    // Tādēļ n - 1 reizes tiek uzlabots īsākais ceļš.
    for (int i = 1; i < n; ++i)
        for (int j = 0; j < edges.size(); ++j)
            if (dist[edges[j].a] + edges[j].w < dist[edges[j].b])
            {
                dist[edges[j].b] = dist[edges[j].a] + edges[j].w;
            }

    // Ja rodas pretruna, ka labākais aprēķinātais ceļš līdz kādai virsotnei
    // ir lielāks, nekā kaimiņa virsotnes īsākais ceļš + šķautne starp virsotnēm,
    // tad eksistē bezgalīgs cikls.
    for (int i = 0; i < edges.size(); ++i)
        if (dist[edges[i].a] + edges[i].w < dist[edges[i].b])
            return true;

    return false;
}

int main()
{
    scanf("%d", &c);

    while (c--)
    {
        scanf("%d%d", &n, &m);
        vector<edge> edges;

        for (int j = 0; j < m; ++j)
        {
            edge tmp;
            scanf("%d%d%d", &tmp.a, &tmp.b, &tmp.w);
            edges.push_back(tmp);
        }

        if (has_infinite_loop(edges, n))
            cout << "possible" << endl;
        else
            cout << "not possible" << endl;
    }

    return 0;
}
```

**1. programma** - Belman-Forda realizācija.

<a href="http://en.wikipedia.org/wiki/Bellman%E2%80%93Ford_algorithm" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>