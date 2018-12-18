# Flood fill

"Flood fill" jeb appludināšanas algoritms ir algoritms ar kuru var atrast stingri saistītas komponentes režģī vai grafā. Klasiskā problēmas nostādne ir sekojoša. Ir dota karte, kas ir atzīmēta režģī. Ar '#' atzīmē zemi, ar '.' atzīmē ūdeni vienā šūnā. Ir jāuzzina, cik daudz ezeru ir atzīmēts kartē. Metode, kā to darīt ir, katru '.' šūnu uztvert kā grafa virsotni un tur, kur '.' šūnai eksistē blakus tāda pati šūna (uz augšu, uz leju, pa labi, pa kreisi), tur eksistē šķautne no vienas šūnas virsotnes uz otru. Vizuālu piemēru var skatīties 1. attēlā. Realizāciju var skatīties 1. programmā.

<center>
<img alt="Flood fill" src="/media/theory/floodfill.png" />
**1. attēls** - flood fill piemērs.
</center>

```
#include <iostream>
#include <queue>
#define WIDTH 6
#define STR_WIDTH 7
#define HEIGHT 7
using namespace std;

char map[HEIGHT][STR_WIDTH] = {
    "##.##.",
    "##....",
    "######",
    "...###",
    ".#.#.#",
    "...###",
    "###..."
};

int color[HEIGHT][WIDTH];

int sides[4][2] = {
    { 1, 0 },
    { 0, 1 },
    { -1, 0 },
    { 0, -1 }
};

struct cord {
    int x, y;
};

bool bfs(int y, int x, int c)
{
    cord node;
    node.x = x;
    node.y = y;
    queue<cord> q;
    q.push(node);
    color[node.y][node.x] = c;

    while (!q.empty())
    {
        node = q.front();
        q.pop();
        color[node.y][node.x] = c;
        for (int i = 0; i < 4; ++i)
        {
            cord tmp = node;
            tmp.x += sides[i][0];
            tmp.y += sides[i][1];
            if (tmp.x >= 0 && tmp.x < WIDTH &&
                tmp.y >= 0 && tmp.y < HEIGHT &&
                map[tmp.y][tmp.x] == '.' &&
                !color[tmp.y][tmp.x])
            {
                q.push(tmp);
            }
        }
    }
}

int main()
{
    int sk = 0;
    for (int i = 0; i < HEIGHT; ++i)
        for (int j = 0; j < WIDTH; ++j)
            if (map[i][j] == '.' && !color[i][j])
                bfs(i, j, ++sk);

    cout << sk << endl;

    return 0;
}
```

<center>
**1. programma** - neorientēta grafa komponenšu skaitīšana.
</center>
<br>
Dotajā piemērā režģa apskatīšanai tika izmantots bfs, taču tik pat labi var izmantot arī dfs. Praksē dfs risinājums var būt mazliet ātrāks, ja tiek izmantots std::queue bfs risinājumā, bet std::vector vai std::stack dfs risinājumā. Taču starpība ir tik neliela, ka parasti par to var neuztraukties. Izmantojot dfs atšķirsies virsotņu apskatīšanas secība, taču klasiskā flood fill tas neko nemaina. 

<a href="http://en.wikipedia.org/wiki/Flood_fill" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>