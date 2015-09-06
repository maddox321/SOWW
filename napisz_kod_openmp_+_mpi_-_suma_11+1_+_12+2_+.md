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