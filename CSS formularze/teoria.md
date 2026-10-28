# Teoria: wygląd formularzy

HTML formularza znasz z [`html/06_formularze`](../../html/06_formularze/) i [`html/07_formularze_pola`](../../html/07_formularze_pola/). Z działu 07 umiesz już ustawić `display: block` i szerokość w `%`. Ten dział odpowiada na pytanie: **jak pomalować formularz, żeby dało się go czytać i trafić w pole**.

Układ „etykieta obok pola na flexie” — semestr 3. Tu pola idą **jedno pod drugim**: etykieta nad inputem, odstęp marginesem, pełna szerokość w karcie.

`:focus` jest tu (fokus klawiatury / klik w pole). Przy zwykłych linkach w dziale 06 go nie wymagaliśmy — przy polach tekstowych fokus to część czytelności i dostępności.

Kolory marki na zadaniach: `#1e4d7b`, `#c9a227`, `#ffffff`, `#132f4d`.

---

## 1. HTML zostaje, malujesz CSS

W zadaniach formularz **już jest** w HTML (w tym klasa `pole` na polach tekstowych). Nie przerabiasz znaczników pod Flex. Nie stylizujesz checkboxa jak pola na imię — zostanie kwadracikiem systemowym.

Przycisk wysyłki: `<button type="submit">`. Nie myl z linkiem `a` — to inny element i inne domyślne style przeglądarki.

**Po co to jest.** Na egzaminie i na zajęciach oceniany jest CSS: padding, ramka, szerokość, fokus. Semantyka formularza jest gotowa — nie tracisz czasu na przepisanie HTML.

**Typowa pomyłka.** Dodać `display: flex` na `form` „żeby etykieta była obok”. Poza zakresem. Albo dać klasę `pole` checkboxowi i dziwić się kwadratowi rozciągniętemu na 100% szerokości.

---

## 2. Etykieta nad polem — `display: block`

`label` domyślnie jest inline. Żeby tekst etykiety był **nad** polem:

```css
label {
  display: block;
  margin-bottom: 4px;
  font-weight: 700;
}
```

Krótki margines pod etykietą oddziela napis od inputu, bez sklejania w jedną linię z sąsiadem.

**Po co to jest.** Formularz w kolumnie jest czytelny na wąskim ekranie i w karcie: najpierw nazwa pola, potem kontrolka. Bez Flexa i bez tabeli.

**Typowa pomyłka.** Zostawić `label` jako inline — etykieta staje obok pola albo „tańczy” w zależności od szerokości. Albo próbować układać etykietę przez `float` zamiast prostego `display: block`.

---

## 3. Pole na całą szerokość karty

```css
.pole {
  display: block;
  width: 100%;
  box-sizing: border-box;
  padding: 8px;
  border: 1px solid #1e4d7b;
  margin-bottom: 16px;
}
```

`width: 100%` + padding bez `border-box` **wychodzi poza** kartę — to ten sam problem co w dziale 05. Klasa `pole` jest na `input`, `textarea` i `select` — **nie** na checkboxie.

Ramka pola: cienka, `solid`, kolor z palety strony. Domyślna ramka przeglądarki bywa szara, zaokrąglona inaczej na każdym systemie i „wypada” z designu karty.

**Po co to jest.** Pola wyrównane do szerokości karty wyglądają jak jeden formularz, a nie jak wąskie systemowe kontrolki przy lewej krawędzi.

**Typowa pomyłka.** Pominąć `box-sizing: border-box` — pole z paddingiem wystaje poza `main` / kartę. Albo stylować `input` globalnie tak agresywnie, że psuje też checkbox / radio.

---

## 4. Karta formularza — `form` jako pudełko

Pola mogą być ładne, a cały formularz nadal „pływa” przy lewej krawędzi na całą szerokość. Często `form` dostaje własną **kartę**:

```css
form {
  width: 80%;
  max-width: 28rem;
  padding: 16px;
  border: 2px solid #1e4d7b;
  box-sizing: border-box;
}
```

`width: 80%` — względem rodzica (np. `main`). `max-width: 28rem` — na szerokim monitorze karta nie robi się kilometrowa. Padding i ramka + `border-box` — ta sama zasada co przy `.pole`.

Wyśrodkowanie karty w poziomie (gdy ma sens): `margin: 0 auto` (dział 05) — tylko jeśli polecenie tego wymaga.

**Po co to jest.** Formularz wygląda jak jeden spójny blok marki, a nie jak lista kontrolek rozciągnięta na cały ekran.

**Typowa pomyłka.** Dać `width: 80%` bez `max-width` — na dużym monitorze formularz jest nienaturalnie szeroki. Albo `width: 100%` na `form` i dziwić się, że „karta” nie widać. Albo Flex na `form` „żeby wyśrodkować” — poza zakresem tego działu.

---

## 5. Przycisk

```css
button {
  padding: 8px 16px;
  background-color: #1e4d7b;
  color: #ffffff;
  border: 0;
  font-size: 1rem;
}
button:hover {
  background-color: #132f4d;
}
```

To ten sam pomysł `:hover` co przy linkach, tylko na `button`: zmiana tła sygnalizuje klikalność. Kursor `pointer` nie jest wymagany (przycisk i tak jest klikalny) — jeśli polecenie go nie każe, nie musisz go dopisywać.

**Po co to jest.** Przycisk „Wyślij” ma wyglądać jak element marki, a nie jak szary systemowy kontroler. Hover potwierdza, że da się kliknąć.

**Typowa pomyłka.** Stylować `a` zamiast `button` albo odwrotnie. Albo zostawić domyślną grubą ramkę przycisku i walczyć z tłem, które „nie dochodzi do krawędzi” — często pomaga `border: 0` (gdy design tak zakłada).

---

## 6. `:focus` — widać, które pole jest aktywne

```css
.pole:focus {
  border-color: #c9a227;
  outline: 2px solid #c9a227;
}
```

Fokus pojawia się po kliknięciu w pole albo po dojściu klawiszem Tab. **Nie** zdejmuj `outline` na `none`, chyba że dajesz inną, **wyraźną** ramkę albo obrys fokusu. Uczeń z klawiaturą musi widzieć, gdzie jest.

**Po co to jest.** Bez widocznego fokusu formularz jest trudniejszy (i gorszy dostępnościowo). Złota ramka z palety łączy stan aktywny z resztą marki.

**Typowa pomyłka.** `outline: none` „bo brzydkie” i zero zamiennika — na sprawdzianie to błąd. Albo stylować `:focus` tylko na `a`, a pola tekstowe zostawić bez sygnału.

---

## 7. Czcionka w polu

`input` / `select` / `button` **nie biorą** automatycznie kroju z `body` — arkusz przeglądarki ustawia im własne fonty. Często:

```css
.pole,
button {
  font-family: inherit;
  font-size: 1rem;
}
```

`inherit` = weź z rodzica. To bywa extra / zestaw, niekoniecznie pierwsze zadanie dnia — ale warto wiedzieć, czemu pole „ma inny font niż reszta strony”.

`textarea` możesz podwyższyć: `min-height: 8rem;` (jednostka z działu 07), żeby pole na wiadomość nie wyglądało jak jedna linia.

**Po co to jest.** Formularz wizualnie należy do tej samej strony co nagłówki i akapity, a nie do domyślnego UI systemu.

**Typowa pomyłka.** Ustawić ładny font tylko na `body` i uznać temat za zamknięty — pola nadal wyglądają „obco”.

---

## 8. Czego ten dział świadomie nie uczy

| Temat | Gdzie |
| ----- | ----- |
| Etykieta obok pola (Flex / Grid) | semestr 3 |
| Walidacja JS, `required` jako temat CSS | HTML / później |
| Pełna stylizacja checkbox / radio | poza ścieżką podstawową |
| `:focus` na zwykłych linkach jako wymóg | nie ten dział (tu pola) |

Tu: kolumna, pełna szerokość, karta `form`, ramka, hover przycisku, widoczny fokus. Reszta layoutu formularza przyjdzie z Flexem.

---

## 9. Checklist przed oddaniem

- Etykieta `display: block` — nad polem, nie obok (bez Flexa na `form`).
- `.pole` ma `width: 100%`, padding, ramkę i **`box-sizing: border-box`**.
- Karta: na `form` często `width` + `max-width` + padding + ramka + `border-box`.
- Checkbox **bez** klasy `pole` (nie rozciągaj go jak pola tekstowego).
- `:focus` jest widoczny (kolor ramki i/lub `outline`) — nie `outline: none` w próżni.
- Hover na przycisku; przycisk to `button`, nie stylowany `a` „na niby”.
- Bez Flex/Grid na układ etykieta–pole.

---

## Dalej

Formularz w kolumnie jest czytelny i spójny z marką. Na ścieżce CSS dalej: Flex w semestrze 3 ([`09_flex`](../09_flex/)) — wtedy etykieta obok pola staje się naturalnym kolejnym krokiem layoutu.
