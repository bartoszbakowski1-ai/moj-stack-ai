# Gmail: jak podłączyć do Claude

Poczta Google, którą Claude może przeszukiwać i podsumowywać po podłączeniu connectora (Google udostępnia też własny serwer MCP w wersji Developer Preview). Claude szuka maili, streszcza wątki i przygotowuje szkice odpowiedzi.

- Sposób: Connector w Claude
- Logowanie: OAuth
- Darmowy plan: tak
- Płatny plan od: konto Gmail darmowe; Google Workspace Business Starter od 31,50 zł/mies. za użytkownika netto (14 dni próby) (stan na listopad 2026)
- Strona: https://workspace.google.com/intl/en/gmail/
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/gmail

## Kroki

1. Otwórz claude.ai > Customize > Connectors i przy Gmail kliknij Connect.
2. Zaloguj się na konto Google i zaakceptuj uprawnienia (przycisk zmieni się na Disconnect).
3. W rozmowie kliknij plus > Connectors i włącz Gmail.
4. Na Team i Enterprise najpierw Owner włącza connector dla organizacji.
5. W Claude Code connectory z claude.ai są widoczne w /mcp (podłączenie wykonuje się w ustawieniach claude.ai).

Adres serwera MCP: `https://gmailmcp.googleapis.com/mcp/v1`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Gmail do Claude Code.
Gmail jest w katalogu connectorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Connectors). Jeśli w Claude Code, podłącz go jako serwer MCP.
Adres serwera MCP: https://gmailmcp.googleapis.com/mcp/v1
Dokumentacja: https://claude.com/docs/connectors/google/gmail
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Dokumentacja claude.com mówi, że connector jest tylko do odczytu i wyszukiwania (bez tworzenia i wysyłania), a plany to Pro, Max, Ultra, Team i Enterprise. Strona wpisu w katalogu wymienia 29 narzędzi, w tym create_draft i send_message. Aktualny zakres niepotwierdzony, sprawdź przed publikacją.
- Ręczna ścieżka Google (Developer Preview): własny projekt Google Cloud, włączone gmailmcp.googleapis.com, klient OAuth z zaznaczonym 'Use this client for an AI-powered agent' i redirect https://claude.ai/api/mcp/auth_callback, dodany jako custom connector. To nie jest potrzebne przy connectorze z katalogu.
- E-maile od nieznanych nadawców mogą zawierać ukryte instrukcje (prompt injection). Przeglądaj akcje Claude i nie dawaj mu zatwierdzania bez kontroli.

## Źródła

- https://claude.com/marketplace/connectors/gmail
- https://claude.com/docs/connectors/google/gmail
- https://developers.google.com/workspace/gmail/api/guides/configure-mcp-server
- https://workspace.google.com/pricing
- https://workspace.google.com/intl/en/gmail/
