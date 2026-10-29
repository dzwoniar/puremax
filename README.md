# Puremax — landing page usług czyszczenia

Statyczny prototyp strony usług czyszczenia elewacji, dachów i kostki brukowej. Główny scenariusz to przejście od prezentacji efektu oraz pakietów do prośby o wycenę i próbę czyszczenia 1 m².

**Status:** demo interfejsu. Formularz i wybór zdjęcia nie przesyłają danych ani plików.

## Co jest zaimplementowane

- Responsywny landing page z ofertą, procesem współpracy, pakietami, referencjami i FAQ.
- Suwak „przed / po” obsługiwany myszą i dotykiem.
- Formularz wyceny z wyborem rodzaju usługi i lokalnym wyborem zdjęcia.
- Wyświetlanie nazwy wybranego pliku i zmiana stanu przycisku po zatwierdzeniu formularza.
- Rozwijane odpowiedzi FAQ oraz dolne CTA dla urządzeń mobilnych.

## Technologia i architektura

Projekt używa HTML, CSS i JavaScript bez frameworka. Wszystkie style i skrypty są osadzone w [index.html](index.html). Zewnętrznie pobierane są fonty DM Sans i Instrument Serif przez Google Fonts. Nie ma paczek npm, bundlera, API ani bazy danych.

```text
.
├── index.html   # sekcje strony, style, suwak, FAQ i formularz
└── README.md
```

## Uruchomienie lokalne

Wymagane: Git, Python 3 i współczesna przeglądarka.

```sh
git clone https://github.com/dzwoniar/puremax.git
cd puremax
python -m http.server 8000
```

Wejdź na [http://localhost:8000](http://localhost:8000). Na Windows można uruchomić serwer poleceniem `py -3 -m http.server 8000`. Zatrzymanie: `Ctrl+C`. Nie jest potrzebna instalacja zależności; bez połączenia z internetem fonty zastąpią lokalne kroje pisma.

## Przepływ interakcji

Suwak zmienia `clip-path` warstw prezentacji oraz pozycję uchwytu. `toggleFaq()` steruje otwartą odpowiedzią. `handleFile()` odczytuje wyłącznie nazwę pliku wybranego w przeglądarce. `handleSubmit()` zatrzymuje wysłanie formularza, pokazuje komunikat sukcesu i blokuje przycisk; nie wykonuje żądania sieciowego.

## Granice demonstracji

- Linki telefoniczne i polityka prywatności zawierają wartości zastępcze.
- Wybrany plik nie jest przesyłany, a komunikat „Wysłano” stanowi wyłącznie stan demonstracyjny.
- Sekcje efektów i referencji prezentują zawartość prototypu. Repozytorium nie potwierdza wyników usług ani działania procesu wyceny.
- Aby obsługiwać rzeczywiste zapytania, trzeba podłączyć endpoint do `handleSubmit()`, przesyłanie plików i walidację danych po stronie serwera.

Repozytorium nie zawiera automatycznych testów. Przy zmianach warto sprawdzić suwak na myszce i ekranie dotykowym, FAQ, wybór zdjęcia oraz widok mobilny.
