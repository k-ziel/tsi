# Karta Pomocy Dostępnej: Krok po kroku do Obramowań i Cieni CSS

*Dokument przygotowany z myślą o uczniach preferujących uporządkowaną, jednoznaczną procedurę działania krok po kroku.*

---

### Instrukcja 1: Jak dodać ramkę do elementu?
1. Otwórz plik `style.css`.
2. Wpisz regułę dla elementu:
   ```css
   .karta {
     border: 2px solid #0284c7;
   }
   ```
   * Liczba `2px` to grubość.
   * Słowo `solid` to linia ciągła.
   * Kod `#0284c7` to kolor ramki.

---

### Instrukcja 2: Jak zaokrąglić rogi pudełka?
1. W regule elementu dopisz właściwość `border-radius`:
   ```css
   .karta {
     border-radius: 12px;
   }
   ```
2. Jeśli chcesz zrobić idealne koło:
   * Ustaw jednakową szerokość i wysokość: `width: 80px; height: 80px;`.
   * Ustaw: `border-radius: 50%;`.

---

### Instrukcja 3: Jak dodać miękki, profesjonalny cień?
1. W regule elementu dopisz:
   ```css
   .karta {
     box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
   }
   ```
   * `0` – cień nie ucieka w lewo ani w prawo.
   * `8px` – cień przesuwa się lekko w dół.
   * `16px` – cień jest miękko rozmyty.
   * `rgba(0, 0, 0, 0.1)` – kolor to delikatna, 10% czerń.
