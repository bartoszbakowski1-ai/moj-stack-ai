# ChatGPT: jak podłączyć do Claude

ChatGPT to asystent AI firmy OpenAI, konkurencyjny wobec Claude. Drugi model obok Claude, do porównania odpowiedzi i zadań, w których jest mocniejszy.

- Sposób: Obok Claude
- Logowanie: brak
- Darmowy plan: tak
- Płatny plan od: 8 USD/mies. (Go, ceny w USA), 20 USD/mies. (Plus) (stan na listopad 2026)
- Strona: https://chatgpt.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/chatgpt

## Kroki

1. Nie ma oficjalnego sposobu, by podłączyć ChatGPT jako narzędzie do Claude.
2. Odwrotny kierunek działa: ChatGPT potrafi dodawać zewnętrzne serwery MCP, więc możesz używać tych samych narzędzi (np. Vercel) w obu aplikacjach.
3. Jeśli potrzebujesz modeli OpenAI w swoim workflow, użyj API OpenAI z kluczem API, to osobny produkt niż ChatGPT.

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz ChatGPT do Claude Code.
ChatGPT nie ma oficjalnego połączenia z Claude. Pokaż mi najprostszy sposób, żeby używać go razem z Claude (eksport, kopiowanie, plik).
Dokumentacja: https://learn.chatgpt.com/docs/extend/mcp
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Oficjalne dokumenty OpenAI opisują Codex i ChatGPT jako klienty MCP (łączące się z serwerami), a nie serwery do podłączenia pod Claude. Czy Codex da się uruchomić jako serwer MCP dla Claude, nie potwierdziłem w oficjalnych źródłach (niepotwierdzone).
- Dokumentacja Vercel pokazuje to samo w drugą stronę: instrukcja dodania serwera MCP do ChatGPT istnieje, ale nie ma odpowiednika "ChatGPT jako narzędzie w Claude".
- Ceny dotyczą USA i mogą się różnić w innych krajach; Pro zaczyna się od 100 USD/mies.

## Źródła

- https://learn.chatgpt.com/docs/extend/mcp?surface=cli
- https://learn.chatgpt.com/docs/pricing
- https://github.com/openai/codex
- https://vercel.com/docs/agent-resources/vercel-mcp
