# Jak się komunikować z procesem stworzonym przez MPI_COMM_SPAWN

Interkomunikator - komunikator zawierający dwie grupy procesów zamiast jednej. 

MPI_Comm_spawn (MPI-2) jest kolektywną operacją na rozmnażających się procesach. 

MPI_Comm_spawn tworzy interkomunikator, zawierający jako dwie grupy procesy rozmnażające (spawning processes) i procesy rozmnażane (spawned processes), za pomocą którego można komunikować się z rozmnożonymi procesami. 

Rozmnożone procesy mogą pobrać interkomunikator za pomocą MPI_Comm_get_parent().
