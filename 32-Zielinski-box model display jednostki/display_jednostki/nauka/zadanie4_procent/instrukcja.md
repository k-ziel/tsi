# Nauka – Szerokość w procentach

## Cel

`main` ma zajmować `80%` szerokości rodzica i skalować się przy zmianie okna — nie stałe `px`.

## Przydatne

`width: 80%;` liczy się względem rodzica. Z paddingiem i ramką dodaj `box-sizing: border-box`, żeby zewnętrzna szerokość mieściła się w tych 80%, a nie wychodziła poza. Nie zastępuj `%` pikselami.

## Wymagania

1. `title`: `Jednostki — procent`.
2. `main`: `width: 80%;`, `padding: 16px;`, `border: 2px solid #1e4d7b;`, `box-sizing: border-box;`.
3. Autor, stopka. Nie zastępuj `%` pikselami.

## Oczekiwany wynik

Otwórz stronę: karta treści węższa niż okno. Zwęż / poszerz okno — karta skaluje się z szerokością (zostaje ok. 80% rodzica).
