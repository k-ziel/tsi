# Nauka – display: block

## Cel

Numer sali w `span` ma dostać szerokość i stanąć w osobnej linii — najpierw trzeba zmienić `display`.

## Przydatne

`span` jest domyślnie `inline`: `width` go zwykle nie rozciąga. Ustaw `display: block;` na klasie `.sala`, potem `width: 80px;` oraz padding i ramkę. Blok zachowuje się jak akapit — zajmuje własny wiersz. Bez Flexa.

## Wymagania

1. `title`: `Display — block`.
2. Na numerze sali klasa `sala`.
3. `.sala`: `display: block;`, `width: 80px;`, `padding: 4px 8px;`, `border: 2px solid #1e4d7b;`.
4. Autor, stopka.

## Oczekiwany wynik

Otwórz stronę: numer sali jest w osobnej linii (nie obok słowa „nr”), w granatowej ramce o szerokości `80px`.
