# Julkaise repository GitHubiin

Tämä kansio voidaan tarkistaa paikallisesti ennen GitHub-repon luomista.

1. Tarkista lisenssi: repository käyttää MIT-lisenssiä (`LICENSE`).
2. Luo GitHubissa uusi repository ja valitse sen näkyvyys. Älä luo GitHubissa valmista README-tiedostoa, koska tässä kansiossa on jo sellainen.
3. Kopioi uuden repon HTTPS- tai SSH-osoite.
4. Avaa terminaali tämän kansion juuressa ja julkaise tiedostot esimerkiksi näin:

   ```sh
   git init -b main
   git add README.md LICENSE .gitignore .agents docs
   git commit -m "Add grocery shopping list skills"
   git remote add origin <GitHub-repon-osoite>
   git push -u origin main
   ```

Jos kansiossa on jo Git-repository, jätä `git init -b main` väliin. Tarkista `git status` ennen committia ja varmista, että mukana ovat vain julkiseen repoon tarkoitetut tiedostot.

Älä julkaise käyttäjän ostoslistan linkkejä, allergioita, ruokavaliorajoitteita, tunnuksia, mieltymysprofiilia tai ostoslistan sisältöä. Pidä nämä tiedot paikallisina tai poissa Gitistä.

Repositoryn taitoja voi asentaa useisiin agentteihin Vercelin `skills`-CLI:llä, esimerkiksi `npx skills add OWNER/REPO --agent claude-code`. Claude Code ‑pluginmarketplacea varten taidot pitää lisäksi paketoida pluginiksi ja tehdä marketplace-luettelo; ks. [Claude Coden julkaisuohje](https://code.claude.com/docs/en/plugins/publish). Tarkista muiden alustojen omat asennusohjeet. Alustan kyvyt ja käyttäjän tilin oikeudet ratkaisevat, mitkä toiminnot onnistuvat.
