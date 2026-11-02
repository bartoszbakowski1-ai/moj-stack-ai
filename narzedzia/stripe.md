# Stripe: jak podłączyć do Claude

Platforma płatności online, której oficjalny serwer MCP pozwala Claude odczytywać i modyfikować klientów, płatności, faktury, subskrypcje i produkty. Claude sprawdza płatności, klientów i tworzy linki do płatności.

- Sposób: Connector w Claude
- Logowanie: OAuth
- Darmowy plan: tak
- Płatny plan od: brak abonamentu, prowizja od transakcji (Polska: 1,5% + 1,00 zł dla standardowych kart EOG) (stan na listopad 2026)
- Strona: https://stripe.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/stripe

## Kroki

1. claude.ai lub Desktop: otwórz wpis Stripe w katalogu, wybierz Connect to Claude i zaloguj się do Stripe w oknie OAuth.
2. W rozmowie kliknij plus, wybierz Connectors i włącz Stripe. Na Team i Enterprise najpierw właściciel dodaje connector do przestrzeni.
3. Claude Code: uruchom claude mcp add --transport http stripe https://mcp.stripe.com/, potem /mcp i uwierzytelnij przez OAuth.
4. W OAuth wybierz konta live lub sandbox i nadaj osobne uprawnienia dla każdego środowiska.
5. Dla autonomicznych agentów użyj agent API key jako Bearer w nagłówku Authorization (zmienna środowiskowa w .mcp.json).

```bash
claude mcp add --transport http stripe https://mcp.stripe.com/
```

Adres serwera MCP: `https://mcp.stripe.com`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Stripe do Claude Code.
Stripe jest w katalogu connectorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Connectors). Jeśli w Claude Code, podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add --transport http stripe https://mcp.stripe.com/
Adres serwera MCP: https://mcp.stripe.com
Dokumentacja: https://docs.stripe.com/mcp
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Do 30.11.2026 trzeba przejść z pełnych kluczy secret i restricted API keys bez znacznika Agent na agent API keys lub OAuth. Od grudnia 2026 Stripe MCP odrzuca takie klucze (401).
- Serwer ma narzędzia finansowe (Treasury: send_money, transfer_money, convert_currency, refund). Część akcji wymaga potwierdzenia w Dashboard (Human confirmation). Zacznij od sandboxa i włącz zatwierdzanie narzędzi.
- Admin może włączyć lub wyłączyć dostęp MCP dla całego zespołu w Dashboard (osobno live i sandbox).

## Źródła

- https://claude.com/marketplace/connectors/stripe
- https://docs.stripe.com/mcp
- https://stripe.com/pricing
