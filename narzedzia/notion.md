# Notion: jak podłączyć do Claude

Aplikacja do notatek, wiki, baz danych i projektów, z oficjalnym hostowanym serwerem MCP do wyszukiwania i edycji stron. Claude czyta i tworzy strony oraz bazy w Notion, na przykład bazę klientów.

- Sposób: Connector w Claude
- Logowanie: OAuth
- Darmowy plan: tak
- Płatny plan od: 9,50 EUR/mies. za osobę (Plus; cena w EUR wg wersji strony, do 20% taniej przy rozliczeniu rocznym) (stan na listopad 2026)
- Strona: https://www.notion.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/notion

## Kroki

1. claude.ai lub Desktop: wejdź w Settings > Connectors, znajdź Notion i kliknij Connect (albo Add to Claude na stronie wpisu).
2. Zaloguj się do Notion i wybierz workspace, do którego Claude ma mieć dostęp.
3. Claude Code: uruchom claude mcp add --transport http notion https://mcp.notion.com/mcp.
4. W Claude Code wpisz /mcp i dokończ logowanie OAuth.
5. Business i Enterprise: właściciel workspace może utworzyć token MCP w portalu Developer i użyć go jako Bearer zamiast logowania w przeglądarce.

```bash
claude mcp add --transport http notion https://mcp.notion.com/mcp
```

Adres serwera MCP: `https://mcp.notion.com/mcp`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Notion do Claude Code.
Notion jest w katalogu connectorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Connectors). Jeśli w Claude Code, podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add --transport http notion https://mcp.notion.com/mcp
Adres serwera MCP: https://mcp.notion.com/mcp
Dokumentacja: https://developers.notion.com/guides/mcp/get-started-with-mcp
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Łączyć mogą się tylko członkowie workspace (goście są odrzucani). Admin może zablokować dodawanie serwerów MCP.
- Lokalny serwer open source notion-mcp-server (z tokenem integracji) nie jest już aktywnie rozwijany. Używaj hostowanego mcp.notion.com.
- Część funkcji (tokeny MCP, wyższe limity, wyszukiwanie w podłączonych źródłach) wymaga planów Business lub Enterprise.

## Źródła

- https://claude.com/marketplace/connectors/notion
- https://developers.notion.com/guides/mcp/get-started-with-mcp
- https://www.notion.com/pricing
