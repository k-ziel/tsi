# Zadanie 5: Cienie wewnętrzne (inset) i cienie wielowarstwowe

## Cel ćwiczenia
Nauczysz się stosować cień wklęsły (`inset`) do stylizowania paneli i pól wejściowych oraz łączyć cienie wielowarstwowe.

## Instrukcja wykonania
1. W pliku `style.css` dla wnęki wyświetlacza o klasie `.panel-wklewsly` ustaw:
   * Szerokość: `width: 320px;`, dopełnienie: `padding: 20px;`, margines dolny: `margin-bottom: 25px;`.
   * Tło: ciemnoszary grafit `#0f172a` oraz zielony kolor tekstu `#4ade80;`.
   * Krój czcionki o stałej szerokości: `font-family: monospace;`.
   * Cień wewnętrzny: `box-shadow: inset 0 3px 8px rgba(0, 0, 0, 0.6);`.
   * Zaokrąglenie: `border-radius: 6px;`.
2. Dla karty wielowarstwowej o klasie `.karta-wielowarstwowa` ustaw:
   * Szerokość: `width: 320px;`, dopełnienie: `padding: 20px;`, tło białe, zaokrąglenie `border-radius: 12px;`.
   * Dwa nałożone cienie po przecinku:
     `box-shadow: 0 2px 4px rgba(0, 0, 0, 0.06), 0 12px 24px rgba(0, 0, 0, 0.1);`

## Treść do wpisania
* Tytuł: `Zaawansowane Techniki Operowania Cieniem`
* Tekst wyświetlacza: `SYSTEM STATUS: OK | BUFFER: 1024 KB | TEMPERATURE: 41 C`
* Tekst karty: `Fotorealistyczny cień dwuwarstwowy łączy ostry cień przykrawędziowy z miękkim rozmyciem przestrzennym.`
