# Zadanie 5: Interaktywna karta jako blokowy odnośnik

## Opis zadania
Ostylowanie karty informacyjnej ze znacznikiem <a> jako elementem blokowym reagującym na najechanie uniesieniem cienia i zmianą obramowania.

## Treść do wpisania
* Karta 1: Tytuł "Pakiet Startowy WWW", Cena "1200 PLN", Opis "Strona wizytówkowa zoptymalizowana pod urządzenia mobilne."
* Karta 2: Tytuł "Pakiet Biznes Pro", Cena "3400 PLN", Opis "Sklep internetowy z płatnościami online i integracją kurierską."

## Instrukcja wykonania krok po kroku
1. Ustaw dla odnośników `.karta-link` właściwości: `display: block`, `text-decoration: none`, kolor tekstu `#1e293b`, tło białe, obramowanie `2px solid #e2e8f0`, `border-radius: 8px`, `padding: 20px`, `margin-bottom: 20px`.
2. Dodaj cień początkowy: `box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05)`.
3. W stanie `.karta-link:hover`:
   - Zmień kolor obramowania na `#3b82f6`.
   - Zwiększ cień na `0 10px 20px rgba(0, 0, 0, 0.12)`.
   - Zmień kolor nagłówka `h3` wewnątrz karty na `#2563eb`.
4. W stanie `.karta-link:focus` zapewnij `outline: 3px solid #3b82f6; outline-offset: 3px;`.
