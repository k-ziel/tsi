# Pomoc Dostępna: Stylowanie odnośników i tworzenie przycisków

Materiał przygotowany w formie prostych instrukcji krok po kroku.

---

## Słowniczek podstawowych pojęć
* **Odnośnik (link):** Element `<a>`, który po kliknięciu przenosi na inną stronę.
* **Pseudoklasa:** Specjalny dopisek w CSS (np. `:hover`), który włącza styl tylko w określonym momencie.
* **:hover (najechanie):** Styl, gdy myszka znajduje się nad przyciskiem.
* **:active (kliknięcie):** Styl w momencie, gdy trzymasz wciśnięty lewy przycisk myszy.
* **:focus (zaznaczenie):** Styl, gdy najedziesz na element klawiszem Tab.
* **display: inline-block:** Polecenie, które pozwala nadawać odnośnikowi marginesy i padding jak przyciskowi.

---

## Krok 1: Jak usunąć domyślne podkreślenie linku?
1. Wybierz znacznik `a` w pliku `style.css`.
2. Wpisz polecenie `text-decoration: none;`.
3. Podkreślenie zniknie.

---

## Krok 2: Jak zmienić link w wyglądający przycisk?
Wykonaj następujące kroki w klasie przycisku:
1. Dodaj `display: inline-block;` (aby przycisk przyjął odstępy).
2. Dodaj `padding: 12px 24px;` (odstęp tekstu od krawędzi).
3. Dodaj `background-color: #2563eb;` (kolor tła przycisku).
4. Dodaj `color: #ffffff;` (biały kolor tekstu).
5. Dodaj `border-radius: 6px;` (zaokrąglone rogi).
6. Dodaj `cursor: pointer;` (kursor zmienia się w łapkę).

---

## Krok 3: Jak dodać reakcję na najechanie myszką?
```css
.przycisk:hover {
  background-color: #1d4ed8; /* Ciemniejszy odcień niebieskiego */
}
```

---

## Krok 4: Jak zapewnić widoczność dla klawiatury (Klawisz Tab)?
```css
.przycisk:focus {
  outline: 3px solid #2563eb;
  outline-offset: 3px;
}
```
