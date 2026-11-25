# Zadanie 6: Nowoczesna karta ofertowa w standardzie CKE

## Cel ćwiczenia
Zintegrujesz obramowanie, zaokrąglenie narożników oraz cień pudełka w kompletnym komponencie karty ofertowej typowym dla arkuszy egzaminacyjnych CKE INF.03.

## Instrukcja wykonania
1. W pliku `style.css` dla karty o klasie `.karta-ofertowa` ustaw:
   * Szerokość: `width: 340px;`.
   * Centrowanie w poziomie: `margin: 30px auto;`.
   * Dopełnienie: `padding: 25px;`.
   * Tło: białe `#ffffff`.
   * Obramowanie: `1px solid #e2e8f0;`.
   * Zaokrąglenie: `border-radius: 12px;`.
   * Cień: `box-shadow: 0 8px 20px rgba(0, 0, 0, 0.08);`.
2. Dla etykiety planu o klasie `.plan-tag` ustaw `display: inline-block;`, `padding: 4px 12px;`, `border-radius: 20px;`, tło jasnoniebieskie `#e0f2fe`, kolor ciemnoniebieski `#0369a1` oraz pogrubienie.
3. Dla ceny w klasie `.cena-glowna` zdefiniuj rozmiar `font-size: 28px;`, kolor granatowy `#0f172a` oraz wytłuszczenie.
4. Dla przycisku o klasie `.btn-aktywuj` ustaw:
   * `display: block; width: 100%;`
   * Dopełnienie: `padding: 12px;`
   * Tło niebieskie `#0284c7`, kolor biały, brak obramowania (`border: none;`).
   * Zaokrąglenie: `border-radius: 8px;`.
   * Cień przycisku: `box-shadow: 0 4px 12px rgba(2, 132, 199, 0.35);`.

## Treść do wpisania
* Etykieta planu: `Najpopularniejszy`
* Nazwa pakietu: `Hosting Bezpieczny SSD`
* Parametry: `50 GB przestrzeni dyskowej NVMe, nielimitowany transfer, bezpłatny certyfikat SSL.`
* Cena: `199 zł / rok`
* Przycisk: `Aktywuj konto hostingowe`
