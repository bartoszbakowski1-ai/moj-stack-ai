# Google Analytics 4: jak podłączyć do Claude

Google Analytics 4 to bezpłatne narzędzie Google do analityki ruchu na stronie i w aplikacji, a oficjalny serwer analytics-mcp (tylko do odczytu) pozwala Claude pobierać raporty. Claude czyta ruch i konwersje na stronie z GA4.

- Sposób: Serwer MCP (lokalnie)
- Logowanie: konto serwisowe
- Darmowy plan: tak
- Strona: https://marketingplatform.google.com/about/analytics/
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/google-analytics-4

## Kroki

1. Zainstaluj Python 3.10 lub nowszy oraz pipx.
2. W projekcie Google Cloud włącz Google Analytics Admin API i Google Analytics Data API.
3. Utwórz konto serwisowe i pobierz jego klucz JSON; zapisz bezwzględną ścieżkę do pliku.
4. W GA4 wejdź w Administracja > Zarządzanie dostępem do usługi (Property access management) i dodaj e-mail konta serwisowego z rolą co najmniej Wyświetlający (Viewer).
5. Dodaj serwer w Claude Code poleceniem podanym niżej albo wpisem analytics-mcp w claude_desktop_config.json (command pipx, args run analytics-mcp, env z dwiema zmiennymi).
6. Sprawdź w /mcp, czy analytics-mcp jest połączony, i poproś o podsumowanie kont (get_account_summaries).
7. Zamiast konta serwisowego możesz użyć własnego loginu: gcloud auth application-default login z zakresem analytics.readonly.

```bash
claude mcp add analytics-mcp --scope user -e "GOOGLE_APPLICATION_CREDENTIALS=PATH_TO_CREDENTIALS_JSON" -e "GOOGLE_CLOUD_PROJECT=YOUR_PROJECT_ID" -- pipx run analytics-mcp
```

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Google Analytics 4 do Claude Code.
Podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add analytics-mcp --scope user -e "GOOGLE_APPLICATION_CREDENTIALS=PATH_TO_CREDENTIALS_JSON" -e "GOOGLE_CLOUD_PROJECT=YOUR_PROJECT_ID" -- pipx run analytics-mcp
Dokumentacja: https://developers.google.com/analytics/devguides/MCP
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Model dostępu: serwer używa Application Default Credentials, a konto (użytkownika lub serwisowe) musi mieć dostęp do właściwości GA4. Samo konto serwisowe w Google Cloud nie wystarczy, trzeba dodać jego e-mail w GA4.
- Repozytorium googleanalytics/google-analytics-mcp jest oznaczone jako Experimental, domyślnie tylko do odczytu (zapis wymaga flagi --allow-write i zakresu analytics.edit).
- Nie ma oficjalnego connectora Google Analytics w katalogu Claude (wyszukiwanie dało tylko rozwiązania zewnętrzne, np. Supermetrics). Ceny Analytics 360 nie są podane na sprawdzonej stronie.

## Źródła

- https://developers.google.com/analytics/devguides/MCP
- https://github.com/googleanalytics/google-analytics-mcp
- https://pypi.org/project/analytics-mcp/
- https://support.google.com/analytics/answer/9305587
- https://marketingplatform.google.com/about/analytics/
- https://claude.ai/directory?q=google+analytics
