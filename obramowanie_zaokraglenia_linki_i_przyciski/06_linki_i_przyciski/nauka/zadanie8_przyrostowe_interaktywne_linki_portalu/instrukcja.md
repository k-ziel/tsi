# Zadanie 8: Przyrostowe – Interaktywne odnośniki i przyciski Portalu IT-Partner

## Opis zadania
Rozbudowa Portalu Usługowo-Handlowego (Projekt Capstone) o pełny system interaktywnych odnośników w nawigacji, przycisków CTA oraz przycisków w kartach usług z zachowaniem kontraktu DOM.

## Treść do wpisania
* Logo i tytuł portalu: "IT-Partner - Nowoczesne Rozwiązania Biznesowe"
* Nawigacja: "Usługi", "Cennik", "Zamówienie", "Kontakt"
* Przycisk w banerze głównym: "Sprawdź Pełną Ofertę Serwisową"
* Przycisk w formularzu wyceny: "Oblicz Koszt Wyceny"
* Przycisk wysyłki: "Wyślij Zamówienie"

## Instrukcja wykonania krok po kroku
1. Rozbuduj arkusz stylów `style.css` portalu o pełną obsługę pseudoklas odnośników i przycisków.
2. W menu nawigacyjnym (`nav a`):
   - Zastosuj regułę LVHA: brak podkreślenia, kolor #0284c7, na `:hover` podkreślenie i kolor #0369a1.
   - Zapewnij wyraźny `:focus` dla nawigacji klawiszowej.
3. Przyciski akcji (`#btn-oblicz` oraz `#btn-wyslij`):
   - Nadaj `display: inline-block`, `padding: 12px 24px`, kolor biały, `border-radius: 6px`, `cursor: pointer`.
   - `#btn-oblicz`: tło `#2563eb`, na `:hover` `#1d4ed8`, na `:active` `#1e40af` i cień wewnętrzny.
   - `#btn-wyslij`: tło `#16a34a`, na `:hover` `#15803d`, na `:active` `#166534`.
4. Przyciski w kartach usług (`.karta-uslugi a`):
   - Ostyluj jako przyciski CTA wariantu outline lub pełnego.
5. Zachowaj integralność selektorów kontraktu DOM: `#tytul-portalu`, `#logo`, `#baner-glowny`, `#btn-oblicz`, `#btn-wyslij`, `#wynik`, `.karta-uslugi`.
