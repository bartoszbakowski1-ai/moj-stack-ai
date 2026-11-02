# WordPress: jak podłączyć do Claude

WordPress to najpopularniejszy system do tworzenia stron i blogów, dostępny jako hosting WordPress.com lub własna instalacja. Claude zarządza wpisami i stronami w WordPressie.

- Sposób: Konektor w Claude
- Logowanie: OAuth
- Darmowy plan: tak
- Płatny plan od: 4 USD/mies. (Personal, rozliczenie roczne) (stan na listopad 2026)
- Strona: https://wordpress.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/wordpress

## Kroki

1. Włącz MCP na swoim koncie WordPress.com w ustawieniach pod adresem my.wordpress.com/me/preferences/mcp.
2. W claude.ai wejdź w Customize, potem Connectors, i dodaj WordPress.com z katalogu.
3. Zaloguj się, wybierz poziom dostępu (pełny albo tylko odczyt) i kliknij Allow.
4. W Claude Code uruchom komendę claude mcp add, a potem wpisz /mcp i uwierzytelnij serwer wpcom-mcp.

```bash
claude mcp add --transport http wpcom-mcp https://public-api.wordpress.com/wpcom/v2/mcp/v1
```

Adres serwera MCP: `https://public-api.wordpress.com/wpcom/v2/mcp/v1`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz WordPress do Claude Code.
WordPress jest w katalogu konektorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Konektory). Jeśli w Claude Code, podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add --transport http wpcom-mcp https://public-api.wordpress.com/wpcom/v2/mcp/v1
Adres serwera MCP: https://public-api.wordpress.com/wpcom/v2/mcp/v1
Dokumentacja: https://developer.wordpress.com/docs/mcp/
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Oficjalne źródła różnią się co do planów: dokumentacja developer.wordpress.com mówi, że MCP działa na każdej stronie WordPress.com, także darmowej, a wpis w katalogu Claude mówi o planach płatnych i stronach z Jetpack AI lub Complete. Sprawdź przed publikacją.
- Dotyczy WordPress.com i stron z Jetpack. Dla samodzielnie hostowanego WordPress istnieje oficjalny pakiet WordPress/mcp-adapter (STDIO przez WP-CLI lub HTTP), ale to osobna, bardziej techniczna ścieżka.
- Odłączenie w Claude nie usuwa dostępu po stronie WordPress.com, trzeba to zrobić w Security, Connected applications.

## Źródła

- https://developer.wordpress.com/docs/mcp/
- https://claude.com/marketplace/connectors/wordpress-com
- https://github.com/WordPress/mcp-adapter
- https://wordpress.com/pricing/
