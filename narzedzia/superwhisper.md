# Superwhisper: jak podłączyć do Claude

Superwhisper to aplikacja do dyktowania głosem na Mac, Windows, iOS i Androida, która wpisuje tekst w dowolnej aplikacji, także w oknie rozmowy z Claude. Dyktujesz zamiast pisać, a tekst trafia prosto do Claude.

- Sposób: Serwer MCP (lokalnie)
- Logowanie: brak
- Darmowy plan: tak
- Płatny plan od: 8,49 USD/mies. (Pro, plan miesięczny; są też opcje roczna i dożywotnia) (stan na listopad 2026)
- Strona: https://superwhisper.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/superwhisper

## Kroki

1. Do samego dyktowania w Claude nie potrzebujesz MCP: Superwhisper wpisuje tekst w dowolnej aplikacji, więc kliknij pole wiadomości w Claude i dyktuj.
2. Do MCP zainstaluj CLI na Macu: curl -fsSL https://superwhisper.com/install-cli.sh | bash.
3. Najprościej włącz Claude w aplikacji: Meeting settings > Agents.
4. Alternatywnie w terminalu uruchom superwhisper mcp install claude-code (albo claude-desktop).
5. Sprawdź połączone aplikacje komendą superwhisper mcp status.
6. Poproś Claude o przeszukanie historii dyktowań lub spotkań; serwer działa lokalnie przez stdio.

```bash
superwhisper mcp install claude-code
```

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Superwhisper do Claude Code.
Podłącz go jako serwer MCP.
Oficjalne polecenie: superwhisper mcp install claude-code
Dokumentacja: https://superwhisper.com/docs/get-started/cli
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- CLI i serwer MCP działają tylko na macOS. Transkrypcja plików (transcribe) wymaga Pro, a czy sam MCP wymaga płatnego planu, jest niepotwierdzone.
- Superwhisper nie ma oficjalnego connectora w katalogu Claude (wyszukiwanie w katalogu nie dało wyników), więc to lokalny serwer MCP, nie zdalny.
- Treści odczytane przez Claude trafiają do modelu i podlegają jego ustawieniom prywatności.

## Źródła

- https://superwhisper.com/docs/get-started/cli
- https://superwhisper.com/blog/cli-mcp
- https://superwhisper.com
- https://claude.ai/directory?q=superwhisper
