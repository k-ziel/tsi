# Kompendium Teoretyczne: Stylowanie odnośników, pseudoklasy (:hover, :active, :focus) i przyciski UI

## 1. Domyślny wygląd odnośnika i jego ograniczenia

Domyślnie element `<a>` w przeglądarkach internetowych posiada:
* Kolor niebieski dla odnośników nieodwiedzonych,
* Kolor fioletowy dla odnośników odwiedzonych,
* Ciągłe podkreślenie (`text-decoration: underline`),
* Wyświetlanie liniowe (`display: inline`).

Jako element ściśle liniowy (`display: inline`), odnośnik **ignoruje** pionowe marginesy (`margin-top`, `margin-bottom`) oraz sztywne wymiary (`width`, `height`). Aby przekształcić go w pełnoprawny przycisk lub kafelek, konieczna jest zmiana właściwości `display` na `inline-block` lub `block`.

---

## 2. Reguła LVHA – kolejność pseudoklas w kaskadzie

Pseudoklasy odnośników muszą być zdefiniowane w arkuszu stylów w **ściśle określonej kolejności**, zapamiętywanej akronimem **LVHA**:

```css
/* 1. Link - odnośnik nieodwiedzony */
a:link {
  color: #0284c7;
  text-decoration: none;
}

/* 2. Visited - odnośnik już odwiedzony przez użytkownika */
a:visited {
  color: #64748b;
}

/* 3. Hover - kursor myszy znajduje się nad odnośnikiem */
a:hover {
  color: #0369a1;
  text-decoration: underline;
}

/* 4. Active - moment kliknięcia (przycisk myszy wciśnięty) */
a:active {
  color: #0c4a6e;
}
```

### Dlaczego kolejność ma kluczowe znaczenie?
Wszystkie te pseudoklasy mają **dokładnie taką samą specyficzność selektora** (jedna pseudoklasa = waga 0-1-0). Zgodnie z zasadą kaskadowości, gdy dwa selektory mają identyczną wagę, **wygrywa ten, który w kodzie CSS znajduje się niżej**:
* Gdyby reguła `:hover` została umieszczona przed `:visited`, odwiedzony link nigdy nie zmieniłby wyglądu po najechaniu myszą, ponieważ deklaracja `:visited` nadpisałaby `:hover`.
* Gdyby `:active` zostało umieszczone przed `:hover`, efekt wciśnięcia przycisku nigdy nie byłby widoczny, bo stan najechania (`:hover`) przykryłby stan kliknięcia.

---

## 3. Dostępność cyfrowa i pseudoklasa :focus

Wielu użytkowników (oraz egzaminatorzy sprawdzający dostępność cyfrową WCAG 2.1) nawiguje po stronach internetowych za pomocą klawiatury (klawisz **Tab** do przechodzenia i **Enter** do aktywacji).

### Obsługa fokusu (`:focus`)
```css
/* Prawidłowe stylowanie fokusu klawiatury */
.btn:focus {
  outline: 3px solid #2563eb;
  outline-offset: 3px;
}
```

> [!IMPORTANT] Żelazna zasada dostępności WCAG
> **Nigdy nie usuwaj konturu bez podania zamiennika!** Zapis `outline: none;` lub `outline: 0;` bez alternatywnego wyróżnienia (np. wyraźnego `box-shadow` lub obramowania) jest kardynalnym błędem dostępności, uniemożliwiającym osobom korzystającym z klawiatury orientację, gdzie aktualnie znajduje się kursor.

Właściwość `outline-offset` pozwala odsunąć linię konturu od krawędzi elementu na zewnątrz (np. o 2px lub 3px), dzięki czemu zarys nie zlewa się z obramowaniem przycisku.

---

## 4. Budowa przycisku wezwania do działania (Call To Action – CTA)

Przycisk tworzymy najczęściej ze znacznika `<a>` (gdy prowadzi do innej podstrony) lub `<button>` (gdy wywołuje akcję w formularzu).

### Anatomia profesjonalnego przycisku:
```css
.btn-glowny {
  display: inline-block;        /* Pozwala nadać padding i trzymać przycisk w linii */
  padding: 12px 24px;          /* Wygodna strefa kliknięcia (min. 44px wysokości wg WCAG) */
  font-family: Arial, sans-serif;
  font-size: 16px;
  font-weight: bold;
  text-decoration: none;        /* Usunięcie podkreślenia linku */
  color: #ffffff;               /* Wysoki kontrast tekstu */
  background-color: #2563eb;   /* Wyrazisty kolor tła */
  border: 2px solid #2563eb;    /* Obramowanie w kolorze tła */
  border-radius: 6px;           /* Zaokrąglenie narożników */
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); /* Delikatny cień */
  cursor: pointer;              /* Wskaźnik łapki */
}

/* Stan najechania myszą */
.btn-glowny:hover {
  background-color: #1d4ed8;   /* Lekkie przyciemnienie */
  border-color: #1d4ed8;
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15); /* Efekt uniesienia */
}

/* Stan wciśnięcia przycisku */
.btn-glowny:active {
  background-color: #1e40af;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);   /* Efekt spłaszczenia cienia */
}
```

---

## 5. System wariantów przycisków w UI

W profesjonalnych interfejsach stosuje się hierarchię przycisków:
1. **Primary (Główny):** pełne wyraziste tło, przyciąga uwagę do najważniejszej akcji (np. „Kup teraz”, „Zarejestruj się”).
2. **Secondary (Pomocniczy):** stonowane tło (np. szare, neutralne), dla akcji pobocznych (np. „Wróć”, „Anuluj”).
3. **Outline / Ghost (Obrysowy):** przezroczyste tło z widoczną ramką; po najechaniu wypełnia się kolorem.
4. **Zablokowany (.zablokowany):** wyszarzone tło, zablokowany kursor (`cursor: not-allowed;`), zmniejszona przezroczystość (`opacity: 0.5;`).

---

## 6. Dydaktyka: Typowe pomyłki uczniów

> [!WARNING] Typowa pomyłka 1: Próba nadania paddingu pionowego linkowi bez display: inline-block
> Uczeń pisze: `a { padding: 20px; }` i nie zmienia właściwości `display`. Link nałoży się na sąsiednie linie tekstu, psując czytelność akapitu. Zawsze należy dodać `display: inline-block;`!

> [!WARNING] Typowa pomyłka 2: Zła kolejność reguł w arkuszu (np. :hover przed :visited)
> Skutkuje to tym, że po kliknięciu w link przestaje on reagować na najechanie myszą. Zawsze pamiętaj o kolejności LVHA!

> [!WARNING] Typowa pomyłka 3: Wyłączenie obrysu bez zamiennika (outline: none)
> Skutkuje to całkowitą utratą dostępności klawiaturowej. Uczeń na egzaminie traci punkty za błędy dostępności.
