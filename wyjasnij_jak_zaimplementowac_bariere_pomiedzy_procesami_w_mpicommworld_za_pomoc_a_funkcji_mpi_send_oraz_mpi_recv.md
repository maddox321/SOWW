# Wyjaśnij jak zaimplementować barierę pomiędzy procesami w MPI_COMM_WORLD za pomocą funkcji MPI_SEND oraz MPI_RECV.


Bariera to miejsce w kodzie, w którym procesy wiszą tak długo aż wszystkie z grupy do niego dojdą. Pojęcie bariery w przetwarzaniu równoległym definiujemy dla grupy procesów jako miejsce synchronizacji, które każdy z nich musi osiągnąć zanim obliczenia będą kontynuowane.

Jak jesteś slave to robisz send i meldujesz się masterowi i czekasz na potwierdzenie, że możesz iść dalej. (recv)

Jak jesteś master to czekasz na meldunek od każdego slave'a (recv od każdego). Jak już każdy slave się zgłosi, to wysyłasz wszystkim potwierdzenie. (send)

```
Slave: 
    send(bariera, master);
    read(bariera, master);
Master: 

// czekamy na wszystkich
foreach (s in slejvy) {
    recv(bariera, s);
}

// wszyscy przybyli, zwalniamy ich
foreach (s in slejvy) {
    send(blokada, s);
}

// po barierze
```