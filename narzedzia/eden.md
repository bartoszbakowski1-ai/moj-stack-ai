# Eden: jak podłączyć do Claude

Eden to narzędzie dla twórców do researchu postów z social mediów, zarządzania tablicami i notatkami, analityki oraz planowania publikacji, które łączy się z Claude przez MCP. Claude czyta Twoje tablice z notatkami i materiałami, więc pracuje na Twoim kontekście.

- Sposób: Serwer MCP (adres)
- Logowanie: OAuth
- Darmowy plan: tak
- Płatny plan od: 7,50 USD/mies. (Personal, rozliczenie roczne 90 USD) (stan na listopad 2026)
- Strona: https://eden.so
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/eden

## Kroki

1. W Eden wejdź w Settings, potem MCP.
2. Kliknij Connect Claude. Claude otworzy stronę Connectors z uzupełnionym Eden, potwierdź.
3. Zaloguj się kontem Eden w oknie przeglądarki i kliknij Connect Eden.
4. W nowym chacie włącz Eden pod ikoną narzędzi.
5. W Claude Code uruchom komendę claude mcp add i zaloguj się kontem Eden, gdy Claude Code o to poprosi.

```bash
claude mcp add --transport http eden https://mcp.eden.so/mcp
```

Adres serwera MCP: `https://mcp.eden.so/mcp`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Eden do Claude Code.
Podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add --transport http eden https://mcp.eden.so/mcp
Adres serwera MCP: https://mcp.eden.so/mcp
Dokumentacja: https://eden.so/help/eden-mcp/quick-start/
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Łączenie jest darmowe na każdym planie, ale wyszukiwania i analizy zużywają kredyty Eden (np. 0,3 kredytu za wyszukiwanie, 0,5 za odczyt postu), a odczyt własnej przestrzeni i zapisy są bezpłatne.
- Na stronie cennika dane strukturalne podają Personal za 9 USD, a sekcja planów 7,50 USD przy płatności rocznej, więc dokładną cenę miesięczną trzeba sprawdzić w koszyku.
- Nie znalazłem Eden w oficjalnym katalogu Claude, dlatego przycisk Connect Claude dodaje go jako własny connector (obecność w katalogu niepotwierdzona).

## Źródła

- https://eden.so/help/eden-mcp/
- https://eden.so/help/eden-mcp/quick-start/
- https://eden.so/help/eden-mcp/installing-with-cli/
- https://eden.so/help/eden-mcp/connecting-ai-assistants/
- https://eden.so/features/mcp/
- https://eden.so/pricing
