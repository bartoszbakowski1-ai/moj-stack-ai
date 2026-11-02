# Kit (ConvertKit): jak podłączyć do Claude

Platforma e-mail marketingu dla twórców (newslettery, sekwencje, formularze, landing page), dawniej ConvertKit. Claude zarządza subskrybentami, tagami i newsletterem w Kit.

- Sposób: Konektor w Claude
- Logowanie: OAuth
- Darmowy plan: okres próbny
- Płatny plan od: 33 USD/mies. (Creator, 1000 subskrybentów, rozliczane rocznie = 390 USD/rok) (stan na listopad 2026)
- Strona: https://kit.com
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/kit

## Kroki

1. Upewnij się, że masz płatne konto Kit (Creator lub Creator Pro) i konto Claude na dowolnym planie.
2. Otwórz wpis Kit w katalogu (claude.ai/directory/kit-mcp) i kliknij Connect to Claude, albo wejdź w Settings > Connectors > Discover, wyszukaj kit i kliknij plus.
3. Zaloguj się do Kit, wybierz konto z listy i kliknij Authorize & Accept Terms.
4. Kilka kont Kit: usuń standardowy konektor, dodaj każdy jako custom connector z adresem https://app.kit.com/mcp?nazwa (nazwa to krótki identyfikator konta).
5. W Claude Code connectory z claude.ai są widoczne w /mcp. Samego polecenia claude mcp add dla Kit pomoc Kit nie podaje.

Adres serwera MCP: `https://app.kit.com/mcp`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Kit (ConvertKit) do Claude Code.
Kit (ConvertKit) jest w katalogu konektorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Konektory). Jeśli w Claude Code, podłącz go jako serwer MCP.
Adres serwera MCP: https://app.kit.com/mcp
Dokumentacja: https://help.kit.com/en/articles/17332706-how-to-connect-kit-to-claude
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Kit ma plan Free (do 10 000 subskrybentów), ale serwer MCP jest dostępny tylko na płatnych planach Creator i Creator Pro. Creator ma 14 dni próby bez karty.
- Każdy endpoint API v4 jest narzędziem, więc Claude może zmieniać prawdziwych subskrybentów i broadcasty. Wysyłka i usuwanie wymagają potwierdzenia. Limit: 120 zapytań na minutę na token.
- Osobny serwer https://developers.kit.com/mcp to tylko dokumentacja deweloperska (bez dostępu do konta).

## Źródła

- https://help.kit.com/en/articles/17332706-how-to-connect-kit-to-claude
- https://developers.kit.com/mcp/kit-mcp
- https://kit.com/pricing
