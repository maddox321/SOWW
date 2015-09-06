# Prawo Amdahla

Zakłada że czas wykonywania programu inicjującego na pojedyńczym procesorze jest stały.
Przyspieszenie ocenia jakość zaimplementowanych konstrukcji i technik równoległości.

Speed-up SA

SA=t(1)/t(N)

t(1) – the execution time of application A running on a parallel machine with one processor

t(N) – the execution time of application A running on the same parallel machine with N processors.

Let us assume that: s_i denotes the i-th part of the program's instructions to be executed sequentially r_j denotes the j-th part of the program's instructions to be executed in parallel

Let us define: s=s_0+s_1+…+s_k and

r=r_0+r_1+…+r_l.

Then S=(s+r)/(s+r/N)=1/(s+r/N).
