# Figma: jak podłączyć do Claude

Figma to narzędzie do projektowania interfejsów i współpracy nad designem w przeglądarce. Claude czyta projekty z Figmy i zamienia je na kod strony.

- Sposób: Connector w Claude
- Logowanie: logowanie kontem Figma w przeglądarce (Allow access)
- Darmowy plan: tak
- Płatny plan od: 16 USD/mies. (Professional, miejsce Full; okres rozliczenia niepotwierdzony) (stan na listopad 2026)
- Strona: https://www.figma.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/figma

## Kroki

1. W claude.ai wejdź w Customize, potem Connectors, i dodaj Figma z katalogu.
2. Zaloguj się kontem Figma i kliknij Allow access.
3. W Claude Code najprościej zainstaluj wtyczkę: claude plugin install figma@claude-plugins-official, zrestartuj, wpisz /plugin i zaloguj się.
4. Ręcznie: uruchom komendę claude mcp add, potem /mcp, wybierz figma i Authenticate.

```bash
claude mcp add --transport http figma https://mcp.figma.com/mcp
```

Adres serwera MCP: `https://mcp.figma.com/mcp`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Figma do Claude Code.
Figma jest w katalogu connectorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Connectors). Jeśli w Claude Code, podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add --transport http figma https://mcp.figma.com/mcp
Adres serwera MCP: https://mcp.figma.com/mcp
Dokumentacja: https://help.figma.com/hc/en-us/articles/39888612464151-Claude-Code-and-Figma-Set-up-the-MCP-server
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Zdalny serwer jest dostępny na planach Starter, Professional, Education, Organization, Government i Enterprise. Limity wywołań na planie darmowym niepotwierdzone.
- W Claude i Claude Code narzędzie get_screenshot zwraca na razie opis tekstowy zamiast obrazu.
- Zapis na kanwie wymaga zdalnego serwera i miejsca Full, a funkcja jest w becie.

## Źródła

- https://claude.com/marketplace/connectors/figma
- https://help.figma.com/hc/en-us/articles/32132100833559
- https://help.figma.com/hc/en-us/articles/39888612464151-Claude-Code-and-Figma-Set-up-the-MCP-server
- https://www.figma.com/pricing/
