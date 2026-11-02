# Vercel: jak podłączyć do Claude

Vercel to platforma hostingowa i wdrożeniowa dla stron i aplikacji, w tym projektów Next.js. Claude sprawdza wdrożenia, logi i błędy stron Next.js bez wchodzenia w panel.

- Sposób: Connector w Claude
- Logowanie: OAuth
- Darmowy plan: tak
- Płatny plan od: 20 USD/mies. (Pro, na użytkownika) (stan na listopad 2026)
- Strona: https://vercel.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/vercel

## Kroki

1. W claude.ai wejdź w Customize, potem Connectors, i dodaj Vercel z katalogu (lub użyj przycisku Add to Claude na stronie connectora).
2. Zaloguj się kontem Vercel i zatwierdź dostęp w oknie autoryzacji.
3. W chacie włącz Vercel w menu plus, potem Connectors.
4. W Claude Code uruchom komendę claude mcp add, potem wpisz /mcp i uwierzytelnij serwer.
5. Alternatywnie dodaj własny connector z URL https://mcp.vercel.com (Settings, Connectors, Add custom connector).

```bash
claude mcp add --transport http vercel https://mcp.vercel.com
```

Adres serwera MCP: `https://mcp.vercel.com`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Vercel do Claude Code.
Vercel jest w katalogu connectorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Connectors). Jeśli w Claude Code, podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add --transport http vercel https://mcp.vercel.com
Adres serwera MCP: https://mcp.vercel.com
Dokumentacja: https://vercel.com/docs/agent-resources/vercel-mcp
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Vercel MCP jest dostępny na wszystkich planach Vercel, a połączenie daje Claude takie same uprawnienia jak Twoje konto Vercel, więc włącz potwierdzanie akcji.
- Serwer przyjmuje tylko klienty zatwierdzone przez Vercel, Claude jest na liście obsługiwanych.
- Dodanie własnego connectora wymaga planu Pro, Max, Team lub Enterprise Claude, ale connector z katalogu jest dostępny dla wszystkich użytkowników.

## Źródła

- https://vercel.com/docs/agent-resources/vercel-mcp
- https://claude.com/marketplace/connectors/vercel
- https://vercel.com/pricing
- https://support.claude.com/en/articles/11176164-pre-built-web-connectors-using-remote-mcp
