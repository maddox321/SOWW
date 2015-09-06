# Co oznaczają przedrostki

* przedrostek “b” przed np SEND oznacza buforowany; wiadomośc zostanie wysłana do bufora jeśli nie został wywołany odpowiedni recv, jeśli bufor się przepełni będzie błąd
* “s” oznacza synchroniczny, synchronizuje send i recv
* Jednak co oznacza “r” jak ready - że jak ktoś nie jest gotowy do odbioru, to send się nie wykona. 
*