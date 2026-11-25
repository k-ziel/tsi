# Kompendium Teoretyczne: Obramowania, Zaokrąglenia (border-radius) i Cienie (box-shadow)

## 1. Właściwości obramowania (Border)

### Składniki obramowania
Obramowanie w CSS definiują trzy składowe:
1. **Grubość (`border-width`):** np. `1px`, `2px`, `4px`, lub słowa kluczowe `thin`, `medium`, `thick`.
2. **Styl linii (`border-style`):**
   * `solid` – linia ciągła (najczęściej stosowana).
   * `dashed` – linia kreskowana (przerywana).
   * `dotted` – linia kropkowana.
   * `double` – linia podwójna (wymaga grubości co najmniej 3px).
   * `none` – brak ramki (usuwa domyślne ramki, np. w polach formularzy).
3. **Kolor (`border-color`):** nazwa barwy, HEX (`#0284c7`), RGB, RGBA.

### Zapis skrócony (*shorthand*)
Najczęściej stosuje się zapis skrócony łączący wszystkie trzy parametry:
```css
/* grubość styl kolor */
border: 2px solid #0284c7;
```

### Obramowania jednostronne
Obramowanie można nadać tylko wybranej krawędzi pudełka. Jest to podstawowa technika tworzenia eleganckich separatorów i lewych pasków wyróżnienia (*accent borders*):
```css
.karta-wyrozniona {
  border-left: 5px solid #2563eb; /* lewa krawędź akcentowa */
  border-bottom: 1px solid #cbd5e1; /* dolna linia oddzielająca */
}
```

---

## 2. Zaokrąglanie narożników (`border-radius`)

Właściwość `border-radius` pozwala zaokrąglać narożniki obramowania oraz przycinać tło elementu do zaokrąglonego kształtu.

### Składnia jedno-, dwu- i czterowartościowa
```css
/* Wszystkie 4 rogi jednakowo */
border-radius: 12px;

/* Przekątne: góra-lewo i dół-prawo: 15px | góra-prawo i dół-lewo: 0px */
border-radius: 15px 0;

/* Zgodnie z ruchem wskazówek zegara: góra-lewo, góra-prawo, dół-prawo, dół-lewo */
border-radius: 10px 20px 30px 40px;
```

### Właściwości dedykowane konkretnym narożnikom
* `border-top-left-radius: 15px;` – lewy górny róg
* `border-top-right-radius: 15px;` – prawy górny róg
* `border-bottom-right-radius: 15px;` – prawy dolny róg
* `border-bottom-left-radius: 15px;` – lewy dolny róg

### Tworzenie kół i owali (*Pill & Circle Shape*)
Gdy element ma **dokładnie taką samą szerokość i wysokość** (jest kwadratem), nadanie `border-radius: 50%;` tworzy idealne koło (technika stosowana do awatarów i ikon):
```css
.awatar {
  width: 80px;
  height: 80px;
  border-radius: 50%;
}
```

---

## 3. Cienie pudełek (`box-shadow`)

Właściwość `box-shadow` dodaje efekt głębi i uniesienia elementu ponad płaszczyznę strony.

### Składnia parametrów
```css
box-shadow: offset-x offset-y blur-radius spread-radius color;
```
1. **`offset-x` (wymagany):** Przesunięcie cienia w poziomie (wartości dodatnie w prawo, ujemne w lewo).
2. **`offset-y` (wymagany):** Przesunięcie cienia w pionie (wartości dodatnie w dół, ujemne w górę).
3. **`blur-radius` (opcjonalny, domyślnie 0):** Promień rozmycia cienia. Im większa wartość, tym cień jest bardziej miękki i rozmyty.
4. **`spread-radius` (opcjonalny, domyślnie 0):** Rozproszenie (powiększenie lub pomniejszenie) rozmiaru cienia.
5. **`color`:** Kolor cienia. **Dobra praktyka:** używanie barw z kanałem przezroczystości, np. `rgba(0, 0, 0, 0.1)`, zamiast twardej czerni.

### Przykłady profesjonalnych cieni
```css
/* Subtelny cień karty (nowoczesny UI) */
box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);

/* Wyrazisty cień uniesienia (efekt hover / modal) */
box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);

/* Cień wewnętrzny (efekt wklęsłości / wciśniętego przycisku) */
box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.2);

/* Cień wielowarstwowy (efekt fotorealistyczny) */
box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1), 0 10px 20px rgba(0, 0, 0, 0.05);
```

---

## 4. Dydaktyka: "Po co to jest?" oraz typowe pomyłki

### Po co to jest?
Współczesny interfejs internetowy (tzw. styl *Material Design* czy *Flat Design 2.0*) opiera się na hierarchii wizualnej budowanej za pomocą zaokrągleń i miękkich cieni. Elementy z cieniem sprawiają wrażenie zawieszonych bliżej użytkownika, co podświadomie sugeruje ich klikalność i ważność. Na egzaminie INF.03 zadania często wymagają precyzyjnego odwzorowania specyfikacji: np. zaokrąglenia narożników o dokładnie 15 pikseli, cienkiej ramki w kolorze podanym w HEX oraz cienia zdefiniowanego w wartościach pikselowych.

### Typowe pomyłki uczniów
> [!WARNING] Typowa pomyłka 1: Brak właściwości `border-style`
> Uczeń pisze: `border-width: 2px; border-color: red;` i dziwi się, że ramka się nie wyświetla. Domyślna wartość `border-style` wynosi `none`! Zawsze należy zdefiniować styl obramowania (lub użyć zapisu skróconego `border: 2px solid red;`).

> [!WARNING] Typowa pomyłka 2: Twardy, czarny cień psujący estetykę
> Uczeń wpisuje `box-shadow: 5px 5px 5px black;`. Taki cień wygląda archaicznie i przytłacza treść. Zawsze stosuj przezroczystość alfa: `box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);`.

> [!WARNING] Typowa pomyłka 3: Próba zrobienia koła z prostokąta
> Uczeń nadaje `border-radius: 50%` elementowi o wymiarach `width: 200px; height: 100px;`. Wynikiem będzie spłaszczona elipsa, a nie koło. Koło powstaje tylko wtedy, gdy szerokość i wysokość są identyczne!
