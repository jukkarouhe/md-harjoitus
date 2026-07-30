# Markdown- ja GitHub-harjoitus

tämä dokumentti kokoaa opitut asiat askel askeleelta.

## Markdown-syntaksi

Otsikot tehdään risuaita-merkillä. Yksi risuaita on pääotsikko, kaksi risuaitaa on alaotsikko, kolme on sitä seuraava taso.

## matoviiva näppiksellä

Aaltoviiva ~ kirjoitetaan suomalaisella Mac-näppäimistöllä näin:

Paina Option (⌥) + ¨ – ¨-näppäin sijaitsee Å-näppäimen oikealla puolella, Enter-näppäimen vieressä. Option-näppäin on välilyöntinäppäimen vieressä (siinä lukee ⌥ tai "alt").
Ruudulle ei ilmesty vielä mitään (tai näkyy himmeä ~) – paina sitten välilyöntiä, ja ~ ilmestyy.

## Listat

Numeroimaton lista tehdään viivalla rivin alussa:

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

Teksti voi olla *kursivoitua* yhdellä tähdellä tai **lihavoitua** kahdella tähdellä. Koodi ja komennot merkitään `takahipsuilla` ( ` löytyy + merkin ja backspacen välistä)


## Linkit

Linkki tehdään hakasulkeilla ja kaarisulkeilla:

[Noppa-Yatzy pelitaulukko](https://jukkarouhe.github.io/yatzy/)

Linkkiteksti tulee hakasulkeisiin ja osoite kaarisulkeisiin.

## Kuvat

Kuva lisätään kuten linkki, mutta eteen tulee huutomerkki:

![poreallas kansi auki](kuvat/poreallas-kansi-auki.JPEG)

Polku kuvat/kuvan-nimi.jpg on suhteellinen polku: se tarkoittaa "tämän .md-tiedoston sijainnista katsottuna kuvat-kansiossa oleva tiedosto". Suhteelliset polut ovat tärkeitä, koska ne toimivat sellaisenaan myös GitHubissa ja MkDocs-sivustolla – toisin kuin koneesi absoluuttiset polut (esim. /Users/...).

## Koodilohkot

Yksittäinen komento merkitään takahipsuilla keskelle tekstiä,
esimerkiksi komento `ls -la` listaa myös piilotiedostot.

Monirivinen koodilohko tehdään kolmella takahipsulla:

```
mkdir kuvat
cd kuvat
ls
```

Kolmen takahipsun perään voi lisätä kielen nimen,
jolloin koodi saa värityksen:

```bash
cd ~/Projects/md-harjoitus
git status
ls la
```

Selitys: Aiemmin opit yksittäisen takahipsun tekstin keskellä. Koodilohko taas alkaa rivillä, jolla on kolme takahipsua ``` ja päättyy samanlaiseen riviin. Kaikki niiden välissä näytetään sellaisenaan harmaalla pohjalla – Markdown-merkit eivät vaikuta lohkon sisällä. Takahipsu tehtiin siis Shift + ´ ja välilyönti; kolme peräkkäin vaatii saman kolmesti (tai kikka: paina Shift + ´ kolme kertaa peräkkäin ja lopuksi välilyönti – saat kolme hipsua kerralla).

Kielen nimi avaavan rivin perässä (esim. ```bash) kertoo, millä kielellä koodi on kirjoitettu, jolloin editori ja GitHub värittävät sen luettavammaksi. Terminaalikomennoille käytetään nimeä bash, Python-koodille python ja niin edelleen.

## Taulukot

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

### 1. Kohdekansio
Työskentelet Terminaalissa, siirry aluksi projektikansioon:

`cd ~/Projects/md-harjoitus`


### 2. Alusta Git-repositorio:

`git init`

Mitä tapahtuu: init (initialize) luo kansioon piilotetun .git-alikansion, johon Git alkaa tallentaa kaikkien tiedostojen muutoshistoriaa. Kansiostasi tuli juuri repositorio eli "repo". Tämä tehdään vain kerran per projekti. Näet piilokansion halutessasi komennolla ls -la (tuo -a näyttää piilotiedostot – kuten DOSin dir /a!).

### 3. Katso tilanne

`git status`

Tämä on Gitin tärkein peruskomento – se kertoo aina, mitä repossa on meneillään. Nyt sen pitäisi listata punaisella "Untracked files" -otsikon alla ohje.md ja kuvat/-kansio: Git näkee tiedostot, mutta ei vielä seuraa niitä.

Sama VS Codessa: katso vasemman reunan Source Control -kuvaketta (kolme palloa viivoilla yhdistettynä, Cmd + Shift + G). Näet samat tiedostot listassa merkinnällä U (Untracked). VS Code huomasi git init-komennon automaattisesti.

### 4. tiedostojen lisääminen seurantaan ja commit

Commit tehdään kahdessa vaiheessa. Ensin valitaan mukaan otettavat tiedostot:

`git add .`

Selitys: add siirtää tiedostot valmistelualueelle (staging area) eli "seuraavaan valokuvaan mukaan tulevat". Piste tarkoittaa "kaikki tämän kansion tiedostot". Aja `git status` uudelleen – tiedostot näkyvät nyt vihreällä, valmiina commitoitavaksi.

Sitten itse commit:

`git commit -m "Ensimmäinen versio: Markdown-perusteet dokumentoitu"`

Selitys: commit tallentaa valmistelualueen sisällön pysyväksi tilannekuvaksi historiaan. -m (message) antaa commitille viestin, joka kuvaa mitä tehtiin – kirjoita viestit aina niin, että ymmärrät ne vielä kuukausienkin päästä.

Sama VS Codessa: Source Control -paneelissa paina tiedoston vieressä +-merkkiä (= git add), kirjoita viesti yläreunan tekstikenttään ja paina Commit-nappia.
