# Google Drive: jak podłączyć do Claude

Google Drive to chmura Google na pliki, dokumenty, arkusze i prezentacje, do której Claude może zajrzeć, żeby wyszukiwać i czytać Twoje pliki. Claude szuka i czyta dokumenty, arkusze i pliki z Dysku Google.

- Sposób: Konektor w Claude
- Logowanie: OAuth
- Darmowy plan: tak
- Płatny plan od: 8,99 zł/mies. (Google One Basic 100 GB, cennik widoczny dla Polski) (stan na listopad 2026)
- Strona: https://drive.google.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/google-drive

## Kroki

1. Wejdź w Customize > Connectors w claude.ai albo w aplikacji Claude Desktop.
2. Wybierz Discover, wyszukaj Google Drive i otwórz jego stronę.
3. Kliknij Connect to Claude i zaloguj się kontem Google, które ma dostęp do Twoich plików.
4. Zatwierdź zakres dostępu, a gdy wrócisz do Connectors, sprawdź status Connected.
5. W chacie kliknij +, wybierz Connectors i włącz Google Drive dla tej rozmowy.
6. W Claude Code złącze dodane w claude.ai pojawi się samo, jeśli zalogowałeś się kontem claude.ai (sprawdź w /mcp).

Adres serwera MCP: `https://drivemcp.googleapis.com/mcp/v1`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Google Drive do Claude Code.
Google Drive jest w katalogu konektorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Konektory). Jeśli w Claude Code, podłącz go jako serwer MCP.
Adres serwera MCP: https://drivemcp.googleapis.com/mcp/v1
Dokumentacja: https://developers.google.com/workspace/drive/api/guides/configure-mcp-server
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Claude widzi tylko pliki, do których ma dostęp Twoje konto Google, a właściciel organizacji może ograniczyć złącze do samego odczytu.
- Instrukcja Google dla ręcznego dodania serwera (własny klient OAuth w Google Cloud, redirect https://claude.ai/api/mcp/auth_callback) wymienia plany Claude Enterprise, Pro, Max i Team. Z katalogu łączysz bez własnego klienta OAuth.
- Google ostrzega przed prompt injection w dokumentach z niezaufanych źródeł, więc sprawdzaj akcje, które Claude wykonuje.

## Źródła

- https://claude.com/marketplace/connectors/google-drive
- https://developers.google.com/workspace/drive/api/guides/configure-mcp-server
- https://claude.com/docs/connectors/overview
- https://support.claude.com/en/articles/11176164-use-connectors-to-extend-claude-s-capabilities
- https://code.claude.com/docs/en/mcp
- https://one.google.com/about/plans
