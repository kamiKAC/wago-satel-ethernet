# wago-satel-ethernet
SatelEthernet module for integration of WAGO PLC with Satel INTEGRA using ETHM-1(Plus) module

</p>Plik EXP należy zaimportować do Codesys przez meny Projekt->Importuj<p>

Wejścia:
<ul>
<li>xOpen_Client: 	    BOOL;   - uaktywnia połączenie do modułu ETHM-1
<li>IP:                 STRING;	- adres IP  modulu ETHM-1
<li>Port:               WORD;		- port integracji modulu ETHM-1
<li>StatusReadInterval: TIME;   - czas pomiędzy odpytaniami o stan centrali INTEGRA
<li>Arm:          			BOOL;	  - uzbraja alarm (musi być podany PIN)
<li>Disarm:       			BOOL;   - rozbraja alarm (musi być podany PIN)
<li>PIN:			          STRING; - kod uzbrojenia/rozbrojenia alarmu
<li>Zone:         			STRING;	- strefy do uzbrojenia/rozbrojenia oddzielone przecinkami
<li>wyjscia_prog_1:     ARRAY [1..128] OF BOOL; - tablica zawierajaca stany wyjść aktywnych do zaprogramowania w centrali od 1 do 128, TRUE - wyjście aktywne, FALSE - wyjście bez zmian
<li>wyjscia_prog_0:     ARRAY [1..128] OF BOOL; - tablica zawierajaca stany wyjść do zaprogramowania w centrali od 1 do 128, TRUE - wyjście nieaktywne, FALSE - wyjście bez zmian
</ul>

Wyjścia:
<ul>
<li>czujki:                 ARRAY [1..128] OF BOOL; - tablica zawierająca stany czujek od 1 do 128, TRUE - czujka aktywna, FALSE - czujka nieaktywna
<li>strefy:                 ARRAY [1..32] OF BOOL;	- tablica zawierająca stany stref od 1 do 32, TRUE - strefa uzbrojona, FALSE - strefa rozbrojona
<li>wyjscia:                ARRAY [1..128] OF BOOL; - tablica zawierająca stany wyjść od 1 do 128, TRUE - wyjście aktywne, FALSE - wyjście nieaktywne
<li>xCLIENT_OPEN:           BOOL; - połączenie do modułu ETHM-1 aktywne
<li>wSOCKET:                WORD; - numer wtyczki (socketu) połączenia z modułem ETHM-1
<li>IntegraStatus:          BYTE;	- status ostaniego polecenia dla centrali INTEGRA:
<ul>
<li>0x00 - ok
<li>0x01 - wprowadzony PIN został odnaleziony
<li>0x02 - brak dostępu
<li>0x03 - wybrany użytkownik nie istnieje
<li>0x04 - wybrany użytkownik już istnieje
<li>0x05 - nieprawidłowy PIN jub PIN już istnieje
<li>0x06 - kod telefoniczny już istnieje
<li>0x07 - wprowadzony PIN jest taki sam
<li>0x08 - inny błąd
<li>0x11 - nie można uzbroić, ale wymuszone uzbrojenie jest możliwe
<li>0x12 - nie można uzbroić
<li>0x8? - inne błędy
<li>0xFF - polecenie zaakceptowane(tzn. długość ramki i suma kontrolna prawidłowe), polecenie zostanie przetworzone
</ul>
</ul>
<p>UWAGA: wszystkie zmienne typu STRING podajemy w cudzysłowie pojedynczym, np. 'tekst'</p>
