# Teoria: multimedia w HTML

Znasz już obrazy (`img`). Ten dział dotyczy **osadzania filmu, dźwięku i obcej strony** w dokumencie HTML. Na egzaminie INF.03 dostajesz pliki (np. `.mp4`, `.mp3`) w folderze obok HTML — tak samo tu: ścieżki **względne**, bez CSS.

---

## 1. Film — `<video>`

```html
<video src="media/film.mp4" controls width="320" height="180">
  Przeglądarka nie obsługuje odtwarzania wideo.
</video>
```

| Atrybut | Po co |
| ------- | ----- |
| `src` | Ścieżka do pliku (np. `media/film.mp4`). |
| `controls` | Pasek: play, głośność, pełny ekran. **Na zajęciach i na arkuszu prawie zawsze go wstawiasz** — bez niego film jest, ale uczeń / komisja nie odtworzy go wygodnie. |
| `width`, `height` | Rozmiar w pikselach (jak przy `img`). |
| `poster` | Obrazek **przed** odtworzeniem (okładka), np. `images/okladka.svg`. |
| `autoplay` | Start sam z siebie. Przeglądarki często **blokują** autoplay z dźwiękiem. |
| `muted` | Bez dźwięku. Para `autoplay` + `muted` ma szansę zadziałać. |
| `loop` | Powtarzanie od początku. |
| `preload` | Podpowiedź: `none` / `metadata` / `auto` — nie musisz jej używać na starcie. |

`<video>` **nie jest pusty** — ma znacznik zamykający `</video>`. Między znacznikami wstawiasz **tekst zapasowy** (gdy przeglądarka nie umie odtworzyć pliku).

Format na arkuszu: zwykle **MP4** (`video/mp4`). Inne (`webm`, `ogg`) rzadziej.

Nie wstawiaj `autoplay` z dźwiękiem na stronie szkolnej — zaskakuje i drażni. Jeśli arkusz każe autoplay, dodaj `muted` albo licz się z blokadą.

---

## 2. Dźwięk — `<audio>`

```html
<audio src="media/podcast.wav" controls>
  Przeglądarka nie obsługuje odtwarzania dźwięku.
</audio>
```

Działa analogicznie do `video`, tylko **nie ma** `poster`, `width` ani `height` (to nie jest obraz).

Na egzaminie częsty plik to **MP3**. W materiałach bywa też WAV — w `src` wpisujesz **dokładną nazwę z folderu**, nie zgadujesz rozszerzenia.

`controls` — tak samo: wstawiaj, chyba że treść zadania mówi inaczej.

---

## 3. Kilka plików: `<source>`

Zamiast `src` na `<video>` / `<audio>` możesz podać źródła wewnątrz:

```html
<video controls width="320">
  <source src="media/film.mp4" type="video/mp4" />
  <p>Przeglądarka nie obsługuje odtwarzania wideo.</p>
</video>
```

- Przeglądarka bierze **pierwszy** format, który umie.
- `type` to typ MIME (`video/mp4`, `audio/mpeg` dla MP3, `audio/wav` dla WAV).
- Tekst (lub link) **pod** `source`, nadal wewnątrz `video` / `audio`, to treść zapasowa.

Nie mieszaj: albo `src` na kontenerze, albo `source` w środku — nie oba na raz.

---

## 4. Podpis: `figure` i `figcaption`

Jak przy zdjęciu — film, dźwięk albo ramka mogą mieć podpis:

```html
<figure>
  <video src="media/film.mp4" controls></video>
  <figcaption>Relacja z dnia otwartego, 2026.</figcaption>
</figure>
```

`figcaption` opisuje **ten** materiał, nie całą stronę.

---

## 5. Osadzanie strony — `<iframe>`

`iframe` pokazuje **inną stronę** w ramce (mapa, film z serwisu, lokalny plik HTML).

```html
<iframe
  src="media/ramka.html"
  title="Repertuar tygodnia"
  width="400"
  height="240"
></iframe>
```

| Atrybut | Po co |
| ------- | ----- |
| `src` | Adres lub plik względny. |
| `title` | Krótki opis **dla czytników** (co jest w ramce). Nie mylić z `title` dokumentu w `head`. |
| `width`, `height` | Rozmiar ramki w pikselach. |

Na arkuszu bywa film z YouTube, np.:

```html
<iframe
  src="https://www.youtube.com/embed/IDENTYFIKATOR"
  title="Film instruktażowy"
  width="560"
  height="315"
  allowfullscreen
></iframe>
```

Na zajęciach **offline** osadzasz lokalny plik (`media/ramka.html`) — mechanizm ten sam, tylko `src` nie wymaga internetu.

Nie wstawiaj iframe bez `title`. Nie używaj `src` absolutnego z dysku (`C:\...`) — na egzaminie padnie.

`sandbox` ogranicza, co wolno stronie w ramce — na INF.03 zwykle nie jest wymagany.

---

## 6. Mapa obrazkowa — `<map>` i `<area>` (uzupełnienie)

Klikalne obszary na **jednym** obrazie (plan sali, mapa budynku). Na nowszych stronach rzadkie, na arkuszach nadal się zdarza.

```html
<img src="images/plan.png" alt="Plan sali: ekran i wejście" usemap="#plan-sali" width="400" height="160" />
<map name="plan-sali">
  <area shape="rect" coords="0,0,199,159" href="#ekran" alt="Ekran projekcyjny" />
  <area shape="rect" coords="200,0,399,159" href="#wejscie" alt="Wejście na salę" />
</map>
```

- `usemap="#nazwa"` na `img` musi się zgadzać z `name` na `map` (z kratką tylko w `usemap`).
- `shape`: `rect` (prostokąt), `circle`, `poly`.
- `coords` dla `rect`: `x1,y1,x2,y2` (lewy górny i prawy dolny róg, piksele obrazu).
- Każde `area` ma **`alt`** (jak `img`) oraz `href` (podstrona albo kotwica `#id`).

Współrzędne dostajesz w treści zadania albo mierzysz w edytorze grafiki. Nie zgaduj „na oko”, jeśli arkusz podaje liczby.

---

## 7. Ścieżki i porządek plików

Przykład katalogu zadania:

```
index.html
media/film.mp4
media/podcast.wav
media/ramka.html
images/okladka.svg
```

Jeśli `archiwum.html` leży **obok** `index.html`, obie strony używają tych samych ścieżek: `media/film.mp4`, nie `/media/film.mp4`.

Nie zmieniaj nazw plików z `media/` i `images/` — instrukcja podaje je dosłownie.

---

## 8. Semantyka wokół mediów

Multimedia wstawiasz w `main` (albo w `section` w `main`), nie w `head`.

Ramka i film nie zastępują `h1`. Najpierw nagłówek strony, potem odtwarzacz.

Stopka i `meta name="author"` — jak w poprzednich działach HTML.
