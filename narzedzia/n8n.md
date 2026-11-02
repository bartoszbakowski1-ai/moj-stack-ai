# n8n: jak podłączyć do Claude

Platforma do automatyzacji workflow (self-hosted lub w chmurze), która udostępnia własną instancję jako serwer MCP dla Claude. Claude buduje, uruchamia i poprawia automatyzacje w n8n.

- Sposób: Connector w Claude
- Logowanie: OAuth
- Darmowy plan: okres próbny
- Płatny plan od: 20 EUR/mies. (Cloud Starter, rozliczane rocznie); wersja self-hosted Community Edition dostępna na GitHub (cena niepotwierdzona na stronie cennika) (stan na listopad 2026)
- Strona: https://n8n.io
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/n8n

## Kroki

1. Jako właściciel lub admin instancji wejdź w Settings > Instance-level MCP i włącz Enable MCP access.
2. W ustawieniach wybranych workflow włącz Available in MCP (klient widzi tylko takie workflow).
3. Kliknij Connect a client, na zakładce OAuth wybierz Claude i skopiuj Server URL (kończy się na /mcp-server/http).
4. claude.ai lub Desktop: Settings > Connectors > Add custom connector (albo One-click setup w n8n), wklej Server URL i zatwierdź dostęp w n8n.
5. Claude Code: uruchom komendę z góry, potem /mcp i wybierz n8n, aby dokończyć OAuth. Wariant z kluczem: dodaj nagłówek Authorization: Bearer <TOKEN> z zakładki API key.
6. Osobna opcja: węzeł MCP Server Trigger w workflow wystawia własny adres MCP (test i produkcyjny) z uwierzytelnianiem None, Bearer lub Header.
7. Chcesz dać Claude tylko jeden workflow? Dodaj w nim węzeł MCP Server Trigger: dostaje własny adres, a narzędzia z tego workflow stają się narzędziami Claude.

```bash
claude mcp add --transport http n8n https://<twoja-domena-n8n>/mcp-server/http
```

Adres serwera MCP: `https://<twoja-domena-n8n>/mcp-server/http`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz n8n do Claude Code.
n8n jest w katalogu connectorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Connectors). Jeśli w Claude Code, podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add --transport http n8n https://<twoja-domena-n8n>/mcp-server/http
Adres serwera MCP: https://<twoja-domena-n8n>/mcp-server/http
Dokumentacja: https://docs.n8n.io/connect/connect-to-n8n-mcp-server
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Klienci chmurowi (claude.ai) wymagają publicznie dostępnej instancji n8n. Kroki per klient wymagają n8n 2.33.0 lub nowszego.
- Każdy podłączony klient widzi wszystkie workflow oznaczone jako Available in MCP, nie da się ograniczyć widoczności do jednego klienta. Klucze API nie pojawiają się na liście połączonych klientów, odcina się je tylko przez rotację tokena.
- Wpis n8n w katalogu Anthropic istnieje (n8n GmbH, 27 narzędzi), ale adres MCP jest zawsze adresem twojej instancji. Strona katalogu nie podaje URL, więc zależność wpisu od instancji jest niepotwierdzona.

## Źródła

- https://claude.com/marketplace/connectors/n8n
- https://docs.n8n.io/advanced-ai/mcp/accessing-n8n-mcp-server/
- https://docs.n8n.io/connect/connect-to-n8n-mcp-server
- https://docs.n8n.io/connect/connect-to-n8n-mcp-server/mcp-client-examples
- https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-langchain.mcptrigger
- https://n8n.io/pricing
