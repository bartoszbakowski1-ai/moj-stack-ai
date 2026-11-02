# Fireflies: jak podłączyć do Claude

Fireflies to asystent AI, który nagrywa, transkrybuje i streszcza spotkania online, a Claude może na ich podstawie wyciągać wnioski i zadania. Claude czyta transkrypcje i podsumowania spotkań.

- Sposób: Connector w Claude
- Logowanie: OAuth
- Darmowy plan: tak
- Płatny plan od: 10 USD/mies. za użytkownika (Pro, rozliczenie roczne; 18 USD przy płatności miesięcznej) (stan na listopad 2026)
- Strona: https://fireflies.ai
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/fireflies

## Kroki

1. Zaloguj się do Fireflies kontem Google lub Microsoft, którego używasz do spotkań.
2. W claude.ai lub Claude Desktop wejdź w Customize > Connectors, otwórz Discover i wybierz Fireflies.
3. Kliknij Connect (Connect to Claude) i zatwierdź autoryzację OAuth w Fireflies.
4. Alternatywa dla Claude Desktop: weź klucz API z Fireflies (Settings > Developer Settings) i dodaj wpis mcp-remote z nagłówkiem Authorization: Bearer w claude_desktop_config.json.
5. W Claude Code connector dodany w claude.ai pojawia się po zalogowaniu kontem claude.ai (sprawdź w /mcp).
6. W chacie włącz Fireflies przez + > Connectors i poproś o np. podsumowanie ostatniego spotkania.

Adres serwera MCP: `https://api.fireflies.ai/mcp`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Fireflies do Claude Code.
Fireflies jest w katalogu connectorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Connectors). Jeśli w Claude Code, podłącz go jako serwer MCP.
Adres serwera MCP: https://api.fireflies.ai/mcp
Dokumentacja: https://docs.fireflies.ai/getting-started/mcp-configuration
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Które plany Fireflies obejmują MCP, niepotwierdzone w dokumentacji. Narzędzie fireflies_get_rule_executions wymaga Enterprise, a fireflies_search i fireflies_fetch są eksperymentalne.
- Blog Fireflies mówi o płatnym planie Claude (Pro, Team, Enterprise), natomiast dokumentacja Claude mówi, że connectory z katalogu działają na wszystkich planach. Wymóg planu Claude niepotwierdzony.
- Wpis w katalogu Claude pokazuje 3 narzędzia (get_user, get_transcript, get_transcripts), a dokumentacja Fireflies opisuje 19 narzędzi serwera, więc zakres zależy od wersji.

## Źródła

- https://claude.com/marketplace/connectors/fireflies
- https://docs.fireflies.ai/getting-started/mcp-configuration
- https://docs.fireflies.ai/mcp-tools/overview
- https://fireflies.ai/blog/fireflies-claude
- https://guide.fireflies.ai/articles/3039542843-learn-about-fireflies-mcp-server-connect-your-ai-tool
- https://fireflies.ai/blog/fireflies-pricing-which-plan-is-right-for-you
