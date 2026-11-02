# Shopify: jak podłączyć do Claude

Shopify to platforma do tworzenia i prowadzenia sklepów internetowych. Claude zarządza produktami, zamówieniami i treściami sklepu.

- Sposób: Connector w Claude
- Logowanie: zatwierdzenie dostępu w panelu Shopify (OAuth niepotwierdzone)
- Darmowy plan: okres próbny
- Płatny plan od: 79 PLN/mies. (Basic, rozliczenie roczne; 109 PLN miesięcznie) (stan na listopad 2026)
- Strona: https://www.shopify.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/shopify

## Kroki

1. W claude.ai dodaj connector Shopify z katalogu (Customize, Connectors) lub poproś Claude o Shopify w chacie.
2. Użyj przeglądarki desktopowej do konfiguracji.
3. Zatwierdź dostęp do danych w panelu Shopify, do którego zostaniesz przekierowany. Domyślnie tylko odczyt, zapis wymaga Twojej zgody.
4. W rozmowie wymień Shopify z nazwy i sprawdź, że connector jest włączony dla chatu.

Adres serwera MCP: `https://setup.shopify.com/mcp`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Shopify do Claude Code.
Shopify jest w katalogu connectorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Connectors). Jeśli w Claude Code, podłącz go jako serwer MCP.
Adres serwera MCP: https://setup.shopify.com/mcp
Dokumentacja: https://help.shopify.com/en/manual/ai-powered-tools/connecting-ai-tools/shopify-connector-for-claude
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Connector nie ma dodatkowej opłaty po stronie Shopify, ale potrzebujesz aktywnej subskrypcji Claude i sklepu (lub utworzysz go z poziomu Claude). Ceny wzięte ze strony wyświetlonej dla Polski: 3 dni za darmo, potem 4 PLN/mies. przez 3 miesiące.
- Claude nie zmieni planu, płatności, podatków ani domen, nie edytuje opublikowanego motywu, nie wystawia zwrotów i nie anuluje zamówień. Zamówienia i klienci są tylko do odczytu.
- Dla Claude Code Shopify oferuje osobne narzędzia dla deweloperów: claude mcp add --transport stdio shopify-dev-mcp -- npx -y @shopify/dev-mcp@latest oraz claude plugin install shopify-ai-toolkit@claude-plugins-official. Oficjalna strona connectora nie opisuje Claude Code.

## Źródła

- https://help.shopify.com/en/manual/ai-powered-tools/connecting-ai-tools/shopify-connector-for-claude
- https://help.shopify.com/en/manual/apps/connecting-ai-tools
- https://claude.com/marketplace/connectors/shopify
- https://shopify.dev/docs/apps/build/devmcp
- https://www.shopify.com/pricing
