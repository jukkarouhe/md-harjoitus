# Markdown- ja GitHub-harjoitus

tämä dokumentti kokoaa opitut asiat askel askeleelta.

## Markdown-syntaksi

Otsikot tehdään # risuaita-merkillä. Yksi risuaita on pääotsikko, kaksi risuaitaa on alaotsikko, kolme on sitä seuraava taso. Jätä välilyönti # merkin/merkkien ja otsikkotekstin väliin.

## matoviiva näppiksellä

Aaltoviiva ~ kirjoitetaan suomalaisella Mac-näppäimistöllä näin:

Paina Option (⌥) + ¨ – ¨-näppäin sijaitsee Å-näppäimen oikealla puolella, Enter-näppäimen vieressä. Option-näppäin on välilyöntinäppäimen vieressä (siinä lukee ⌥ tai "alt").
Ruudulle ei ilmesty vielä mitään (tai näkyy himmeä ~) – paina sitten välilyöntiä, ja ~ ilmestyy.

## Listat

Numeroimaton lista tehdään tavuviivalla rivin alussa:

- ensimmäinen asia
- toinen asia
- kolmas asia
    - sisennetty alakohta (tab tai 4 spacea alkuun)

Numeroitu lista tehdään numerolla ja pisteellä

1. ensimmäinen vaihe
2. toinen vaihe
3. kolmas vaihe

Yksi tärkeä sääntö vielä: jätä tyhjä rivi ennen listan alkua – muuten lista ei muotoidu oikein vaan jää osaksi edellistä kappaletta.

Kiva yksityiskohta: numeroiden ei tarvitse olla oikeassa järjestyksessä – vaikka kirjoittaisit joka riville 1., Markdown numeroi ne silti 1, 2, 3. Tämä helpottaa, kun lisäät kohtia listan keskelle.

## Tekstin korostukset

Teksti voi olla *kursivoitua* yhdellä tähdellä sanan alussa ja lopussa tai **lihavoitua** kahdella tähdellä sanan alussa ja lopussa. 

Koodi ja komennot merkitään `takahipsuilla` ( ` löytyy + merkin ja backspacen välistä). 

eli: ´koodi ´ mutta hipsujen ja sanan välissä ei saa olla välilyöntiä.


## Linkit

Linkki tehdään hakasulkeilla ja kaarisulkeilla:

Linkkitekstin hakasulkeisiin
: 

[Noppa-Yatzy pelitaulukko] 

ja urlin kaarisulkeisiin: 
(https://jukkarouhe.github.io/yatzy/)

Kirjoitetaan *peräkkäin ilman välilyöntiä* jolloin saadaan nätti linkki:

[Noppa-Yatzy pelitaulukko](https://jukkarouhe.github.io/yatzy/)


## Kuvat

Kuva lisätään kuten linkki, mutta eteen tulee huutomerkki:

![poreallas kansi auki] (kuvat/poreallas-kansi-auki.JPEG)

(ja yhteenkirjoitettuna ilman välilyöntiä)

![poreallas kansi auki](kuvat/poreallas-kansi-auki.JPEG)

Polku kuvat/kuvan-nimi.jpg on suhteellinen polku: se tarkoittaa "tämän .md-tiedoston sijainnista katsottuna kuvat-kansiossa oleva tiedosto". Suhteelliset polut ovat tärkeitä, koska ne toimivat sellaisenaan myös GitHubissa ja MkDocs-sivustolla – toisin kuin koneesi absoluuttiset polut (esim. /Users/...).

## Koodilohkot

Yksittäinen komento merkitään takahipsuilla keskelle tekstiä,
esimerkiksi komento `ls -la` listaa myös piilotiedostot.

Monirivinen koodilohko tehdään kolmella takahipsulla siten että 

ensimmäisellä rivillä on ```

ja koodilohkon lopuksi viimeisellä rivillä on taas ``` jolloin saadaan muotoilu:

```
mkdir kuvat
cd kuvat
ls
```

Kolmen takahipsun perään voi lisätä kielen nimen, esim bash
jolloin koodi saa värityksen:

```bash
cd ~/Projects/md-harjoitus
git status
ls la
```

Selitys: Aiemmin opit yksittäisen takahipsun tekstin keskellä. Koodilohko taas alkaa rivillä, jolla on kolme takahipsua ``` ja päättyy samanlaiseen riviin. Kaikki niiden välissä näytetään sellaisenaan harmaalla pohjalla – Markdown-merkit eivät vaikuta lohkon sisällä. Takahipsu tehtiin siis Shift + ´ ja välilyönti; kolme peräkkäin vaatii saman kolmesti (tai kikka: paina Shift + ´ kolme kertaa peräkkäin ja lopuksi välilyönti – saat kolme hipsua kerralla).

Kielen nimi avaavan rivin perässä (esim. ```bash) kertoo, millä kielellä koodi on kirjoitettu, jolloin editori ja GitHub värittävät sen luettavammaksi. Terminaalikomennoille käytetään nimeä bash, Python-koodille python ja niin edelleen.

## Taulukot


Taulukot kirjoitetaan kuten allaoleva esimerkki näyttää mutta ilman tyhjää riviä otsikon ja toisen rivin välissä:

|Komento|Selitys|

|---|---|
|ls |listaa kansion sisällön|
|cd|vaihtaa kansiota|
|mkdir|luo uuden kansion|


Kun tyhjää riviä ei ole otsikon jälkeen, taulukko näyttää tältä:

|Komento|Selitys|
|---|---|
|ls |listaa kansion sisällön|
|cd|vaihtaa kansiota|
|mkdir|luo uuden kansion|

Selitys: taulukon sarakkeet erotetaan pystyviivalla |. Ensimmäinen rivi on otsikkorivi, toinen rivi viivoineen |---|---| erottaa otsikot sisällöstä (se on pakollinen), ja loput rivit ovat taulukon sisältöä. Pystyviiva tehdään suomalaisella Mac-näppäimistöllä Option (⌥) + 7. Sarakkeiden leveyksien ei tarvitse olla siistejä tai kohdakkain – Markdown tasaa taulukon automaattisesti.

## Peruskomennot terminaalissa

Macin terminaali ei aja DOSia vaan Unix-pohjaista komentotulkkia (Macissa oletuksena zsh-niminen tulkki). Komennot ovat siksi eri nimisiä, vaikka tekevät samoja asioita. Tässä muutama vastinpari, jotka tunnistat:

|DOS	|Mac/Unix	|Mitä tekee|
|---|---|---|
|dir	|ls	|listaa kansion sisällön|
|cd	|cd	|vaihtaa kansiota (sama!)|
|md / mkdir	|mkdir	|luo kansion|
|copy	|cp	|kopioi tiedoston|
|del	|rm	|poistaa tiedoston|
|type	|cat	|näyttää tiedoston sisällön|
|cls	|clear	|tyhjentää ruudun|

Pari muuta eroa: Unix käyttää kauttaviivaa / polkujen erottimena, kun DOS käytti kenoviivaa \. Ja Unixissa isot ja pienet kirjaimet ovat merkitseviä – Ohje.md ja ohje.md ovat eri tiedostoja, mikä DOSissa ei pitänyt paikkaansa.


## Git paikallisesti

Kahtiajako on Gitin ydinajatus: paikallinen työskentely (add, commit) ja synkronointi etäpalvelimelle (push, pull) ovat erillisiä toimintoja. Tässä käydään läpi paikallinen osuus.

### 1. Kohdekansio
Työskentelet Terminaalissa, siirry aluksi projektikansioon:

`cd ~/Projects/md-harjoitus`


### 2. Alusta Git-repositorio:

`git init`

Mitä tapahtuu: init (initialize) luo kansioon piilotetun .git-alikansion, johon Git alkaa tallentaa kaikkien tiedostojen muutoshistoriaa (versioita). Kansiostasi tuli juuri repositorio eli "repo". Tämä tehdään vain kerran per projekti. Näet piilokansion halutessasi komennolla ls -la (tuo -a näyttää piilotiedostot – kuten DOSin dir /a!).

### 3. Katso tilanne

`git status`

Tämä on Gitin tärkein peruskomento – se kertoo aina, mitä repossa on meneillään. Nyt sen pitäisi listata punaisella "Untracked files" -otsikon alla ohje.md ja kuvat/-kansio: Git näkee tiedostot, mutta ei vielä seuraa niitä.

Sama VS Codessa: katso vasemman reunan Source Control -kuvaketta (kolme palloa viivoilla yhdistettynä, Cmd + Shift + G). Näet samat tiedostot listassa merkinnällä U (Untracked). VS Code huomasi git init-komennon automaattisesti.

### 4. tiedostojen lisääminen seurantaan ja commit

Commit tehdään kahdessa vaiheessa. Ensin valitaan mukaan otettavat tiedostot:

`git add .`

Selitys: add siirtää tiedostot valmistelualueelle (staging area) eli "seuraavaan 'snapshottiin' (versiotallennukseen) mukaan tulevat editoidut tiedostot". Piste tarkoittaa "kaikki tämän kansion tiedostot". Aja `git status` uudelleen – tiedostot näkyvät nyt vihreällä, valmiina commitoitavaksi.

Voit muokata vaikka viittä tiedostoa, mutta ottaa commitiin mukaan vain kaksi niistä (`git add tiedosto1.md tiedosto2.md`) ja jättää loput seuraavaan committiin.

Sitten itse commit:

`git commit -m "Ensimmäinen versio: Markdown-perusteet dokumentoitu"`

Selitys: commit tallentaa valmistelualueen sisällön pysyväksi tilannekuvaksi(versioksi) historiaan tietokoneen projektikansion piilossa olevaan .git hakemistoon. -m (message) antaa commitille viestin, joka kuvaa mitä tehtiin – kirjoita viestit aina niin, että ymmärrät ne vielä kuukausienkin päästä. Komennolla `git log`voi katsoa kaikki aiemmat commitit ja tarvittaessa palata vanhempaan versioon (committiin). Mitään ei tässä vaiheessa ole siirretty GitHubiin.

Sama VS Codessa: Source Control -paneelissa paina tiedoston vieressä +-merkkiä (= git add), kirjoita viesti yläreunan tekstikenttään ja paina Commit-nappia.

Tämä kahtiajako on Gitin ydinajatus: paikallinen työskentely (add, commit) ja synkronointi etäpalvelimelle (push, pull) ovat erillisiä toimintoja. Voit tehdä vaikka kymmenen commitia junassa ilman nettiyhteyttä ja työntää ne kaikki kerralla GitHubiin myöhemmin.

### 5 Katso historia

`git log` komento Terminaalissa: Näet juuri tekemäsi commitin: tekijän, ajan, viestin ja commitin yksilöivän tunnisteen (pitkä merkkijono). Poistu näkymästä painamalla q. Tiiviimpi muoto: `git log --oneline`.

## Git --> GitHub

## Luodaan repositori GitHubiin

Tämä tehdään selaimessa:

1. Mene osoitteeseen github.com ja kirjaudu sisään (tunnus jukkarouhe)
2. Paina oikean yläkulman +-merkkiä ja valitse New repository
3. Täytä lomake:
    - Repository name: md-harjoitus (sama nimi kuin paikallisella kansiolla – ei pakollista, mutta selkeää)
    - Description: vapaaehtoinen, esim. "Markdown- ja Git-harjoitusprojekti"
    - Public / Private: valitse Public, jos dokumentaatio saa näkyä kaikille – tämä on myös GitHub Pages -julkaisun (vaihe 5) kannalta helpoin valinta ilmaisella tilillä
    - Tärkeää: älä ruksaa kohtia "Add a README", "Add .gitignore" tai "Choose a license" – repositorion pitää syntyä tyhjänä, koska sisältö tulee sinun koneeltasi. Jos GitHub loisi sinne valmiiksi tiedostoja, historiat menisivät ristiin.
4. Paina Create repository

GitHub näyttää nyt ohjesivun, jossa on valmiita komentoja. Käytetään niistä (lokaalisti tietokoneella) keskimmäistä vaihtoehtoa ("push an existing repository from the command line"), mutta käydään komennot läpi itse ymmärtäen.

### 2 Kytketään paikallinen repo GitHubiin (remote)

Terminaalissa projektikansiossa (tarkista siirtymällä `cd ~/Projects/md-harjoitus`):

`git remote add origin git@github.com:jukkarouhe/md-harjoitus.git`

Selitys: `remote` tarkoittaa etärepositoriota eli paikallisen repon "kaveria" verkossa. `add origin` lisää etärepon nimellä origin – se on vakiintunut nimi ensisijaiselle etärepolle (nimi voisi olla mikä vain, mutta origin on käytäntö, jota kaikki noudattavat). Osoite `git@github.com:...` on SSH-muotoinen osoite, eli yhteys todennetaan SSH-avaimellasi – salasanaa ei kysytä.

Tarkista toimiko paikallisen repon kytkentä GitHubiin komennolla

`git remote -v`

Terminaalin pitäisi tulostaa origin kaksi kertaa (fetch ja push):

```
jukkarouhe@Jukkas-MacBook-Pro md-harjoitus % git remote -v
origin	git@github.com:jukkarouhe/md-harjoitus.git (fetch)
origin	git@github.com:jukkarouhe/md-harjoitus.git (push)
jukkarouhe@Jukkas-MacBook-Pro md-harjoitus % 
```

### 3 Haaran nimeäminen ja commitin työntö GitHubiin

Ensin yhtenäistetään haaran nimi. Muistat ehkä `git init` -komennon vihjeen "master"-nimestä – GitHubin nykykäytäntö on main, joten nimetään paikallinen haara sen mukaiseksi:

`git branch -M main`

Selitys: `branch -M main` nimeää nykyisen haaran uudelleen nimellä main. (Haarat käsitellään syvemmin myöhemmin – tässä vaiheessa riittää tietää, että main on projektin päälinja, se aikajana jolle commitisi ovat tallentuneet.)

Sitten itse työntö:

`git push -u origin main`

Selitys: `push` lähettää paikalliset commitit etärepoon. `origin main` tarkoittaa "origin-nimiseen etärepoon, main-haaraan". Valitsin `-u` (upstream) tekee kytkennän muistiin: jatkossa pelkkä `git push` riittää, koska Git muistaa minne tämän haaran commitit kuuluvat. Tämä `-u` tarvitaan siis vain ensimmäisellä kerralla.

Jos SSH-yhteys kysyy ensimmäisellä kerralla "Are you sure you want to continue connecting (yes/no)?", vastaa yes – se on normaali varmistus, kun koneesi ottaa yhteyttä GitHubiin ensimmäistä kertaa.

Sama VS Codessa: Source Control -paneelin ...-valikosta (siis kolmen pisteen kautta avautuvasta drop-down valikosta source control osion yläpalkista) löytyvät Remote → Add Remote ja Push. Ensimmäisen pushin jälkeen VS Coden alapalkkiin ilmestyy myös synkronointikuvake (nuolet ympyränä), joka hoitaa push/pull-toiminnot yhdellä klikkauksella.

### 4: Onnistuminen tarkistus

Päivitä selaimessa repositoriosi sivu (github.com/jukkarouhe/md-harjoitus). Sinun pitäisi nähdä `ohje.md` ja `kuvat`-kansio siellä – ja hienona yksityiskohtana GitHub näyttää `ohje.md`:n sisällön valmiiksi muotoiltuna suoraan reposivulla, koska Markdown on GitHubin äidinkieltä. Voit myös klikata commit-historiaa (kellokuvake tai "commits") ja nähdä tekemäsi commitit viesteineen.

