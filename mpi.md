# MPI

MPI - Protokół komunikacyjny będący standardem przesyłania komunikatów pomiędzy procesami programów równoległych działających na jednym lub więcej komputerach. 

Interfejs ten wraz z protokołem oraz semantyką specyfikuje, jak jego elementy winny się zachowywać w dowolnej implementacji. 

Celami MPI są wysoka jakość, skalowalność oraz przenośność. 

MPI jest dominującym modelem wykorzystywanym obecnie w klastrach komputerów oraz superkomputerach. 

Funkcje MPI:
* MPI_Init – musi być wywołana na początku program
* MPI_Finalize – musi być wywołana przed zakończeniem programu
* MPI_Comm_size – pobiera rozmiar danego komunikatora, jeżeli jest używany z MPI_COMM_WORLD zwraca liczbę wszystkich procesów w programie
* MPI_Comm_rank – zwraca stopień/rangę wywoływanego procesu
* MPI_Reduce – wykonuje określone działanie na wynikach częściowych otrzymanych w procesach i zapisuje wynik tej operacji na jednym procesie
* MPI_Allreduce – analogicznie do MPI_Reduce, lecz wynik zapisywany jest do wszystkich procesów
* MPI_Probe – blokujący; pozwala na podejrzenie nadchodzącej wiadomości bez odbierania jej
* MPI_Iprobe – nieblokujący wersja MPI_Probe; flag = true, jeśli wiadomość może być odebrana
* MPI_Cancel – pozwala na anulowanie nadchodzącej wiadomości (zwalania pamięć zajmowaną przez tą wiadomość)
* MPI_Request– zwracany po sfinalizowaniu komunikacji

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

Testowanie zakończenia komunikacji “punkt-punkt”:
* MPI_Wait – blokujący (czeka na zakończenie podanej operacji)
* MPI_Waitany – czeka na zakończenie którejkolwiek operacji z tablicy
* MPI_Waitall - czeka na zakończenie wszystkich operacji z tablicy
* MPI_Waitsome – czeka dopóki jakieś operacje się nie zakończą
* MPI_Test – działa jak MPI_Wait(), z tym że nie czeka na zakończenie operacji a zwraca true lub flase
* MPI_Testany – analogicznie do MPI_Waitany()
* MPI_Testall – analogicznie do MPI_Waitall()
* MPI_Testsome – analogicznie do MPI_Waitsome()

Komunikacja kolektywna:
* MPI_Barrier - synchronizacja
* MPI_Bcast - rozgłaszanie
* MPI_Scatter - rozsiewanie
* MPI_Scatterv - rozsiewanie w częściach
* MPI_Gather – zbieranie przez pojedynczy proces
* MPI_Gatherv – zbieranie przez pojedynczy proces do określonych lokalizacji
* MPI_Allgather - zbieranie przez wszystkie procesy
* MPI_Alltoall - zbieranie i rozsiewanie przez wszystkie procesy
* MPI_Get_count() - zwraca ilość (liczbę) elementów danego typu w zmiennej count
* MPI_StartAll - rozpoczyna zbiór kontekstów wiadomości (tabilicę uchwytów)
* MPI_Comm_Spawn - jest kolektywną operacją na rozmnażających się procesach. MPI_Comm_spawn tworzy interkomunikator, zawierający jako dwie grupy procesy rozmnażające (spawning processes) i procesy rozmnażane (spawned processes), za pomocą którego można komunikować się z rozmnożonymi procesami. Rozmnożone procesy mogą pobrać interkomunikator za pomocą MPI_Comm_get_parent()
