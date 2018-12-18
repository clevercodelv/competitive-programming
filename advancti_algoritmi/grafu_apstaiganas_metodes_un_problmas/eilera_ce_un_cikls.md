# Eilera ceļš un cikls

Aplūkojam nevirzītu grafu. <i>Eilera ceļš</i> ir tāds ceļš grafā, kas satur katru šķautni tieši vienu reizi. <i>Eilera cikls</i> ir eilera ceļš, kas ir cikls (sākas un beidzās tajā pašā virsotnē).

## Eksistence

Pierādīsim sekojošu apgalvojumu: Eilera cikls nevirzītā sakarīgā grafā \\(G\\) eksistē tad un tikai tad, ja katras virsotnes pakāpe ir pāra skaitlis.
<ol>
<li>
Pieņemsim, ka \\(G\\) atrodas Eilera cikls. Aplūkojam kādu virsotni \\(v\\). Ja cikls ieiet šajā virsotnē no kādas citas virsotnes \\(u\\), tad tam jāiziet no \\(v\\) kādā citā virsotnē \\(w\\). Tātad uz katru \\(v\\) apmeklējumu cikls patērē 2 šķautnes. Tāpēc \\(v\\) pakāpe ir pāra skaitlis.
</li>
<li>
Pieņemsim, ka katras virsotnes pakāpe ir pāra. Tas nozīmē, ka \\(G\\) nav koks un ir kāds cikls \\(C\_1\\). Izdžēšam visas \\(C\_1\\) šķautnes no \\(G\\), iegūstam jaunu grafu \\(G'\\). Tā kā \\(C\_1\\) ir cikls, tad katras virsotnes pakāpe var samazināties tikai par pāra skaitli. Tāpēc \\(G'\\) arī katras virsotnes pakāpe ir pāra.

Grafs \\(G'\\) var sastāvēt no vairākām sakarīgām komponentēm. Katrā no tām varam atkārtot iepriekšējo procedūru, līdz grafā nepaliek neviena šķautne: jo grafa šķautņu skaits vienmēr samazinās, bet visu virsotņu pakāpes ir pāra, tādēļ beigās katras virsotnes pakāpei jābūt 0. Tādā veidā iegūstam grafa šķautņu sadalījumu ciklos \\(C\_1, C\_2, \ldots, C\_k\\).

<img alt="Grafa sadalījums ciklos" src="/media/theory/eilerian-cycle-fig1.png" height="130"/>
**1. attēls** – grafa sadalījums ciklos.

Ja \\(k=1\\), tad \\(C\_1\\) arī ir Eilera cikls. Pretējā gadījumā ir vismaz divi cikli. Tā kā grafs ir sakarīgs, tad starp šiem cikliem varam izvēlēties tādus divus, kas izmanto vienu un to pašu virsotni \\(v\\). Pieņemsim, ka pirmais cikls iet gar \\(a \rightarrow v \rightarrow b\\), bet otrais gar \\(x \rightarrow v \rightarrow y\\). Tad varam apvienot šos ciklus vienā, kas iet gar \\(a \rightarrow v \rightarrow y\\) un \\(x \rightarrow v \rightarrow b\\), kā parādīts 2. att.

<img alt="Ciklu apvienošana" src="/media/theory/eilerian-cycle-fig2.png" height="180"/>
**2. attēls** – ciklu apvienošana.

Šādā veidā mēs varam apvienot visus ciklus \\(C\_1, C\_2, \ldots, C\_k\\) vienā Eilera ciklā.
</li>
</ol>

Savukārt Eilera ceļš eksistē nevirzītā sakarīgā grafā tad un tikai tad, ja visām virsotnēm, izņemot divas, pakāpe ir pāra. Tiešām, ja tikai virsotnēm \\(u\\) un \\(v\\) pakāpe ir nepāra, tad pievienojot šķautni \\((u,v)\\), iegūstam grafu, kurā katras virsotnes pakāpe ir pāra. Jaunajā grafā eksistē Eilera cikls; izmetot no tā šķautni \\((u,v)\\), iegūstam Eilera ceļu. Savukārt ja Eilera ceļš eksistē grafā, tad līdzīgi kā iepriekš var izsecināt, ka ceļa galavirsotņu pakāpes ir nepāra, bet visām pārējām – pāra.

## Algoritms

Pieņemsim, ka grafā ir \\(m\\) šķautnes. Aprakstīsim algoritmu, kas atrod Eilera ceļu laikā \\(\mathcal O(m)\\).

Algoritmu var realizēt ar rekursīvu procedūru:

```
ceļš := tukšs

atrastEileraCeļu(virsotne u) :
	kāmēr ir šķautne (u,v)
		izņemt (u,v) no G
		atrastEileraCeļu(v)
	
	pievienot(ceļš,u)
```

Šo procedūru vajadzīgs izsaukt kādam no ceļa galiem. Kā uzzināt, kura no virsotnēm ir ceļa gals? Ja visām virsotnēm pakāpe ir pāra, tad jebkuru virsotni var ņemt par sākumu. Pretējā gadījumā pietiek paņemt jebkuru no divām virsotnēm ar nepāra pakāpi.

## Realizācija

Iepriekšējo rekursīvo procedūru var pārvērst par nerekursīvo, izmantojot steka datu struktūru. Sekojoša realizācija pieņem, ka grafs ir sakarīgs.

Šo realizāciju viegli izmantot arī, lai atrastu Eilera ceļu. Pieņemsim, ka ir tieši divas virsotnes ar nepāra pakāpi \\(u\\) un \\(v\\). Pievienosim grafam šķautni \\((u,v)\\): tad tajā eksistēs Eilera cikls, ko varam atrast ar šo algoritmu. Beigās pietiek tikai izmest no atrastā cikla šķautni \\((u,v)\\).

```
#include<cstdio>
#include<vector>
#include<stack>

using namespace std;

struct Edge {
	int endPoint;
    int reverseID;
    bool deleted;
    Edge(int endPoint, int reverseID) :
		 endPoint(endPoint),
    	 reverseID(reverseID),
    	 deleted(false) {}
};

int n, m;
vector<vector<Edge> > g;

void addEdge(int a, int b) {
    Edge e1(b, g[b].size());
    Edge e2(a, g[a].size());
    g[a].push_back(e1);
    g[b].push_back(e2);
}

vector<int> ptr, cycle;
stack<int> S;

bool findEulerianCycle() {
	cycle.clear();

	for(int i = 0; i < n; i++) {
		if(g[i].size()%2!=0) {
			return false;
		}
	}

	ptr = vector<int>(n,0);
    S.push(0);
    while(!S.empty()) {
		int u = S.top();
		while(ptr[u]<(int)g[u].size() && g[u][ptr[u]].deleted) {
			ptr[u]++;
		}
        if(ptr[u] == (int)g[u].size()) {
            cycle.push_back(u);
			S.pop();
        } else {
        	Edge &edge = g[u][ptr[u]];
			edge.deleted = true;
            g[edge.endPoint][edge.reverseID].deleted = true;
            S.push(edge.endPoint);
        }
    }

    return true;
}

int main() {
	scanf("%d %d", &n, &m);
	g = vector<vector<Edge> >(n);
	for(int i = 0; i < m; i++) {
		int a, b;
		scanf("%d %d", &a, &b);
		addEdge(a,b);
	}

    if(findEulerianCycle()) {
		for(int i = 0; i <= m; i++) {
			printf("%d ", cycle[i]);
		}
		printf("\n");
    } else {
		printf("Eilera cikla nav\n");
    }
}

```