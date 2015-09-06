# Prawo Amdahla

Prawo Amdahla wychodzi z założenia, że duży matematyczny czy inżynierski problem typowo składa się z takich części, które udaje się zrównoleglić i z takich, dla których nie jest to możliwe. 

Prawo Amdahla stanowi, iż fragmenty programu, które nie mogą być zrównoleglone ograniczają możliwe do osiągnięcia przyspieszenie całego procesu. 

Ten związek jest definiowany przez następujące równanie: 

S = 1/(1-P), 
gdzie: 
* S jest maksymalnym, możliwym do osiągnięcia przyspieszeniem programu, 
* P jest ułamkiem, który określa jaką część obliczeń można "zrównoleglić". 


Na przykład, jeśli sekwencyjna część programu stanowi 10% całkowitego czasu potrzebnego na jego wykonanie (1-P = 0.1) to można osiągnąć nie więcej niż 10-krotne przyspieszenie, niezależnie od ilości procesorów jakie zostaną dodane. Tworzy to odgórny limit przydatności dodawania większej ilości jednostek obliczeniowych. 

Jeśli zadanie nie może być podzielone z uwagi na ograniczenia wynikające z sekwencyjności problemu, dodanie mocy przetwarzania nie wpłynie na czas jego wykonania.