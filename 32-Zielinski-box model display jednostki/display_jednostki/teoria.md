# Teoria: `display` i jednostki

Znasz pudełko (`width`, padding, margin) i wygląd odnośników. Ten dział łączy dwa pytania: **czy element stoi w rzędzie, czy zaczyna nową linię** (`display`) oraz **jakie jednostki oprócz `px`** możesz podać przy rozmiarze.

Bez zmiany `display` często „nie działa” `width` na `span` albo padding na linku w menu wygląda krzywo. Procent i `rem` pozwalają opisać szerokość względem rodzica i pismo względem korzenia dokumentu — nadal bez mediów RWD jako tematu.

Flex i Grid — semestr 3. `vw` / `vh` — [`14_rwd`](../14_rwd/). Tu ich nie uczysz jako głównego narzędzia. `display: none` omawiamy krótko na końcu (extra / sprawdzian).

Kolory marki na zadaniach: `#1e4d7b`, `#c9a227`, `#ffffff`, `#132f4d`.

---

## 1. Domyślne zachowanie

| Typ | Przykłady | Co robi |
| --- | --------- | ------- |
| `block` | `p`, `h1`, `div`, `header`, `main` | nowa linia, szerokość na całą dostępną; `width`, padding i margin działają ze wszystkich stron |
| `inline` | `a`, `span`, `strong`, `em` | w linii z tekstem; **`width` / `height` się nie biorą**; pionowy margin praktycznie nie działa |

Dlatego `span { width: 80px; }` **nic nie zmienia**, dopóki nie zmienisz `display`. Element inline nie buduje pełnego „pudełka” pod szerokość w ten sam sposób co blok.

**Po co to jest.** Zanim ustawisz rozmiar, musisz wiedzieć, **jakim typem** jest element. Inaczej godzinami szukasz błędu w `width`, a problem leży w `display`.

**Typowa pomyłka.** Ustawić `width` / `height` na `span` albo zwykłym `a` i uznać, że CSS „nie działa”. Działa — tylko inline ignoruje te właściwości.

---

## 2. `display: block`

```css
.sala {
  display: block;
  width: 80px;
  padding: 4px 8px;
  border: 2px solid #1e4d7b;
}
```

Albo odnośniki jeden pod drugim (bez Flexa):

```css
nav a {
  display: block;
}
```

Każdy `a` zajmuje całą dostępną szerokość i schodzi do nowej linii — klasyczna kolumna linków.

**Po co to jest.** Chcesz, żeby inline’owy znacznik zachowywał się jak pudełko: miał `width`, pełny padding i stał w osobnej linii (etykieta, znacznik sali, pozycja menu pod sobą).

**Typowa pomyłka.** Dać `display: flex` na `nav`, „bo tak się robi menu”. Na tej ścieżce Flex jest poza zakresem — tu wystarczy `block` (kolumna) albo `inline-block` (rząd).

---

## 3. `display: inline-block`

W **rzędzie** jak inline, ale `width`, `height`, padding i margin jak w bloku. Typowe **menu przed Flexem**:

```css
nav a {
  display: inline-block;
  padding: 8px 16px;
  text-decoration: none;
  color: #1e4d7b;
}
nav a:hover {
  color: #c9a227;
}
```

Padding na zwykłym inline `a` w pionie bywa ucięty albo dziwnie się składa z linią tekstu — `inline-block` daje przewidywalne pudełko wciąż w jednym rzędzie.

Nie ustawiasz tu `display: flex` na `nav`.

**Po co to jest.** Punkty menu mają mieć wygodny obszar kliknięcia (padding) i stać obok siebie, bez zawijania każdego linku do osobnej linii jak przy `block`.

**Typowa pomyłka.** Zostawić `a` jako inline, dodać duży padding i dziwić się nierównym wysokościom / nachodzeniu na sąsiadów. Albo użyć `float` zamiast `inline-block` — inny, starszy temat, niepotrzebny na tych zadaniach.

---

## 4. Procenty (`%`)

```css
main {
  width: 80%;
  box-sizing: border-box;
}
```

`%` liczy się od **szerokości rodzica**, nie od „ekranu w próżni”. `80%` na `main` w `body` to w przybliżeniu 80% szerokości treści strony (rodzica).

Na paddingu wartość w `%` też jest liczona od **szerokości** rodzica (nie od wysokości) — na razie `%` dawaj głównie na **`width`**.

Przy `width: 80%` + padding pamiętaj o `box-sizing: border-box` z działu 05 — inaczej pudełko łatwo wystaje poza rodzica.

**Po co to jest.** Blok ma zajmować część szerokości kontenera i **skalować się** razem z nim, bez wpisywania sztywnych 900px.

**Typowa pomyłka.** Myśleć, że `%` to zawsze procent okna przeglądarki. To procent rodzica — jeśli rodzic jest wąski, 80% też będzie wąskie.

---

## 5. `rem`

`1rem` = rozmiar czcionki na **`html`** (korzeń dokumentu). Domyślnie przeglądarka ≈ `16px`, więc `1rem` ≈ 16px, `1.5rem` ≈ 24px.

```css
html {
  font-size: 16px;
}
body {
  font-size: 1rem;
}
h1 {
  font-size: 1.75rem;
}
```

Zmiana `html { font-size: … }` skaluje **wszystkie** `rem` na stronie. Dlatego `rem` jest wygodniejszy niż mieszanka samych `px` przy późniejszym dopasowaniu pisma — tu uczysz się **zapisu i sensu**, nie zapytań `@media`.

**Po co to jest.** Nagłówki i tekst bazowy trzymasz w jednej „skali” względem korzenia. Później jedna zmiana na `html` rusza całą typografię opartą o `rem`.

**Typowa pomyłka.** Używać `rem` jako głównego tematu do **wszystkiego** (marginesy, ramki 1px) albo mylić `rem` z `%`. Ramkę 1–2px często zostawiasz w `px`; `rem` naturalnie pasuje do **pisma**.

---

## 6. `em` (krótko)

`em` liczy się od **czcionki tego elementu** (często dziedziczonej z rodzica).

```css
p {
  font-size: 1rem;
}
p strong {
  font-size: 1.25em; /* 1.25 × rozmiar p */
}
```

Gdy zagnieżdżasz `em` w `em`, rozmiary się **mnożą** i łatwo przesadzić. Na arkuszu, jeśli masz wybór: **`rem`** na pismo, `%` na szerokość, `px` na cieniutką ramkę (1–2px).

**Po co to jest.** Lokalne skalowanie względem najbliższego kontekstu pisma (np. mocniejszy `strong` w akapicie) — bez ruszania całego `html`.

**Typowa pomyłka.** Budować całą stronę na zagnieżdżonych `em` i nie rozumieć, czemu w środku listy font jest gigantyczny. Na start preferuj `rem`.

---

## 7. `display: none` vs `visibility: hidden` (extra)

Gdy element ma **zniknąć**:

```css
.archiwum {
  display: none;
}
```

`display: none` — element **nie bierze udziału w układzie**: nie widać go i **nie zostaje dziura**. Sąsiedzi zsuwają się jakby go nie było.

```css
.archiwum {
  visibility: hidden;
}
```

`visibility: hidden` — element jest niewidoczny, ale **miejsce w flow zostaje** (pusta dziura o jego rozmiarze).

**Po co to jest.** Schowanie „archiwalnego” akapitu albo bloku, który nie ma się liczyć w układzie — na sprawdzianie zwykle chodzi o brak dziury, więc `display: none`.

**Typowa pomyłka.** Użyć `visibility: hidden`, gdy polecenie każe „schować i nie zostawiać luki”. Albo mylić z `opacity: 0` (też zostawia miejsce i bywa klikalne).

---

## 8. Czego ten dział świadomie nie uczy

| Temat | Gdzie |
| ----- | ----- |
| Flex / Grid | semestr 3 ([`09_flex`](../09_flex/) itd.) |
| `vw` / `vh`, media queries | [`14_rwd`](../14_rwd/) |
| `transition` / animacje | późniejsze działy |
| Formularze (`:focus`, `.pole`) | [`08_formularze`](../08_formularze/) |

Tu: trzy tryby `display` na co dzień + `%` / `rem` / krótko `em` + chowanie elementu (`none` vs `hidden`). Reszta layoutu i RWD przyjdzie później.

---

## 9. Checklist przed oddaniem

- `width` na `span` / `a` bez zmiany `display` → zwykle bez efektu; potrzebujesz `block` albo `inline-block`.
- Menu w jednym rzędzie + padding: `inline-block`, nie Flex.
- Menu w kolumnie: `display: block` na `a`.
- `%` = względem **rodzica**; `rem` = względem `html`; `em` = względem czcionki elementu / dziedziczenia.
- `box-sizing: border-box` przy `width: 80%` + padding — inaczej pudełko wystaje.
- Schować bez dziury: `display: none` (nie `visibility: hidden`).
- Ramka nadal może być w `px`; bez `display: flex` i bez `vw` / `vh` jako rozwiązania tego działu.

---

## Dalej

Wiesz, kiedy pudełko w ogóle przyjmuje `width`, i umiesz zapisać `%` oraz `rem`. Następny dział [`08_formularze`](../08_formularze/) — wygląd pól, etykiet, przycisku i `:focus` (pola jedno pod drugim, bez Flexa na formularzu).
