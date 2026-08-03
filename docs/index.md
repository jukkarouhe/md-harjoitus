# Markdown- ja GitHub-harjoitus

Tämä dokumentti kokoaa opitut asiat askel askeleelta: Markdown-syntaksi, Git paikallisesti, GitHub-yhteys, päivittäinen työskentelyrutiini ja lopuksi dokumentaation julkaisu verkkosivuna MkDocsilla.

---

# Osa 1: Markdown-syntaksi

## Otsikot

Otsikot tehdään risuaita-merkillä `#`. Yksi risuaita on pääotsikko, kaksi alaotsikko, kolme sitä seuraava taso. Jätä välilyönti risuaidan ja otsikkotekstin väliin.

```markdown
# Pääotsikko
## Alaotsikko
### Kolmostason otsikko
```

## Listat

Numeroimaton lista tehdään tavuviivalla rivin alussa:

```markdown
- ensimmäinen asia
- toinen asia
- kolmas asia
    - sisennetty alakohta (tab tai 4 välilyöntiä alkuun)
```

Numeroitu lista tehdään numerolla ja pisteellä:

```markdown
1. ensimmäinen vaihe
2. toinen vaihe
3. kolmas vaihe
```

Kaksi tärkeää huomiota:

- Jätä **tyhjä rivi** ennen listan alkua – muuten lista jää osaksi edellistä kappaletta.
- Numeroiden ei tarvitse olla oikeassa järjestyksessä – vaikka kirjoittaisit joka riville `1.`, Markdown numeroi ne silti 1, 2, 3. Tämä helpottaa kohtien lisäämistä listan keskelle.

## Tekstin korostukset

Teksti voi olla *kursivoitua* yhdellä tähdellä (`*sana*`) tai **lihavoitua** kahdella tähdellä (`**sana**`) sanan alussa ja lopussa, ilman välilyöntiä tähtien ja sanan välissä.

Koodi ja komennot merkitään `takahipsuilla`: esimerkiksi `` `koodi` ``, ilman välilyöntiä hipsujen ja tekstin välissä.

## Linkit

Linkki tehdään hakasulkeilla ja kaarisulkeilla, peräkkäin ilman välilyöntiä:

```markdown
[Näkyvä linkkiteksti](https://osoite.fi)
```

Esimerkki:

```markdown
[Noppa-Yatzy pelitaulukko](https://jukkarouhe.github.io/yatzy/)
```

## Kuvat

Kuva lisätään kuten linkki, mutta eteen tulee huutomerkki, ja jälleen ilman välilyöntiä hakasulkeiden ja kaarisulkeiden välissä:

```markdown
![Kuvan kuvausteksti](kuvat/kuvan-nimi.jpg)
```

Polku `kuvat/kuvan-nimi.jpg` on **suhteellinen polku**: se tarkoittaa "tämän .md-tiedoston sijainnista katsottuna kuvat-kansiossa oleva tiedosto". Suhteelliset polut toimivat sellaisenaan myös GitHubissa ja MkDocs-sivustolla – toisin kuin koneen absoluuttiset polut (esim. `/Users/...`).

## Koodilohkot

Yksittäinen komento merkitään takahipsuilla keskellä tekstiä, esimerkiksi komento `ls -la` listaa myös piilotiedostot.

Monirivinen koodilohko tehdään kolmella takahipsulla: ensimmäisellä rivillä kolme takahipsua, sisältö, ja viimeisellä rivillä taas kolme takahipsua:

````markdown
```
mkdir kuvat
cd kuvat
ls
```
````

Kolmen takahipsun perään voi lisätä kielen nimen, jolloin koodi saa värityksen (terminaalikomennoille `bash`, Python-koodille `python` jne.):

````markdown
```bash
cd ~/Projects/md-harjoitus
git status
```
````

Koodilohkon sisällä Markdown-merkit eivät vaikuta – kaikki näytetään sellaisenaan harmaalla pohjalla.

## Taulukot

Taulukon sarakkeet erotetaan pystyviivalla `|`. Ensimmäinen rivi on otsikkorivi, toinen rivi viivoineen (`|---|---|`) erottaa otsikot sisällöstä (pakollinen), ja loput rivit ovat sisältöä. Sarakkeiden leveyksien ei tarvitse olla siistejä tai kohdakkain – Markdown tasaa taulukon automaattisesti.

```markdown
| Komento | Selitys |
|---------|---------|
| ls      | listaa kansion sisällön |
| cd      | vaihtaa kansiota |
| mkdir   | luo uuden kansion |
```

## Erikoismerkit suomalaisella Mac-näppäimistöllä

| Merkki | Näppäinyhdistelmä |
|---|---|
| `~` (aaltoviiva) | Option (⌥) + ¨ (Å:n oikealla puolella), sitten välilyönti |
| `` ` `` (takahipsu) | Shift + ´ (+ -näppäimen ja Backspacen välissä), sitten välilyönti |
| `\|` (pystyviiva) | Option (⌥) + 7 |
| `[` `]` (hakasulkeet) | Option + 8 / Option + 9 |
| `(` `)` (kaarisulkeet) | Shift + 8 / Shift + 9 |

¨ ja ´ ovat niin sanottuja tarkemerkkejä ("kuolleita näppäimiä"), jotka jäävät odottamaan seuraavaa merkkiä yhdistyäkseen siihen (kuten ñ). Välilyönti kertoo, että haluat merkin yksinään.

## Terminaalin peruskomennot (DOS-vertailu)

Macin terminaali ei aja DOSia vaan Unix-pohjaista komentotulkkia (oletuksena zsh). Komennot ovat siksi eri nimisiä, vaikka tekevät samoja asioita:

| DOS | Mac/Unix | Mitä tekee |
|---|---|---|
| dir | ls | listaa kansion sisällön |
| cd | cd | vaihtaa kansiota (sama!) |
| md / mkdir | mkdir | luo kansion |
| copy | cp | kopioi tiedoston |
| del | rm | poistaa tiedoston |
| type | cat | näyttää tiedoston sisällön |
| cls | clear | tyhjentää ruudun |

Kaksi muuta eroa: Unix käyttää kauttaviivaa `/` polkujen erottimena (DOS käytti kenoviivaa `\`), ja Unixissa isot ja pienet kirjaimet ovat merkitseviä – `Ohje.md` ja `ohje.md` ovat eri tiedostoja.

---

# Osa 2: Git paikallisesti

Gitin ydinajatus on kahtiajako: **paikallinen työskentely** (add, commit) ja **synkronointi etäpalvelimelle** (push, pull) ovat erillisiä toimintoja. Tässä osassa käydään läpi paikallinen puoli.

## 2.1 Siirry projektikansioon

**Terminaalissa:**

```bash
cd ~/Projects/md-harjoitus
```

## 2.2 Tarkista Git-asetukset

Git leimaa jokaiseen commitiin tekijän nimen ja sähköpostin. Tarkista, ovatko ne asetettu:

**Terminaalissa:**

```bash
git config --global user.name
git config --global user.email
```

Jos rivit tulostavat nimen ja sähköpostin, kaikki on kunnossa. Jos ne palauttavat tyhjää, aseta ne (käytä GitHub-tilin sähköpostia):

```bash
git config --global user.name "Oma Nimi"
git config --global user.email "oma@osoite.fi"
```

`--global` tarkoittaa, että asetus koskee kaikkia projekteja tällä koneella, ei vain tätä kansiota.

## 2.3 Alusta repositorio

**Terminaalissa:**

```bash
git init
```

`init` (initialize) luo kansioon piilotetun `.git`-alikansion, johon Git tallentaa tiedostojen muutoshistorian. Kansiosta tulee **repositorio** eli "repo". Tämä tehdään vain kerran per projekti. Piilokansio näkyy komennolla `ls -la` (`-a` näyttää piilotiedostot – kuten DOSin `dir /a`).

**VS Codessa:** Avaa kansio (File → Open Folder). Paina vasemman reunan Source Control -kuvaketta (Cmd + Shift + G). Jos kansio ei ole vielä Git-repo, näkyy sininen nappi **Initialize Repository** – se tekee saman kuin `git init`.

## 2.4 Tarkista tilanne

**Terminaalissa:**

```bash
git status
```

Tämä on Gitin tärkein peruskomento – se kertoo aina, mitä repossa on meneillään. Alustuksen jälkeen sen pitäisi listata punaisella "Untracked files" -otsikon alla kaikki kansion tiedostot: Git näkee ne, mutta ei vielä seuraa niitä.

**VS Codessa:** Source Control -paneelissa samat tiedostot näkyvät merkinnällä **U** (Untracked).

## 2.5 Lisää tiedostot seurantaan ja tee commit

Commit tehdään kahdessa vaiheessa: ensin valitaan mukaan otettavat tiedostot, sitten otetaan tilannekuva.

**Terminaalissa:**

```bash
git add .
```

`add` siirtää tiedostot **valmistelualueelle** (staging area) eli seuraavaan tilannekuvaan mukaan tuleviksi. Piste tarkoittaa "kaikki tämän kansion tiedostot". Voit myös valita vain osan: `git add tiedosto1.md tiedosto2.md`. Aja `git status` uudelleen – tiedostot näkyvät nyt vihreällä, valmiina commitoitavaksi.

```bash
git commit -m "Ensimmäinen versio: Markdown-perusteet dokumentoitu"
```

`commit` tallentaa valmistelualueen sisällön pysyväksi tilannekuvaksi historiaan, `.git`-kansioon. `-m` (message) antaa commitille kuvaavan viestin. Tässä vaiheessa mitään ei ole vielä siirretty GitHubiin – kaikki tapahtuu vain paikallisesti.

**VS Codessa:** Source Control -paneelissa paina tiedoston vieressä **+** (Stage Changes) – vastaa `git add`. Tiedosto siirtyy Staged Changes -listaan. Kirjoita viesti yläreunan kenttään ja paina **Commit**. Jos painat Commit ilman että mitään on stagettu, VS Code kysyy haluatko commitoida kaikki muutokset kerralla – se vastaa `git add .` + commit.

## 2.6 Katso historia

**Terminaalissa:**

```bash
git log
```

Näet tekijän, ajan, viestin ja commitin tunnisteen. Poistu näkymästä painamalla **q**. Tiiviimpi muoto: `git log --oneline`.

**VS Codessa:** avaa tiedosto ja katso vasemman paneelin alaosasta **Timeline**-osiota – siinä näkyvät tiedoston commitit aikajärjestyksessä.

---

# Osa 3: GitHub-yhteys

## 3.1 Luo repositorio GitHubiin

Tämä tehdään selaimessa:

1. Mene osoitteeseen github.com ja kirjaudu sisään
2. Paina oikean yläkulman **+**-merkkiä ja valitse **New repository**
3. Täytä lomake:
   - **Repository name:** sama nimi kuin paikallisella kansiolla (ei pakollista, mutta selkeää)
   - **Public / Private:** valitse **Public**, jos dokumentaatio saa näkyä kaikille – helpoin valinta myös GitHub Pages -julkaisua varten
   - **Älä ruksaa** "Add a README", "Add .gitignore" tai "Choose a license" – repositorion pitää syntyä tyhjänä, koska sisältö tulee koneelta. Muuten historiat menisivät ristiin.
4. Paina **Create repository**

## 3.2 Kytke paikallinen repo GitHubiin (remote)

**Terminaalissa:**

```bash
git remote add origin git@github.com:kayttajatunnus/repo-nimi.git
```

`remote` tarkoittaa etärepositoriota eli paikallisen repon "kaveria" verkossa. `add origin` lisää etärepon nimellä **origin** – vakiintunut nimi ensisijaiselle etärepolle. SSH-muotoinen osoite (`git@github.com:...`) todentaa yhteyden SSH-avaimella – salasanaa ei kysytä.

Tarkista kytkentä:

```bash
git remote -v
```

Tulosteessa pitäisi näkyä origin kahdesti (fetch ja push).

**VS Codessa:** Source Control -paneelin **…**-valikko → **Remote → Add Remote** → liitä osoite → anna nimeksi origin.

## 3.3 Nimeä haara ja työnnä commitit

**Terminaalissa:**

```bash
git branch -M main
```

Nimeää nykyisen haaran uudelleen nimellä **main** – GitHubin nykykäytäntö (Gitin oma oletusnimi voi olla "master"). Haara on projektin päälinja, se aikajana jolle commitit tallentuvat.

```bash
git push -u origin main
```

`push` lähettää paikalliset commitit etärepoon. `-u` (upstream) tekee kytkennän muistiin: jatkossa pelkkä `git push` riittää. Jos SSH-yhteys kysyy ensimmäisellä kerralla varmistusta yhteyden luotettavuudesta, vastaa **yes**.

**VS Codessa:** **…**-valikko → **Push**. Ensimmäisen pushin jälkeen alapalkkiin ilmestyy synkronointikuvake (nuolet ympyränä), joka hoitaa push/pull-toiminnot yhdellä klikkauksella jatkossa. Kuvakkeen vieressä näkyvät numerot kertovat odottavista commiteista: ↓ tulossa GitHubista, ↑ lähdössä sinne.

## 3.4 Tarkista onnistuminen

Päivitä repositorion sivu selaimessa. Tiedostojen pitäisi näkyä siellä, ja Markdown-tiedosto näkyy valmiiksi muotoiltuna suoraan reposivulla. Commit-historia näkyy "commits"-linkistä.

---

# Osa 4: Päivittäinen työskentelyrutiini

Rutiini on sykli: **muokkaa → tarkista → commitoi → työnnä**.

## 4.1 Muokkaa

Tee muutokset tiedostoihin VS Codessa ja tallenna (Cmd + S). VS Code merkitsee muokatun tiedoston **M**-kirjaimella (Modified), ja Source Control -kuvakkeeseen ilmestyy numero.

## 4.2 Tarkista mitä muuttui

**Terminaalissa:**

```bash
git status
git diff
```

`status` kertoo mitkä tiedostot muuttuivat, `diff` näyttää rivi riviltä mitä muuttui – poistetut rivit miinuksella (punaisella), lisätyt plussalla (vihreällä). Poistu diff-näkymästä painamalla **q**.

**VS Codessa:** klikkaa muuttunutta tiedostoa Source Control -paneelissa – avautuu rinnakkaisnäkymä, jossa vasemmalla edellinen commitoitu versio ja oikealla nykyinen, muutokset värein korostettuna. Sulje näkymä klikkaamalla ylälaidasta tabin kiinni.

## 4.3 Commitoi

**Terminaalissa:**

```bash
git add tiedoston-nimi.md
git commit -m "Kuvaava viesti tehdystä muutoksesta"
```

Kun tiedosto nimetään erikseen (ei pistettä), commitiin tulee vain se tiedosto.

**VS Codessa:** Source Control → tiedoston vieressä **+** → kirjoita viesti → **Commit**.

## 4.4 Työnnä GitHubiin

**Terminaalissa:**

```bash
git push
```

**VS Codessa:** klikkaa alapalkin synkronointikuvaketta.

## 4.5 Hae muutoksia (pull)

**Terminaalissa:**

```bash
git pull
```

`pull` hakee GitHubista commitit, joita koneella ei vielä ole. Yhdellä koneella työskennellessä tämä tuntuu turhalta, mutta muuttuu tärkeäksi heti, jos (a) tiedostoja muokataan suoraan GitHubin selainkäyttöliittymässä, (b) käytössä on toinen tietokone, tai (c) projektiin tulee toinen tekijä. **Hyvä tapa:** aloita työskentelysessio aina `git pull`-komennolla (tai VS Coden synkronointikuvakkeella).

## 4.6 Terminaalikomennot VS Coden sisällä

VS Codessa on sisäänrakennettu terminaali, joka toimii täsmälleen kuten erillinen Terminal-sovellus, mutta samassa ikkunassa – sovellusten välillä ei tarvitse vaihtaa.

Avaa se näppäinyhdistelmällä **Ctrl + `** (gravis-merkki, Esc-näppäimen alapuolella) tai valikosta **Terminal → New Terminal**.

Työnjako yhden ikkunan sisällä:

- **Tiedostojen editointi:** VS Coden editori
- **git add / commit / push / pull:** Source Control -paneeli hiirellä, TAI komennot sisäänrakennetussa terminaalissa
- **Ulkopuolisten työkalujen komennot** (esim. `mkdocs serve`, `mkdocs gh-deploy`): aina sisäänrakennetussa terminaalissa, koska ne eivät ole Git-komentoja eikä niille ole nappia Source Control -paneelissa

## 4.7 Yleisimmät ongelmatilanteet ja ratkaisut

| Tilanne | Ratkaisu |
|---|---|
| Push hylätään: "rejected... remote contains work" | GitHubissa on committeja joita koneella ei ole. Aja `git pull` ensin, sitten `git push` uudelleen |
| Commit-viesti unohtui ja avautui outo editori | Kirjoita viesti, paina Esc, kirjoita `:wq` ja Enter (vim-editori). Jatkossa muista `-m "viesti"` |
| Väärä tiedosto stagessa | `git restore --staged tiedosto.md` poistaa stagesta (muutokset säilyvät). VS Codessa: tiedoston vieressä **−** (Unstage) |
| Muutokset halutaan perua kokonaan | `git restore tiedosto.md` palauttaa viimeisimmän commitin version. VS Codessa: tiedoston vieressä ↩ (Discard Changes). **Varo:** muutokset katoavat oikeasti |
| Ei muistikuvaa mitä on tehty | `git status` kertoo aina tilanteen. VS Codessa: Source Control -paneeli |

---

# Osa 5: MkDocs ja julkaisu GitHub Pagesiin

## 5.1 Kaksi tapaa julkaista

- **Pikatapa:** repositorion asetuksista (Settings → Pages) voi kytkeä Pagesin päälle suoraan main-haarasta, jolloin GitHub tekee md-tiedostoista yksinkertaiset sivut. Toimii, mutta lopputulos on vaatimaton.
- **Suunniteltu tapa (tässä käytetty):** rakennetaan sivusto MkDocsilla ja Material-teemalla. Saadaan hakutoiminto, navigaatio ja ammattimainen ulkoasu, ja julkaisu tapahtuu komennolla `mkdocs gh-deploy`, joka hoitaa GitHub Pages -kytkennän automaattisesti.

## 5.2 Tarkista MkDocs-asennus

**Terminaalissa, projektikansiossa:**

```bash
mkdocs --version
```

Jos komento ei löydy, se ei ole terminaalin hakupolussa (PATH), tai se on asennettu virtuaaliympäristöön (venv), joka pitää aktivoida. Kokeile:

```bash
python3 -m mkdocs --version
```

Jos tämä tulostaa version, paketti on asennettu ja kyse on vain hakupolusta. Jos tuli virhe "No module named mkdocs", tarkista pip-listaus:

```bash
pip3 list | grep -i mkdocs
```

`pip3 list` listaa kaikki asennetut Python-paketit, `grep -i mkdocs` suodattaa rivit joissa lukee mkdocs. Jos asennusta ei löydy lainkaan, se on ehkä asennettu virtuaaliympäristöön jonkin toisen projektin yhteydessä. Etsi se:

```bash
find ~/Projects -name "pyvenv.cfg"
```

## 5.3 Virtuaaliympäristö (venv)

Venv on eristetty "laatikko" Python-paketeille per projekti. Ilman sitä kaikki paketit menisivät yhteen kasaan koko koneelle, ja eri projektien versiotarpeet voisivat riidellä keskenään. Aktivoituna `pip install` asentaa paketit vain siihen kansioon.

**Luo virtuaaliympäristö:**

```bash
python3 -m venv .venv
```

`.venv` on luotavan kansion nimi (piste alussa piilottaa sen tavallisesta listauksesta).

**Aktivoi se:**

```bash
source .venv/bin/activate
```

`source` ajaa skriptin nykyisessä terminaali-istunnossa, mikä on välttämätöntä aktivoinnin pysyvyydelle. Onnistuessaan komentorivin alkuun ilmestyy `(.venv)`.

**Asenna paketit requirements.txt:stä:**

Jos requirements.txt on toisen projektin kansiossa, kopioi se ensin:

```bash
cp ~/Projects/toinen-projekti/requirements.txt ~/Projects/md-harjoitus/requirements.txt
```

Asenna paketit:

```bash
pip install -r requirements.txt
```

`-r` (requirements) lukee asennettavat paketit tiedostosta rivi riviltä. Tämä asentaa MkDocsin, Material-teeman, ghp-importin ja niiden riippuvuudet samoina versioina kuin tiedostossa lukee.

**Tarkista asennus:**

```bash
mkdocs --version
```

**Tärkeä muistisääntö:** venv pitää aktivoida **jokaisessa uudessa terminaali-istunnossa** erikseen (`source .venv/bin/activate`) ennen kuin mkdocs-komennot toimivat. Pois venvistä pääsee komennolla `deactivate`.

`.venv`-kansiota ei koskaan viedä Gitiin (iso, koneriippuvainen) – siksi requirements.txt on olemassa: sen avulla kuka tahansa voi pystyttää saman ympäristön uudelleen.

## 5.4 Järjestä kansiot MkDocsin tapaan

MkDocs odottaa, että sisältö on **docs**-kansiossa ja asetustiedosto **mkdocs.yml** projektin juuressa. `docs/index.md` on sivuston etusivu.

```bash
mkdir docs
git mv ohje.md docs/index.md
git mv kuvat docs/kuvat
```

`git mv` siirtää (ja tarvittaessa nimeää) tiedoston niin, että Git ymmärtää kyseessä olevan siirron eikä poistoa + uutta tiedostoa – tiedoston koko historia säilyy ehjänä.

**Huomio:** jos siirrettävä tiedosto on samaan aikaan auki VS Codessa, editorin välilehti ei aina päivity automaattisesti, ja saatat vahingossa jatkaa kirjoittamista vanhaan tiedostonimeen. Varmuuden vuoksi `git mv`-komennon jälkeen:

1. Sulje vanha välilehti (Cmd + W) ja avaa tiedosto uudelleen tiedostopaneelista oikeasta sijainnista
2. Aja `git status` ja tarkista, että vanha tiedostonimi ei näy "untracked"-listassa

## 5.5 Luo mkdocs.yml

Luo VS Codessa projektin **juureen** (samalle tasolle kuin docs-kansio, ei sen sisään) tiedosto `mkdocs.yml`:

```yaml
site_name: Markdown- ja GitHub-harjoitus
```

`site_name` on ainoa pakollinen asetus alkuun. YAML-muodossa kaksoispisteen jälkeen täytyy olla yksi välilyönti ennen arvoa.

## 5.6 Käynnistä esikatselu

```bash
mkdocs serve
```

Avaa selaimessa **http://localhost:8000**. Palvelin pysäytetään terminaalissa **Ctrl + C** -näppäinyhdistelmällä. Jätä palvelin käyntiin muokatessasi tiedostoja – selain päivittyy automaattisesti tallennuksen jälkeen.

## 5.7 .gitignore – jätä .venv ja .DS_Store pois Gitistä

Luo projektin juureen tiedosto `.gitignore`:

```
.venv/
.DS_Store
```

`.gitignore` listaa polut, joita Git ei koskaan seuraa – ne eivät näy `git status`-listauksessa eivätkä päädy committeihin. `.DS_Store` on macOS Finderin oma piilotiedosto kansion näkymäasetuksille, ei osa projektin sisältöä.

Jos `.DS_Store` on jo vahingossa päätynyt seurantaan, lopeta sen seuraaminen (levyltä se ei poistu):

```bash
git rm --cached .DS_Store
```

Tarkista `git status`-komennolla, että `.venv` eikä `.DS_Store` näy listassa lainkaan.

## 5.8 Committoi MkDocs-rakenne

```bash
git add docs/index.md mkdocs.yml requirements.txt .gitignore
git status
```

Kun kaikki on "Changes to be committed" -listassa:

```bash
git commit -m "MkDocs-projektirakenne: docs-kansio, mkdocs.yml, .gitignore"
git push
```

## 5.9 Ota käyttöön Material-teema

Muokkaa `mkdocs.yml`:

```yaml
site_name: Markdown- ja GitHub-harjoitus
theme:
  name: material
  language: fi
  features:
    - navigation.instant
    - search.suggest
```

`theme: name: material` kertoo MkDocsille, että käytetään asennettua Material-pakettia sisäänrakennetun oletusteeman sijaan. `language: fi` vaihtaa teeman valmiit tekstit suomeksi. `features`-lista ottaa käyttöön lisäominaisuuksia: `navigation.instant` nopeuttaa sivujen välistä siirtymistä, `search.suggest` näyttää hakuehdotuksia kirjoittaessa.

**YAML-huomio:** sisennys pitää olla täsmälleen sama koko tiedostossa (esim. aina 2 välilyöntiä per taso) – YAML käyttää sisennystä rakenteen merkitsemiseen.

Tallenna ja päivitä selain – näkyviin tulee siisti navigaatiopalkki, hakukenttä ja modernimpi typografia.

### Vaihtoehtoisia teemoja

| Teema | Asennus | Kuvaus |
|---|---|---|
| mkdocs | sisäänrakennettu | MkDocsin oletusteema, Bootstrap-pohjainen. Yksinkertainen mutta vaatimaton |
| readthedocs | sisäänrakennettu | Jäljittelee Read the Docs -sivustojen ulkoasua. Siisti mutta hieman vanhahtava |
| material | `pip install mkdocs-material` | Suosituin vaihtoehto, käytössä tässä projektissa. Hakutoiminto, tumma/vaalea tila, runsaasti lisäominaisuuksia |
| mkdocs-bootstrap4 | erillinen asennus | Bootstrap 4 -pohjainen ulkoasu |
| mkdocs-alabaster | erillinen asennus | Kevyt, minimalistinen – suosittu pienissä henkilökohtaisissa projekteissa |
| mkdocs-windmill | erillinen asennus | Yksinkertainen, responsiivinen, kevyempi kuin Material |

## 5.10 Committoi teema-asetus

```bash
git add mkdocs.yml
git commit -m "Otettu käyttöön Material-teema"
git push
```

## 5.11 Julkaise GitHub Pagesiin

```bash
mkdocs gh-deploy
```

Tämä yksi komento tekee kolme asiaa: (1) rakentaa koko sivuston valmiiksi HTML/CSS/JS-tiedostoiksi `site`-väliaikaiskansioon, (2) luo tai päivittää repositorion erillisen **gh-pages**-haaran, joka sisältää vain rakennetun sivuston (ei .md-lähdetiedostoja), ja (3) työntää sen haaran GitHubiin automaattisesti.

Repositoriossa on nyt kaksi haaraa: **main** (lähdemateriaali – docs-kansio, mkdocs.yml) ja **gh-pages** (valmis, rakennettu sivusto, jonka GitHub Pages tarjoilee selaimeen). gh-pages-haaraa ei koskaan muokata käsin – se syntyy aina uudelleen `mkdocs gh-deploy`-komennolla main-haaran sisällöstä.

GitHub saattaa tarvita hetken (yleensä alle minuutin) ottaakseen gh-pages-haaran käyttöön Pages-palveluna ensimmäistä kertaa.

## 5.12 Tarkista julkaisu

Avaa selaimessa `https://kayttajatunnus.github.io/repo-nimi/`.

Jos sivu ei aukea:

1. Mene repositorioon → **Settings** → **Pages**
2. Tarkista, että ylhäällä lukee **"Your site is live at ..."** – jos kyllä, kokeile pakottaa selain lataamaan sivu uudelleen ilman välimuistia (Cmd + Shift + R)
3. Jos ei, tarkista **Source**-kohdasta, että valittuna on **Deploy from a branch** ja haara **gh-pages**
4. Varmista tarvittaessa terminaalissa, että haara syntyi: `git branch -a`

## 5.13 Sivuston päivittäminen jatkossa

Muokkaa .md-tiedostoja docs-kansiossa, commitoi ja pushaa normaalisti (Osa 4). Kun haluat päivittää **julkisen** sivuston vastaamaan uusinta versiota, aja uudelleen:

```bash
mkdocs gh-deploy
```

Tämä on ainoa ylimääräinen askel julkaisussa – itse sisällönmuokkaus ei muutu miksikään. Uusien sivujen lisääminen onnistuu lisäämällä .md-tiedostoja docs-kansioon – MkDocs huomaa ne automaattisesti navigaatioon.


last edited: 3.8.2026