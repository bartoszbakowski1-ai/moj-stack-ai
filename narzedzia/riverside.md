# Riverside: jak podłączyć do Claude

Riverside to platforma do nagrywania i edycji podcastów oraz wideo, a jej MCP pozwala Claude przeszukiwać transkrypcje, ciąć klipy i publikować w mediach społecznościowych. Nagrywasz rozmowy i podcasty, a transkrypcje dajesz Claude do dalszej pracy.

- Sposób: Connector w Claude
- Logowanie: OAuth
- Darmowy plan: okres próbny
- Płatny plan od: 34 USD/mies. (Grow, rozliczenie roczne; 39 USD przy płatności miesięcznej) (stan na listopad 2026)
- Strona: https://riverside.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/riverside

## Kroki

1. Zaloguj się do Riverside na komputerze i upewnij się, że masz plan Grow, Webinar lub Business.
2. W Riverside kliknij menu konta w lewym dolnym rogu > Settings > Your account > MCP.
3. Przy Claude kliknij Connect, co otworzy connector Riverside w katalogu Claude.
4. Kliknij Connect to Claude i poczekaj na status Connected.
5. W Claude Code uruchom polecenie podane niżej, potem /mcp i zaloguj się.
6. Aby publikować posty przez Claude, najpierw podłącz platformy społecznościowe w panelu Riverside.

```bash
claude mcp add --transport http --scope user riverside https://mcp.riverside.com/mcp
```

Adres serwera MCP: `https://mcp.riverside.com/mcp`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Riverside do Claude Code.
Riverside jest w katalogu connectorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Connectors). Jeśli w Claude Code, podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add --transport http --scope user riverside https://mcp.riverside.com/mcp
Adres serwera MCP: https://mcp.riverside.com/mcp
Dokumentacja: https://support.riverside.com/hc/en-us/articles/37803607978141-Connect-to-Riverside-MCP
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- MCP jest w planach Grow, Webinar i Business. Niższe plany (Free, Pro) nie mają MCP wg strony pomocy. Płatne plany mają 14-dniowy trial.
- Agent zawsze tworzy nową edycję zamiast nadpisywać oryginał, ale eksportowanych plików sam nie pobierze. Planowanie sesji nagraniowych zostaje w Riverside.
- Na darmowym koncie Claude możesz dodać tylko jeden connector, a na Team i Enterprise admin organizacji musi go najpierw dodać.

## Źródła

- https://support.riverside.com/hc/en-us/articles/37803607978141-Connect-to-Riverside-MCP
- https://riverside.com/mcp
- https://riverside.com/pricing
- https://claude.com/marketplace/connectors/riverside
