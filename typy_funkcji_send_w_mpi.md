# Typy funkcji send w MPI

Blokująca komunikacja “punkt-punkt”:
* MPI_Send  – standardowy blokujący “send”; funkcja może blokować proces wysyłający do czasu, gdy wiadomość zostanie odebrana przez odbiorcę. Zależy to od czynników takich jak rozmiar wiadomości, liczba wiadomości wysłanych do odbiorcy, itd.
* MPI_Bsend – buforowany “send”; programista dostarcza bufor, który może być ponownie wykorzystany, gdy wiadomość została odebrana. Funkcja zwraca sterowanie po zapisaniu do bufora.
Inaczej: Buforowane blokujące wysyłanie. W odróżnieniu od zwykłej funkcji wysyłającej dane nie są kopiowane bezpośrednio do odbiorcy, lecz do specjalnie przygotowanego systemowego bufora. Funkcja zwraca sterowanie dopiero jeśli dane zostaną do niego skopiowane
* MPI_Ssend – synchroniczny blokujący “send”; funkcja nie zwróci sterowania do momentu, w którym odbiorca zacznie odbierać daną wiadomość
* MPI_Rsend – blokujący “ready send”; funkcja pozwalająca na optymalizację (pominięcie negocjacji bufora pomiędzy nadawcą a odbiorcą), wymaga jednak pewności, iż odpowiadająca funkcja odbiorcza została wcześniej wywołana.
* MPI_Recv – standardowe blokujące odbieranie danych

Nieblokująca komunikacja “punkt-punkt”:
* MPI_Isend –nieblokujący odpowiednik MPI_Send(); zaczyna wysyłać dane, wszystkie zapytania zapisuje w tablicy, a program w tym czasie wykonywany jest dalej
* MPI_Irsend - nieblokujący odpowiednik MPI_Rsend()
* MPI_Issend - nieblokujący odpowiednik MPI_Ssend()
* MPI_Ibsend - nieblokujący odpowiednik MPI_Bsend()
* MPI_Irecv  – nieblokujący odpowiednik MPI_Recv()