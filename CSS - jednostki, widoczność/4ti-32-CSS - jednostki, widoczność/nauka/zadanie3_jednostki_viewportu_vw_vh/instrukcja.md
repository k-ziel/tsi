# Zadanie 3: Jednostki obszaru wyświetlania — vw oraz vh

---

## 1. Cel zadania
Opanowanie jednostek opartych o obszar wyświetlania okna przeglądarki (*viewport units*): `vh` (wysokość viewportu) oraz `vw` (szerokość viewportu). Zrozumienie pułapki `100vw` powodującej niepożądany poziomy pasek przewijania oraz zaprojektowanie reprezentacyjnej sekcji powitalnej (Hero Banner) o wysokości zależnej od okna przeglądarki bez użycia Flexboxa.

---

## Treść do wpisania
* Sekcja Hero:
  - Tytuł h1: "Globalny Monitoring Floty Transportowej"
  - Podtytuł: "Telematyka satelitarna GPS i optymalizacja tras tranzytowych w czasie rzeczywistym."
  - Przycisk CTA: "Otwórz Pulpit Operacyjny"
* Karta informacyjna pod banerem:
  - Nagłówek h2: "Parametry Transmisji Telemetrycznej"
  - Tekst: "Odświeżanie pakietów danych co 15 sekund z marginesem błędu pozycjonowania poniżej 2 metrów."

---

## 2. Wskazówki dydaktyczne (Kluczowe mechanizmy)
- $1\text{vh}$ to $1\%$ wysokości okna przeglądarki, a $1\text{vw}$ to $1\%$ szerokości okna przeglądarki.
- **Pułapka `100vw`:** W systemach stacjonarnych (np. Windows) `100vw` uwzględnia fizyczną szerokość pionowego paska przewijania (zwykle ok. $15\text{--}17\text{px}$). Użycie `width: 100vw` zamiast `width: 100%` powoduje powstanie nieestetycznego poziomego paska przewijania (*overflow-x*). Dla szerokości stron zawsze stosuj `width: 100%`!
- Dla sekcji Hero bezpieczniej jest używać `min-height: 60vh` zamiast sztywnego `height: 60vh`, aby w przypadku mniejszych ekranów lub dużej ilości treści tekst nie wylewał się poza tło sekcji (*content overflow*).
- Wyśrodkowanie w pionie w CSS bez Flexboxa można elegancko uzyskać poprzez symetryczne dopełnienia wewnętrzne oparte o `vh` (np. `padding: 12vh 1rem`).

---

## 3. Wymagania techniczne
1. W pliku `index.html` dołącz zewnętrzny arkusz stylów `style.css`.
2. Zdefiniuj uniwersalny reset marginesów, dopełnień i `box-sizing: border-box`.
3. Dla `body`:
   - `background-color: #0f172a`,
   - `color: #f8fafc`,
   - bezszeryfowy stos czcionek systemowych,
   - `line-height: 1.6`.
4. Dla paska nawigacji `.pasek-gorny`:
   - wysokość: `60px`,
   - tło: `#1e293b`,
   - obramowanie dolne: `1px solid #334155`,
   - dopełnienie boczne: `2rem`,
   - linia tekstu: wyśrodkowanie w pionie za pomocą `line-height: 60px`,
   - logo: wielkość `1.1rem`, waga `bold`, kolor `#38bdf8`.
5. Dla sekcji powitalnej `.sekcja-hero`:
   - minimalna wysokość: `min-height: 60vh`,
   - tło z gradientem liniowym: `linear-gradient(180deg, #1e293b 0%, #0f172a 100%)`,
   - obramowanie dolne: `2px solid #3b82f6`,
   - wyśrodkowanie tekstu: `text-align: center`,
   - dopełnienie pionowe oparte o `vh`: `padding: 12vh 1rem 8vh 1rem`.
6. Dla typografii w sekcji Hero:
   - nagłówek `h1`:
     - wielkość oparta o rem: `2.5rem`,
     - kolor: `#ffffff`,
     - margines dolny: `1.5rem`.
   - podtytuł `.opis-hero`:
     - maksymalna szerokość: `650px`,
     - margines pionowy: `0 auto 2rem auto`,
     - wielkość: `1.15rem`,
     - kolor: `#94a3b8`.
7. Dla przycisku akcji `.btn-glowny`:
   - wyświetlanie `inline-block`,
   - `padding: 0.8rem 2rem`,
   - tło: `#3b82f6`,
   - kolor: `#ffffff`,
   - brak podkreślenia,
   - zaokrąglenie: `6px`,
   - waga czcionki: `bold`.
8. Dla sekcji zawartości `.sekcja-metryki`:
   - maksymalna szerokość `max-width: 960px`,
   - margines: `3rem auto`,
   - padding: `0 1.5rem`,
   - text-align: `center`.
9. Dla kart metryk `.karta-metryki`:
   - wyświetlanie `inline-block`,
   - szerokość `width: 30%`,
   - margines boczny: `1.5%`,
   - tło: `#1e293b`,
   - obramowanie: `1px solid #334155`,
   - zaokrąglenie: `8px`,
   - padding: `1.5rem 1rem`,
   - wyrównanie pionowe: `top`.

---

## 4. Oczekiwany wynik
Górna belka ma stałą wysokość 60px. Poniżej znajduje się efektowny baner powitalny Hero o dynamicznej wysokości adaptującej się do wysokości okna (60vh), z wycentrowanym hasłem i przyciskiem akcji. Pod banerem umieszczone są trzy karty metryk w jednym wierszu bez poziomego paska przewijania.
