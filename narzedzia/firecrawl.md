# Firecrawl: jak podłączyć do Claude

Firecrawl to usługa do wyszukiwania, scrapingu i crawlowania stron internetowych z wynikiem gotowym dla modeli AI. Claude pobiera treść dowolnej strony internetowej w czystym formacie.

- Sposób: Connector w Claude
- Logowanie: OAuth
- Darmowy plan: tak
- Płatny plan od: 19 USD/mies. (Hobby, 5000 kredytów) (stan na listopad 2026)
- Strona: https://www.firecrawl.dev
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/firecrawl

## Kroki

1. W claude.ai lub Claude Desktop wejdź w Customize, potem Connectors, wyszukaj Firecrawl i kliknij Connect.
2. Zaloguj się do Firecrawl, wybierz zespół i zatwierdź dostęp.
3. W Claude Code uruchom komendę claude mcp add, potem wpisz /mcp, wybierz firecrawl i zaloguj się w przeglądarce.
4. Upewnij się, że aktywny jest tylko jeden serwer o nazwie firecrawl.

```bash
claude mcp add --transport http firecrawl https://mcp.firecrawl.dev/v2/mcp-oauth
```

Adres serwera MCP: `https://mcp.firecrawl.dev/v2/mcp-oauth`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Firecrawl do Claude Code.
Firecrawl jest w katalogu connectorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Connectors). Jeśli w Claude Code, podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add --transport http firecrawl https://mcp.firecrawl.dev/v2/mcp-oauth
Adres serwera MCP: https://mcp.firecrawl.dev/v2/mcp-oauth
Dokumentacja: https://docs.firecrawl.dev/mcp-server
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Plan Free ma 1000 kredytów miesięcznie i nie wymaga karty. Dostępny jest też tryb bez konta i bez klucza (Search, Scrape, Parse w dziennych limitach).
- Alternatywa dla logowania: klucz API i adres https://mcp.firecrawl.dev/v2/mcp z tokenem Bearer. Nigdy nie wklejaj klucza do chatu.
- Adres w katalogu Claude (https://mcp.firecrawl.dev/v2/mcp-search) różni się od adresu z dokumentacji do ręcznego dodania (mcp-oauth). Na Team i Enterprise connector musi najpierw dodać Owner.

## Źródła

- https://docs.firecrawl.dev/mcp-server
- https://docs.firecrawl.dev/quickstarts/claude-desktop
- https://docs.firecrawl.dev/quickstarts/claude-code.md
- https://claude.com/marketplace/connectors/firecrawl
- https://www.firecrawl.dev/pricing
