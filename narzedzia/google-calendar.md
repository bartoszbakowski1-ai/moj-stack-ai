# Google Calendar: jak podłączyć do Claude

Kalendarz Google, który Claude może czytać po podłączeniu connectora (spotkania, uczestnicy, dostępność). Claude sprawdza kalendarz, szuka wolnych terminów i dodaje wydarzenia.

- Sposób: Connector w Claude
- Logowanie: OAuth
- Darmowy plan: sprawdź na stronie producenta
- Strona: https://workspace.google.com/intl/en/products/calendar/
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/google-calendar

## Kroki

1. Otwórz claude.ai > Customize > Connectors i przy Google Calendar kliknij Connect.
2. Zaloguj się na konto Google i zaakceptuj uprawnienia.
3. W rozmowie kliknij plus > Connectors i włącz Google Calendar.
4. Na Team i Enterprise najpierw Owner włącza connector dla organizacji.
5. W Claude Code connectory z claude.ai są widoczne w /mcp.

Adres serwera MCP: `https://calendarmcp.googleapis.com/mcp/v1`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Google Calendar do Claude Code.
Google Calendar jest w katalogu connectorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Connectors). Jeśli w Claude Code, podłącz go jako serwer MCP.
Adres serwera MCP: https://calendarmcp.googleapis.com/mcp/v1
Dokumentacja: https://claude.com/docs/connectors/google/calendar
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Dokumentacja claude.com opisuje connector jako tylko do odczytu (bez tworzenia i zmiany wydarzeń), na planach Pro, Max, Ultra, Team i Enterprise. Dokumentacja Google dla serwera MCP wymienia narzędzia create_event, update_event i delete_event. Aktualny zakres niepotwierdzony.
- Ręczna ścieżka Google (Developer Preview) wymaga projektu Google Cloud, klienta OAuth z zaznaczonym 'Use this client for an AI-powered agent' i redirectu https://claude.ai/api/mcp/auth_callback. Przy connectorze z katalogu nie jest potrzebna.
- Nie znalazłem w przeczytanych źródłach osobnej oficjalnej informacji o cenie samego Kalendarza Google, więc pola cennika zostawiam jako niepotwierdzone (kalendarz jest częścią Google Workspace).

## Źródła

- https://claude.com/marketplace/connectors/google-calendar
- https://claude.com/docs/connectors/google/calendar
- https://developers.google.com/workspace/calendar/api/guides/configure-mcp-server
- https://workspace.google.com/pricing
