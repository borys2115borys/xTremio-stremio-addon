# Roadmap — xTremio Stremio addon

> Przegląd źródłowego `README.md`, `package.json` i początku `index.js` z 02.11.2026. Repo ma zero otwartych Issues, a [PR #1](https://github.com/borys2115borys/xTremio-stremio-addon/pull/1) dotyczy polityki review. To **propozycja kolejnych prac**, nie diagnoza wycieku lub stwierdzenie awarii.

## Najpierw bezpieczeństwo

| Priorytet | Zadanie | Dlaczego / akceptacja |
| --- | --- | --- |
| P0 | **Sposób przechowywania i przekazywania danych IPTV** | `encodeConfig` koduje `serverUrl`, nazwę użytkownika i hasło przez `base64url`. To kodowanie odwracalne, **nie szyfrowanie**; URL instalacyjny może utrwalić dane w historii, logach reverse proxy i udostępnieniach. Zidentyfikować przepływ, miejsca zapisu, referrer/logi i warianty bezpiecznej dystrybucji zgodne ze Stremio, bez łamania kompatybilności. Do decyzji właściciela: stateless vs krótkożyjący token/serwerowy sekret. |
| P0 | **Usunąć stały token TMDB z kodu i rozważyć jego rotację** | `index.js` zawiera `TMDB_TOKEN` bezpośrednio w źródle. Przenieść do środowiska procesu, przy braku konfiguracji działać fail-closed w funkcji TMDB lub jawnie bez tej integracji. Nigdy nie drukować tokenu w testach/logach; sprawdzić zalecenia dostawcy co do rotacji. |
| P1 | **Ograniczyć ryzyko SSRF i zaufania do reverse proxy** | Zweryfikować wszystkie połączenia do `cfg.serverUrl` oraz `x-forwarded-host`/`x-forwarded-proto`: walidacja schematu/hosta, brak dostępu do prywatnych IP/metadanych chmury przy instalacji dostępnej publicznie, brak fałszowania bazowego URL. Każda zmiana musi zachować zgodne adresy legalnych usług IPTV. |
| P1 | **Kontrakt testów regresyjnych** | W `package.json` jest `start` i `dev`, bez `test`. Dodać testy `encodeConfig/decodeConfig`, wadliwych wejść, błędów upstream, tokenów w logach, cache i błędów parsowania; CI na synthetic fixtures bez prawdziwych loginów. |
| P2 | **Utrzymanie i dokumentacja wdrożenia** | Check zależności, health/smoke, ograniczenie timeoutów/cache i runbook restartu. Po testach przegląd README pod kątem jawnego ostrzeżenia o wrażliwych linkach instalacyjnych. |

## Bramka pracy

Najpierw osobny PR audytowy dokumentujący konkretne przepływy i zgodność ze Stremio; następne zmiany bezpieczeństwa w małych osobnych PR, z testami. Nie zapisywać danych IPTV, tokenów, rzeczywistych URL-i instalacyjnych ani prywatnych adresów w Issues, PR, CI czy testach. Bez zmiany działającej konfiguracji/produkcji bez świadomej decyzji właściciela.
