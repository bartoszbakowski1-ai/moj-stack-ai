# Grok (xAI): jak podłączyć do Claude

Grok to asystent AI i rodzina modeli firmy xAI, dostępne w aplikacji, na X oraz przez płatne API. Drugi model do tekstów, grafik i wideo, gdy chcesz porównać wynik z Claude.

- Sposób: Klucz API
- Logowanie: klucz API
- Darmowy plan: tak
- Płatny plan od: 8 USD/mies. (plan Plus subskrypcji X; API jest rozliczane osobno za zużycie) (stan na listopad 2026)
- Strona: https://x.ai
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/grok

## Kroki

1. Załóż konto na console.x.ai i doładuj konto kredytami (bez kredytów API nie działa).
2. Utwórz klucz na stronie API Keys w konsoli xAI.
3. Zapisz klucz jako zmienną środowiskową XAI_API_KEY.
4. Wywołuj API pod adresem https://api.x.ai/v1 z nagłówkiem Authorization: Bearer, na przykład ze skryptu, który uruchamia Claude Code.

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Grok (xAI) do Claude Code.
Grok (xAI) nie ma oficjalnego serwera MCP. Użyj klucza API: trzymaj go w pliku .env poza repozytorium.
Dokumentacja: https://docs.x.ai/developers/quickstart
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Nie znalazłem oficjalnego connectora ani serwera MCP xAI dla Claude. Dokumentacja xAI opisuje tylko, że Grok sam łączy się z zewnętrznymi serwerami MCP (Remote MCP Tools), i nie wspomina o Claude.
- Subskrypcja Grok i API to osobne produkty: dokumentacja cennika subskrypcji nie wspomina o dostępie do API, a API wymaga kredytów. Nieoficjalne mostki MCP istnieją, ale nie są polecane jako źródło.
- Darmowy plan dotyczy aplikacji Grok z limitami, a nie API (darmowe kredyty API niepotwierdzone).

## Źródła

- https://docs.x.ai/docs/guides/tools/remote-mcp-tools
- https://docs.x.ai/developers/tools/remote-mcp
- https://docs.x.ai/docs/overview
- https://docs.x.ai/developers/quickstart
- https://docs.x.ai/x-subscription/pricing
