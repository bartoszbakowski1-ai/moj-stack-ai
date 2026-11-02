# Webflow: jak podłączyć do Claude

Webflow to wizualny kreator stron z wbudowanym CMS i hostingiem. Claude edytuje strony i kolekcje CMS w Webflow.

- Sposób: Konektor w Claude
- Logowanie: OAuth
- Darmowy plan: tak
- Płatny plan od: 15 USD/mies. (Basic, rozliczenie roczne) (stan na listopad 2026)
- Strona: https://webflow.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/webflow

## Kroki

1. W claude.ai wejdź w Customize, potem Connectors, i dodaj Webflow z katalogu.
2. Zaloguj się do Webflow, wybierz strony, do których Claude ma mieć dostęp, i zainstaluj aplikację MCP Bridge.
3. W Claude Code uruchom komendę claude mcp add, potem /mcp, wybierz Webflow i zaloguj się w oknie przeglądarki.
4. Dla osobnych projektów dodaj serwer z opcją -s project w folderze projektu.

```bash
claude mcp add --transport http webflow https://mcp.webflow.com/mcp
```

Adres serwera MCP: `https://mcp.webflow.com/mcp`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Webflow do Claude Code.
Webflow jest w katalogu konektorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Konektory). Jeśli w Claude Code, podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add --transport http webflow https://mcp.webflow.com/mcp
Adres serwera MCP: https://mcp.webflow.com/mcp
Dokumentacja: https://developers.webflow.com/mcp/installing/claude-code
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Jedna autoryzacja daje dostęp do jednego workspace, zmiana workspace wymaga usunięcia i ponownego dodania connectora. MCP nie tworzy nowych projektów, strona musi już istnieć w dashboardzie.
- Część funkcji (zrzuty elementów, wgrywanie obrazów, odczyt zaznaczenia) wymaga otwartego Designera z aplikacją Bridge.
- Plan Starter jest darmowy i na stronie cennika ma pozycję Webflow AI MCP server.

## Źródła

- https://claude.com/marketplace/connectors/webflow
- https://developers.webflow.com/mcp/installing/claude-code
- https://developers.webflow.com/mcp/v1.0.0/reference/overview
- https://webflow.com/pricing
