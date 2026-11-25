# Zadanie 7: Zestaw przycisków i plakietek z cieniami (Design Tokens)

## Cel ćwiczenia
Zbudujesz bibliotekę mikro-komponentów (przyciski akcji, odznaki, statusy) łączących zaokrąglenia i cienie w spójny miniaturowy Design System.

## Instrukcja wykonania
1. W pliku `style.css` dla bazowej klasy przycisku `.btn-systemowy` ustaw:
   * `display: inline-block;`, dopełnienie: `10px 20px;`, margines: `8px;`.
   * Brak obramowania (`border: none;`), zaokrąglenie: `border-radius: 8px;`.
   * Cień: `box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);`.
   * Wytłuszczenie: `font-weight: bold;`, kolor biały.
2. Dla wariantu podstawowego `.btn-glowny` ustaw tło ciemnoniebieskie `#0284c7` i cień błękitny `box-shadow: 0 4px 12px rgba(2, 132, 199, 0.4);`.
3. Dla wariantu sukcesu `.btn-sukces` ustaw tło zielone `#15803d` i cień zielony `box-shadow: 0 4px 12px rgba(21, 128, 61, 0.4);`.
4. Dla wariantu ostrzeżenia `.btn-alarm` ustaw tło czerwone `#dc2626` i cień czerwony `box-shadow: 0 4px 12px rgba(220, 38, 38, 0.4);`.
5. Dla pigułkowego wskaźnika statusu `.status-pill` ustaw `display: inline-block;`, `padding: 4px 14px;`, `border-radius: 9999px;`, tło żółte `#fef3c7`, kolor brązowy `#92400e` oraz cień `box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.1);`.

## Treść do wpisania
* Tytuł: `Biblioteka Komponentów Przyciskowych i Odznak`
* Przycisk główny: `Zapisz zmiany w projekcie`
* Przycisk sukcesu: `Zatwierdź zamówienie`
* Przycisk alarmu: `Usuń wpis z bazy`
* Wskaźnik statusu: `W trakcie synchronizacji`
