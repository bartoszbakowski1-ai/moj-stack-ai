# Meta Ads: jak podłączyć do Claude

Meta Ads to system reklamowy Facebooka i Instagrama, a oficjalny serwer MCP Meta (Meta Ads AI Connectors) pozwala Claude czytać raporty i zarządzać kampaniami. Claude czyta wyniki kampanii na Facebooku i Instagramie i pomaga je poprawiać.

- Sposób: Konektor w Claude
- Logowanie: OAuth
- Darmowy plan: sprawdź na stronie producenta
- Strona: https://www.facebook.com/business/ads
- Instrukcja na stronie: https://www.bartbakowski.com/wiedza/moj-stack-ai/meta-ads

## Kroki

1. Upewnij się, że masz dostęp do konta reklamowego w Meta Business (konto Facebook lub Meta Managed Account).
2. W Claude wejdź w Customize > Connectors i wyszukaj Meta Ads, albo dodaj własny connector z adresem https://mcp.facebook.com/ads.
3. Zaloguj się przez Facebook Login for Business i zatwierdź uprawnienia (minimum ads_mcp_management oraz ads_read lub ads_management).
4. W Claude Code użyj polecenia podanego niżej, podając ID własnej aplikacji Meta (wymaga use case Create & manage ads with ads MCP server).
5. Dla zmian tworzących lub edytujących reklamy ustaw w Claude tryb Needs approval przy narzędziach zapisu.
6. Zacznij od odczytu: poproś o raport wydatków z ostatnich 7 dni.

```bash
claude mcp add --transport http --client-id <META_APP_ID> meta-ads https://mcp.facebook.com/ads
```

Adres serwera MCP: `https://mcp.facebook.com/ads`

## Prompt do Claude Code

Skopiuj i wklej w Claude Code:

```text
Podłącz Meta Ads do Claude Code.
Meta Ads jest w katalogu konektorów Claude. Jeśli pracuję w aplikacji Claude, powiedz mi, gdzie kliknąć (Ustawienia, Konektory). Jeśli w Claude Code, podłącz go jako serwer MCP.
Oficjalne polecenie: claude mcp add --transport http --client-id <META_APP_ID> meta-ads https://mcp.facebook.com/ads
Adres serwera MCP: https://mcp.facebook.com/ads
Dokumentacja: https://developers.facebook.com/documentation/ads-commerce/ads-ai-connectors/ads-mcp-server/ads-mcp-server-get-started.md
Nie wpisuj kluczy ani haseł do plików w repozytorium. Gdy potrzebujesz klucza, powiedz mi, gdzie go wygenerować.
Na końcu sprawdź połączenie jednym prostym zapytaniem (np. lista elementów) i powiedz mi, co działa.
```

## Na co uważać

- Wpis Meta Ads widziałem w rejestrze connectorów Claude (adres https://mcp.facebook.com), ale nie w publicznej wyszukiwarce katalogu bez logowania. Meta w dokumentacji podaje adres z końcówką /ads.
- Cena samego MCP nie jest podana w dokumentacji Meta. Płacisz za budżety reklamowe, a narzędzia potrafią tworzyć kampanie i zmieniać budżety, więc włącz zatwierdzanie akcji.
- Agencje zarządzające danymi innych firm muszą uzyskać Advanced Access do uprawnienia ads_mcp_management przez app review; tokeny systemowe z rolą Admin nie działają, a narzędzia są wdrażane stopniowo.

## Źródła

- https://developers.facebook.com/documentation/ads-commerce/ads-ai-connectors/ads-mcp-server/ads-mcp-server-overview
- https://developers.facebook.com/documentation/ads-commerce/ads-ai-connectors/ads-mcp-server/ads-mcp-server-get-started.md
- https://developers.facebook.com/blog/post/2026/07/16/meta-ads-mcp-server/
- https://developers.facebook.com/documentation/ads-commerce/llms.txt
- https://claude.com/docs/connectors/overview
