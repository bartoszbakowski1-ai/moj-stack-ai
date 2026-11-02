# Composio: jak podłączyć do Claude

Platforma łącząca agentów AI z setkami aplikacji przez jeden serwer MCP, z wczytywaniem narzędzi na żądanie. Jedno połączenie, przez które Claude dostaje setki aplikacji naraz.

- Sposób: Serwer MCP (adres)
- Logowanie: OAuth
- Darmowy plan: tak
- Płatny plan od: 29 USD/mies. (Pro) (stan na listopad 2026)
- Strona: https://composio.dev
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/composio

## Kroki

1. claude.ai lub Desktop: wejdź w Settings > Connectors > Add custom connector, nazwa Composio, adres https://connect.composio.dev/mcp.
2. Zaloguj się na konto Composio, gdy Claude otworzy okno logowania.
3. Claude Code: wygeneruj adres sesji przez SDK (@composio/core, composio.create(USER_ID, {toolkits:['composio']})) i uruchom wydrukowaną komendę claude mcp add z nagłówkiem X-API-Key.
4. Zrestartuj Claude Code, sprawdź claude mcp list, potem /mcp i Authenticate.
5. Połącz konkretne aplikacje (Gmail, Slack itd.) w panelu Composio lub poprzez narzędzia Composio w rozmowie.

```bash
claude mcp add --transport http composio-composio "YOUR_MCP_URL_HERE" --headers "X-API-Key:YOUR_COMPOSIO_API_KEY"
```

Adres serwera MCP: `https://connect.composio.dev/mcp`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Composio do Claude Code.
Podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add --transport http composio-composio "YOUR_MCP_URL_HERE" --headers "X-API-Key:YOUR_COMPOSIO_API_KEY"
Adres serwera MCP: https://connect.composio.dev/mcp
Dokumentacja: https://composio.dev/claude
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Nie znalazłem potwierdzenia wpisu Composio w katalogu Anthropic (adresy claude.com/marketplace/connectors/composio dają 404). Oficjalna strona Composio opisuje wyłącznie ręczne dodanie jako custom connector.
- Komenda dla Claude Code z oficjalnej strony Composio używa adresu sesji generowanego przez SDK, a nie stałego connect.composio.dev/mcp. Strona composio.dev/claude nie podaje komendy dla Claude Code.
- Dane logowania do połączonych aplikacji przechodzą przez Composio, więc ocena zaufania do pośrednika jest po stronie użytkownika. Plan Hobby: 100 000 wywołań narzędzi miesięcznie.

## Źródła

- https://composio.dev/claude
- https://composio.dev/toolkits/composio/framework/claude-code
- https://composio.dev/pricing
- https://claude.com/marketplace/connectors/composio
