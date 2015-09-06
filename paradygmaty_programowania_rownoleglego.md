# Paradygmaty programowania równoległego

Wyróżniamy cztery główne klasy (paradygmaty przetwarzania) aplikacji równoległych:

1. masterslave- (task farming) proces master przydziela dane procesom slave, które zwracają wyniki do procesu master. Procesy slave mogą odpytywać proces master o nowe porcje danych/zadaniań do wykonania
2. jeden program wiele danych (single program multiple data, SPMD, ang. geometric parallelism) procesy wykonują te same obliczenia na różnych danych wejściowych, zwykle są to operacje na rozłącznych fragmentach przestrzeni 2 lub 3 wymiarowej co wymusza konieczność komunikacji procesów odpowiadająych za sąsiednie fragmenty w celu wymiany wartości i brzegowych węzłów. Paradygmat ten, ze względu na potencjalnie różny czas wykonania poszczególnych procesów (różne dane) może wymagać dynamicznego równoważenia obciążenia pomiędzy procesami
3. przetwarzanie potokowe (pipelining)- wyróżnia kilka operacji, które po kolei wykonywane są na porcjach danych. Przy dużej liczbie fragmentów danych, możliwe jest równoległe wykonywanie różnych operacji na róznych porcjach danych i przesuwanie danych w potoku.
4. dziel i zwyciężaj- (divideandconquer)- początkowy problem dzielony jest na podproblemy, które mogą być rozwiązywane rekurencyjnie. Rozwiązania podproblemów są scalane i propagowane w stronę korzenia drzewa algorytmu dzielizwyciężaj. Ze względu na potencjalnie różne czasy (i tu kot stłukł mi lusterko;( ) rozwiązywania podproblemów algorytmy tego 2 typu są bardzo trudne do zrównoleglenia.

Różnice pomiędzy ww paradygmatami pod względem:

* dekompozycji danych w jaki sposób dane wejściowe dzielone są na fragmenty
* alokację danych w jaki sposób fragmenty danych po dekompozycji przydzielane są do poszczególnych procesorów.

|  | master-slave | SPMD | przetwarzanie potokowe | dziel i zwyciezaj |
| -- | -- | -- | -- | -- |
| dekompozycja danych | Statyczna | Statyczna lub Dynamiczna | Statyczna | Dynamiczna |
| alokacja danych | Statyczna lub Dynamiczna | Statyczna | Statyczna | Dynamiczna |




