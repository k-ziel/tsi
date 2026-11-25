# Zadanie 4: Matematyka w CSS — funkcja calc() w praktyce

---

## 1. Cel zadania
Opanowanie funkcji matematycznej `calc()`, łączenie jednostek względnych i bezwzględnych (`%`, `rem`, `px`), zrozumienie krytycznej reguły spacji wokół operatorów dodawania i odejmowania oraz stworzenie klasycznego dwukolumnowego układu aplikacji (stały panel boczny i elastyczna treść główna) bez użycia Flexboxa.

---

## Treść do wpisania
* Nagłówek: "Kalkulacja Kosztów Frachtu Międzynarodowego"
* Panel główny (lewy):
  - Tytuł h2: "Dyspozycja Trasy i Ładunku"
  - Trasa: "Warszawa — Rotterdam (1 240 km)"
  - Pojazd: "Scania R500 V8 Highline (Euro 6)"
  - Ładunek: "24 palety euro, masa całkowita 18.4 t"
* Pasek boczny (prawy, stały 280px):
  - Tytuł h3: "Podsumowanie Opłat"
  - Myto i opłaty drogowe: "420.00 EUR"
  - Paliwo szacunkowe: "680.00 EUR"
  - Razem netto: "1 100.00 EUR"

---

## 2. Wskazówki dydaktyczne (Kluczowe mechanizmy)
- **Krytyczna reguła składni:** W funkcji `calc()` operatory `+` oraz `-` **muszą** być bezwzględnie otoczone spacjami z obu stron, np. `calc(100% - 30px)`. Zapis `calc(100%-30px)` jest traktowany przez parser CSS jako błąd składniowy (rozpoznaje ciąg `-30px` jako identyfikator/liczbę ujemną) i cała deklaracja zostaje odrzucona!
- Dzielenie i mnożenie: Dzielenie wykonuje się przez liczbę bez jednostki, np. `calc(100% / 3)`. Mnożenie dopuszcza liczbę bez jednostki po jednej ze stron, np. `calc(2rem * 1.5)`.
- W układzie ze stałym panelem bocznym o szerokości $260\text{px}$ i odstępem $20\text{px}$, szerokość obszaru roboczego wynosi dokładnie `calc(100% - 280px)`. Obie sekcje mogą być ułożone obok siebie za pomocą `display: inline-block` z wyrównaniem `vertical-align: top`.

---

## 3. Wymagania techniczne
1. W pliku `index.html` dołącz zewnętrzny arkusz stylów `style.css`.
2. Zdefiniuj uniwersalny reset marginesów, dopełnień i `box-sizing: border-box`.
3. Dla `body`:
   - tło: `#f1f5f9`,
   - tekst: `#1e293b`,
   - bezszeryfowy stos czcionek systemowych,
   - `line-height: 1.5`.
4. Dla kontenera `.kontener-glowny`:
   - maksymalna szerokość: `1100px`,
   - wycentrowanie: margines pionowy `2rem`, poziomy `auto`,
   - dopełnienie boczne: `1.5rem`.
5. Dla nagłówka widoku `.naglowek-widoku`:
   - tło: `#ffffff`,
   - obramowanie: `1px solid #cbd5e1`,
   - zaokrąglenie: `8px`,
   - padding: `1.5rem`,
   - margines dolny: `1.5rem`.
6. Dla wiersza roboczego `.wiersz-roboczy`:
   - wyzerowanie czcionki: `font-size: 0`,
   - zapobieganie niepożądanym przerwom między elementami `inline-block`.
7. Dla stałego panelu bocznego `.panel-boczny`:
   - wyświetlanie `inline-block`,
   - stała szerokość: `width: 260px`,
   - margines prawy obliczony matematycznie lub stały: `margin-right: 20px`,
   - wyrównanie pionowe: `vertical-align: top`,
   - przywrócenie czcionki: `font-size: 1rem`,
   - tło: `#ffffff`,
   - obramowanie: `1px solid #cbd5e1`,
   - zaokrąglenie: `8px`,
   - padding: `1.25rem`.
8. Dla elastycznej zawartości głównej `.obszar-glowny`:
   - wyświetlanie `inline-block`,
   - szerokość obliczona funkcją `calc()`: `width: calc(100% - 280px)`,
   - wyrównanie pionowe: `vertical-align: top`,
   - przywrócenie czcionki: `font-size: 1rem`,
   - tło: `#ffffff`,
   - obramowanie: `1px solid #cbd5e1`,
   - zaokrąglenie: `8px`,
   - padding: `1.5rem`.
9. Dla siatki dwóch kart informacyjnych `.wiersz-podwojny`:
   - wyzerowanie czcionki: `font-size: 0`,
   - margines górny: `1rem`.
10. Dla równej karty wewnątrz siatki `.karta-polowkowa`:
    - wyświetlanie `inline-block`,
    - szerokość z użyciem `calc()` z uwzględnieniem odstępu 1rem: `width: calc((100% - 1rem) / 2)`,
    - wyrównanie: `vertical-align: top`,
    - przywrócenie czcionki: `font-size: 0.95rem`,
    - tło: `#f8fafc`,
    - obramowanie: `1px solid #e2e8f0`,
    - zaokrąglenie: `6px`,
    - padding: `1rem`.
11. Dla pierwszej karty z pary (`.karta-polowkowa:first-child`):
    - margines prawy: `1rem`.

---

## 4. Oczekiwany wynik
Aplikacja wyświetla panel boczny o stałej szerokości 260px oraz główny obszar roboczy dynamicznie zajmujący całą pozostałą szerokość kontenera (`calc(100% - 280px)`). Wewnątrz obszaru roboczego znajdują się dwie karty idealnie dopasowane do połówki szerokości pomniejszonej o przerwę (`calc((100% - 1rem) / 2)`).
