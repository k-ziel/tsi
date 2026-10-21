# Nauka – Witryna medialna (podsumowanie)

## Cel

Złóż dwie podstrony: film i ramka na starcie, dźwięk z podpisem w archiwum — semantyka i menu, bez CSS.

## Przydatne

Zestaw z działu: `video`, `audio`, `iframe` + `title`, `figure`, ścieżki względne, `header` / `nav` / `main` / `footer`.

Pliki: `media/film.mp4`, `media/podcast.wav`, `media/ramka.html`.

## Wymagania

1. `index.html` (start) i `archiwum.html` w tym samym katalogu.
2. Na obu: UTF-8, autor, różne `title`, `h1` nazwy koła, menu Start / Archiwum, stopka.
3. **Start:** w `main` film z `controls` oraz `iframe` do `media/ramka.html` (z `title`).
4. **Archiwum:** `figure` z `audio` (`controls`, `media/podcast.wav`) i `figcaption`.
5. Działające menu. Żadnego `autoplay`.

## Oczekiwany wynik

Menu przełącza strony. Na starcie widać film i repertuar w ramce. W archiwum — odtwarzacz dźwięku z podpisem.
