# Zadanie 1: Stany odnośników w regule LVHA

## Opis zadania
Ostylowanie listy odnośników nawigacyjnych z zachowaniem reguły kaskadowości LVHA (:link, :visited, :hover, :active), usunięciem domyślnego podkreślenia i jego przywróceniem po najechaniu.

## Treść do wpisania
* Odnośnik 1: "Strona Główna Portalu"
* Odnośnik 2: "Katalog Produktów i Usług"
* Odnośnik 3: "Odwiedzona Baza Wiedzy i FAQ"
* Odnośnik 4: "Kontakt z Doradcą Klienta"

## Instrukcja wykonania krok po kroku
1. W pliku `style.css` ostyluj listę odnośników w kontenerze `.menu-linkow`.
2. Zastosuj regułę LVHA:
   - `:link` – kolor tekstu #0284c7, brak podkreślenia (`text-decoration: none`).
   - `:visited` – kolor tekstu #64748b.
   - `:hover` – kolor tekstu #0369a1, podkreślenie dolne (`text-decoration: underline`).
   - `:active` – kolor tekstu #b91c1c.
3. Ustaw dla odnośników `font-family: Arial, sans-serif` oraz rozmiar `font-size: 16px`.
