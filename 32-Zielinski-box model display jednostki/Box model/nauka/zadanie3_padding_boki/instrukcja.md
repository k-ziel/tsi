# Nauka – Padding: pion i poziom

## Cel

Karta ma mieć inny padding góra/dół niż lewo/prawo — więcej powietrza po bokach.

## Przydatne

Skrót z dwiema wartościami: `padding: 8px 24px;` — pierwsza to pion (góra i dół), druga to poziom (lewo i prawo). Nie pisz czterech osobnych `padding-top` itd., jeśli wystarczą dwie wartości. Ramka pokazuje, gdzie kończy się powietrze.

## Wymagania

1. `title`: `Box — boki paddingu`.
2. Akapit z klasą `karta`.
3. `.karta`: `border: 2px solid #1e4d7b;` oraz `padding: 8px 24px;`.
4. Autor, stopka.

## Oczekiwany wynik

Otwórz stronę: w granatowej ramce widać wyraźnie więcej powietrza po lewej i prawej (`24px`) niż u góry i dołu (`8px`).
