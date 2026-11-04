# Nauka – inline-block

## Cel

Menu ma być w **jednym rzędzie**, ale z widocznym paddingiem w ramce każdego odnośnika.

## Przydatne

`display: inline-block` łączy cechy: elementy stoją obok siebie (jak inline), ale biorą `width` / padding / border jak bloki. To nie jest `display: flex`. Na `nav a` ustaw `inline-block`, większy padding poziomy, kolor, brak kreski, ramkę `2px`.

## Wymagania

1. `title`: `Display — rząd`.
2. `nav a`: `display: inline-block;`, `padding: 8px 16px;`, `color: #1e4d7b;`, `text-decoration: none;`, `border: 2px solid #1e4d7b;`.
3. `nav a:hover`: `color: #c9a227;`.
4. Autor, stopka.

## Oczekiwany wynik

Otwórz stronę: Start i Stopka obok siebie; w każdej ramce widać powietrze z paddingu. Najedź — złoty. To nadal rząd, nie kolumna jak przy `block`.
