# MPI odebranie komunikatu o nieznanym rozmiarze

// sprawdzenie przychodzącej wiadomości bez odbierania jej

MPI_Probe (int source, int tag, MPI_Comm, int *flag, MPI_Status *status)

// jeżeli flag = true to wiadomość doszła i można ją odebrać

// sprawdzamy liczbę odebranych elementów danego typu

MPI_Get_count (MPI_Status *status, MPI_Datatype dtype, int *count)

// odbieramy wiadomość

MPI_Recv ()

