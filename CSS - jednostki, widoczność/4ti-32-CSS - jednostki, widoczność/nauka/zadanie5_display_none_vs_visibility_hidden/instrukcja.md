# Zadanie 5: Kontrola widoczności — display: none a visibility: hidden

---

## 1. Cel zadania
Zbadanie fundamentalnych różnic w zachowaniu przeglądarki podczas stosowania właściwości `display: none` (całkowite wycięcie z drzewa renderowania, utrata zajmowanego miejsca, załamanie przepływu dokumentu) oraz `visibility: hidden` (ukrycie wizualne z bezwzględnym zachowaniem wymiarów pudełka i przestrzeni w dokumencie). Zapobieganie niepożądanym skokom interfejsu (*Layout Shift*).

---

## Treść do wpisania
* Tytuł: "Laboratorium kontroli widoczności w CSS"
* Podtytuł: "Porównanie wpływu ukrywania elementów na geometrię i przepływ dokumentu."
* Panel 1: "1. Rezerwacja przestrzeni (visibility: hidden)"
  - Komunikat alert1: "OSTRZEŻENIE SYSTEMOWE: Przekroczono dopuszczalny czas jazdy tachografu dla pojazdu #104."
  - Etykieta przycisku: "Przełącz: visibility"
* Panel 2: "2. Całkowite wycięcie z układu (display: none)"
  - Komunikat alert2: "POWIADOMIENIE LOGISTYCZNE: Wpłynęło nowe zlecenie załadunku dla kierowcy #208."
  - Etykieta przycisku: "Przełącz: display"

---

## 2. Wskazówki dydaktyczne (Kluczowe mechanizmy)
- `display: none`:
  - Element nie bierze udziału w tworzeniu geometrii strony.
  - Okoliczne elementy przesuwają się na jego miejsce (przeliczenie układu — *reflow*).
  - Żaden element potomny nie może zostać wyświetlony, jeśli rodzic ma `display: none`.
- `visibility: hidden`:
  - Element jest niewidoczny dla oka, ale pozostaje fizyczną "niewidzialną bryłą" w dokumencie.
  - Sąsiednie elementy nie zmieniają swojego położenia (brak *reflow*).
  - Wyjątkowa cecha: element potomny wewnątrz ukrytego rodzica może zostać przywrócony za pomocą `visibility: visible`!

---

## 3. Wymagania techniczne
1. W pliku `index.html` dołącz zewnętrzny arkusz stylów `style.css` oraz skrypt `script.js`.
2. Zdefiniuj uniwersalny reset marginesów, dopełnień i `box-sizing: border-box`.
3. Dla `body`:
   - tło: `#f8fafc`,
   - kolor tekstu: `#0f172a`,
   - bezszeryfowy stos czcionek systemowych,
   - `line-height: 1.5`.
4. Dla kontenera `.kontener`:
   - maksymalna szerokość: `840px`,
   - margines pionowy `2rem`, poziomy `auto`,
   - dopełnienie boczne: `1rem`.
5. Dla paneli demonstracyjnych `.panel-porownawczy`:
   - tło: `#ffffff`,
   - obramowanie: `1px solid #cbd5e1`,
   - zaokrąglenie: `8px`,
   - padding: `1.5rem`,
   - margines dolny: `2rem`.
6. Dla komunikatu rezerwującego miejsce `.alert-rezerwacja`:
   - minimalna wysokość: `48px`,
   - tło: `#fee2e2`,
   - obramowanie: `1px solid #ef4444`,
   - zaokrąglenie: `6px`,
   - padding: `0.75rem 1rem`,
   - kolor tekstu: `#991b1b`,
   - margines dolny: `1rem`,
   - reguła ukrywania: klasa `.niewidoczny` ustawia `visibility: hidden;`.
7. Dla komunikatu zwijanego `.alert-zwiniecie`:
   - tło: `#fef3c7`,
   - obramowanie: `1px solid #f59e0b`,
   - zaokrąglenie: `6px`,
   - padding: `0.75rem 1rem`,
   - kolor tekstu: `#92400e`,
   - margines dolny: `1rem`,
   - reguła ukrywania: klasa `.ukryty` ustawia `display: none;`.
8. Dla przycisków kontrolnych `.btn-przepnij`:
   - wyświetlanie `inline-block`,
   - padding: `0.5rem 1rem`,
   - tło: `#0284c7`,
   - kolor: `#ffffff`,
   - brak podkreślenia,
   - zaokrąglenie: `4px`,
   - kursor wskaźnika (`cursor: pointer`),
   - obramowanie: `none`,
   - margines górny: `0.5rem`.
9. W pliku `script.js`:
   - obsłuż kliknięcia przycisków za pomocą `addEventListener`,
   - przycisk 1 przełącza klasę `.niewidoczny` na pierwszym alercie (`classList.toggle`),
   - przycisk 2 przełącza klasę `.ukryty` na drugim alercie (`classList.toggle`),
   - kod JS musi być poprawny syntaktycznie i przejść test `node --check`.

---

## 4. Oczekiwany wynik
Uczeń obserwuje dwa panele. W pierwszym panelu ukrycie komunikatu z `visibility: hidden` pozostawia puste, nienaruszone miejsce w układzie, a przycisk poniżej nie skacze w górę. W drugim panelu ukrycie z `display: none` natychmiast zapada pustą przestrzeń, a przycisk skacze do góry, demonstrując reflow.
