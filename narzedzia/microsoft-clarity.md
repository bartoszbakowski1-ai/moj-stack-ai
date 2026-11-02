# Microsoft Clarity: jak podłączyć do Claude

Microsoft Clarity to bezpłatne narzędzie do analizy zachowań na stronie (nagrania sesji, mapy cieplne), a oficjalny serwer MCP Microsoftu pozwala Claude pobierać z niego dane. Claude czyta nagrania sesji i mapy kliknięć ze strony.

- Sposób: Serwer MCP (lokalnie)
- Logowanie: token
- Darmowy plan: tak
- Płatny plan od: brak planów płatnych (Clarity: Free forever) (stan na listopad 2026)
- Strona: https://clarity.microsoft.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/microsoft-clarity

## Kroki

1. W projekcie Clarity wejdź w Settings > Data Export i kliknij Generate new API token (tokeny tworzy tylko administrator projektu).
2. Nadaj tokenowi nazwę (4 do 32 znaków, bez spacji) i zapisz go w bezpiecznym miejscu.
3. W Claude Desktop otwórz Settings > Extensions, wyszukaj Microsoft Clarity i kliknij Install.
4. Wpisz token API w ustawieniach rozszerzenia.
5. Alternatywa dla innych klientów: dodaj wpis npx @microsoft/clarity-mcp-server z argumentem --clarity_api_token (wymaga Node.js 16 lub nowszego).
6. Zadawaj proste pytania z zakresem dat, np. głębokość przewijania dla ostatnich 2 dni według urządzenia.

```bash
npx @microsoft/clarity-mcp-server --clarity_api_token=your-token-here
```

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Microsoft Clarity do Claude Code.
Podłącz go jako serwer MCP.
Oficjalne polecenie: npx @microsoft/clarity-mcp-server --clarity_api_token=your-token-here
Dokumentacja: https://learn.microsoft.com/en-us/clarity/third-party-integrations/clarity-mcp-server
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- To lokalne rozszerzenie (Desktop extension) w katalogu Claude, nie zdalny connector, więc nie ma adresu URL i działa głównie w Claude Desktop. Instrukcji specyficznej dla Claude Code Microsoft nie podaje (niepotwierdzone).
- Limity Data Export API: 10 zapytań dziennie na projekt, dane z ostatnich 1 do 3 dni, maksymalnie 3 wymiary i 1000 wierszy bez paginacji.
- Nazwy narzędzi w opisie katalogu (query-analytics-data) i w README (query-analytics-dashboard) różnią się nieznacznie.

## Źródła

- https://learn.microsoft.com/en-us/clarity/third-party-integrations/clarity-mcp-server
- https://learn.microsoft.com/en-us/clarity/setup-and-installation/clarity-data-export-api
- https://github.com/microsoft/clarity-mcp-server
- https://claude.ai/directory/ant.dir.gh.microsoft.clarity-mcp-server
- https://claude.com/marketplace/connectors/microsoft-clarity
- https://clarity.microsoft.com/
