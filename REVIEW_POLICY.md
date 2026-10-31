# Polityka PR: bez obowiązkowego niezależnego review

**Decyzja właściciela: 2026-10-31.** Obowiązuje we wszystkich repozytoriach `borys2115borys`; zastępuje wcześniejsze instrukcje nakazujące osobny, niezależny przegląd kodu przez drugi czat/agenta lub osobną kolejkę ACC.

- **Niezależne review nie jest warunkiem otwarcia, kontynuacji ani scalenia PR.** Nie twórz w tym celu zadania, kolejki, claimu, sesji ani blokady `BLOCKED`. Brak niezależnego review, brak `ACC-REVIEW: PASS` i brak recenzenta nie są samodzielnymi powodami zatrzymania pracy.
- Po udanych **rzeczywiście wymaganych** testach/CI na aktualnym SHA, potwierdzeniu zakresu zmian i spełnieniu pozostałych warunków GitHub, wykonawca może scalić PR zgodnie z autoryzacją właściciela. **Nie omijaj** technicznie wymaganego GitHub approval, branch protection, status check, podpisów ani zasad bezpieczeństwa, jeśli faktycznie obowiązują.
- Nie uznawaj nieuruchomionych, pominiętych lub niezaliczonych testów za PASS. Rozbieżne checki wymagają ustalenia przyczyny; manualny `FINAL` nie wyłącza automatycznie kontroli wymaganych przez GitHub.
- Zachowaj odrębne decyzje właściciela, w tym akceptację nowych wzorców wizualnych, wdrożeń, zmian produkcji i danych, wydatków, sekretów i operacji wykraczających poza zakres zadania. Ta polityka **nie jest zgodą** na te czynności.
- Historyczne raporty i wcześniejsze review mogą pozostać jako dowody. Istniejące aktywne lub niepewne (`UNKNOWN`) intenty ACC wymagają bezpiecznego rozliczenia; nie usuwaj ich automatycznie i nie ponawiaj wiadomości.
- Dobrowolny przegląd kodu jest dopuszczalny, ale nie należy go automatycznie zlecać, traktować jak bramki merge ani wymagać jego wyniku.

**Pierwszeństwo:** te zasady mają pierwszeństwo przed starszymi fragmentami README, roadmap, promptów, opisów issue/PR i instrukcji ACC, które nazywały niezależne review obowiązkowym. Nie zmieniają retrospektywnie historycznych faktów ani statusów zatwierdzeń.
