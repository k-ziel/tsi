# Zadanie 6: Witryna ogłoszeniowa w standardzie CKE INF.03

## Opis zadania
Ostylowanie modułu rekrutacyjnego w ścisłym reżimie specyfikacji arkusza egzaminacyjnego CKE: belka nawigacji, przyciski akcji, pseudoklasy hover i active.

## Treść do wpisania
* Nagłówek serwisu: "Portal Ofert Pracy IT-Kariera"
* Tytuł oferty: "Młodszy Programista Frontend (Junior Web Developer)"
* Widełki płacowe: "Wynagrodzenie: 6000 - 8500 PLN brutto"
* Przycisk 1: "Aplikuj na Stanowisko"
* Przycisk 2: "Zapisz Ofertę na Później"

## Instrukcja wykonania krok po kroku
1. W module `.ogloszenie` ostyluj przycisk główny `.btn-aplikuj`:
   - `display: inline-block`, `padding: 12px 26px`, tło `#d97706`, tekst biały, brak podkreślenia, zaokrąglenie `4px`.
   - Na `:hover` tło `#b45309`.
   - Na `:active` tło `#92400e` i cień wewnętrzny `box-shadow: inset 0 2px 4px rgba(0,0,0,0.3)`.
2. Przycisk pomocniczy `.btn-zapisz`:
   - `display: inline-block`, `padding: 12px 26px`, tło białe, ramka `2px solid #d97706`, tekst `#d97706`, brak podkreślenia.
   - Na `:hover` tło `#fef3c7`.
3. Ustaw `cursor: pointer` oraz obsługę `:focus` z obrysem 2px dla obu przycisków.
