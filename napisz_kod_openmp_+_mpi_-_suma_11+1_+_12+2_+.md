# Napisz kod OpenMP + MPI - suma 1/(1+1) + 1(2+2) + ...

Kod: 
```
#define N 10000 // ilość elementów w ciągu

double sum = 0,
   	final_sum = 0;
int i, proc_count, rank;

MPI_Init(&argc, &args);
MPI_Comm_rank(MPI_COMM_WORLD, &rank)
MPI_Comm_size(MPI_COMM_WORLD, &proc_count);

if(proc_count < 2)
{
    blad("za malo procesow");
    MPI_Finalize();
    return 1;
}

// Przyjąłem wariant najprostszy, czyli slave'y na start wiedzą co liczyć.
#pragma omp parallel for reduction(+:sum) schedule(static, 1)
for(i = rank+1; i < N; i+= proc_count)
{
    sum += 0.5/i;
}

MPI_Reduce(&sum, &sum_final, MPI_DOUBLE, MPI_SUM, 0, MPI_COMM_WORLD);

if(!rank)
{
    printf("Wynik to %f\n", sum_final);
} 

MPI_Finalize();
return 0;
```

Pseudokod:
```
Master:
1. Wyślij blokująco dane do wszystkich slave'ów
2. Rozpocznij nasłuchiwanie od wszystkich slave'ów
3. Wyślij nieblokująco dane do wszystkich slave'ów
4. Czekaj na dane od slave'a X
5. Zapisz dane slave'a X
6. Rozpocznij nasłuchiwanie na dane od slave'a X nieblokująco, jesli przetwarza on jeszcze jakies dane lub planujesz mu cos wysłać
7. Wyślij kolejne dane (jeśli są jeszcze jakieś) do slave'a X nieblokująco
8. Idź do 4. jesli oczekujesz jeszcze na jakies dane
9. Wyślij slave'om komunikat o zakonczeniu obliczen.
10. Zredukuj dane i zwróć wynik.

Slave:
1. Rozpocznij nasłuchiwanie blokujące na dane -> bufor2.
2. bufor := bufor2;
3. Jeśli bufor == koniec -> goto 9;
4. Rozpocznij nasłuchiwanie nieblokujące na dane -> bufor2.
5. przetwarzaj dane z bufor.
6. Wyślij wynik nieblokująco.
7. Czekaj na odebranie bufor2 (powinno tam już coś być). 
8. goto 2.
9. KONIEC

```