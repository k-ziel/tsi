# Teoria: Jednostki Względne, Funkcja calc() i Trójkąt Widoczności w CSS3
## Kwalifikacja INF.03 — Część Kliencka (Frontend & Narzędzia)
### Przedmiot: Projektowanie stron internetowych | Semestr 2 (Moduł 08)

---

## 1. System Jednostek w CSS3: Bezwzględne vs Względne

W kaskadowych arkuszach stylów każda wartość liczbowa określająca wymiary pudełka, wielkość czcionki, margines czy położenie wymaga podania jednostki (jedynym wyjątkiem jest wartość `0`).

Jednostki w CSS dzielimy na dwie fundamentalne kategorie:

```
┌────────────────────────────────────────────────────────────────────────┐
│                          JEDNOSTKI W CSS                               │
├──────────────────────────────────────┬─────────────────────────────────┤
│         JEDNOSTKI BEZWZGLĘDNE        │        JEDNOSTKI WZGLĘDNE       │
├──────────────────────────────────────┼─────────────────────────────────┤
│ • px (piksel CSS, 1/96 cala)         │ • % (względem rodzica w DOM)    │
│ • cm, mm, in (fizyczne — do druku)   │ • em (względem rodzica/własnego)│
│ • pt, pc (typograficzne — do druku)  │ • rem (względem roota: <html>)  │
│                                      │ • vw, vh, vmin, vmax (viewport) │
└──────────────────────────────────────┴─────────────────────────────────┘
```

### A. Jednostka bezwzględna: Piksel CSS (`px`)
- **Definicja:** Piksel CSS nie jest fizycznym pikselem matrycy monitora, lecz znormalizowaną jednostką kątową odpowiadającą $1/96$ cala przy typowej odległości wzroku od ekranu.
- **Zalety:** Daje projektantowi pełną, geometryczną kontrolę nad grubościami obramowań (`border: 1px solid`) czy precyzyjnymi cieniami (`box-shadow: 0 4px 6px`).
- **Wady (Bariera dostępności cyfrowej — WCAG 2.1):** Jeśli wielkość tekstu na stronie zostanie zdefiniowana w `px` (np. `p { font-size: 14px; }`), część starszych przeglądarek lub trybów czytania uniemożliwia osobie słabowidzącej przeskalowanie tekstu za pomocą ustawień systemowych.

### B. Jednostka procentowa (`%`)
- Jednostka procentowa odnosi się zawsze do **wartości tej samej właściwości u bezpośredniego rodzica blokowego**.
- Dla właściwości poziomej (`width: 50%`) oznacza połowę szerokości obszaru zawartości (*content-box*) rodzica.
- **Kluczowa pułapka wysokości (`height: 100%`):**
  Deklaracja `height: 100%` na elemencie zadziała **wyłącznie wtedy**, gdy jego rodzic ma jawnie zdefiniowaną wysokość (w `px`, `vh` lub innym ustalonym rozmiarze). Jeśli rodzic ma domyślne `height: auto`, przeglądarka nie wie, z jakiej wartości wyliczyć procent, i deklaracja `height: 100%` jest po prostu ignorowana!

---

## 2. Jednostki Typograficzne: `em` kontra `rem`

Rozumienie różnicy pomiędzy `em` a `rem` jest jednym z najczęściej testowanych zagadnień na egzaminie zawodowym INF.03.

```
                    ┌─────────────────────────┐
                    │      <html> (Root)      │ <── rem odnosi się ZAWSZE tutaj!
                    └────────────┬────────────┘
                                 │
                    ┌────────────▼────────────┐
                    │    Rodzic (np. <aside>) │ <── em dla font-size bierze wartość stąd
                    └────────────┬────────────┘
                                 │
                    ┌────────────▼────────────┐
                    │  Element potomny (np. p)│ <── em dla padding/margin bierze
                    └─────────────────────────┘     wartość z WŁASNEGO font-size!
```

### A. Jednostka `em` (Element Relative)
1. **Dla właściwości `font-size`:** $1\text{em}$ oznacza wielkość czcionki **bezpośredniego rodzica**. Jeśli rodzic ma `font-size: 16px`, to `2em` dziecka = $32\text{px}$.
2. **Dla właściwości pudełkowych (`padding`, `margin`, `width`):** $1\text{em}$ oznacza wielkość czcionki **tego samego (własnego) elementu**!
   ```css
   .przycisk {
     font-size: 20px;
     padding: 0.5em 1em; /* góra/dół: 10px, boki: 20px */
   }
   ```
   *Zaleta:* Zmiana wielkości tekstu przycisku automatycznie i proporcjonalnie powiększa jego dopełnienie wewnętrzne.

#### ⚠️ Groźna pułapka kaskadowego mnożenia `em` (Compounding Trap):
Jeśli w zagnieżdżonej liście zadeklarujemy:
```css
ul li {
  font-size: 1.2em; /* 120% rodzica */
}
```
Wtedy:
- Poziom 1: $16\text{px} \times 1.2 = 19.2\text{px}$
- Poziom 2: $19.2\text{px} \times 1.2 = 23.04\text{px}$
- Poziom 3: $23.04\text{px} \times 1.2 = 27.65\text{px}$
Tekst w podpunktach staje się gigantyczny i niszczy makietę strony!

### B. Jednostka `rem` (Root Element Relative) — Złoty Standard
- Jednostka `rem` odnosi się **ZAWSZE do elementu głównego dokumentu: `<html>`**, niezależnie od tego, jak głęboko w strukturze DOM znajduje się dany element.
- Domyślna wartość `font-size` dla `<html>` w przeglądarkach wynosi $16\text{px}$:
  - $1\text{rem} = 16\text{px}$
  - $1.5\text{rem} = 24\text{px}$
  - $2\text{rem} = 32\text{px}$
  - $0.75\text{rem} = 12\text{px}$
- **Dlaczego `rem` to fundament dostępności cyfrowej?**
  Gdy użytkownik z wadą wzroku ustawi w przeglądarce domyślny rozmiar tekstu na $24\text{px}$, wówczas $1\text{rem}$ automatycznie staje się równe $24\text{px}$, a cała typografia serwisu skaluje się harmonijnie bez żadnych błędów.

---

## 3. Jednostki Okna Przeglądarki: Viewport Units (`vw`, `vh`, `vmin`, `vmax`)

Jednostki te uniezależniają wymiary elementu od jego przodków w drzewie DOM i odnoszą się bezpośrednio do rozmiaru widocznego obszaru okna przeglądarki (*viewport*):

| Jednostka | Definicja | Przykładowe zastosowanie |
|---|---|---|
| `1vw` (*viewport width*) | 1% aktualnej szerokości okna przeglądarki | Skalowanie nagłówków lub elastyczne odstępy |
| `1vh` (*viewport height*) | 1% aktualnej wysokości okna przeglądarki | Sekcje powitalne Hero na pełną wysokość ekranu |
| `1vmin` (*viewport minimum*) | 1% z **mniejszego** wymiaru okna (min z szerokości i wysokości) | Kwadratowe widżety, które muszą mieścić się na ekranie pionowym i poziomym |
| `1vmax` (*viewport maximum*) | 1% z **większego** wymiaru okna (max z szerokości i wysokości) | Tła dekoracyjne pokrywające cały ekran |

### ⚠️ Pułapka poziomego paska przewijania (`100vw`):
Nigdy nie definiuj głównego kontenera strony jako `width: 100vw`.
Jednostka `100vw` obejmuje całą szerokość ekranu **wraz z pionowym paskiem przewijania** przeglądarki (o szerokości ok. 15–17px w systemie Windows). W rezultacie strona staje się szersza niż dostępna przestrzeń robocza i na dole pojawia się nieestetyczny poziomy pasek przewijania (`overflow-x`).
- **Złota reguła:** Do pełnej szerokości kontenera używaj `width: 100%`, a jednostkę `vh` rezerwuj dla wysokości (`min-height: 100vh`).

---

## 4. Funkcja Matematyczna `calc()` w CSS3

Funkcja `calc()` pozwala na wykonywanie dynamicznych obliczeń matematycznych w czasie renderowania strony. Jej największą siłą jest możliwość **mieszania jednostek różnych kategorii**, np. procentów i pikseli:

```css
.kolumna {
  width: calc(100% - 40px);
}
```

### A. Dostępne operatory:
- `+` (dodawanie)
- `-` (odejmowanie)
- `*` (mnożenie — co najmniej jeden argument musi być czystą liczbą bez jednostki, np. `calc(10px * 2)`)
- `/` (dzielenie — dzielnik musi być czystą liczbą bez jednostki, np. `calc(100% / 3)`)

### ⚠️ Błąd krytyczny CKE: Żelazna reguła spacji wokół operatorów `+` i `-`:
W funkcji `calc()` operatory dodawania (`+`) oraz odejmowania (`-`) **MUSZĄ być bezwzględnie oddzielone spacjami z obu stron**:

```css
/* ❌ BŁĄD SKŁADNIOWY — przeglądarka całkowicie ignoruje regułę! */
width: calc(100%-20px); 
margin-left: calc(50%+10px);

/* ✔️ POPRAWNA SKŁADNIA: */
width: calc(100% - 20px);
margin-left: calc(50% + 10px);
```
*Dlaczego?* W języku CSS znak myślnika (`-`) jest dozwolonym znakiem w nazwach identyfikatorów i właściwości (np. `font-size`, `-20px`). Bez spacji przeglądarka traktuje ciąg `%-20px` jako nierozpoznany identyfikator, unieważniając całą regułę!

---

## 5. Trójkąt Widoczności w CSS: `display: none` vs `visibility: hidden` vs `opacity: 0`

Jednym z najważniejszych sprawdzianów dojrzałości programisty frontendu jest świadome operowanie trzema różnymi mechanizmami ukrywania zawartości:

```
                          TRÓJKĄT WIDOCZNOŚCI
                                  ▲
                                 / \
                                /   \
          PRZEPŁYW DOKUMENTU   /     \   INTERAKTYWNOŚĆ
         (Zajmowanie miejsca) /       \  (Klikalność / Zdarzenia)
                             /         \
                            /___________\
                               WIDZIALNOŚĆ
                             (Piksele na ekranie)
```

### Tabela Komparatywna Właściwości:

| Właściwość i wartość | Czy zajmuje miejsce w układzie strony? | Czy reaguje na kliknięcia i zdarzenia myszy? | Czy jest odczytywany przez czytniki ekranu (a11y)? | Płynne animacje z `transition`? | Wpływ na elementy potomne |
|---|:---:|:---:|:---:|:---:|---|
| **`display: none;`** | ❌ **NIE**`<br>`(całkowicie wycięty z drzewa renderowania, 0px) | ❌ **NIE** | ❌ **NIE**`<br>`(niedostępny dla użytkownika) | ❌ **NIE**`<br>`(brak stanów pośrednich) | Wszystkie dzieci znikają bezwarunkowo |
| **`visibility: hidden;`** | ✔️ **TAK**`<br>`(zostawia puste pole o swoich wymiarach) | ❌ **NIE**`<br>`(kliknięcia przenikają pod spód) | ❌ **NIE** | ⚠️ Częściowo`<br>`(skok widoczności) | Dziecko z `visibility: visible` **staje się widoczne!** |
| **`opacity: 0;`** | ✔️ **TAK**`<br>`(zostawia pełną przestrzeń w układzie) | ✔️ **TAK!**`<br>`(element jest „niewidzialny”, ale wciąż klikalny) | ✔️ **TAK**`<br>`(czytnik odczyta treść) | ✔️ **TAK**`<br>`(płynne zanikanie `0.3s ease`) | Zmniejsza przezroczystość wszystkich dzieci |

### A. Kiedy stosować `display: none`?
- Gdy element ma przestać istnieć w makiecie: komunikaty o błędach, które po zniknięciu nie powinny zostawiać pustej dziury w formularzu.
- Zwijane zakładki (tabsy) i menu mobilne.

### B. Kiedy stosować `visibility: hidden`?
- Gdy zależy nam, aby układ strony **nie skakał (nie drgał)** przy pojawianiu się i znikaniu elementu.
- Przykład: wskaźnik ładowania danych w formularzu lub ikona sukcesu przy polu wprowadzania tekstu. Rezerwacja miejsca zapobiega przesuwaniu sąsiednich kontrolek!
- *Wyjątkowa cecha dziedziczenia:* Jeśli rodzic ma `visibility: hidden`, a jedno z dzieci otrzyma `visibility: visible`, to dziecko **zostanie wyświetlone na ekranie**!

### C. Kiedy stosować `opacity: 0`?
- Gdy chcemy uzyskać elegancki efekt płynnego wygaszania lub pojawiania się banera, okna modalnego czy dymka podpowiedzi (*tooltip*).
- **Uwaga na pułapkę „niewidzialnego przycisku”:** Ponieważ element z `opacity: 0` wciąż przechwytuje kliknięcia, może zablokować linki leżące pod nim! Aby temu zapobiec, łączy się go z właściwością `pointer-events: none;`.

---

## 6. Checklista Dobrego Kodu (CSS3 Box Model & Jednostki)

1. [ ] **Podstawa typograficzna:** Czy wielkości nagłówków i akapitów bazują na jednostce `rem` zamiast sztywnych `px`?
2. [ ] **Spacje w obliczeniach:** Czy w każdej funkcji `calc()` operatory `+` i `-` mają spacje z obu stron?
3. [ ] **Viewport bezpieczny:** Czy uniknięto deklaracji `width: 100vw` na elementach mogących wywołać poziomy pasek przewijania?
4. [ ] **Wysokość sekcji:** Czy dla sekcji powitalnych użyto `min-height: ...vh` zamiast sztywnego `height`, zabezpieczając treść przed ucięciem?
5. [ ] **Płynność layoutu:** Czy do alertów niepowodujących przeskoków makiety rozważono `visibility: hidden` zamiast `display: none`?
6. [ ] **Czystość kodu:** Brak `display: flex`, `display: grid`, stylów liniowych `style=""` oraz reguł `@media`.
