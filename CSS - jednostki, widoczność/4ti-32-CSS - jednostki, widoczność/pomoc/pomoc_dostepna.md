# Materiał Pomocniczy o Ułatwionej Percepcji — Moduł 08: Jednostki Względne i Widoczność

Materiały pomocnicze wspierające samodzielną realizację zadań laboratoryjnych, przygotowane z myślą o osobach preferujących jednoznaczny, dosłowny przekaz instruktażowy oraz ułatwioną percepcję kroków technologicznych.

---

## 1. Wyjaśnienie kluczowych pojęć w prostych słowach

### Czym różni się `px` od `rem`?
- **Piksel (`px`)** to sztywna linijka. Jeśli powiesz przeglądarce: *"ten tekst ma mieć 16 pikseli"*, to będzie miał 16 pikseli zawsze — nawet wtedy, gdy osoba niedowidząca poprosi przeglądarkę o powiększenie wszystkich liter na ekranie.
- **Jednostka `rem`** to guma krawiecka. Oznacza: *"weź standardowy rozmiar liter ze strony i pomnóż go"*. Domyślnie $1\text{rem} = 16\text{px}$. Jeśli wpiszesz $2\text{rem}$, tekst będzie dwa razy większy ($32\text{px}$). Gdy użytkownik powiększy litery w przeglądarce, Twoja strona powiększy się razem z nimi.

### Dlaczego jednostka `em` bywa niebezpieczna?
Jednostka `em` patrzy na swojego bezpośredniego rodzica. Jeśli w liście zagnieżdżonej każdy kolejny podpunkt będzie miał `1.5em`, to podpunkty będą stawać się coraz większe (jak śnieżna kula), aż rozepchną stronę. Dlatego do wielkości liter prawie zawsze używamy `rem`.

### Dlaczego funkcja `calc()` wymaga spacji przy minusie i plusie?
W języku CSS myślnik jest częścią słów (np. `font-size`, `border-radius`). Jeśli napiszesz `100%-20px` bez spacji, przeglądarka myśli, że to jedno długie, dziwne słowo i nie wie, co z nim zrobić. Gdy wstawisz spacje: `100% - 20px`, przeglądarka od razu widzi odejmowanie.

### Trzy sposoby ukrywania — który wybrać?
1. **Chcesz, żeby element całkiem zniknął i inne rzeczy przesunęły się na jego miejsce?**
   Wybierz: `display: none;` (tak ukrywamy np. zamknięte okienka lub nieaktywne zakładki).
2. **Chcesz, żeby element zniknął, ale zostawił puste miejsce, żeby reszta strony nie skakała?**
   Wybierz: `visibility: hidden;` (tak ukrywamy np. wskaźnik ładowania formularza).
3. **Chcesz, żeby element powoli i płynnie się pojawił za pomocą animacji?**
   Wybierz: `opacity: 0;` (pamiętaj, aby dodać `pointer-events: none;`, bo przezroczysty element wciąż można przez przypadek kliknąć).

---

## 2. Krok po kroku: Jak napisać poprawne obliczenie w `calc()`

1. Napisz słowo `calc` i otwórz nawias okrągły: `calc(`.
2. Wpisz pierwszą wartość (np. szerokość kontenera): `100%`.
3. Zrób spację, wpisz znak minusa lub plusa, i zrób kolejną spację: ` - `.
4. Wpisz drugą wartość (np. szerokość marginesu): `40px`.
5. Zamknij nawias: `)`.
6. Całość wygląda tak: `width: calc(100% - 40px);`.
