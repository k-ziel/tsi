# Zadanie 4: Hierarchia i warianty przycisków w UI

## Opis zadania
Budowa spójnego systemu przycisków: główny (primary), pomocniczy (secondary), obrysowy (outline) oraz zablokowany (.btn-zablokowany).

## Treść do wpisania
* Przycisk główny: "Zatwierdź i Zapłać"
* Przycisk pomocniczy: "Zapisz Kopię Roboczą"
* Przycisk obrysowy: "Wróć do Koszyka"
* Przycisk zablokowany: "Funkcja Niedostępna"

## Instrukcja wykonania krok po kroku
1. Zdefiniuj bazową klasę `.btn` z: `display: inline-block`, `padding: 10px 22px`, `font-size: 15px`, `font-weight: 600`, `border-radius: 5px`, `cursor: pointer`, `text-decoration: none`.
2. Wariant `.btn-primary`: tło `#16a34a`, tekst biały, ramka `2px solid #16a34a`. W `:hover` tło `#15803d`.
3. Wariant `.btn-secondary`: tło `#475569`, tekst biały, ramka `2px solid #475569`. W `:hover` tło `#334155`.
4. Wariant `.btn-outline`: tło przezroczyste, tekst `#16a34a`, ramka `2px solid #16a34a`. W `:hover` tło `#16a34a` i tekst biały.
5. Wariant `.btn-zablokowany`: tło `#cbd5e1`, tekst `#94a3b8`, ramka `2px solid #cbd5e1`, kursor `cursor: not-allowed`, wyłączenie kliknięć `pointer-events: none`.
