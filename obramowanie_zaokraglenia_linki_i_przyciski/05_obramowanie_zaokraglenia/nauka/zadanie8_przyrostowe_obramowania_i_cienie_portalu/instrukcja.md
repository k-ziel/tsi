# Zadanie 8: Przyrostowy Projekt Portalu — Zaokrąglenia i Głębokość Wizualna

## Cel ćwiczenia (Projekt Przewodni Capstone)
Wzbogacisz semestralny portal usługowo-handlowy o nowoczesne obramowania, zaokrąglenia (`border-radius`) oraz cienie (`box-shadow`), zachowując architekturę Box Model i rygorystyczny kontrakt selektorów DOM.

## Instrukcja wykonania
1. W pliku `style.css`:
   * Dla kart usługowych o klasie `.karta-uslugi` zdefiniuj: `border: 1px solid #e2e8f0;`, zaokrąglenie `border-radius: 12px;` oraz miękki cień `box-shadow: 0 6px 16px rgba(0, 0, 0, 0.06);`.
   * Dla nagłówka sekcji usług ustaw dolną linię akcentową: `border-bottom: 3px solid #0284c7;`.
   * Dla przycisku `#btn-oblicz` nadaj zaokrąglenie `border-radius: 8px;`, usunięcie domyślnej ramki (`border: none;`) oraz wyrazisty cień: `box-shadow: 0 4px 12px rgba(2, 132, 199, 0.35);`.
   * Dla kontenera kalkulatora i podsumowania `#wynik` ustaw zaokrąglenie `border-radius: 10px;`, lewe obramowanie akcentowe `border-left: 5px solid #0284c7;` oraz cień `box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);`.
   * Zachowaj regułę stanu `.ukryty` sterującą widocznością za pomocą `display: none;`.
2. Zapewnij pełną zgodność z kontraktem selektorów DOM (`#tytul-portalu`, `#usluga`, `#btn-oblicz`, `#wynik`, `.karta-uslugi`, `.aktywny`, `.ukryty`).

## Treść do wpisania
* Tytuł portalu (`#tytul-portalu`): `Portal Usługowo-Techniczny IT-Partner`
* Podtytuł: `Autoryzowane wsparcie infrastruktury serwerowej i sieciowej`
* Karta 1: `Audyt Bezpieczeństwa IT` | Opis: `Testy penetracyjne, analiza podatności i raport zgodności z normami.` | Cena: 450 zł
* Karta 2: `Konfiguracja Chmury Hybrydowej` | Opis: `Wdrożenie chmury prywatnej z replikacją i automatycznym backupem.` | Cena: 890 zł
* Formularz wyceny: Wybór usługi (`#usluga`), Przycisk (`#btn-oblicz`): `Oblicz szacowany koszt`
