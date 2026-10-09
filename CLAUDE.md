# aime – Strawbay Bugs and Fixes

Det här repot är arbetsytan där Rickard och Claude tillsammans blir specialister
på att fixa buggar i Strawbays stack. Buggarna är utvalda SBYCS-tickets i Jira
(strawbay.atlassian.net, projekt SBYCS).

## Regler (gäller alltid, utan undantag)

### 1. Rör aldrig produktionsdata

- Claude läser, skriver, frågar mot eller anropar **aldrig** produktion:
  databaser, API:er, konsoler, köer, lagring eller andra prod-system.
- Claude använder aldrig produktionsnycklar, tokens eller credentials, även om
  de råkar finnas i kod, konfiguration eller miljövariabler.
- Reproduktion och verifiering sker endast lokalt eller i testmiljö.
- Behövs underlag från prod (loggutdrag, felmeddelanden, anonymiserade
  datarader) ber Claude Rickard ta fram det. Claude hämtar det aldrig själv.
- Ändringar når prod endast via PR:er som Rickard granskar och mergar.
  Claude deployar aldrig och promotar aldrig till prod.
- Är det oklart om något är prod: behandla det som prod och fråga först.

### 2. Arbetssätt

- Utgå från Jira-ticketen: läs beskrivning och kommentarer innan något annat.
- Skriv en hypotes om rotorsaken och verifiera den mot koden innan en fix
  föreslås. Gissa inte och presentera aldrig mockade resultat som verkliga.
- Håll varje fix minimal och avgränsad till ticketen. Lägg till test som
  reproducerar buggen när det går.
- Kör repots egna kontroller (lint, typecheck, tester) innan push.
- Skapa PR endast när Rickard ber om det.
- Ändra inte status, tilldelning eller annat i Jira utan att Rickard ber om det.

### 3. Kunskapsbank

Det vi lär oss sparas här i repot så att det finns kvar mellan sessioner:

- `CLAUDE.md` – regler och arbetssätt (den här filen).
- Översikt över Strawbays stack och var komponenterna ligger (läggs till när
  vi har tillgång till koden).
- Bugglogg per ticket: symptom, rotorsak, fix, PR.

## Åtkomst

Strawbays källkod finns inte i det här repot. Strawbay-repona måste vara
kopplade till sessionen (Claude GitHub App installerad på organisationen) för
att Claude ska kunna läsa koden. Om de saknas: säg det direkt och spekulera
inte om koden.
