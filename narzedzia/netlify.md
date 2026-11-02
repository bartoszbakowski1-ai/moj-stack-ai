# Netlify: jak podłączyć do Claude

Netlify to platforma do hostowania i wdrażania stron oraz aplikacji webowych. Claude wdraża i sprawdza strony hostowane na Netlify.

- Sposób: Connector w Claude
- Logowanie: logowanie kontem Netlify w przeglądarce (OAuth niepotwierdzone)
- Darmowy plan: tak
- Płatny plan od: 9 USD/mies. (Personal) (stan na listopad 2026)
- Strona: https://www.netlify.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/netlify

## Kroki

1. W claude.ai wejdź w Customize, potem Connectors.
2. Wyszukaj Netlify i kliknij Connect.
3. Przejdź przez autoryzację konta Netlify.
4. W Claude Code uruchom komendę claude mcp add i zaloguj się, gdy Claude Code o to poprosi (pomocne: netlify login).
5. Po połączeniu ustaw narzędzia tylko do odczytu na Always allow, a zapisujące i usuwające na Needs approval.

```bash
claude mcp add --transport http netlify https://netlify-mcp.netlify.app/mcp
```

Adres serwera MCP: `https://netlify-mcp.netlify.app/mcp`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Netlify do Claude Code.
Netlify jest w katalogu connectorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Connectors). Jeśli w Claude Code, podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add --transport http netlify https://netlify-mcp.netlify.app/mcp
Adres serwera MCP: https://netlify-mcp.netlify.app/mcp
Dokumentacja: https://docs.netlify.com/build/build-with-ai/netlify-mcp-server/
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Plany Netlify są oparte na kredytach (Free 300 kredytów, Personal 1000, Pro 3000).
- Dokumentacja nie opisuje dokładnej metody uwierzytelniania, wpis w katalogu mówi tylko, że wymagane jest logowanie (OAuth niepotwierdzone nazwą).
- Wariant lokalny: claude mcp add netlify -- npx -y @netlify/mcp (wymaga Node 24 lub nowszego).

## Źródła

- https://docs.netlify.com/build/build-with-ai/netlify-mcp-server/
- https://docs.netlify.com/build/build-with-ai/agent-setup-guides/set-up-claude-code-for-netlify/
- https://docs.netlify.com/build/build-with-ai/agent-setup-guides/set-up-claude-web-for-netlify/
- https://claude.com/marketplace/connectors/netlify
- https://www.netlify.com/pricing/
