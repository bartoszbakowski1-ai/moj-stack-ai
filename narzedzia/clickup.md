# ClickUp: jak podłączyć do Claude

Aplikacja do zarządzania zadaniami i projektami, z oficjalnym serwerem MCP do czytania i tworzenia zadań, list, dokumentów i komentarzy. Claude tworzy i aktualizuje zadania oraz listy w ClickUp.

- Sposób: Connector w Claude
- Logowanie: OAuth
- Darmowy plan: tak
- Płatny plan od: 9 USD/mies. za użytkownika (Core, rozliczane rocznie; zwykła cena 12 USD) (stan na listopad 2026)
- Strona: https://clickup.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/clickup

## Kroki

1. claude.ai lub Desktop (Pro, Team, Enterprise): Settings > Connectors > Add, nazwa ClickUp, adres https://mcp.clickup.com/mcp (lub wpis ClickUp w katalogu).
2. Claude Desktop na planie Free: edytuj claude_desktop_config.json i dodaj serwer przez npx -y mcp-remote https://mcp.clickup.com/mcp, potem zrestartuj aplikację.
3. Claude Code: uruchom claude mcp add --transport http clickup https://mcp.clickup.com/mcp.
4. W sesji Claude Code wpisz /mcp i dokończ logowanie.

```bash
claude mcp add --transport http clickup https://mcp.clickup.com/mcp
```

Adres serwera MCP: `https://mcp.clickup.com/mcp`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz ClickUp do Claude Code.
ClickUp jest w katalogu connectorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Connectors). Jeśli w Claude Code, podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add --transport http clickup https://mcp.clickup.com/mcp
Adres serwera MCP: https://mcp.clickup.com/mcp
Dokumentacja: https://developer.clickup.com/docs/connect-an-ai-assistant-to-clickups-mcp-server-1
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Tylko OAuth. Nie można użyć własnego klucza API ani tokenu osobistego. Brak narzędzi do usuwania (celowy środek bezpieczeństwa).
- Limity wywołań MCP na 24 godziny bez dodatku Everything AI: Free 100, Core/Unlimited 300, Business 1000, Business Plus 2500, Enterprise 5000.
- Strona cennika nie pokazała planu Unlimited. Najbliższy aktualny płatny plan to Core.

## Źródła

- https://claude.com/marketplace/connectors/clickup
- https://developer.clickup.com/docs/connect-an-ai-assistant-to-clickups-mcp-server
- https://developer.clickup.com/docs/connect-an-ai-assistant-to-clickups-mcp-server-1
- https://clickup.com/pricing
