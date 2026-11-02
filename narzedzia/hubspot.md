# HubSpot: jak podłączyć do Claude

Platforma CRM, marketingu i sprzedaży, której connector dla Claude pozwala czytać i tworzyć kontakty, firmy, deale, zadania i treści marketingowe. Claude czyta i aktualizuje kontakty, firmy i szanse sprzedaży w CRM.

- Sposób: Connector w Claude
- Logowanie: OAuth
- Darmowy plan: tak
- Płatny plan od: 7 USD/mies. za miejsce (Starter, płatne rocznie, promocja dla nowych klientów); 10 USD przy rozliczeniu miesięcznym (stan na listopad 2026)
- Strona: https://www.hubspot.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/hubspot

## Kroki

1. W claude.ai lub Desktop wejdź w Settings > Connectors > Browse i wybierz HubSpot, kliknij Connect.
2. Zaloguj się na wybrane konto HubSpot, zaznacz uprawnienia i kliknij Connect app.
3. W rozmowie kliknij plus > Connectors i włącz HubSpot.
4. Jeśli nie jesteś Super Adminem ani nie masz App Marketplace Access, poproś Super Admina o zatwierdzenie connectora.

Adres serwera MCP: `https://mcp.hubspot.com/anthropic`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz HubSpot do Claude Code.
HubSpot jest w katalogu connectorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Connectors). Jeśli w Claude Code, podłącz go jako serwer MCP.
Adres serwera MCP: https://mcp.hubspot.com/anthropic
Dokumentacja: https://knowledge.hubspot.com/integrations/set-up-and-use-the-hubspot-connector-for-claude
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Pomoc HubSpot wymaga płatnego planu Anthropic (Pro, Max, Team lub Enterprise) i pozwala podłączyć tylko jedno konto HubSpot do jednego konta Claude.
- Ograniczenia: hurtowe tworzenie lub aktualizacja do 10 rekordów naraz, brak usuwania, dane objęte Sensitive Data są niedostępne. Ustaw narzędzia zapisu na Needs Approval.
- Pomoc HubSpot nie opisuje komendy dla Claude Code. Osobny, deweloperski serwer mcp.hubspot.com wymaga aplikacji na nowej platformie deweloperskiej HubSpot (inny sposób niż connector).

## Źródła

- https://claude.com/marketplace/connectors/hubspot
- https://knowledge.hubspot.com/integrations/set-up-and-use-the-hubspot-connector-for-claude
- https://developers.hubspot.com/mcp
- https://www.hubspot.com/pricing/crm
