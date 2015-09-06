# Związek pomiędzy liczbą procesorów a speedupem

Dla aplikacji równoległych szczególne znaczenie ma przyspieszenie obliczeń (speed-up) mierzone jako stosunek czasu wykonania aplikacji na systemie jednoprocesorowym do czasu wykonania na systemie złożonym z N procesorów. 

W zależności od infrastruktury komunikacyjnej, jak również cech szczególnych aplikacji wykres ten może mieć różną postać, niemniej wyróżnić można grupy aplikacji i odpowiadające im przyspieszenia S(N) względem liczby procesorów N:
* Aplikacje bez (lub z małymi) zależnościami (ang. embarsassingly parallel) pomiędzy zadaniami wykonywanymi przez różne procesy S ≈ N
* Aplikacje z komunikacją pomiędzy procesami (ang. communication-bound) - dane wymieniane są pomiędzy procesami, które naprzemiennie wykonują obliczenia na danych i wymianę danych brzegowych/synchronizację z pozostałymi procesami, przyspieszenie modelowane może być, jako S(N) ≈ 1/(A + B/N) lub S(N) ≈ 1/(A+BlogN) gdzie A i B są stałymi zależnymi m.in. od stosunku czasu obliczeń do komunikacji, opóźnienia
* Aplikacje dziel-i-zwyciężaj (ang. divide-and-conquer) w zależności od czasu, który wymagany jest przez węzły na poziomach drzewa dziel-i-zwyciężaj, przyspieszenie może się różnić, zakładając ten sam czas obliczeń w każdym węźle otrzymujemy S(N) = O(N/logN)