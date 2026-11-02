# Letterly: jak podłączyć do Claude

Letterly to aplikacja do dyktowania i notatek głosowych, których treść Claude może przeszukiwać, przepisywać, tłumaczyć i tworzyć. Claude czyta Twoje notatki głosowe i robi z nich treści, na przykład newsletter.

- Sposób: Konektor w Claude
- Logowanie: OAuth
- Darmowy plan: tak
- Strona: https://letterly.app
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/letterly

## Kroki

1. Utwórz konto w Letterly (wystarczy darmowe) i nagraj choć jedną notatkę.
2. W claude.ai lub Claude Desktop wejdź w Customize > Connectors i wyszukaj Letterly w katalogu (Discover).
3. Kliknij Connect to Claude i zaloguj się do Letterly (link e-mail, Google albo Apple).
4. Alternatywnie dodaj własny connector (Add custom connector) z adresem https://mcp.letterly.app/mcp.
5. W Claude Code uruchom polecenie podane niżej, potem /mcp, wybierz letterly i Authenticate.
6. Sprawdź połączenie: claude mcp list powinno pokazać letterly.

```bash
claude mcp add --transport http letterly https://mcp.letterly.app/mcp
```

Adres serwera MCP: `https://mcp.letterly.app/mcp`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Letterly do Claude Code.
Letterly jest w katalogu konektorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Konektory). Jeśli w Claude Code, podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add --transport http letterly https://mcp.letterly.app/mcp
Adres serwera MCP: https://mcp.letterly.app/mcp
Dokumentacja: https://letterly.app/mcp
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Letterly na własnych stronach opisuje dodanie jako Add custom connector z URL, a w rejestrze connectorów Claude występuje jako pozycja katalogu, więc obie ścieżki powinny działać.
- Plan Free: 10 notatek, nagrania do 3 minut i 20 dyktowań. Pro (miesięczny, roczny lub dożywotni) znosi te limity, ale ceny nie są podane na oficjalnych stronach, które sprawdziłem. Strona pomocy wspomina o 7-dniowym trialu Pro.
- Wymagany plan Letterly dla MCP niepotwierdzony. Narzędzia usuwające notatki i prompty są dostępne, więc zostaw w Claude potwierdzanie akcji destrukcyjnych.

## Źródła

- https://letterly.app/mcp
- https://letterly.app/mcp/claude/
- https://letterly.app/mcp/claude-code/
- https://letterly.app/mcp/other/
- https://help.letterly.app
- https://letterly.app/
