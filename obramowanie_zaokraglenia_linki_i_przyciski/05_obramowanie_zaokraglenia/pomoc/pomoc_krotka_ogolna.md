# Szybka Ściąga: Obramowania, Zaokrąglenia i Cienie CSS

## 1. Obramowanie (Border)
```css
border: 1px solid #cbd5e1;       /* Pełna ramka */
border-left: 4px solid #0284c7;  /* Lewa krawędź akcentowa */
border-bottom: 2px dashed #94a3b8;/* Dolna linia kreskowana */
border: none;                    /* Usunięcie obramowania */
```

## 2. Zaokrąglanie narożników (border-radius)
```css
border-radius: 8px;              /* Wszystkie rogi */
border-radius: 16px 0;           /* Przekątne narożniki */
border-radius: 50%;              /* Idealne koło (gdy width == height) */
border-top-left-radius: 12px;    /* Wybrany róg */
```

## 3. Cienie pudełek (box-shadow)
```css
/* Cień subtelny */
box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08);

/* Cień uniesienia (karta, przycisk) */
box-shadow: 0 10px 20px rgba(0, 0, 0, 0.12);

/* Cień wewnętrzny (wklęsły) */
box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.15);

/* Poświata (glow) */
box-shadow: 0 0 12px rgba(2, 132, 199, 0.5);
```
