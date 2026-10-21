# Nauka – source i tekst zapasowy

## Cel

Podaj źródło filmu przez `source` (nie przez `src` na `video`) i zostaw treść zapasową.

## Przydatne

Wewnątrz `video`: `<source src="..." type="video/mp4">`. Poniżej — akapit, gdy odtwarzanie nie zadziała. Nie łącz `src` na `video` z `source`.

Plik: `media/film.mp4`.

## Wymagania

1. `title`: `Źródła filmu`.
2. `h1`: „Materiał w MP4”.
3. `video` z `controls`, wewnątrz `source` do `media/film.mp4` z odpowiednim `type`.
4. Akapit zapasowy wewnątrz `video` (informacja, że odtwarzanie nie jest obsługiwane).
5. Autor, stopka.

## Oczekiwany wynik

Film się odtwarza. W kodzie widać `source` i tekst zapasowy, bez `src` na znaczniku `video`.
