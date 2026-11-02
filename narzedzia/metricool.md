# Metricool: jak podłączyć do Claude

Metricool to narzędzie do planowania postów i analityki w mediach społecznościowych, które z Claude pozwala planować publikacje i czytać statystyki. Claude planuje posty i czyta statystyki social mediów.

- Sposób: Konektor w Claude
- Logowanie: OAuth
- Darmowy plan: tak
- Płatny plan od: 16 EUR/mies. (Starter, 5 marek, rozliczenie roczne, ceny netto bez VAT) (stan na listopad 2026)
- Strona: https://metricool.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/metricool

## Kroki

1. W claude.ai lub Claude Desktop wejdź w Settings > Connectors > Add > Browse connectors i wyszukaj Metricool.
2. Kliknij Connect to Claude na stronie connectora.
3. Sprawdź prośbę o uprawnienia i kliknij Grant access po zalogowaniu do Metricool.
4. Upewnij się, że Metricool ma status Connected (klucz API nie jest potrzebny).
5. W Claude Code uruchom polecenie podane niżej, wpisz claude, potem /mcp, wybierz Metricool i Authenticate.
6. Zatwierdź dostęp w przeglądarce (Grant access) i wróć do Claude Code.

```bash
claude mcp add --transport http metricool https://ai.metricool.com/mcp
```

Adres serwera MCP: `https://ai.metricool.com/mcp`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Metricool do Claude Code.
Metricool jest w katalogu konektorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Konektory). Jeśli w Claude Code, podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add --transport http metricool https://ai.metricool.com/mcp
Adres serwera MCP: https://ai.metricool.com/mcp
Dokumentacja: https://help.metricool.com/how-to-connect-metricools-mcp-with-claude-0l84v
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- MCP działa na każdym planie Metricool, także Free (1 marka, do 20 postów miesięcznie, bez LinkedIn i X), ale obowiązują limity planu.
- Według Metricool Claude Code wymaga subskrypcji Claude Pro lub Max, a darmowe konto Claude pozwala na jeden connector naraz.
- Narzędzia z katalogu dotyczą m.in. planowania i edycji postów, więc przed publikacją sprawdzaj, co Claude zaplanował.

## Źródła

- https://help.metricool.com/how-to-connect-metricools-mcp-eqp9h
- https://help.metricool.com/how-to-connect-metricools-mcp-with-claude-0l84v
- https://claude.com/marketplace/connectors/metricool-social-media-management
- https://metricool.com/pricing/
