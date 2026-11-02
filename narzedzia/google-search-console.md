# Google Search Console: jak podłączyć do Claude

Google Search Console to bezpłatne narzędzie Google pokazujące, jak strona wypada w wynikach wyszukiwania, w tym kliknięcia, wyświetlenia, pozycje, indeksowanie i mapy witryn. Claude sprawdza, na jakie frazy strona pokazuje się w Google i co poprawić.

- Sposób: Serwer MCP społeczności
- Logowanie: konto serwisowe
- Darmowy plan: tak
- Płatny plan od: brak planów płatnych (Search Console jest bezpłatny) (stan na listopad 2026)
- Strona: https://search.google.com/search-console/about
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/google-search-console

## Kroki

1. Wybierz serwer społecznościowy AminForou/mcp-gsc (najwięcej gwiazdek na GitHubie spośród sprawdzonych) i zainstaluj uv.
2. W projekcie Google Cloud włącz Search Console API i utwórz konto serwisowe z kluczem JSON.
3. W Search Console otwórz Ustawienia > Użytkownicy i uprawnienia > Dodaj użytkownika i wpisz e-mail konta serwisowego z pełnym dostępem (widać to tylko właścicielowi usługi).
4. W claude_desktop_config.json dodaj wpis z command uvx, args mcp-search-console, env GSC_CREDENTIALS_PATH ze ścieżką do klucza i GSC_SKIP_OAUTH ustawionym na "true".
5. Użyj bezwzględnych ścieżek i całkowicie zrestartuj Claude Desktop po zmianie konfiguracji.
6. Poproś Claude o listę usług (list_properties), a potem o raport wydajności z ostatnich 28 dni.
7. Zamiast konta serwisowego możesz użyć OAuth: klient Desktop z Google Cloud i zmienna GSC_OAUTH_CLIENT_SECRETS_FILE.

```bash
uvx mcp-search-console
```

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Google Search Console do Claude Code.
Podłącz go jako serwer MCP.
Oficjalne polecenie: uvx mcp-search-console
Dokumentacja: https://github.com/AminForou/mcp-gsc
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Nie znalazłem oficjalnego serwera MCP Google dla Search Console w dokumentacji Google; wszystkie opcje są społecznościowe. AminForou/mcp-gsc: 2,1 tys. gwiazdek, licencja MIT. Drugi wybór: https://github.com/ahonn/mcp-server-gsc (282 gwiazdki, tylko narzędzie search_analytics, konto serwisowe jako administrator).
- Dodawanie lub usuwanie usług i usuwanie map witryn jest domyślnie wyłączone (włącza je GSC_ALLOW_DESTRUCTIVE). Przed użyciem sprawdź kod i aktywność repozytorium.
- Brak oficjalnego connectora Search Console w katalogu Claude. Jeśli nie chcesz konta serwisowego, ten serwer obsługuje też logowanie OAuth przeglądarką.

## Źródła

- https://github.com/AminForou/mcp-gsc
- https://github.com/ahonn/mcp-server-gsc
- https://support.google.com/webmasters/answer/7687615
- https://support.google.com/webmasters/answer/9128668
- https://claude.ai/directory?q=search+console
