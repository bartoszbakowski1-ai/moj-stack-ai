# Hostinger: jak podłączyć do Claude

Dostawca hostingu, domen i serwerów VPS, który ma oficjalny serwer MCP do zarządzania kontem (hosting, domeny, DNS, VPS, billing). Claude zarządza domenami, DNS i serwerem VPS, a przez SSH pracuje bezpośrednio na serwerze.

- Sposób: Serwer MCP (adres)
- Logowanie: OAuth
- Darmowy plan: nie
- Płatny plan od: 6,49 USD/mies. (VPS KVM 1, płatne z góry za 24 mies. = 155,76 USD; odnowienie 11,99 USD/mies.) (stan na listopad 2026)
- Strona: https://www.hostinger.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/hostinger

## Kroki

1. Uruchom w terminalu: claude mcp add --transport http hostinger https://mcp.hostinger.com
2. Otwórz Claude Code i wpisz /mcp, wybierz hostinger i zaloguj się przez przeglądarkę (OAuth).
3. W claude.ai lub Claude Desktop wejdź w Ustawienia > Connectors > Add custom connector i wklej https://mcp.hostinger.com.
4. Alternatywa lokalna (stdio): zainstaluj Node.js 24+, wykonaj npm install -g @hostinger/mcp i ustaw zmienną HOSTINGER_API_TOKEN (token z hPanel > API).
5. Nie masz klucza SSH? Wygeneruj go poleceniem `ssh-keygen -t ed25519`.
6. Dostęp przez SSH do VPS: dodaj klucz publiczny w hPanel (VPS > Settings > SSH keys), potem połącz się ssh root@IP_VPS i pracuj w Claude Code na serwerze.

```bash
claude mcp add --transport http hostinger https://mcp.hostinger.com
```

Adres serwera MCP: `https://mcp.hostinger.com`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Hostinger do Claude Code.
Podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add --transport http hostinger https://mcp.hostinger.com
Adres serwera MCP: https://mcp.hostinger.com
Dokumentacja: https://github.com/hostinger/api-mcp-server
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Serwer MCP daje szerokie uprawnienia (kupno usług, DNS, VPS, billing). Token API dziedziczy uprawnienia użytkownika, który go utworzył, więc włącz zatwierdzanie wywołań narzędzi.
- Starsza nazwa pakietu hostinger-api-mcp i zmienna API_TOKEN pojawiają się w części artykułów pomocy. Aktualny pakiet to @hostinger/mcp, a zmienna to HOSTINGER_API_TOKEN (API_TOKEN jest oznaczona jako przestarzała).
- Hostinger nie opisuje w dokumentacji kroków dla claude.ai ani wpisu w katalogu Anthropic. Komenda dla Claude Code jest podana oficjalnie. Dokładne polecenie ssh dla VPS i port nie są podane w przeczytanych artykułach pomocy (login root podaje tylko artykuł o rozwiązywaniu problemów z SSH).
- SSH daje Claude pełny dostęp do serwera. Przed poleceniami, które coś kasują albo restartują, sprawdzaj, co Claude chce uruchomić.

## Źródła

- https://github.com/hostinger/api-mcp-server
- https://raw.githubusercontent.com/hostinger/api-mcp-server/main/README.md
- https://www.hostinger.com/support/11079316-hostinger-api-mcp-server/
- https://docs.hostinger.com/api-reference/overview
- https://docs.hostinger.com/api-reference/tools.md
- https://docs.hostinger.com/hostinger-connector/overview.md
- https://www.hostinger.com/vps-hosting
- https://www.hostinger.com/support/5723772-how-to-connect-to-your-vps-via-ssh-at-hostinger/
- https://www.hostinger.com/support/5634532-how-to-generate-ssh-keys-and-add-them-to-hpanel
- https://www.hostinger.com/support/4792364-how-to-use-ssh-keys-at-hostinger-vps/
