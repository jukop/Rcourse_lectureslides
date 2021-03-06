
# R-ohjelmoinnin perusteet

## Mikä R on ja mitä sillä tehdään?

Ohjelmoinnin tavoitteena on kirjoittaa eli koodata ohjelma, joka
suorittaa jonkun halutun tehtävän. Ohjelma koostuu useista komennoista,
joista jokainen tekee jotain hyvin yksinkertaista.

R on tehty ensisijaisesti tilastotiedettä ja data-analyysiä varten.
R:llä kirjoitetaan yleensä lyhyitä ohjelmia, joita kutsutaan
skripteiksi. R:llä ei siis ole tarkoitus kehittää esimerkiksi pelejä,
tai muita ohjelmia joissa on graafinen käyttöliittymä, kuten vaikkapa
Photoshop. R ei myöskään ole web-ohjelmointiin tarkoitettu kieli (vaikka
oikeilla paketeilla R:lläkin pystyy tekemään web-sovelluksia).

R on korkean tason ohjelmointikieli. Tämä tarkoittaa sitä, että R:ssä on
paljon valmiita komentoja, joiden “alta” löytyy paljon lisää koodia,
johon R-ohjelmoijan ei kuitenkaan tarvitse itse koskea. Esimerkiksi
tilastollisen t-testin testin laskeminen vaatii useita matemaattisia
välivaiheita, mutta R-ohjelmoija voi suorittaa testin yhdellä komennolla
(`t.test`) joka antaa kaikki tarvittavat tiedot testistä.

R:n käyttöä ja ohjelmointia muutenkin oppii parhaiten tekemällä. Tässä
dokumentaatiossa on tekstin väliin upotettu R-koodia harmaissa
laatikoissa, kuten alla olevassa esimerkissä. Kahdella ruudulla eli
`##`-merkinnällä alkavat rivit eivät ole koodia vaan koodin ajamisen
aiheuttamia tulosteita (output). Otetaan ensimmäiseksi esimerkiksi
klassinen [“Hello,
world!”](https://en.wikipedia.org/wiki/%22Hello,_World!%22_program)-komento:

``` r
print("Hello, world!")
```

    ## [1] "Hello, world!"

`print`-funktio tulostaa sille annetun tekstin konsoliin. `print` on
kätevä funktio mm. ohjelman toiminnan testaamiseen ja pidemmän ohjelman
etenemisen seurantaan. R:ää voi käyttää myös laskimen sijaan. Alla
olevassa esimerkissä lasketaan kuinka paljon jää hintaa 80 euron
hintaiselle tuotteelle 35% alennuksen jälkeen.

``` r
80 * (1 - 0.35)
```

    ## [1] 52

Yksittäisten komentojen ajamisesta ei kuitenkaan ole yleensä hyötyä,
ellei tuloksia voi tallentaa johonkin. Ohjelmointikielissä tietoja
tallennetaan muuttujiin, joita käsitellään seuraavaksi.

## Muuttujat (Variables)

**Muuttujat** (variables) ovat yksi tärkeimmistä ohjelmointikielien
rakenteista. Muuttujien tehtävä on säilyttää tietoa ja tuloksia
edellisistä laskutoimituksista. Alla on yksinkertainen esimerkki
muuttujien käytöstä R:ssä

``` r
x <- 3
y <- 5
z <- x + y

z
```

    ## [1] 8

Edellisessä esimerkissä **sijoitetaan (assign)** eli tallennetaan
muuttujaan x arvo 3 ja muuttujaan y arvo 4. Sen jälkeen muuttujien x ja
y summa sijoitetaan muuttujaan z, jonka jälkeen tulostetaan muuttujan z
arvo. `<-` on R:n **sijoitusoperaattori** (Myös yhtä kuin-merkki `=`
toimii melkein aina, mutta `<-` on suositellumpi). Mutta miten muuttujan
z arvo tulostui konsoliin, vaikka koodissa ei käytetty funktiota
`print`? R:n erikoisominaisuus moneen muuhun ohjelmointikieleen
verrattuna on se, että print-käskyä ei tarvitse aina kirjoittaa, vaan
pelkästään muuttujan (tai laskutoimituksen) kirjoittaminen tulostaa
arvon konsoliin. Alla olevassa koodissa kaikki rivit tulostavat saman
tuloksen:

``` r
z
print(z)

x + y
print(x + y)

3 + 5
print(3 + 5)
```

Muuttujiin voi sijoittaa muutakin kuin yksittäisiä lukuja, kuten
merkkijonoja (strings), vektoreita, tai paljon monimutkaisempiakin
rakenteita.

``` r
x <- "Hello world"
x
```

    ## [1] "Hello world"

## Kommentit

Myöhemmin vastaan tulevassa koodissa käytetään kommentteja. Kommentit
ovat koodin oheen kirjoitettua tekstiä, joka ei ole ohjelmointikieltä,
ja joka ohitetaan koodia ajettaessa. Kommenttien tarkoitus on kuvailla
koodin toimintaa. Oman koodin kommentointia on hyvä harjoitella alusta
lähtien, vaikka ensimmäisten tehtävien koodi onkin hyvin yksinkertaista.
hyvä nyrkkisääntö on muistaa, että koodia kirjoitetaan ihmisille, ei
koneelle. R:ssä kommentit merkataan `#`-symbolilla. Edellinen esimerkki
kommentoituna voisi näyttää jotakuinkin tältä:

``` r
# Assign arbitrary numbers to two variables
x <- 3
y <- 5
# Sum of two variables
z <- x + y
# Print the results
z
```

    ## [1] 8

## Vektorit (Vectors)

Nyt kun muuttujat ovat tuttuja, voimme siirtyä käsittelemään vektoreita.
R:n vektorit ovat yksinkertaisia järjestettyjä tietorakenteita, jotka
koostuvat alkioista (elements), esimerkiksi desimaaliluvuista. Alla
oleva esimerkki sijoittaa muuttujaan x vektorin, joka sisältää 5 lukua.

``` r
x <- c(1, 2, 7.4, 15, 0.2)
x
```

    ## [1]  1.0  2.0  7.4 15.0  0.2

Yksinkertaisin tapa tehdä vektori R:ssä on käyttää `c()`-funktiota, joka
luo vektorin, jossa on sille annetut arvot annetussa järjestyksessä.
Monet R-kielen komennot ja funktiot luovat vektoreita, alla muutama
esimerkki:

``` r
# Regular sequences
seq(1, 10)
```

    ##  [1]  1  2  3  4  5  6  7  8  9 10

``` r
seq(0, 1, by = 0.2)
```

    ## [1] 0.0 0.2 0.4 0.6 0.8 1.0

``` r
seq_len(6)
```

    ## [1] 1 2 3 4 5 6

``` r
3:9
```

    ## [1] 3 4 5 6 7 8 9

``` r
# Repeat values
rep(1, 5)
```

    ## [1] 1 1 1 1 1

``` r
rep(c(1, 2), 3) # Repeat vector c(1,2) 3 times
```

    ## [1] 1 2 1 2 1 2

``` r
rep(c(1, 2, 3), 3) # Repeat all values in vector c(1, 2, 3) 3 times
```

    ## [1] 1 2 3 1 2 3 1 2 3

### Vektorilaskentaa

Vektoreilla laskeminen on usein hyvin intuitiivista (lisää
vaaranpaikoista myöhemmin). Kun vektoriin kohdistetaan laskutoimintoja,
sama operaatio tehdään kaikille vektorin alkioille (engl.
vectorization).

``` r
x <- c(1, 2, 3, 6, 10)
x * 2
```

    ## [1]  2  4  6 12 20

``` r
x / 2 + 1
```

    ## [1] 1.5 2.0 2.5 4.0 6.0

Entä jos vektoreita lisää toisiinsa, tai kertoo keskenään? Jos vektorit
ovat samanpituisia, operaatio toteutetaan alkio kerrallaan. Jos vektorit
ovat eripituisia, R yrittää kierrättää (recycle) lyhyempää vektoria
niin, että siitä tulee yhtä pitkä kuin pidempi vektori. Tämän jälkeen
operaatio suoritetaan alkio kerrallaan (itse asiassa näin tapahtui myös
aiemmissa esimerkeissä, kun vektori kerrottiin yksittäisellä luvulla.
R:ssä yksittäiset luvut ovat vektoreita, joiden pituus on 1). Jos
kierrätys ei onnistu, eli pidemmän vektorin pituus ei ole jaollinen
lyhyemmän pituudella, R antaa virheilmoituksen.

``` r
x <- c(1, 2, 3, 6, 10, 2)
y <- c(1, 1, 1, 3, 3, 3) # or rep(c(1, 3), each = 3)
z <- c(2, 4)

x + y # Element-wise sum
```

    ## [1]  2  3  4  9 13  5

``` r
x * y # Element-wise multipliocation
```

    ## [1]  1  2  3 18 30  6

``` r
x + z
```

    ## [1]  3  6  5 10 12  6

R:ssä on myös paljon funktioita, joilla voi laskea vektoreista erilaisia
tunnuslukuja, kuten keskiarvon, mediaanin, keskihajonnan jne.

``` r
x <- c(1, 2, 3, 6, 10, 2)
# Sample mean (average)
mean(x)
```

    ## [1] 4

``` r
# Standard deviation
sd(x)
```

    ## [1] 3.405877

``` r
# Sum
sum(x)
```

    ## [1] 24

### Ei-numeeriset vektorit

#### Merkkijonovektorit

Vektorien ei ole pakko sisältää lukuja. Vektorit voivat sisältää
esimerkiksi merkkijonoja, kuten alussa nähty “Hello, world!”.
Merkkijonotyypin nimi R:ssä on `character`.

``` r
x <- c("Hello, world!", "R is the best", "I", "like", "programming", "!")
x
```

    ## [1] "Hello, world!" "R is the best" "I"             "like"         
    ## [5] "programming"   "!"

Merkkijonovektoreiden muokkausta varten on omia funktiota, tärkeimpinä
`paste` ja `paste0`, jotka yhdistävät merkkijonoja toisiinsa. Myös
numeerisia vektoreita voi antaa näille funktioille, ja ne muutetaan
merkkijonoiksi.

``` r
first_names <- c("Diana", "Peter", "Bruce")
last_names <- c("Prince", "Parker", "Wayne")
paste(first_names, last_names)
```

    ## [1] "Diana Prince" "Peter Parker" "Bruce Wayne"

``` r
students <- paste0("Student_", 1:5)
```

#### Loogiset vektorit

Kolmas yleinen vektorityyppi on looginen vektori, joka sisältää arvoja
`TRUE` eli tosi tai `FALSE` eli epätosi. Loogisia vektoreita käytetään
yleensä joko merkitsemään binäärisiä muuttuja (esimerkiksi paastosiko
koehenkilö ennen näytteenottoa) tai vektorien ja matriisien
indeksoinnissa (tästä lisää pian). Tällöin loogisia vektoreita syntyy
erilaisten loogisten operaattorien avulla:

``` r
x <- c(1, 2, 3, 6, 10, 2)

x > 3 # Is the element of x greater than 3?
```

    ## [1] FALSE FALSE FALSE  TRUE  TRUE FALSE

``` r
x >= 3 # Greater or equal to three=
```

    ## [1] FALSE FALSE  TRUE  TRUE  TRUE FALSE

``` r
x == 6 # Equal to 6?
```

    ## [1] FALSE FALSE FALSE  TRUE FALSE FALSE

``` r
x != 2 # Not equal to 2?
```

    ## [1]  TRUE FALSE  TRUE  TRUE  TRUE FALSE

#### Loogiset vektorit ja matematiikka

Jos loogiselle vektorille tekee operaation, joka odottaa numeerista
vektoria, R muuttaa automaattisesti arvot `TRUE` ykkösiksi ja arvot
`FALSE` nolliksi. Tämä on erityisen hyödyllistä käytettäessä funktiota
`sum`. Tällä tavalla saadaan helposti tietää esim. kuinka moni vektorin
alkio täyttää tietyn ehdon:

``` r
x <- c(1, 3, 5, 2, 19)
above_3 <- x > 3

# Logical vector automatically converted to numeric
x + 1
```

    ## [1]  2  4  6  3 20

``` r
# how many elements of x are smaller than 10?
sum(x < 10)
```

    ## [1] 4

### Vektorien indeksointi ja leikkely

Usein vektorista halutaan poimia vain tietyt arvot, esimerkiksi vain
ensimmäiset 5 arvoa, tai vain arvot, jotka täyttävät tietyt ehdot. R:ssä
vektorin indeksointiin käytetään hakasulkeita `[]`. Yleisimmät
indeksointitavat ovat antaa hakasulkeiden sisään vektori kokonaislukuja,
jotka vastaavat järjestyslukuja, jotka vektorista halutaan poimia (HUOM
kokeneemmat koodarit, R:ssä indeksointi alkaa ykkösestä, ei nollasta!).
Toinen vaihtoehto on käyttää loogista vektoria, jolloin vektorista
poimitaan ne alkiot, joiden kohdalla loogisen vektorin arvo on TRUE.
Tämä on yksinkertaisempaa kuin miltä se kuulostaa:

``` r
x <- c(1, 2, 3, 6, 10, 2)

# Picking exact elements
x[2:3] # Second and third values
```

    ## [1] 2 3

``` r
x[c(4, 5, 1)] # Note that the order does not have to be increasing
```

    ## [1]  6 10  1

``` r
# Using logical vector as condition
x[x > 3]
```

    ## [1]  6 10

``` r
# The condition can be based on another vector
characters <- c("Yoda", "C-3PO", "Rey", "R2-D2", "Anakin", "Baby Yoda")
heights <- c(66, 175, 170, 109, 183, 40.5)
# Only characters shorter than 120 cm
characters[heights < 120]
```

    ## [1] "Yoda"      "R2-D2"     "Baby Yoda"

### Puuttuvat arvot

Monessa tutkimusprojektissa törmätään syystä tai toisesta jossain
vaiheessa puuttuviin arvoihin. Hyvä esimerkki ovat seurantatutkimukset,
jossa usein seurannan lopussa on jäljellä vähemmän koehenkilöitä kuin
alussa.

Puuttuvia arvoja merkataan R:ssä merkinnällä `NA` (not available).
Puuttuvat arvot noudattavat yksinkertaista logiikkaa: mikä tahansa
operaatio `NA`:lle antaa tulokseksi `NA`. Funktiot, jotka operoivat koko
vektoria, kuten `sum` tai `mean` voidaan erikseen asettaa poistamaan
puuttuvat arvot ennen summan, keskiarvon tms. laskemista.

``` r
missing <- c(1, 2, NA, 4, NA, 6)
full <- seq(1, 6)

# Addition with NA returns NA
missing + full
```

    ## [1]  2  4 NA  8 NA 12

``` r
# Sum of vector with NAs returns NA
sum(missing)
```

    ## [1] NA

``` r
# Removing NAs before summation
sum(missing, na.rm = TRUE)
```

    ## [1] 13

HUOM! Funktio `is.na` tarkistaa, onko jokin arvo puuttuva. Perinteinen
yhtäsuuruuden testaaminen ei siis toimi

``` r
# Just returns NA
NA == NA
```

    ## [1] NA

``` r
# Returns a logical value as expected
is.na(NA)
```

    ## [1] TRUE

``` r
is.na(1)
```

    ## [1] FALSE

``` r
# is.na operates element-wise on a vector
missing <- c(1, 2, NA, 4, NA, 6)
is.na(missing)
```

    ## [1] FALSE FALSE  TRUE FALSE  TRUE FALSE

## Tehtävien aloitus

Tämän ohjeen ja R:n virallisen manuaalin tai pienen googlailun avulla
selviät ensimmäisen viikon tehtävistä. Katso vielä etusivulta vinkki
tehtävien tallentamisesta R-skriptiin
[(linkki)](https://github.com/antonvsdata/r_intro#kurssin-suoritus-rstudiolla).
