# Mieltymykset ja rajoitteet

Käytä lyhyttä käyttäjäprofiilia vain, jos käyttäjä on kertonut tiedot tai pyytänyt niiden tallentamista. Älä päättele yksityisiä mieltymyksiä selaamisesta, aiemmista ostoksista tai yksittäisestä ostoslistasta. Pidä allergiat ja kiellot erillään mieltymyksistä. `allergies`, `never_buy` ja kielletyt ainesosat ovat aina ehdottomia poissulkuja.

Ehdotus profiilin kentiksi:

```yaml
household_size: null
planning_horizon_days: null
budget_amount: null
budget_currency: EUR
budget_type: target # target tai hard_limit; kysy tarvittaessa
price_estimate_store: null
dietary_rules: []
allergies: []
never_buy: []
exact_products: []
preferred_brands: []
preferred_origin: []
prefer_frozen: null
convenience_level: null # basic, mixed tai ready-to-use
pantry_items: []
avoid_food_waste: true
```

Tulkitse kentät näin:

- `allergies`, `never_buy`, kielletyt ainesosat ja nimenomaiset ruokavaliorajoitteet ovat ehdottomia poissulkuja. Niitä ei saa pisteyttää, lieventää eikä ohittaa hinnan, tarjouksen, saatavuuden, helppouden tai listapyynnön vuoksi.
- Älä koskaan ehdota, valitse, lisää tai korvaa tuotteella, joka sisältää käyttäjän ilmoittaman allergeenin tai kielletyn ainesosan.
- Jos tuotteen ainesosa-, allergeeni- tai ristikontaminaatiotieto puuttuu tai on epäselvä, jätä tuote pois ja kerro syy. Älä väitä tuotetta turvalliseksi äläkä pyydä käyttäjää hyväksymään riskialtista tuotetta.
- Yksittäinen ostoslistapyyntö ei kumoa pysyvää allergiaa tai kieltoa. Jos listan rivi on ristiriidassa profiilin kanssa, ohita rivi ja kerro ristiriidasta.
- `exact_products` tarkoittaa, että määritelty tuote tai merkki/muoto pitää säilyttää. Älä korvaa sitä hiljaisesti.
- Merkki, kotimaisuus, pakaste/tuore ja helppous ovat mieltymyksiä, ellei käyttäjä sano esimerkiksi “vain”, “täytyy olla” tai vastaavaa. Kerro merkittävästä kompromissista väittämättä, että toive toteutui.
- `budget_amount` on tavoite, ellei käyttäjä määritä sitä ehdottomaksi rajaksi (`budget_type: hard_limit`). Jos suunnitelma ei mahdu tavoitteeseen, kerro arvioitu erotus ja ehdota muutoksia. Kovan ylärajan kohdalla älä esitä sen ylittävää ostoslistaa budjettiin sopivana. Älä kuitenkaan riko hiljaisesti ruokavaliorajoitteita, tarkkoja tuotevaatimuksia tai muita ehdottomia ehtoja summan saavuttamiseksi.
- `price_estimate_store` yksilöi kaupan tai myymälän, jos käyttäjä haluaa kauppakohtaisen arvion. Hinnat ja saatavuus voivat vaihdella kaupan, ajankohdan, jäsenhinnan ja tarjouksen mukaan; kerro aina käytetty lähde ja hintojen ajankohta, jos ne ovat saatavilla.
- `prefer_frozen` ja `convenience_level` kuvaavat ostotapaa. Pakaste voi vähentää hävikkiä ja esivalmistelua; tuore voi sopia reseptiin paremmin. Valmiit tuotteet voivat maksaa enemmän, joten vertaa myös paketin kokonaishintaa.
- `pantry_items` pitää päivittää käyttäjän kanssa. Älä käsittele vanhaa listaa ajantasaisena tarkistamatta.

Kysy profiilin muistamisesta, jos pysyvyydestä olisi olennaista hyötyä. Älä luo tai kirjoita profiilitiedostoa automaattisesti. Jos profiili on paikallisessa työtilassa, kunnioita sen rajausta äläkä kopioi henkilötietoja julkiseen repositorioon.
