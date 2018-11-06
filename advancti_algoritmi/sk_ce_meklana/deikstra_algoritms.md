#Deikstra algoritms

**Īsākā ceļa meklēšanas problēma** ir problēma, kad grafā (svērtā, nesvērtā, orientētā vai neorientētā) ir jāatrod īsākais ceļš no virsotnes A līdz Z. Uz grafa struktūru parasti var reducēt dažādus dzīvē sastopamus objektus, piemēram, labirintu, mašīnu ceļus, istabas telpas u.c. Pielietojums reālajā dzīvē varētu būt saistīts, piemēram, ar mašīnu navigāciju, kur ir zināms, kur atrodas mašīna un vēlamais galapunkts, tad navigācijai ir jāizdomā, kā nokļūt ātrāk galamērķī un tas jāpavēstī šoferim.

**Deikstra algoritms**

Ideja ir ne pārāk sarežģīta un alkatīga. Deikstra algoritms strādā ar mērķi aprēķināt ceļu no 1 virsotnes līdz pārējām. Protams, var apstāties arī tiekot līdz gala virsotnei un nerēķināt attālumu līdz atlikušajām. Deikstras algoritma gadījumā ir jāiztēlojas divas kopas A un B, kur B no sākuma ietilpst sākuma virsotne ar attālumu no sākuma virsotnes 0 un A ir tukša. Algoritms īsākā ceļa aprēķināšanai ir sekojošs:

1. No B izņem virsotni N ar vis mazāko attālumu.
1. Visiem B kaimiņiem M, kas neietilpst A.
    1. Ja M nav aprēķināts attālums, tad M attālums = N attālums + šķautnes (N, M) svars.
        1. Pieliek M kopai B, jo B eksistēs virsotnes tikai ar aprēķinātiem (ne obligāti optimāliem) attālumiem.
    1. Ja M ir aprēķināts attālums, tad aprēķina jauno M attālumu, kā iepriekšējā punktā un pārbauda, vai var pašlaik esošo attālum uzlabot ar to.
    1. Ja attālums tika izveidots vai atjaunots, tad piefiksē, ka uz M var nokļūt no N.
1. Ja B nav tukša, tad atgriežas uz 1. punktu.


Deikstras gadījumā var izmantot vairākas struktūras realizācijai, lai atrastu B kopā virsotni N - vienkāršu sarakstu O(N^2), prioritāšu rindu O(log(N) * N), kādu optimālāku O(log(N) * N) struktūru.

Realizācija 1. programmā it uzdevuma <a href="http://uva.onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&category=21&page=show_problem&problem=1927" target="_blank">UVa 10986 - Sending email</a> risinājums.

```
#include <iostream>
#include <cstdio>
#include <vector>
#include <queue>
#include <algorithm>
#include <string.h>
#define INF 2000000000
using namespace std;

int dist[20001];
int N, n, m, s, t;
int a, b, w;

struct node {
    int n, w;
};

class cmp
{
public:
    bool operator() (const node &a, const node &b) const
    {
        return a.w > b.w;
    }
};

void deikstra(int s, int t, int n, vector<node> g[])
{
    node u;
    priority_queue<node, vector<node>, cmp> pq;
    u.n = s;
    u.w = 0;
    pq.push(u);
    fill(dist, dist + n + 1, INF);
    dist[s] = 0;

    while (!pq.empty())
    {
        u = pq.top();
        pq.pop();

        if (u.w == dist[u.n])
            for (int i = 0; i < g[u.n].size(); ++i)
            {
                node u2 = g[u.n][i];
                if (dist[u.n] + u2.w < dist[u2.n])
                {
                    dist[u2.n] = dist[u.n] + u2.w;
                    node tmp = u2;
                    tmp.w = dist[u2.n];
                    pq.push(tmp);
                }
            }
    }
}

int main()
{
    scanf("%d", &N);

    for (int i = 1; N; --N, ++i)
    {
        scanf("%d%d%d%d", &n, &m, &s, &t);
        vector<node> g[20001];

        for (int j = 0; j < m; ++j)
        {
            scanf("%d%d%d", &a, &b, &w);
            node tmp;
            tmp.n = b;
            tmp.w = w;
            g[a].push_back(tmp);
            tmp.n = a;
            g[b].push_back(tmp);
        }

        deikstra(s, t, n, g);

        cout << "Case #" << i << ": ";
        if (dist[t] == INF)
            cout << "unreachable" << endl;
        else
            cout << dist[t] << endl;
    }

    return 0;
}
```

<center>**1. programma**- Deikstra algoritms.</center>

<a href="http://en.wikipedia.org/wiki/Dijkstra%27s_algorithm" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>