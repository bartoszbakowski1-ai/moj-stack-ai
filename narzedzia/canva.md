# Canva: jak podłączyć do Claude

Canva to edytor graficzny online, a jego connector (Canva AI Connector) pozwala Claude wyszukiwać, tworzyć, edytować i eksportować projekty. Claude tworzy i edytuje projekty graficzne w Canvie.

- Sposób: Connector w Claude
- Logowanie: OAuth
- Darmowy plan: tak
- Płatny plan od: 450 zł/rok (Canva Pro, cennik widoczny dla Polski) (stan na listopad 2026)
- Strona: https://www.canva.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/canva

## Kroki

1. Zaloguj się do właściwego konta Canva w przeglądarce.
2. W Claude otwórz Settings > Connectors (lub Customize > Connectors), znajdź Canva i wybierz go.
3. Postępuj według komunikatów, zaloguj się i zatwierdź autoryzację w Canva.
4. Sprawdź, czy Canva ma status Connected.
5. Rozpocznij nowy chat, otwórz ustawienia chatu i włącz Canva w sekcji Connectors.
6. Poproś Claude np. o wyszukanie projektu albo wygenerowanie nowego i eksport do PDF.

Adres serwera MCP: `https://mcp.canva.com/mcp`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Canva do Claude Code.
Canva jest w katalogu connectorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Connectors). Jeśli w Claude Code, podłącz go jako serwer MCP.
Adres serwera MCP: https://mcp.canva.com/mcp
Dokumentacja: https://www.canva.com/help/connect-claude-to-canva/
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Wg centrum pomocy Canva connector jest dostępny dla wszystkich kont, także Free, ale szablony marki (Brand Templates), autofill i zmiana rozmiaru wymagają płatnego planu. Strona cennika Canva wymienia "Canva AI connectors" przy Pro i Business, więc zakres dostępu niepotwierdzony jednoznacznie.
- Na kontach zespołowych (Teams, Business, Education, Enterprise) admin musi włączyć Canva AI Connector w Controls and Permissions.
- Akcje AI (np. generowanie projektów) mogą zużywać miesięczny limit Canva AI.

## Źródła

- https://claude.com/marketplace/connectors/canva
- https://www.canva.com/help/mcp-agent-setup/
- https://www.canva.com/help/connect-claude-to-canva/
- https://www.canva.dev/docs/apps/mcp/access/
- https://canva.dev/docs/mcp/
- https://www.canva.com/pricing/
