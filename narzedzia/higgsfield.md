# Higgsfield: jak podłączyć do Claude

Higgsfield to platforma do generowania obrazów, wideo i audio przez AI, którą można sterować z poziomu Claude. Claude zleca wideo i grafiki AI bez przełączania się do kolejnej aplikacji.

- Sposób: Serwer MCP (adres)
- Logowanie: OAuth
- Darmowy plan: tak
- Płatny plan od: 15 USD/mies. (Starter, 200 kredytów) (stan na listopad 2026)
- Strona: https://higgsfield.ai
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/higgsfield

## Kroki

1. W claude.ai lub Claude Desktop wejdź w Customize, potem Connectors.
2. Kliknij Add, potem Add custom connector, nazwij go Higgsfield i wklej URL https://mcp.higgsfield.ai/mcp.
3. Kliknij Connect i zaloguj się w oknie Higgsfield. Klucz API nie jest potrzebny.
4. W chacie otwórz menu plus, potem Connectors i włącz Higgsfield.
5. W Claude Code zainstaluj CLI Higgsfield (npm i -g @higgsfield/cli), zaloguj się komendą higgsfield auth login i dodaj skille: npx skills add higgsfield-ai/skills.

```bash
npm i -g @higgsfield/cli
higgsfield auth login
```

Adres serwera MCP: `https://mcp.higgsfield.ai/mcp`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Higgsfield do Claude Code.
Podłącz go jako serwer MCP.
Oficjalne polecenie: npm i -g @higgsfield/cli
higgsfield auth login
Adres serwera MCP: https://mcp.higgsfield.ai/mcp
Dokumentacja: https://higgsfield.ai/blog/Generate-AI-Videos-From-Claude-with-Higgsfield-MCP
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Każda generacja przez MCP zużywa kredyty po standardowych stawkach, a funkcje unlimited i darmowe generacje działają tylko w aplikacji webowej.
- Na darmowym planie Claude można dodać tylko jeden własny connector, a to, czy sam plan Free Higgsfield pozwala na MCP, nie jest opisane (niepotwierdzone).
- Oficjalna instrukcja dla Claude Code opisuje CLI, a nie dodanie URL MCP komendą claude mcp add. Cena 15 USD może zakładać rozliczenie roczne, strona cennika nie wczytała się w pełni.

## Źródła

- https://higgsfield.ai/blog/Generate-AI-Videos-From-Claude-with-Higgsfield-MCP
- https://higgsfield.ai/creator-hub/help-center/mcp-cli/what-is-higgsfield-mcp
- https://higgsfield.ai/blog/higgsfield-pricing-explained
- https://higgsfield.ai/blog/unlimited-mcp
