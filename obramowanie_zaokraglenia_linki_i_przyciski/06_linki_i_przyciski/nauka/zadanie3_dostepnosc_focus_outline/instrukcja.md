# Zadanie 3: Dostępność cyfrowa i pseudoklasa :focus

## Opis zadania
Projektowanie widocznego i estetycznego wskaźnika fokusu dla klawiatury przy użyciu właściwości outline i outline-offset zgodnie z wytycznymi WCAG 2.1.

## Treść do wpisania
* Przycisk 1: "Pobierz Specyfikację PDF"
* Przycisk 2: "Zobacz Przykłady Rozwiązań"
* Komunikat pomocniczy: "Naciśnij klawisz Tab na klawiaturze, aby przetestować widoczność obrysu fokusu."

## Instrukcja wykonania krok po kroku
1. Ostyluj przyciski klasy `.btn-pobierz` z `display: inline-block`, `padding: 10px 20px`, tłem `#0f766e` i białym tekstem.
2. Zaprojektuj stan `:focus`:
   - Ustaw wyraźny obrys: `outline: 3px solid #0d9488`.
   - Ustaw odstęp obrysu: `outline-offset: 4px`.
3. Upewnij się, że obrys nie jest usuwany przez `outline: none`.
4. Dodaj stan `:hover` z kolorem tła `#115e59`.
