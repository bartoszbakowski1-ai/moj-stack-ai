# Slack: jak podłączyć do Claude

Komunikator zespołowy, którego oficjalny serwer MCP pozwala Claude wyszukiwać wiadomości, kanały i pliki oraz wysyłać wiadomości. Claude czyta kanały, szuka wiadomości i pisze w Slacku.

- Sposób: Connector w Claude
- Logowanie: OAuth
- Darmowy plan: tak
- Płatny plan od: 8,25 EUR/mies. za użytkownika (Pro, rozliczane miesięcznie; 6,75 EUR przy rocznym; cena w EUR wg wersji strony) (stan na listopad 2026)
- Strona: https://slack.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/slack

## Kroki

1. Upewnij się, że admin workspace Slacka zatwierdził integrację MCP.
2. Claude Desktop: Customize > Connectors > plus, znajdź Slack i dodaj go, potem dokończ OAuth do swojego workspace.
3. claude.ai: dodaj Slack z katalogu connectorów (wpis Slack w katalogu Anthropic).
4. Claude Code: wpisz /plugin install slack lub claude plugin install slack, serwer MCP skonfiguruje się automatycznie.
5. Zaloguj się do Slacka w oknie OAuth, które pojawi się po załadowaniu wtyczki.

```bash
claude plugin install slack
```

Adres serwera MCP: `https://mcp.slack.com/mcp`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Slack do Claude Code.
Slack jest w katalogu connectorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Connectors). Jeśli w Claude Code, podłącz go jako serwer MCP.
Oficjalne polecenie: claude plugin install slack
Adres serwera MCP: https://mcp.slack.com/mcp
Dokumentacja: https://docs.slack.dev/ai/slack-mcp-server/connect-to-claude/
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Wymagana zgoda admina workspace. Nie znalazłem w oficjalnych źródłach, czy darmowy plan Slacka pozwala na użycie serwera MCP (niepotwierdzone).
- Zarządzanie dostępem MCP przez dostawcę tożsamości wymaga planu Slack Enterprise+ i Claude Team lub Enterprise.
- Dokumentacja Slacka opisuje kroki dla Claude Desktop i Claude Code, ale nie dla claude.ai w przeglądarce.

## Źródła

- https://claude.com/marketplace/connectors/slack
- https://docs.slack.dev/ai/mcp-server
- https://docs.slack.dev/ai/slack-mcp-server/connect-to-claude/
- https://slack.com/help/articles/48855576908307-Guide-to-the-Slack-MCP-server
- https://slack.com/pricing
