# Wyjaśnij jak zaimplementować w kodzie procesu (C+MPI) odbieranie dowolnych wiadomości od procesów o rankach 2,3 i 8. 

Int MPI_Recv( void *buf, int count, MPI_Datatype datatype, int source, 
int tag, MPI_Comm comm, MPI_Status *status )

wołamy to x3 (albo Irecv jak ktoś woli nieblokująco) z MPI_ANY_TAG i source odpowiednio 2,3 i 8
