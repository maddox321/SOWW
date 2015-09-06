# MPI_IRECV

MPI_Irecv - Rozpoczyna nie blokowany odbiór; 

Wejściowe parametry: 
* buf - początkowy adres bufora odbioru; 
* count - ilośc elementów w buforze odbioru (integer) ;
* datatype - typ danych bufora odbioru (uchwyt); 
* source - rank nadawcy (integer); 
* tag - identyfikator wiadomości (integer) ;
* comm - komunikator (uchwyt);

Wyjściowe parametry:
* request - kontekst wiadomości używany do badania stanu wiadomości (uchwyt);