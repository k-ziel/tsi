# Zadanie 7 (Dodatkowe): Zaawansowany pulpit analityczny floty z funkcją calc()

---

## 1. Cel zadania
Zbudowanie zaawansowanego pulpitu kontrolno-pomiarowego (*telematics dashboard*), łączącego wielopoziomowe obliczenia matematyczne `calc()`, jednostki `rem`, `vh` oraz właściwości widoczności. Opanowanie precyzyjnego pozycjonowania 3-kolumnowej siatki z marginesami wewnętrznymi w czystym modelu blokowym bez użycia Flexboxa.

---

## Treść do wpisania
* Nagłówek: "Dyspozytornia Centralna — Pulpit Zarządzania Naczepami"
* Pasek narzędziowy: "Filtry statusu floty", "Raport dobowy tachografów", "Zgłoszenia serwisowe"
* Kolumna lewa (karty zdarzeń, calc(100% - 360px)):
  - Zdarzenie 1: "Pojazd KR-88102 — Kontrola temperatury naczepy chłodniczej OK (+3.4°C)"
  - Zdarzenie 2: "Pojazd GD-3391A — Wjazd do terminalu promowego w Świnoujściu"
  - Zdarzenie 3: "Pojazd WZ-5509C — Wymiana opony na trasie A2 — status: ukończono"
* Kolumna prawa (statystyki i alerty, 340px):
  - "Jednostki w trasie: 48"
  - "Jednostki na bazie: 12"
  - "Serwis planowy: 4"

---

## 2. Wskazówki dydaktyczne (Kluczowe mechanizmy)
- Obliczenie szerokości 3 kolumn przy dwóch odstępach bocznych wynoszących $1.5\text{rem}$ ($24\text{px}$):
  $$\text{width} = \text{calc}((100\% - 3\text{rem}) / 3)$$
  Pomiędzy kolumną pierwszą i drugą oraz drugą i trzecią stosuje się odstęp `margin-right: 1.5rem`, a dla trzeciej kolumny (`:nth-child(3n)`) margines prawy wynosi `0`.
- Wykorzystanie `calc()` do skalowania wskaźnika poziomu paliwa z rezerwą: `width: calc(100% - 4rem)`.
- Zastosowanie `visibility: hidden` na wskaźniku ostrzegawczym awarii silnika w celu zapobieżenia drganiom całego panelu wskaźników w trakcie odświeżania danych.

---

## 3. Wymagania techniczne
1. W pliku `index.html` dołącz zewnętrzny arkusz stylów `style.css`.
2. Zdefiniuj uniwersalny reset marginesów, dopełnień i `box-sizing: border-box`.
3. Dla `body`:
   - tło: `#0b1329`,
   - tekst: `#e2e8f0`,
   - bezszeryfowy stos czcionek systemowych,
   - `line-height: 1.5`.
4. Dla kontenera `.kontener-pulpitu`:
   - szerokość `width: 92%`,
   - maksymalna szerokość: `1120px`,
   - margines pionowy: `2rem`, poziomy: `auto`.
5. Dla nagłówka pulpitu `.naglowek-pulpitu`:
   - tło: `#1e293b`,
   - obramowanie: `1px solid #334155`,
   - zaokrąglenie: `8px`,
   - padding: `1.5rem 2rem`,
   - margines dolny: `1.5rem`.
   - tytuł `h1`: wielkość `1.75rem`, kolor `#38bdf8`,
   - podtytuł `p`: wielkość `0.95rem`, kolor `#94a3b8`.
6. Dla wiersza analitycznego `.wiersz-analityczny`:
   - wyzerowanie czcionki: `font-size: 0`,
   - margines dolny: `1.5rem`.
7. Dla kafelka analitycznego `.kafelek-analityczny`:
   - wyświetlanie `inline-block`,
   - szerokość z użyciem `calc()`: `width: calc((100% - 3rem) / 3)`,
   - margines prawy: `1.5rem`,
   - wyrównanie pionowe: `vertical-align: top`,
   - przywrócenie czcionki: `font-size: 0.95rem`,
   - tło: `#1e293b`,
   - obramowanie: `1px solid #334155`,
   - zaokrąglenie: `8px`,
   - padding: `1.5rem`.
8. Dla trzeciego kafelka (`.kafelek-analityczny:nth-child(3n)`):
   - wyzerowanie marginesu prawego: `margin-right: 0`.
9. Dla paska miernika `.kontener-miernika`:
   - tło: `#0f172a`,
   - wysokość: `20px`,
   - zaokrąglenie: `10px`,
   - padding: `2px`,
   - obramowanie: `1px solid #334155`,
   - margines górny: `1rem`.
10. Dla wskaźnika poziomu `.slupek-poziomu`:
    - wysokość: `100%`,
    - zaokrąglenie: `8px`,
    - wariant zielony: `background-color: #10b981; width: calc(100% - 2.5rem);`,
    - wariant niebieski: `background-color: #3b82f6; width: calc(100% - 5rem);`,
    - wariant pomarańczowy: `background-color: #f59e0b; width: calc(100% - 1.2rem);`.
11. Dla wskaźnika błędu krytycznego `.ostrzezenie-awaria`:
    - tło: `#ef4444`,
    - kolor: `#ffffff`,
    - padding: `0.4rem 0.8rem`,
    - zaokrąglenie: `4px`,
    - font-size: `0.85rem`,
    - margines górny: `1rem`,
    - reguła stabilizująca: klasa `.brak-bledu` posiada `visibility: hidden; min-height: 28px;` (aby kafelek zachowywał stałą wysokość).

---

## 4. Oczekiwany wynik
Zaawansowany pulpit analityczny z trzema kafelkami w jednym wierszu, precyzyjnie rozłożonymi za pomocą `calc((100% - 3rem) / 3)`. Każdy kafelek prezentuje precyzyjnie obliczone słupki wskaźników z marginesem rezerwowym oraz stabilną przestrzeń powiadomień bez drgań interfejsu.
