# EasyTools (Easycart i Easymail): jak podłączyć do Claude

Polska platforma dla twórców do sprzedaży produktów cyfrowych (checkout Easycart, strony, kursy, e-maile Easymail), z własnym serwerem MCP. Claude zarządza sklepem, produktami, mailingiem i kursami w EasyTools.

- Sposób: Serwer MCP (adres)
- Logowanie: OAuth
- Darmowy plan: okres próbny
- Płatny plan od: 99 zł/mies. netto (Starter, prowizja 3%); 14 dni próby (stan na listopad 2026)
- Strona: https://www.easy.tools/pl
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/easytools

## Kroki

1. Claude Desktop: Settings > Connectors > Add > Add custom connector, nazwa Easytools, adres https://mcp.easy.tools.
2. Kliknij Add, zaloguj się do easycart i zatwierdź połączenie, potem wróć do Claude.
3. Claude Code z OAuth: dodaj serwer bez nagłówka (claude mcp add --transport http easytools https://mcp.easy.tools), potem /mcp i Authenticate.
4. Claude Code z tokenem: wygeneruj token w cart.easy.tools/creator/store-settings/developer i użyj komendy z nagłówkiem Authorization: Bearer.
5. Do narzędzi Easymail potrzebujesz uprawnienia Manage Easymail API keys na sklepie.

```bash
claude mcp add --transport http easytools https://mcp.easy.tools --header "Authorization: Bearer YOUR_EASYCART_TOKEN"
```

Adres serwera MCP: `https://mcp.easy.tools`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz EasyTools (Easycart i Easymail) do Claude Code.
Podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add --transport http easytools https://mcp.easy.tools --header "Authorization: Bearer YOUR_EASYCART_TOKEN"
Adres serwera MCP: https://mcp.easy.tools
Dokumentacja: https://developers.easy.tools/mcp/connecting
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Strona główna easy.tools w FAQ wspomina o planie darmowym z checkoutem, a strona cennika mówi, że darmowego planu nie ma i jest 14-dniowa próba. Dane z cennika są nowsze i bardziej szczegółowe, ale warto zweryfikować przed publikacją.
- Dokumentacja nie opisuje kroków dla claude.ai w przeglądarce (tylko Desktop i Claude Code) ani wpisu w katalogu Anthropic. Wymagań planu dla MCP nie podano. Domena easytools.pl przekierowuje na www.easy.tools/pl.
- Limit: 100 zapytań na 60 sekund (osobno na sklep dla easycart i na konto dla easymail). Narzędzia zapisu czekają na zatwierdzenie użytkownika.

## Źródła

- https://developers.easy.tools/mcp/
- https://developers.easy.tools/mcp/connecting
- https://www.easy.tools/changelog/easytools-mcp-server
- https://www.easy.tools/pl
- https://www.easy.tools/pl/cennik
