# Sanity: jak podłączyć do Claude

Sanity to headless CMS do zarządzania strukturalną treścią, z edytorem Studio i zapytaniami GROQ. Claude dodaje i poprawia treści na stronie, na przykład wpisy bloga i hasła.

- Sposób: Connector w Claude
- Logowanie: OAuth
- Darmowy plan: tak
- Płatny plan od: 15 USD/miejsce/mies. (Growth) (stan na listopad 2026)
- Strona: https://www.sanity.io
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/sanity

## Kroki

1. W claude.ai wejdź w Customize, potem Connectors, i dodaj Sanity z katalogu.
2. Zaloguj się kontem Sanity i zatwierdź dostęp.
3. W Claude Code uruchom komendę claude mcp add albo npx sanity@latest mcp configure.
4. Przy pierwszym użyciu w Claude Code zaloguj się przez OAuth (alternatywnie ustaw nagłówek Authorization z tokenem API).

```bash
claude mcp add Sanity -t http https://mcp.sanity.io --scope user
```

Adres serwera MCP: `https://mcp.sanity.io`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Sanity do Claude Code.
Sanity jest w katalogu connectorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Connectors). Jeśli w Claude Code, podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add Sanity -t http https://mcp.sanity.io --scope user
Adres serwera MCP: https://mcp.sanity.io
Dokumentacja: https://www.sanity.io/docs/ai/mcp-server
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Dokumentacja Sanity opisuje tylko Claude Code, a wpis w katalogu Claude (claude.com/marketplace) potwierdza connector do claude.ai.
- Sesje OAuth zwykle wygasają po 7 dniach i trzeba się uwierzytelnić ponownie. Wymagany plan Sanity dla MCP niepotwierdzony (wymagane jest konto Sanity).

## Źródła

- https://www.sanity.io/docs/ai/mcp-server
- https://claude.com/marketplace/connectors/sanity
- https://www.sanity.io/pricing
