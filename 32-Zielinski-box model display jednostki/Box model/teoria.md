# Teoria: box model

W [`04_obramowanie`](../04_obramowanie/) nauczyłeś się rysować kreskę wokół elementu (`border`). Ten dział odpowiada na inne pytanie: **skąd się bierze rozmiar pudełka** i **jak zrobić odstęp** — wewnątrz ramki (`padding`) oraz między pudełkami (`margin`).

Wyobraź sobie kartę jak pudełko: w środku leży treść, wokół treści jest „powietrze”, potem ramka, a na zewnątrz przerwa do sąsiada. Bez paddingu tekst oblepia kreskę. Bez marginesu sekcje sklejają się ze sobą.

Jednostka na tych zajęciach to **`px`**. Procenty, `rem` i zmiana `display` (czy element stoi w rzędzie, czy w kolumnie) — dział [`07_display_jednostki`](../07_display_jednostki/). Tu nie są tematem.

Kolory marki na zadaniach: `#1e4d7b`, `#c9a227`, `#ffffff`, `#132f4d`.

---

## 1. Cztery warstwy

Od środka na zewnątrz:

| Warstwa | Właściwość | Co to jest |
| ------- | ---------- | ---------- |
| treść | `width` / `height` | miejsce na tekst / obraz |
| padding | `padding` | odstęp **wewnątrz**, między treścią a ramką |
| border | `border` | kreska (dział 04) |
| margin | `margin` | odstęp **na zewnątrz**, między pudełkami |

Padding nie jest marginesem. Padding = powietrze **w** ramce. Margin = przerwa **między** kartami albo sekcjami.

**Po co to jest.** Na stronie budujesz kartę, `main` albo nagłówek: najpierw wiesz, gdzie jest treść, gdzie „oddech” przy krawędzi, a gdzie dziura do następnego bloku. Bez tej mapy łatwo mylić właściwości i poprawiać „coś, byle odstęp był”.

**Typowa pomyłka.** Dać `margin` zamiast `padding` (albo odwrotnie), bo „i tak jest odstęp”. Margines odpycha sąsiada; padding odsuwa treść od własnej ramki. Na sprawdzianie liczy się właściwa warstwa, nie sam efekt wizualny „jest przerwa”.

---

## 2. `width` (i `height`)

```css
.karta {
  width: 400px;
  border: 2px solid #1e4d7b;
}
```

Domyślnie `width` to szerokość **treści** (obszaru na tekst), a nie całego pudełka z paddingiem i ramką — o tym jest `box-sizing` w sekcji 5.

`height` ustawia wysokość treści. Jeśli tekst się nie mieści, wystaje poza pudełko. Na razie rzadko ruszasz `height`: treść sama „pcha” blok w dół. Sztywna wysokość bywa potrzebna przy pustym kolorowym prostokącie albo gdy polecenie tak każe.

**Po co to jest.** Karta ma mieć konkretną szerokość (np. 320px albo 400px), żeby układ nie rozjeżdżał się „na całą stronę” albo nie był wąski jak kolumna tekstu.

**Typowa pomyłka.** Ustawić tylko `border` i oczekiwać, że pudełko samo będzie „karty wielkości”. Bez `width` (albo bez treści, która rozpycha) blok często zajmuje całą dostępną szerokość rodzica — to normalne zachowanie bloku, nie błąd przeglądarki.

---

## 3. `padding`

Dzięki paddingowi tekst **nie oblepia** ramki.

```css
main {
  border: 2px solid #1e4d7b;
  padding: 16px;
}
```

Skrót — ten sam schemat co przy `margin`:

| Zapis | Znaczenie |
| ----- | --------- |
| `padding: 16px;` | wszystkie boki |
| `padding: 8px 24px;` | góra/dół, lewo/prawo |
| `padding: 8px 16px 24px 32px;` | góra, prawo, dół, lewo (jak zegar) |

Jedna strona: `padding-top`, `padding-right`, `padding-bottom`, `padding-left`. Na arkuszu zwykle wystarczą jedna albo dwie wartości w skrócie.

Ramka z działu 04 jest tu po to, żeby **widać było** padding: bez kreski „powietrze w środku” bywa niewidoczne na jednolitym tle.

**Po co to jest.** W `main`, karcie albo przycisku treść ma oddychać od krawędzi. Czytelnik nie czyta tekstu przyklejonego do linii ramki.

**Typowa pomyłka.** Duży `margin` wewnątrz „żeby tekst odjechał od ramki”. Margines jest na zewnątrz — odsuwa sąsiadów, a nie treść od własnej kreski. Albo cztery osobne `padding-top` itd., gdy wystarczy `padding: 8px 24px`.

---

## 4. `margin`

```css
header {
  margin-bottom: 24px;
}
```

Przerwa **między** `header` a `main`. Ramki się nie sklejają.

Skrót ten sam schemat co padding (`16px`, `8px 24px`, cztery wartości w kolejności zegara).

Przeglądarka daje `body` własny margines (kilka pikseli). Często na stronie:

```css
body {
  margin: 0;
}
```

Potem **Ty** dodajesz odstępy tam, gdzie chcesz — świadomie, a nie „bo przeglądarka coś zostawiła”.

### Wyśrodkowanie bloku: `margin: 0 auto`

Gdy element ma **ustawiony `width`** (np. `400px`) i jest blokiem, możesz wyśrodkować go w poziomie:

```css
main {
  width: 400px;
  margin: 0 auto;
  border: 2px solid #1e4d7b;
  padding: 16px;
  box-sizing: border-box;
}
```

`0` = górny i dolny margines zerowy (albo inna wartość, jeśli potrzebujesz odstępu w pionie). `auto` na lewo i prawo „zjada” wolne miejsce **po równo** — karta staje na środku okna / rodzica.

To **nie** to samo co `text-align: center` na `body`: `text-align` wyrównuje **tekst (i inline) wewnątrz** bloku, a nie przesuwa całego pudełka o stałej szerokości.

**Po co to jest.** Karta treści, formularz albo `main` ma stać na środku strony przy znanym `width` — bez Flexa i bez `position`.

**Typowa pomyłka.** Samo `margin: auto` bez `width` — blok i tak zajmuje 100% szerokości, więc „auto” nie ma czego dzielić. Albo `text-align: center` na rodzicu zamiast `margin: 0 auto` na samym bloku. Ujemnego marginesu na tych zajęciach nie używasz.

Dwa pionowe marginesy sąsiadów czasem się „zwijają” w jeden (collapse) — na egzaminie nie musisz tego liczyć w pikselach. Odstęp między sekcjami dawaj świadomie, np. tylko `margin-bottom` na górnej.

**Po co to jest (margin ogólnie).** Sekcje, karty i bloki mają oddzieloną przestrzeń. Strona nie wygląda jak jeden sklejony prostokąt.

**Typowa pomyłka (margin ogólnie).** Padding na `header`, żeby „odsunąć main” — to powiększa wnętrze nagłówka, a niekoniecznie czytelnie oddziela sekcje. Albo zostawić domyślny margines `body` i dziwić się białej ramce wokół całej strony.

---

## 5. `box-sizing`

Domyślnie (`content-box`): `width: 400px` + padding + border = pudełko **szersze** niż 400px.

```css
.karta {
  width: 320px;
  padding: 16px;
  border: 4px solid #1e4d7b;
  box-sizing: border-box;
}
```

Przy `border-box` **320px to całość** (treść + padding + ramka). Padding „wchodzi do środka”, nie rozpycha na zewnątrz. Łatwiej zaplanować układ: „karta ma 320px” znaczy naprawdę 320px na ekranie.

Na witrynie często na wszystkich elementach:

```css
* {
  box-sizing: border-box;
}
```

Na zajęciach wystarczy na konkretnej karcie / `main`, jeśli polecenie tak każe.

**Po co to jest.** Dodajesz padding albo grubszą ramkę i nadal chcesz, żeby szerokość karty była tą z polecenia — bez ręcznego odejmowania pikseli.

**Typowa pomyłka.** Ustawić `width: 320px`, `padding: 16px` i `border: 4px` bez `border-box`, a potem dziwić się, że karta jest szersza niż sąsiad albo wystaje z kontenera. Druga pomyłka: myśleć, że `box-sizing` „usuwa” padding — nie usuwa; zmienia tylko, **co** oznacza liczba przy `width`.

---

## 6. Czego ten dział świadomie nie uczy

| Temat | Gdzie |
| ----- | ----- |
| `%`, `rem`, `em` | [`07_display_jednostki`](../07_display_jednostki/) |
| `display` (`block` / `inline` / `inline-block`) | [`07_display_jednostki`](../07_display_jednostki/) |
| Wygląd odnośników (`a`, `:hover`) | [`06_linki`](../06_linki/) |
| Ujemny margin jako główny temat | poza ścieżką / później |

Tu budujesz pudełko w pikselach. Inne jednostki i zachowanie w linii pojawią się, gdy pudełko już rozumiesz.

---

## 7. Checklist przed oddaniem

- Padding = w środku ramki; margin = na zewnątrz między elementami.
- `width` (i inne rozmiary w tym dziale) w **`px`**. Bez `%` i `rem` jako tematu rozwiązania.
- Skrót paddingu/marginesu: 1 albo 2 wartości na arkuszu zwykle wystarczą.
- `box-sizing: border-box` — gdy `width` ma oznaczać **całe** pudełko (treść + padding + border).
- Wyśrodkowanie karty o stałym `width`: `margin: 0 auto` (nie `text-align: center` na `body`).
- `border` wolno i warto — żeby **widać było** padding.
- Nie ma zmiany `display` ani jednostek z działu 07, jeśli polecenie tego nie każe.

---

## Dalej

Masz rozmiar i odstępy. Następny dział [`06_linki`](../06_linki/) — jak malować odnośnik (`color`, podkreślenie, stany `:hover` / `:visited`). Jednostki `%` / `rem` i `display` — dopiero [`07_display_jednostki`](../07_display_jednostki/).
