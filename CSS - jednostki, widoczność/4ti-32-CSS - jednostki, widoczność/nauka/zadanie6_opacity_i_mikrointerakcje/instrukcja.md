# Zadanie 6: Przezroczystość i mikrointerakcje — właściwość opacity

---

## 1. Cel zadania
Zrozumienie działania właściwości `opacity` jako trzeciego wierzchołka Trójkąta Widoczności CSS, zbadanie zjawiska dziedziczenia przezroczystości przez wszystkie elementy potomne (w odróżnieniu od izolowanego tła `rgba()`), stworzenie płynnych mikrointerakcji wizualnych za pomocą przejść (*transitions*) na pseudoklasie `:hover` bez użycia Flexboxa.

---

## Treść do wpisania
* Nagłówek: "Katalog Pojazdów Specjalnych — Mikrointerakcje"
* Podtytuł: "Przejścia tonalne opacity przy najechaniu kursorem myszy."
* Karta 1: "Ciągnik Siodłowy Scania 770S", stan: "Gotowy do trasy", przycisk: "Szczegóły Pojazdu"
* Karta 2: "Cysterna Paliwowa Feldbinder", stan: "W trakcie załadunku", przycisk: "Szczegóły Pojazdu"
* Karta 3: "Zestaw Chłodniczy Schmitz", stan: "Dostępny w bazie", przycisk: "Szczegóły Pojazdu"

---

## 2. Wskazówki dydaktyczne (Kluczowe mechanizmy)
- `opacity` przyjmuje wartości od `0.0` (całkowicie przezroczysty / niewidoczny) do `1.0` (w pełni nieprzezroczysty).
- **Pułapka interaktywności:** Element oznaczony `opacity: 0` staje się niewidzialny dla oka, ale zachowuje swoje fizyczne wymiary **oraz nadal reaguje na kliknięcia myszą**! Jeśli ma nie blokować klikania elementów pod spodem, wymaga wyłączenia zdarzeń wskaźnika (`pointer-events: none`).
- **Dziedziczenie bezwzględne:** W przeciwieństwie do `background-color: rgba(0, 0, 0, 0.5)`, która barwi wyłącznie tło danego elementu, `opacity: 0.5` sprawia, że cały element wraz z tekstem, ikonami i potomkami staje się w $50\%$ przezroczysty.
- Płynność animacji: Właściwość `transition: opacity 0.25s ease-in-out` umożliwia tworzenie eleganckich efektów podświetlenia kart po najechaniu kursorem (`:hover`).

---

## 3. Wymagania techniczne
1. W pliku `index.html` dołącz zewnętrzny arkusz stylów `style.css`.
2. Zdefiniuj uniwersalny reset marginesów, dopełnień i `box-sizing: border-box`.
3. Dla `body`:
   - tło: `#0f172a`,
   - kolor tekstu: `#f8fafc`,
   - bezszeryfowy stos czcionek systemowych,
   - `line-height: 1.5`.
4. Dla kontenera `.kontener`:
   - maksymalna szerokość: `900px`,
   - margines pionowy `2.5rem`, poziomy `auto`,
   - dopełnienie boczne: `1.5rem`.
5. Dla nagłówka widoku:
   - `h1`: wielkość `1.6rem`, margines dolny `0.5rem`, kolor `#38bdf8`,
   - `p`: wielkość `0.95rem`, margines dolny `2rem`, kolor `#94a3b8`.
6. Dla wiersza demonstracyjnego `.wiersz-kart`:
   - wyzerowanie wielkości czcionki: `font-size: 0`.
7. Dla interaktywnej karty logistycznej `.karta-interaktywna`:
   - wyświetlanie `inline-block`,
   - szerokość: `width: calc((100% - 2rem) / 3)`,
   - wyrównanie: `vertical-align: top`,
   - przywrócenie czcionki: `font-size: 0.95rem`,
   - tło: `#1e293b`,
   - obramowanie: `1px solid #334155`,
   - zaokrąglenie: `8px`,
   - padding: `1.25rem`,
   - margines prawy: `1rem` (dla ostatniej karty `.karta-interaktywna:last-child` margines prawy wynosi `0`),
   - domyślna przezroczystość: `opacity: 0.6`,
   - płynne przejście: `transition: opacity 0.3s ease, border-color 0.3s ease`.
8. Dla stanu najechania karty `.karta-interaktywna:hover`:
   - pełna widoczność: `opacity: 1`,
   - podświetlenie ramki: `border-color: #38bdf8`.
9. Dla paska stanu zlecenia `.stan-zlecenia`:
   - tło z przezroczystością kanału alfa: `background-color: rgba(56, 189, 248, 0.15)`,
   - kolor tekstu (w 100% czytelny): `#38bdf8`,
   - padding: `0.4rem 0.6rem`,
   - zaokrąglenie: `4px`,
   - margines dolny: `1rem`,
   - waga czcionki: `bold`.
10. Dla ukrytego przycisku akcji w karcie `.btn-szczegoly`:
    - wyświetlanie `block`,
    - text-align: `center`,
    - padding: `0.5rem`,
    - tło: `#0284c7`,
    - kolor: `#ffffff`,
    - text-decoration: `none`,
    - zaokrąglenie: `4px`,
    - margines górny: `1rem`,
    - stan początkowy: `opacity: 0`,
    - płynne przejście: `transition: opacity 0.25s ease`.
11. Dla aktywacji przycisku po najechaniu na kartę (`.karta-interaktywna:hover .btn-szczegoly`):
    - ujawnienie przycisku: `opacity: 1`.

---

## 4. Oczekiwany wynik
Wiersz z trzema kartami zleceń w spoczynku ma subtelnie przygaszoną widoczność (`opacity: 0.6`), a przyciski akcji są całkowicie niewidoczne (`opacity: 0`). Po najechaniu kursorem na dowolną kartę, karta płynnie rozjaśnia się do pełnej nieprzezroczystości (`opacity: 1`), a przycisk akcji płynnie pojawia się w dolnej części karty.
