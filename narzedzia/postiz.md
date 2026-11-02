# Postiz: jak podłączyć do Claude

Postiz to open-source'owe narzędzie (AGPL-3.0) do planowania postów w wielu sieciach społecznościowych, dostępne jako chmura lub self-hosting. Claude planuje posty w social mediach przez otwartoźródłowy harmonogram.

- Sposób: Konektor w Claude
- Logowanie: OAuth
- Darmowy plan: okres próbny
- Płatny plan od: 29 USD/mies. (Standard, 5 kanałów; 278 USD/rok) (stan na listopad 2026)
- Strona: https://postiz.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/postiz

## Kroki

1. Załóż konto w Postiz Cloud i wystartuj 7-dniowy trial albo uruchom własną instancję (Docker).
2. Podłącz swoje kanały społecznościowe w panelu Postiz.
3. W Claude wejdź w Customize > Connectors, wyszukaj Postiz i kliknij Connect to Claude (oznaczenie Community).
4. Alternatywa: wygeneruj klucz API w Postiz (Settings > Developers > Public API) i użyj adresu https://mcp.postiz.com/mcp z nagłówkiem Authorization: Bearer klucz.
5. Przy self-hostingu zamień host na własny serwer; endpointy to /mcp, /mcp/:apiKey i /mcp-oauth.
6. Sprawdź połączenie prośbą: wylistuj moje podłączone konta społecznościowe.

```bash
claude mcp add --transport http postiz https://mcp.postiz.com/mcp --header "Authorization: Bearer TWOJ_KLUCZ_API"
```

Adres serwera MCP: `https://mcp.postiz.com/mcp-oauth-claude`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Postiz do Claude Code.
Postiz jest w katalogu konektorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Konektory). Jeśli w Claude Code, podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add --transport http postiz https://mcp.postiz.com/mcp --header "Authorization: Bearer TWOJ_KLUCZ_API"
Adres serwera MCP: https://mcp.postiz.com/mcp-oauth-claude
Dokumentacja: https://docs.postiz.com/mcp/setup.md
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- To connector Community w katalogu Claude: ma automatyczne testy, ale nie jest zweryfikowany przez Anthropic.
- Chmura nie ma planu darmowego (7 dni trialu, API i MCP w każdym z czterech planów). Koszt hostingu własnej instancji niepotwierdzony, kod jest na licencji AGPL-3.0.
- Dokumentacja Postiz podaje dla Claude Code komendę z flagą --url, która różni się od udokumentowanej składni Claude Code, dlatego niżej jest wariant zgodny z dokumentacją Claude Code.

## Źródła

- https://claude.ai/directory/postiz
- https://docs.postiz.com
- https://docs.postiz.com/llms.txt
- https://docs.postiz.com/mcp/introduction.md
- https://docs.postiz.com/mcp/setup.md
- https://docs.postiz.com/cloud/plans.md
- https://postiz.com/pricing
- https://github.com/gitroomhq/postiz-app
- https://code.claude.com/docs/en/mcp
