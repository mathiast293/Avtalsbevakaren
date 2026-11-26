# Avtalsbevakaren (demo)

En liten agent i Claude Code som läser lokalhyresavtal och gör ett avtalsregister med påminnelser inför uppsägningsdagar.

Allt innehåll är påhittat. Fastigheterna, bolagen och beloppen finns inte.

## Problemet
Ett fastighetsbolag med många långa hyresavtal och ett litet team måste hålla koll på löptider, uppsägningstider, index och optioner. Missar man en uppsägningsdag kan ett avtal förlängas i flera år på villkor man inte ville ha.

## Så fungerar den
1. Avtalen ligger i `avtal/`. Här finns tre påhittade avtal. Det tredje är med flit ofullständigt.
2. Instruktionerna till agenten finns i `CLAUDE.md`: vilka uppgifter som ska tas fram, hur datum räknas ut och vad som ska flaggas.
3. Agenten skriver två filer i `sammanstallning/`:
   - `avtalsregister.md` – översikt, detaljer per avtal med paragrafhänvisningar och en att göra-lista för en människa.
   - `paminnelser.ics` – kalenderhändelser för senaste uppsägningsdag och en påminnelse tre månader innan. Går att importera i Outlook eller Google Kalender.

## De viktigaste reglerna
- Agenten gissar aldrig. Saknas eller är en uppgift oläslig skriver den `[saknas – kontrollera]`.
- Varje uppgift har en paragrafhänvisning, så att den går att kontrollera mot avtalet.
- Har en uppsägningsdag redan passerat påstår agenten inte att avtalet förlängts, utan ber en människa kontrollera.
- Den ändrar inte originalen och skickar eller bokar ingenting.

## Exempel på resultat
Se `sammanstallning/avtalsregister.md`. Där syns alla tre fallen:
- ett avtal att bevaka (uppsägningsdag om drygt ett år),
- ett avtal där uppsägningsdagen har passerat,
- ett avtal med luckor som agenten flaggar i stället för att fylla i.

## Så kör du den
1. Installera Claude Code och logga in.
2. Öppna en terminal i den här mappen och skriv `claude`.
3. Skriv: `Gå igenom avtalen i avtal/ och uppdatera sammanstallning/`

## Nästa steg i en riktig verksamhet
- Läsa skannade PDF-avtal direkt.
- Köra automatiskt när ett nytt avtal läggs i en mapp.
- Samla registret i en intern dashboard per bolag och fastighet.

Skapad tillsammans med Claude.
