# Zadanie 7: Panel narzędziowy z przyciskami funkcyjnymi

## Opis zadania
Projektowanie zaawansowanego paska narzędziowego z przyciskami akcji użytkownika, mikrointerakcjami oraz różnicowaniem stanów.

## Treść do wpisania
* Przycisk Akcji 1: "Pobierz Raport"
* Przycisk Akcji 2: "Udostępnij Wyniki"
* Przycisk Akcji 3: "Drukuj Zestawienie"
* Przycisk Akcji 4: "Usuń Wpis"

## Instrukcja wykonania krok po kroku
1. Zbuduj pasek narzędziowy `.pasek-narzedzi` zawierający przyciski funkcyjne.
2. Przyciski standardowe (`.btn-narzedzie`):
   - `display: inline-block`, `padding: 8px 16px`, `font-size: 14px`, tło `#f8fafc`, ramka `1px solid #cbd5e1`, `border-radius: 4px`, kolor `#334155`.
   - Na `:hover` tło `#e2e8f0`, ramka `#94a3b8`.
   - Na `:active` tło `#cbd5e1`.
3. Przycisk niebezpieczny (`.btn-usun`):
   - Ramka `1px solid #f87171`, kolor `#dc2626`, tło białe.
   - Na `:hover` tło `#fef2f2`, ramka `#dc2626`.
   - Na `:active` tło `#fee2e2`.
4. Zadbaj o estetyczny `:focus` z `outline-offset: 2px` dla każdego elementu.
