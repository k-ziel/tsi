# Nauka – box-sizing

## Cel

Podana szerokość karty ma oznaczać **całe** pudełko: treść + padding + ramka razem, nie samą treść.

## Przydatne

Domyślnie (`content-box`) padding i `border` **dodają się** do `width` — pudełko wychodzi szersze niż `320px`. Z `box-sizing: border-box;` te warstwy mieszczą się w podanym `width`. Ustaw na `.karta`: `width`, `padding`, grubą ramkę i właśnie `border-box`.

## Wymagania

1. `title`: `Box — box-sizing`.
2. Akapit z klasą `karta`.
3. `.karta`: `width: 320px;`, `padding: 16px;`, `border: 4px solid #1e4d7b;`, `box-sizing: border-box;`.
4. Autor, stopka.

## Oczekiwany wynik

Otwórz stronę (albo DevTools → box): zewnętrzna szerokość karty to `320px` **łącznie** z paddingiem i grubą ramką, nie więcej.
