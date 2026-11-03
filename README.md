# 🛒 Ostoslistataidot

**Suunnittele, tarkastele ja täydennä ruokaostoslistaa omilla ehdoillasi.** Tämä repository sisältää kolme uudelleenkäytettävää [Agent Skills](https://agentskills.io) -taitoa. Tavoitteena on, että käyttäjän omat tarpeet ja rajat ohjaavat työtä: työkalu ei päätä puolestasi, millainen ostoslistan pitäisi olla.

> [!IMPORTANT]
> Allergiat, kielletyt tuotteet ja vältettävät ainesosat ovat ehdottomia rajoitteita. Jos tuotteen sopivuutta ei voi varmistaa, taito ohjeistaa jättämään sen pois.

## Sisältö

- [Taidot](#-taidot)
- [Käyttöönotto](#-käyttöönotto)
- [Käyttöesimerkki](#-käyttöesimerkki)
- [Budjetti ja hinnat](#-budjetti-ja-hinnat)
- [Selainkäyttö ja vastuut](#-selainkäyttö-ja-vastuut)
- [Tietosuoja](#-tietosuoja)
- [Lisenssi](#-lisenssi)

## 🧰 Taidot

| Taito | Käyttö | Mitä se tekee |
| --- | --- | --- |
| [`plan-shopping-list`](.agents/skills/plan-shopping-list/SKILL.md) | Kun rakennat uutta listaa | Suunnittelee ateriat ja ostoslistan antamiesi tarpeiden, budjetin ja rajoitteiden mukaan. |
| [`analyze-shopping-list`](.agents/skills/analyze-shopping-list/SKILL.md) | Kun sinulla on jo lista | Kuvaa tai tarkastelee listaa pyytämästäsi näkökulmasta, kuten määrien, hintojen tai tuoteryhmien mukaan. |
| [`fill-k-ruoka-list`](.agents/skills/fill-k-ruoka-list/SKILL.md) | Kun haluat siirtää tarkistetun listan K‑Ruokaan | Etsii tuotteet ja lisää ne pyytämällesi K‑Ruoka-ostoslistalle, jos käytetyllä tekoälytyökalulla on sopiva selainohjaus ja sinulla on muokkausoikeus. |

Voit käyttää taitoja erikseen. Tyypillinen eteneminen on suunnittelu → tarkistus tai analysointi → halutessasi K‑Ruoka-listan täyttö. Viimeinen vaihe vaatii erillisen pyyntösi.

## 🚀 Käyttöönotto

Skillien sisältö on alustariippumatonta, mutta taitojen asennuspaikka ja kutsumistapa riippuvat tekoälytyökalusta.

| Tekoälytyökalu | Taitojen kansio tässä projektissa |
| --- | --- |
| Codex | `.agents/skills/` |
| GitHub Copilot | `.agents/skills/` |
| Claude Code | `.claude/skills/` |
| Muu työkalu | Tarkista työkalun omat ohjeet |

Codex ja GitHub Copilot voivat käyttää tämän repon `.agents/skills/`-kansiota. Claude Codea varten kopioi taitokansiot `.claude/skills/`-kansioon. Agent Skills -muoto ei takaa, että jokaisessa työkalussa olisi selainohjaus tai samat ominaisuudet.

Katso tarkemmat ohjeet: [käyttö eri työkaluissa](docs/USAGE.md) · [julkaisu GitHubiin](docs/PUBLISHING.md).

### Asenna skill-työkalulla

Kun repo on julkaistu GitHubiin, voit asentaa sen taitoja Claude Codeen tai muuhun tuettuun agenttiin [Vercelin `skills`-CLI:llä](https://github.com/vercel-labs/skills):

```bash
npx skills add OWNER/REPO --agent claude-code
```

Korvaa `OWNER/REPO` GitHubin käyttäjä- tai organisaationimellä ja repon nimellä. CLI näyttää repon taidot ja pyytää valitsemaan asennettavat. Vaihda `claude-code` käyttämäsi agentin nimeen, jos haluat asentaa taidot muualle.

## 💬 Käyttöesimerkki

### Suunnittele lista

Kerro esimerkiksi ateriat, henkilömäärä, budjetti, kaapissa olevat tuotteet, mieltymykset sekä ehdottomat rajoitteet:

> Suunnittele kahdelle kolmen päivän ruuat. Budjetti on enintään 60 €. Käytä kaapissa olevat perunat ja pavut. Ei valmisruokaa. Vältä maapähkinää.

### Analysoi lista

Kerro, mitä haluat selvittää. Analysointitaito ei oleta, että listaa pitäisi arvostella tai muuttaa:

> Ryhmittele tämä lista tuoteryhmiin ja arvioi ostettavien pakkausten summa. Älä ehdota muutoksia.

### Täytä K‑Ruoka-lista

Tarkista suunnitelma ensin. Pyydä täyttö erikseen ja anna oikea jaettu lista:

> Lisää tämä tarkistettu lista jaetulle K‑Ruoka-ostoslistalleni. Käytä alla kertomiani budjetti- ja tuotetoiveita. Ohita epäselvät tuotteet ja kerro lopuksi, mitä lisäsit. Älä siirrä tuotteita ostoskoriin.

Kutsuminen vaihtelee alustasta: esimerkiksi Codex käyttää taitojen nimiä `$plan-shopping-list`, `$analyze-shopping-list` ja `$fill-k-ruoka-list`; Claude Code käyttää komentoja `/plan-shopping-list`, `/analyze-shopping-list` ja `/fill-k-ruoka-list`.

## 💶 Budjetti ja hinnat

- Kerro, onko budjetti **tavoite** vai **ehdoton yläraja**.
- Budjettiarvio lasketaan ostettavien pakkausten hinnoista. Se ei ole sama kuin reseptiin käytettyjen ainesosien laskennallinen osuus.
- Vertailussa näytetään mahdollisuuksien mukaan yksikköhinta (esim. €/kg), pakkaushinta ja pakkauskoko. Kilohinta ei yksin kerro, mikä ostos tulee tällä kertaa halvemmaksi.
- Hinta-arviossa kerrotaan kauppa ja hintatietojen ajankohta, jos ne ovat tiedossa. Jäsenhinnat, tarjoukset ja puuttuvat hinnat merkitään; hintoja ei keksitä.
- Jos budjetti ylittyy, työkalu kertoo erotuksen eikä vaihda tuotteita hiljaisesti. Se ei myöskään riko allergioita, kieltoja tai tarkkoja tuotevaatimuksia säästääkseen.

## 🖥️ Selainkäyttö ja vastuut

K‑Ruoka-listan täyttö vaatii tekoälytyökalulta selaimen tai tietokoneen ohjausta. Sinun pitää olla kirjautuneena K‑Ruokaan ja saada muokata juuri kyseistä listaa. Pelkkä taitotiedosto ei anna näitä oikeuksia.

Taito lisää tuotteita ostoslistalle. Se ei siirrä niitä ostoskoriin, tilaa, maksa tai muuta listan jakamisasetuksia. Tarkista tuotteet ja muutokset kaupan sivustolla.

Valitset ja määrität käyttämäsi tekoälyalustan itse. Vastaat sen asetuksista, käyttöoikeuksista, tietosuojasta ja käyttöehdoista. Taitojen ohjeet ovat toimintaperiaatteita, eivät takuu jokaisen alustan toiminnasta.

## 🔒 Tietosuoja

Älä julkaise repositoryssa ostoslistojen linkkejä tai sisältöä, tunnuksia, allergioita, ruokavaliorajoitteita tai henkilökohtaisia mieltymyksiä. Profiilimalli [`preferences.md`](.agents/skills/plan-shopping-list/references/preferences.md) on tyhjä esimerkki: lisää omat tiedot vain paikallisesti, älä versionhallintaan.

## 📄 Lisenssi

Tämä repository käyttää [MIT-lisenssiä](LICENSE). Agent Skills -muoto ei itsessään edellytä tiettyä lisenssiä.

## ⚠️ Rajat

- Tuotehinnat, tarjoukset ja saatavuus muuttuvat.
- Ostoslistan valittu kauppa voi vaikuttaa saatavilla olevaan valikoimaan ja hintoihin.
- Taidot ovat tekoälylle annettuja ohjeita, eivät kaupan tuotetietokanta tai virallinen integraatio.
- Testaa muutokset omassa tekoälytyökalussasi ennen pitkän listan täyttämistä.
