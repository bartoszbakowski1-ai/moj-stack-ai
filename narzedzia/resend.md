# Resend: jak podłączyć do Claude

Usługa do wysyłki e-maili transakcyjnych i marketingowych przez API, z oficjalnym serwerem MCP (domeny, wysyłka, kontakty, broadcasty). Claude wysyła maile transakcyjne i sprawdza, co doszło do odbiorców.

- Sposób: Connector w Claude
- Logowanie: OAuth
- Darmowy plan: tak
- Płatny plan od: 20 USD/mies. (Pro, 50 000 e-maili) (stan na listopad 2026)
- Strona: https://resend.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/resend

## Kroki

1. claude.ai lub Desktop: wejdź w Settings > Connectors, znajdź Resend (wpis w katalogu) i kliknij Connect; alternatywnie Add custom connector z adresem https://mcp.resend.com/mcp.
2. Zaloguj się do Resend w przeglądarce i zatwierdź dostęp (OAuth).
3. Claude Code: uruchom claude plugin install resend@claude-plugins-official, potem /mcp, wybierz resend i dokończ logowanie.
4. Wariant z kluczem API (serwery, CI): claude mcp add --transport http resend https://mcp.resend.com/mcp --header "Authorization: Bearer re_xxxxxxxxx".
5. Wariant lokalny: npx -y resend-mcp z RESEND_API_KEY w env (wymaga zweryfikowanej domeny).

```bash
claude plugin install resend@claude-plugins-official
```

Adres serwera MCP: `https://mcp.resend.com/mcp`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Resend do Claude Code.
Resend jest w katalogu connectorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Connectors). Jeśli w Claude Code, podłącz go jako serwer MCP.
Oficjalne polecenie: claude plugin install resend@claude-plugins-official
Adres serwera MCP: https://mcp.resend.com/mcp
Dokumentacja: https://resend.com/docs/mcp-server
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Narzędzie wysyłające e-maile działa na prawdziwej domenie i prawdziwych odbiorcach. Wymagaj zatwierdzania wywołań, szczególnie dla wysyłki i broadcastów.
- Plan darmowy: 100 e-maili dziennie, 3 domeny. Marketing Free: 1000 kontaktów. Strona katalogu podaje 85 narzędzi.

## Źródła

- https://claude.com/marketplace/connectors/resend
- https://resend.com/docs/mcp-server
- https://resend.com/pricing
