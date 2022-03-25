---
title: Teamkatalog
---

## Hva er produktet?
Teamkatalogen gir en oversikt over alle leveranseteam i NAV og deres tilhørighet til (produkt)områder. 

**Hensikten** med Teamkatalogen er å gi en pålitelig og oppdatert masteroversikt over alle leveranseteam i NAV, team/område-organiseringen og gjøre det enkelt å finne ut hvor ulike personer jobber. Løsningen tilbyr også API-er som gjør det mulig for andre applikasjoner å slå opp teams i sine løsninger.

## Hva kan man bruke det til?
* Hvilke team har vi NAV?
* Hvilke team hører under et gitt område?
* Hva jobber et gitt team med?
* Hvem jobber i teamet, og hvilke roller har de?
* Hvor stor andel eksterne er det i et team eller område?
* Hvor sitter teamet i Fyrstikkalleen? Hvilke dager er de vanligvis der?
* Slå opp i NOM (NAV Organisasjonsmaster) og se hvem som er personalleder for en person, samt hvor personen er ansatt.
* Hvordan komme i kontakt med teamet, f.eks. slackkanal for teamet?


## Hvordan komme i gang?
Løsningen er tilgjenglig på: https://teamkatalog.nav.no/ for alle med NAV-identer - både LES og SKRIV.

**Produksjon**
https://teamkatalog.nav.no/ 

**Test / Preprod**
Alle i NAV har både les- og skrivtilgang til løsningen i preprod: [Teamkatalogen (Test)](https://teamkatalog.nais.preprod.local)


## Kontaktinformasjon
Kontakt teamet bak Teamkatalogen på vår slackkanal [#teamkatalogen](https://nav-it.slack.com/archives/CG2S8D25D)

## Litt om arkitektur
Team katalog repository er bygget på toppen av en postgres tabell som lagrer json i en 'document-db'.
Integrasjon mot NOM for henting av personer.
Siste versjon av et team vil bli publisert på en compacted kafka topic.
All data er åpent tilgjengelig i NAV uten innlogging, brukere med skrivetilgang kan endre data. Innlogging skjer via Single sign-on via Azure AD, brukere i frontend vil få en session cookie som varer i 14 dager. APIet støtter innlogging via Authorization header med Bearer token (access token fra Azure).

### Administratorer (per nå team org) kan aksessere noen få admin tjenester
* Versjonshistorikk som inkludert timestamp , hvem som har endret noe, samt et snapshot av hele dataobjektet når det ble endret.

### Lenker til API og repo
* [Swagger API (Test)](https://teamkatalog-api.nais.preprod.local/swagger-ui.html)
* [Swagger API (Prod)](https://teamkatalog-api.nais.adeo.no/swagger-ui.html)

* [Repo](https://github.com/navikt/team-catalog)


