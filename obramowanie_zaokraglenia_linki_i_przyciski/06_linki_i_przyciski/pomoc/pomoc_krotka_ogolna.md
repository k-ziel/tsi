# Pomoc Podręczna: Stylowanie odnośników i przycisków CSS

## 1. Reguła LVHA (Kolejność w CSS)
Zawsze deklaruj stany odnośników w tej kolejności:
```css
a:link    { color: #0284c7; text-decoration: none; }
a:visited { color: #64748b; }
a:hover   { color: #0369a1; text-decoration: underline; }
a:active  { color: #0c4a6e; }
```

## 2. Dostępność klawiatury (:focus)
Nigdy nie zostawiaj samego `outline: none`. Zastosuj wyraźny zarys:
```css
a:focus, button:focus {
  outline: 3px solid #2563eb;
  outline-offset: 3px;
}
```

## 3. Przycisk ze znacznika <a>
```css
.przycisk {
  display: inline-block;
  padding: 10px 20px;
  background-color: #2563eb;
  color: #ffffff;
  text-decoration: none;
  border-radius: 6px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  cursor: pointer;
}
.przycisk:hover {
  background-color: #1d4ed8;
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
}
.przycisk:active {
  background-color: #1e40af;
  box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.2);
}
```
