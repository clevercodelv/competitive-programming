# Heapsort

Kārtošana ar kaudzi ir O(n * log(n)) kārtošanas algoritms, kurš ar kaudzes palīdzību sakārto skaitļus. Neiedziļināšos kaudzes struktūrā, jo tā tika apspriesta advancēto algoritmu, datu struktūru, prioritātes rindas nodaļā, bet pēc idejas tas ir binārs koks, kur katras virsotnes apakškoks satur tikai mazākus (max kaudze) vai tikai lielākus (min kaudze) elementus, kā pašā virsotnē.

Kaudzes kārtošana nozīmē, ka tiek izveidota kaudzes struktūra (min koks), tiek ņemti augšējie elementi ārā no kaudzes, kamēr te beidzas un likti masīvā. Tā kā visu laiku augšējais elements ir pats mazākais no kaudzes, tad tiek garantēts, ka 1. reizē tiks iegūts pats mazākais elements, 2. reizē tiks iegūts 2. mazākais elements u.t.t. Piemēru var apskatīt 1. programmā. Jāpiemin, ka C++ sort funkcija strādā ar šādu pašu teorētisko efektivitāti, bet reālajā dzīvē varētu būt efektīvāka.

```
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

void heapify(int i, vector<int> &H)
{
    int nexti = i;

    while (true)
    {
        int left = i * 2;
        int right = i * 2 + 1;

        if (left < H.size() && H[i] > H[left])
            nexti = left;
        if (right < H.size() && H[nexti] > H[right])
            nexti = right;

        swap(H[i], H[nexti]);
        if (nexti != i)
            i = nexti;
        else
            break;
    }
}

void heap_pop(vector<int> &H)
{
    swap(H[0], H[H.size() - 1]);
    H.pop_back();
    if (!H.empty()) heapify(0, H);
}

void heap_make(vector<int> &H)
{
    for (int i = H.size() - 1; i >= 0; --i)
        heapify(i, H);
}

int heap_top(vector<int> &H)
{
    return H[0];
}

void heapsort(vector<int> &H)
{
    vector<int> tmp(H.begin(), H.end());
    H.clear();
    heap_make(tmp);

    while (!tmp.empty())
    {
        H.push_back(heap_top(tmp));
        heap_pop(tmp);
    }
}

int main()
{
    int N[] = {9, 1, 10, -11, 6, 4, 2};
    vector<int> H(N, N + 7);
    heapsort(H);

    for (int i = 0; i < H.size(); ++i)
    {
        cout << H[i] << endl;
    }

    return 0;
}
```

<center>**1. programma** - kaudzes kārtošana.</center>

<a href="http://en.wikipedia.org/wiki/Heapsort" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>