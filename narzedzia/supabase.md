# Supabase: jak podłączyć do Claude

Supabase to platforma backendowa z bazą Postgres, logowaniem użytkowników, storage i funkcjami brzegowymi. Claude czyta i zmienia bazę danych, na przykład listę kontaktów albo leadów.

- Sposób: Connector w Claude
- Logowanie: OAuth
- Darmowy plan: tak
- Płatny plan od: 25 USD/mies. (Pro) (stan na listopad 2026)
- Strona: https://supabase.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/supabase

## Kroki

1. W claude.ai wejdź w Customize, potem Connectors, i dodaj Supabase z katalogu.
2. Zaloguj się do Supabase w przeglądarce i wybierz organizację z projektem (token PAT nie jest potrzebny).
3. W Claude Code uruchom komendę claude mcp add, potem w zwykłym terminalu wpisz claude /mcp, wybierz supabase i Authenticate.
4. Ogranicz zakres dodając do URL parametry: ?project_ref=ID (jeden projekt) i ?read_only=true (tylko odczyt).

```bash
claude mcp add --scope project --transport http supabase "https://mcp.supabase.com/mcp"
```

Adres serwera MCP: `https://mcp.supabase.com/mcp`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Supabase do Claude Code.
Supabase jest w katalogu connectorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Connectors). Jeśli w Claude Code, podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add --scope project --transport http supabase "https://mcp.supabase.com/mcp"
Adres serwera MCP: https://mcp.supabase.com/mcp
Dokumentacja: https://supabase.com/docs/guides/getting-started/mcp
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Serwer działa z uprawnieniami dewelopera, więc dokumentacja zaleca ograniczenie do jednego projektu, tryb tylko do odczytu i ręczne zatwierdzanie wywołań (ryzyko prompt injection).
- Darmowe projekty Supabase są pauzowane po tygodniu braku aktywności.

## Źródła

- https://supabase.com/docs/guides/getting-started/mcp
- https://claude.com/marketplace/connectors/supabase
- https://supabase.com/pricing
