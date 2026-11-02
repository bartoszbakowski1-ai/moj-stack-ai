# Apify: jak podłączyć do Claude

Platforma z tysiącami gotowych scraperów i automatyzacji (Actors) do pobierania danych z internetu, w tym z mediów społecznościowych i map. Claude uruchamia gotowe scrapery, na przykład do Google Maps albo Instagrama.

- Sposób: Konektor w Claude
- Logowanie: OAuth
- Darmowy plan: tak
- Płatny plan od: 19 USD/mies. (Starter; 17 USD/mies. przy rozliczeniu rocznym) (stan na listopad 2026)
- Strona: https://apify.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/apify

## Kroki

1. claude.ai lub Desktop: wejdź w Settings > Connectors, znajdź Apify i kliknij Connect (albo Add custom connector z adresem https://mcp.apify.com).
2. Zaloguj się do Apify w przeglądarce i zatwierdź dostęp.
3. Claude Code: uruchom claude mcp add apify "https://mcp.apify.com" -t http, przy pierwszym użyciu otworzy się logowanie Apify.
4. Opcja lokalna: wymaga Node.js 22+, uruchom npx -y @apify/actors-mcp-server i ustaw APIFY_TOKEN w sekcji env konfiguracji klienta.
5. Poproś Claude o wyszukanie Actora w Apify Store i uruchomienie go ze schematem wejścia.

```bash
claude mcp add apify "https://mcp.apify.com" -t http
```

Adres serwera MCP: `https://mcp.apify.com`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Apify do Claude Code.
Apify jest w katalogu konektorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Konektory). Jeśli w Claude Code, podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add apify "https://mcp.apify.com" -t http
Adres serwera MCP: https://mcp.apify.com
Dokumentacja: https://github.com/apify/apify-mcp-server
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Plan darmowy daje 5 USD zużycia platformy miesięcznie. Po wyczerpaniu dostęp jest blokowany do następnego cyklu.
- Actory w Apify Store tworzą niezależni autorzy, a uruchomienia są płatne według zużycia, więc przed dużym przebiegiem sprawdź schemat wejścia i koszt.

## Źródła

- https://claude.com/marketplace/connectors/apify
- https://github.com/apify/apify-mcp-server
- https://www.apify.com/pricing
