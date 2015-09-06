# Nakładanie komunikacji z obliczeniami + przykład + pseudokod przykładu (MPI+C) 

MPI wyróżnia funkcję komunikacji nieblokującej asynchronicznej, zarówno po stronie nadawcy i odbiorcy: 
* MPI_Isend, 
* MPI_Ibsend, 
* MPI_Issend, 
* MPI_Irsend,
* MPI_Irecv. 

Funkcje te rozpoczynają odpowiednie operacje wysyłania i odbioru zwracając uchwyt (MPI_Request), który służy do zakończenia wyżej wymienionych operacji przez wywołanie funkcji rodziny MPI_Wait*. 

Po wywołaniu funkcji MPI_I* proces może wykonać inne operacje pozwalające potencjalnie na wykonanie obliczeń i komunikacji równolegle. 


#Brak pseudokodu - ktos cos ? 