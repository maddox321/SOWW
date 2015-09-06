# Kiedy przyśpieszenie ponad liniowe/ super liniowe?

Kiedy dane wejściowe są bardzo duże i wymagają bardzo dużej ilości pamięci. W przypadku braku podziału danych praca na nich wymaga użycia stronicowania, wczytywania danych z dysku. Po podziale danych na parę maszyn mamy więcej dostępnej pamięci. To samo z pamięcią cache procesora.

Drugi przypadek to przetwarzania nieprzewidywalnych strumieni danych. Istnieje wiele przetwarzanych równocześnie strumieni danych i niektóre mogą zwrócić wynik ostateczny wcześniej, niż inne. 

Nie można przewidzieć, który proces zwróci najszybciej wynik.