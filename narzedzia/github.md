# GitHub: jak podłączyć do Claude

GitHub to platforma do hostowania kodu, pracy zespołowej i automatyzacji nad repozytoriami Git. Claude czyta repozytoria, zakłada gałęzie i pull requesty, przegląda kod.

- Sposób: Serwer MCP (adres)
- Logowanie: token
- Darmowy plan: tak
- Płatny plan od: 4 USD/użytkownik/mies. (Team) (stan na listopad 2026)
- Strona: https://github.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/github

## Kroki

1. Najprościej w claude.ai: wejdź w Customize, potem Connectors, wybierz GitHub Integration i kliknij Connect, żeby dodawać repozytoria do chatu lub projektu.
2. Dla pełnego dostępu (issues, pull requesty) utwórz osobisty token dostępu (PAT) na GitHub.
3. W terminalu uruchom komendę claude mcp add z adresem https://api.githubcopilot.com/mcp i nagłówkiem Authorization Bearer z tokenem (dodaj --scope user dla wszystkich projektów).
4. Zrestartuj Claude Code i sprawdź połączenie komendą claude mcp list.

```bash
claude mcp add --transport http github https://api.githubcopilot.com/mcp -H "Authorization: Bearer YOUR_GITHUB_PAT"
```

Adres serwera MCP: `https://api.githubcopilot.com/mcp/`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz GitHub do Claude Code.
Podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add --transport http github https://api.githubcopilot.com/mcp -H "Authorization: Bearer YOUR_GITHUB_PAT"
Adres serwera MCP: https://api.githubcopilot.com/mcp/
Dokumentacja: https://github.com/github/github-mcp-server
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Wbudowana integracja GitHub w claude.ai jest natywna (nie MCP), działa na każdym planie, ale czyta tylko pliki i gałęzie, bez historii commitów, pull requestów i issues. Do edycji kodu i PR służy Claude Code.
- Zdalny serwer GitHub MCP nie jest wspierany w Claude Desktop wg instrukcji GitHub, tam trzeba użyć lokalnego Dockera (obraz ghcr.io/github/github-mcp-server). Czy GitHub MCP jest osobną pozycją w katalogu Claude, nie potwierdziłem.
- Token PAT traktuj jak hasło, nadaj minimalne zakresy (repo, read:packages, read:org wg dokumentacji GitHub).

## Źródła

- https://github.com/github/github-mcp-server
- https://raw.githubusercontent.com/github/github-mcp-server/main/docs/installation-guides/install-claude.md
- https://claude.com/docs/connectors/github/index.md
- https://claude.com/docs/third-party/claude-desktop/connectors-github
- https://github.com/pricing
