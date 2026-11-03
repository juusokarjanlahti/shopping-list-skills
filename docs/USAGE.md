# Näin käytät taitoja

## Asenna GitHub-reposta

Kun repository on julkaistu GitHubiin, voit asentaa taidot tuettuun agenttiin Vercelin `skills`-CLI:llä:

```sh
npx skills add OWNER/REPO --agent claude-code
```

Korvaa `OWNER/REPO` GitHubin käyttäjä- tai organisaationimellä ja repon nimellä. Komento tunnistaa repon skillit ja kysyy, mitkä niistä asennetaan. Vaihda `claude-code` käyttämäsi agentin tunnisteeseen. Asennuksen jälkeen kutsu taitoa alustan omalla tavalla.

## Analysoi olemassa oleva lista

Käynnistä `analyze-shopping-list` ja kerro, mitä haluat tietää. Taito ei oleta, että listaa pitäisi muuttaa tai arvioida yleisillä mittareilla.

Esimerkkejä:

- "Ryhmittele tämä lista tuoteryhmiin. Älä arvioi sitä tai ehdota muutoksia."
- "Vertaa näiden tuotteiden kilohintoja annettujen hintojen ja pakkauskokojen perusteella."
- "Tarkastele listaa omien budjettirajojeni mukaan ja ehdota säästöjä, mutta älä muuta täsmätuotteita tai allergiarajoitteita."

Jos näkökulma puuttuu, taito kysyy, mitä haluat selvittää, tai tarjoaa neutraaleja analyysivaihtoehtoja.

## 1. Suunnittele ja tarkista lista

Käynnistä `plan-shopping-list`-taito sillä tavalla, jonka oma tekoälytyökalusi tarjoaa. Kerro aikaväli, henkilömäärä, ateriat tai tavoitteet, budjetti (tavoite vai ehdoton yläraja), kotona jo olevat tuotteet, mieltymykset ja rajoitteet. Jos haluat kauppakohtaisen hinta-arvion, kerro myös kauppa tai myymälä.

Tarkista määrät, ehdotetut tuotteet, korvaukset ja budjetin oletukset ennen kuin siirrät listan kaupan palveluun.

Budjettiarviossa erotetaan ostettavien pakkausten hinta siitä, paljonko pakkauksista käytetään aterioihin. Kun hintoja on, tarkista sekä pakkaushinta ja -koko että vastaavien tuotteiden yksikköhinnat. Puuttuvista hinnoista kerrotaan; niitä ei arvata.

## 2. Täytä K‑Ruoka-lista

Käynnistä `fill-k-ruoka-list`-taito oman tekoälytyökalusi käyttöliittymässä. Anna tarkistettu lista, oikea jaettu K‑Ruoka-lista tai sen linkki, valittu kauppa jos tiedossa, sekä tuotemerkin, kotimaisuuden, tuoreuden/pakastuksen, valmiusasteen ja pakkauskoon prioriteetit. Kerro, saako tuotteita korvata. Taito ohittaa epäselvät tuotteet ja kertoo niistä lopuksi.

Esimerkki:

> Lisää alla oleva tarkistettu lista jaetulle K‑Ruoka-ostoslistalleni. Suosi K-Menua tai Pirkkaa ja kotimaista alkuperää, jos hintaero on enintään 20 %. Pakastekasvikset käyvät. Älä korvaa tarkasti nimettyjä tuotteita. Ohita epäselvät osumat ja kerro, mitä et voinut lisätä. Älä siirrä tuotteita ostoskoriin.

Liitä tarkistettu lista pyynnön perään.

## Selaimen käyttö ja vastuut

K‑Ruoka-listan täyttäminen edellyttää, että käyttäjän valitsemassa tekoälytyökalussa on selain- tai tietokoneohjaus käytössä. Käyttäjä kirjautuu omalla tilillään ja varmistaa, että jaettua listaa voi muokata. Jos jokin näistä ehdoista puuttuu, taito ei voi täyttää listaa.

Taitojen sisältö ei anna selaimelle tai käyttäjätilille oikeuksia. Käyttäjä vastaa valitsemansa alustan työkaluista, asetuksista, tietosuojasta ja käyttöehdoista. Käyttäjän tulee tarkistaa valitut tuotteet ja varmistaa sivustolla, että muutokset näkyvät oikealla listalla.

Tuotehaku voi käyttää eri kaupan valikoimaa kuin ostoslistan valittu kauppa. Tarkista listan nimi, kauppa, muokkausoikeus ja nykyiset tuotteet ennen muutoksia. Pysähdy, jos oikea lista tai muokkausoikeus ei ole selvä.

## Muokkausten rajaus

Pyydettyyn ostoslistaan lisääminen on tämän taidon tehtävä. Ostoskoriin siirto, tilaus, maksu, toimituksen valinta ja listan jakamisasetusten muuttaminen ovat erillisiä toimia eivätkä kuulu tähän pyyntöön.

## Loppuraportti

Kerro lopuksi:

- lisättyjen tuotteiden määrä ja nimet tai kategoriat;
- ohitetut tuotteet ja syyt;
- valittu kauppa ja tuotteet, joita ei ollut saatavilla;
- sivuston ilmoittama summa, jos se on luotettava;
- tallentuivatko lisäykset listalle;
- ettei ostoskoria tai tilausta tehty.

## Henkilötiedot

Älä lisää käyttäjän jaetun ostoslistan linkkiä, tunnuksia, allergioita, mieltymyksiä tai ostoslistan sisältöä julkiseen repositoryyn. Pidä ne paikallisina.
