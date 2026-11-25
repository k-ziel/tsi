# Szybka Ściąga Składniowa — Moduł 08: Jednostki Względne i Widoczność

---

## 1. Zestawienie Jednostek w CSS3

```css
/* 1. Jednostka rem (zawsze względem elementu <html>, domyślnie 1rem = 16px) */
body {
  font-size: 1rem;       /* 16px */
  padding: 1.5rem;       /* 24px */
}

h1 {
  font-size: 2rem;       /* 32px */
  margin-bottom: 0.75rem; /* 12px */
}

/* 2. Jednostka em (dla font-size względem rodzica, dla paddingu względem WŁASNEGO font-size) */
.przycisk {
  font-size: 1.25rem;   /* 20px */
  padding: 0.5em 1em;   /* góra/dół: 10px, boki: 20px */
}

/* 3. Jednostki viewportu (okna przeglądarki) */
.hero-sekcja {
  width: 100%;           /* bezpieczna pełna szerokość (nie używaj 100vw z suwakiem!) */
  min-height: 50vh;      /* co najmniej 50% wysokości widocznego okna */
}
```

---

## 2. Funkcja `calc()` — Matematyka w CSS

```css
/* Reguła żelazna: spacje wokół + oraz - są OBOWIĄZKOWE! */
.kolumna-trzy {
  width: calc((100% - 2rem) / 3);
  margin-right: 1rem;
}

.kolumna-trzy:last-child {
  margin-right: 0;
}

/* Odejście od krawędzi kontenera */
.pasek-boczny {
  width: 280px;
}

.zawartosc-glowna {
  width: calc(100% - 300px);
}
```

---

## 3. Trójkąt Widoczności w CSS

```css
/* 1. Całkowite wycięcie z makiety (0px x 0px, przesuwa inne elementy) */
.ukryty {
  display: none;
}

/* 2. Ukrycie wizualne z zachowaniem miejsca (zapobiega drganiom układu) */
.rezerwuj-miejsce {
  visibility: hidden;
}

/* Przywrócenie widoczności wybranego dziecka: */
.rezerwuj-miejsce .pokaz-mnie {
  visibility: visible;
}

/* 3. Płynne przenikanie przezroczystością */
.element-zanikajacy {
  opacity: 0;
  transition: opacity 0.3s ease;
  pointer-events: none; /* zabezpieczenie przed przypadkowym kliknięciem! */
}

.element-zanikajacy.widoczny {
  opacity: 1;
  pointer-events: auto;
}
```
