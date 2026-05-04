# Współtworzenie repozytorium

To repozytorium zawiera statyczną stronę internetową. Większość prac
utrzymaniowych polega na edycji treści: aktualizacji strony głównej,
dodawaniu podstron projektów oraz zarządzaniu obrazami i linkami.

## Struktura repozytorium

- `index.html` zawiera sekcje strony głównej
- `styles.css` zawiera wspólne style strony głównej i podstron projektów
- `script.js` zawiera logikę strony głównej, np. efekt pisania i renderowanie projektów
- `projects.js` zawiera listę projektów pokazywanych na stronie głównej
- `more-about-projects/` zawiera podstrony poszczególnych projektów
- `more-about-projects/project-template.html` jest punktem startowym dla nowych podstron projektów
- `images/` zawiera wszystkie obrazy używane na stronie

## Podgląd lokalny

Ponieważ strona jest statyczna, możesz sprawdzić ją lokalnie na kilka prostych sposobów:

1. Otwórz `index.html` bezpośrednio w przeglądarce, jeśli chcesz szybko sprawdzić tekst lub układ.
2. Jeśli ścieżki względne zachowują się inaczej w Twojej przeglądarce, uruchom katalog przez prosty lokalny serwer statyczny.
3. Przed publikacją sprawdź stronę główną i każdą edytowaną podstronę zarówno na szerokości desktopowej, jak i mobilnej.

## Tutorial: dodawanie nowego projektu

To najczęstsze zadanie przy utrzymaniu tego repozytorium.

### 1. Utwórz podstronę projektu

Skopiuj `more-about-projects/project-template.html` do nowego pliku w tym samym katalogu.

Przykład:

- `more-about-projects/lidar-lab.html`
- `more-about-projects/new-project-name.html`

Zastąp pola tymczasowe właściwym tytułem, opisem, akapitami i opcjonalnymi sekcjami ze zdjęciami.

### 2. Dodaj obrazy projektu

Utwórz osobny folder w `images/` dla nowego projektu.

Przykład:

- `images/lidar-lab/`
- `images/new-project-name/`

Używaj czytelnych nazw plików i trzymaj powiązane zasoby w jednym miejscu.

### 3. Poprawnie podłącz obrazy

W podstronach znajdujących się w `more-about-projects/` ścieżki do obrazów powinny zwykle wyglądać tak:

```html
<img src="../images/new-project-name/example.jpg" alt="Opis zdjęcia" />
```

Wspólne ikony i favicon na podstronach projektów korzystają ze ścieżek liczonych od katalogu głównego, na przykład:

```html
<link rel="stylesheet" href="/styles.css" />
<link rel="icon" href="/images/icons/icon.png" type="image/png" />
```

### 4. Dodaj kartę projektu na stronie głównej

Otwórz `projects.js` i dodaj nowy obiekt do tablicy `projects`:

```js
{
  title: "Tytuł projektu.",
  description: "Krótki opis na stronę główną.",
  path: "new-project-name",
}
```

Wartość `path` musi odpowiadać nazwie pliku bez rozszerzenia `.html`.

Jeśli plik to `more-about-projects/new-project-name.html`, użyj:

```js
path: "new-project-name"
```

### 5. Sprawdź generowany przycisk

Przycisk na stronie głównej jest generowany automatycznie przez `script.js`.
Jeśli pole `path` jest obecne, strona wyświetli przycisk `Zobacz więcej.`, który prowadzi do podstrony projektu.

### 6. Zweryfikuj efekt

Sprawdź, czy:

- nowa karta pojawia się na stronie głównej
- przycisk otwiera właściwą podstronę
- wszystkie obrazy się ładują
- strona wygląda poprawnie na urządzeniach mobilnych
- nie ma uszkodzonych linków

## Tutorial: aktualizacja istniejącego projektu

Jeśli podstrona projektu już istnieje:

1. Edytuj odpowiedni plik w `more-about-projects/`
2. Zaktualizuj tekst, obrazy i nagłówki według potrzeb
3. Jeśli trzeba zmienić także krótki opis na stronie głównej, zaktualizuj odpowiedni wpis w `projects.js`
4. Ponownie sprawdź podstronę i kartę projektu na stronie głównej

## Konwencje ścieżek

To repozytorium używa dwóch najczęstszych stylów zapisu ścieżek:

- Pliki w katalogu głównym, takie jak `index.html`, używają ścieżek w rodzaju `styles.css` lub `images/...`
- Pliki w `more-about-projects/` zwykle używają `../images/...` dla treści strony oraz `/styles.css` dla wspólnych zasobów

Przy dodawaniu nowej treści najlepiej skopiować sposób zapisu ścieżek z najbardziej podobnego istniejącego pliku.

## Konwencje treści

- Opisy na stronie głównej powinny być na tyle krótkie, aby dobrze działały jako karty
- Pełne informacje o projekcie umieszczaj na dedykowanej podstronie
- Dodawaj sensowne atrybuty `alt` do obrazów
- Korzystaj z istniejącej typografii i układów, chyba że celowo wprowadzasz nowy styl sekcji
- Nazwy plików i folderów zapisuj małymi literami i z myślnikami

## Lista kontrolna przed publikacją

Przed wypchnięciem zmian sprawdź:

- strona główna ładuje się poprawnie
- edytowane podstrony projektów ładują się poprawnie
- ścieżki do obrazów są poprawne
- przyciski `Zobacz więcej.` prowadzą do właściwych stron
- układ działa poprawnie na urządzeniach mobilnych
- w treści nie został żaden tekst tymczasowy z `project-template.html`
