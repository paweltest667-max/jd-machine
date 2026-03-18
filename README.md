# 🚜 John Deere Machine Report Analyzer

Aplikacja webowa do generowania raportów PDF z danych telematycznych John Deere Operations Center.

![screenshot](docs/screenshot.png)

## ✨ Funkcje

- 📂 **Wgrywanie PDF** — przeciągnij plik lub wybierz z dysku
- 📊 **Wykresy interaktywne** — czas pracy, obciążenie silnika, zużycie miesięczne
- 🤖 **Analiza AI** — automatyczna analiza i rekomendacje (Claude Sonnet via Anthropic API)
- ⬇️ **Eksport PDF** — profesjonalny raport gotowy do druku

## 📋 Obsługiwane dane

Aplikacja odczytuje następujące sekcje z raportów John Deere:

| Sekcja | Dane |
|--------|------|
| Czas pracy | Praca / Bezczynność / Transport |
| Paliwo | Zużycie całkowite, średnie l/h, DEF |
| Silnik | RPM, obciążenie, temperatury |
| DPF | Poziom sadzy, czyszczenia |
| AutoTrac | Godziny prowadzenia |
| WOM | Tylny wał odbioru mocy |
| Miesięczne | Rozkład obciążenia silnika |

## 🚀 Uruchomienie

Aplikacja jest **w pełni front-endowa** — nie wymaga serwera ani instalacji.

### Opcja 1 — GitHub Pages (zalecane)

1. Zrób fork tego repozytorium
2. Przejdź do **Settings → Pages**
3. Ustaw źródło na `main` branch, folder `/` (root)
4. Aplikacja dostępna pod `https://[twój-login].github.io/jd-machine-report/`

### Opcja 2 — lokalnie

```bash
git clone https://github.com/[twój-login]/jd-machine-report.git
cd jd-machine-report
# Otwórz index.html w przeglądarce
open index.html
```

### Opcja 3 — dowolny hosting statyczny

Wystarczy wgrać plik `index.html` na dowolny hosting (Netlify, Vercel, itp.)

## 🔑 Klucz API Anthropic

Analiza AI używa **Anthropic API** (Claude Sonnet). Klucz API jest wstrzykiwany automatycznie przez infrastrukturę Claude.ai przy korzystaniu z aplikacji w środowisku Anthropic.

Jeśli chcesz uruchomić aplikację **poza** Claude.ai (np. lokalnie lub na własnym serwerze), musisz dodać własny klucz API:

1. Utwórz konto na [console.anthropic.com](https://console.anthropic.com)
2. Wygeneruj klucz API
3. W pliku `index.html` znajdź fragment:
   ```javascript
   headers: { 'Content-Type': 'application/json' },
   ```
   i dodaj:
   ```javascript
   headers: {
     'Content-Type': 'application/json',
     'x-api-key': 'sk-ant-TWÓJ_KLUCZ',
     'anthropic-version': '2023-06-01',
     'anthropic-dangerous-direct-browser-access': 'true'
   },
   ```

> ⚠️ Nie commituj klucza API do publicznego repozytorium.

## 🛠️ Technologie

- **Vanilla JS** — bez frameworków, brak zależności npm
- **PDF.js** — odczyt plików PDF w przeglądarce
- **jsPDF** — generowanie raportów PDF
- **Claude Sonnet API** — analiza AI
- **Google Fonts** — Syne + Space Mono

## 📁 Struktura projektu

```
jd-machine-report/
├── index.html        # Cała aplikacja (single-file)
├── README.md         # Ten plik
└── docs/
    └── screenshot.png  # Zrzut ekranu (opcjonalny)
```

## 📄 Licencja

MIT — możesz swobodnie używać, modyfikować i dystrybuować.

---

*Projekt nie jest oficjalnie powiązany z John Deere ani Anthropic.*
