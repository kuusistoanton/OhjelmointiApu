# Luokat, Oliot ja Alustajat

Tämä moduuli on tarkoitettu opettamaan olioiden käyttöä erilaisissa mahdollisissa oikean elämän tilanteissa, ja perehdyttämään sinut niiden käytössä vaadittuihin Luokkiin sekä Alustajiin.

## Luokat ja oliot (perusteet)

Olio-ohjelmoinnissa käytetty Luokka, on koko järjestelmän alkupiste. Sillä tarkoitetaan yleiskäsitettä, joka määrittää yleiset ja yhteiset piirteet, joita sen luomilla olioilla tulee olemaan.

Luokan toiminnan voi toisella tavalla ajatella eräänlaisena tehtaana. Tällä tehtaalla on alustaja, jolla on vaatimukset mitä sen jokaisella tuotoksella(oliolla) tulee olemaan.

Esimerkkeinä käytämme yleisiä pelitermejä ja ominaisuuksia jotta ymmärtäminen saattaa olla helpompaa.

Tässä esimerkissä meidän tehtaamme(Luokka) on `Pelaaja`, jonka alustajan vaatimuksina ovat että jokaiselle sen luomalle pelaajalle(olio) täytyy antaa `hp` arvo, `armor` arvo, `money` arvo sekä `team` arvo.

Tämä näkyy koodissa seuraavasti.

```python
class Pelaaja: # Tämä on ohjelman Luokka/Tehdas
    def __init__(self, hp, armor, money, team) # Tämä on luokan alustaja (aina "__init__") 

        # Alla luodaan pelaaja(olio) tässä tapauksessa pelaaja1.
        # Voit kuvitella toiminnan siten, että pelaaja1 muuttuja kävelee tehtaaseen,
        # ja hyppää jokaisen alla olevan "self" tilalle.
        # Jonka jälkeen pelaaja1.hp on alustajaan syötetty hp arvo (100), pelaaja1.armor on (50) jne.
        self.hp = hp
        self.armor = armor
        self.team = team
        self.money = money

pelaaja1 = Pelaaja(100, 50, 5000, "Blue")
```

Yllä olevassa koodissa luodaan tasan 1 olio nimeltä `pelaaja1`. Tämä saa arvoikseen `Pelaaja` luokkaan syötetyt arvot `hp: 100`, `armor: 50`, `money: 5000` ja `team: Blue`.

Jos koodiin lisättäisiin pelaaja2, `Pelaaja` luokan avulla se toimisi seuraavasti.

```python

pelaaja1 = Pelaaja(100, 50, 5000, "Blue")
pelaaja2 = Pelaaja(100, 25, 6000, "Red")

````
Luokan ansiosta uusien pelaajien lisääminen on hyvin helppoa. Pitää vain kutsua `Pelaaja` luokkaa ja syöttää sen alustajaan sen vaatimat arvot. Lisäksi täytyy muistaa tallentaa olio muuttujaan, tässä tapauksessa uusi pelaaja(olio) olisi `pelaaja2`.
**HUOM** 
Alustajaan syötetyt arvot voivat olla samat tai eri oliolta oliolle. (voi olla useampi pelaaja jolla on **100 hp**, **50 armor**, joiden joukkue on **Blue** ja jolla on **5000€**)

**MUTTA** 
Jos käytät jo olemassa olevaa muuttujanimeä esim:
```monospace
pelaaja1 = Pelaaja(100, 50, 5000, "Blue")
pelaaja1 = Pelaaja(80, 20, 7000, "Red")
```
tämä korvaa pelaaja1 tiedot uusilla arvoilla. 


## Olioiden käyttö
Seuraavassa esimerkissä katsomme mitä luodulla oliolla pystymme tehdä.
Helpoin esimerkki on pelaajan eri tietojen tulostus jonka voimme tehdä seuraavasti:
```python
class Pelaaja:
    def __init__(self, hp, armor, money, team)
        self.hp = hp
        self.armor = armor
        self.money = money
        self.team = team

pelaaja1 = Pelaaja(100, 50, 5000, "Blue") # Luodaan pelaaja1(olio)

print (f"HP: {pelaaja1.hp}, Armor: {pelaaja1.armor}, Money: {pelaaja1.money}, Team: {pelaaja1.team}" )
```
Esimerkissä ensin luodaan `pelaaja1` olio, jonka jälkeen sen tiedot voidaan tulostaa käyttäen f-string:iä käyttäen muotoa `olion_nimi.haluttu_arvo`.

Kyseinen ohjelma antaisi tuloksen:
```monospace
HP: 100, Armor: 50, Money: 5000, Team: Blue
```

Tätä pystyttäisiin käyttämään esimerkiksi tulostaulukoiden esittelyssä seuraavalla tavalla:
```python
class Pelaaja:
    def __init__(self, name, score)
        self.name = name
        self.score = score

username = input("Give a username: ")
pelaaja1 = Pelaaja(username, 0)
# Luodaan olio käyttäen käyttäjän syöttämää nimiarvoa
# Aloituspisteet ovat 0

print (f"Player: {pelaaja1.name}, Score: {pelaaja1.score}") # Tulostetaan pelaajan aloitustiedot

pelaaja1.score = pelaaja1.score + 100 # Tämän jälkeen pelaaja ansaitsee 100 pistettä
print(f"{pelaaja1.name} ansaitsi 100 pistettä!") # Annetaan käyttäjälle ilmoitus pisteiden saannista

print (f"Player: {pelaaja1.name}, Score: {pelaaja1.score}") # Tulostetaan pelaajan tiedot uudelleen
```
Ohjelma alkaisi kysymällä pelaajan käyttäjänimeä (esimerkkinä `Pertti`) ja toimisi seuraavasti:
```monospace
Give a username: Pertti
>>>
Player: Pertti, Score: 0
Pertti ansaitsi 100 pistettä!
Player: Pertti, Score: 100
```

Huomaa Python-kielen vakiintunut kirjoitustapa luokkien nimille: ne kirjoitetaan isoin alkukirjaimin. Jos luokan nimi koostuu
useammasta sanasta, sanat kirjoitetaan yhteen ilman alaviivamerkkiä siten, että kukin sana aloitetaan isolla
alkukirjaimella. Tästä kirjoitustyylistä käytetään nimitystä *CamelCase*. Esimerkki tällaisesta luokan nimestä
on `NäytönSuorakulmio`.


## Alustaja eli konstruktori

Edellä Koira-olio luotiin siten, että ensin tehtiin olio ilman ominaisuuksia, ja sen jälkeen oliolle määritettiin
ominaisuudet yksi kerrallaan. Tämä on ohjelmoijalle melko työläs tapa luoda olioita.

Olioiden luonnin helpottamiseksi luokan sisälle kirjoitetaan usein alustaja eli konstruktori, joka automaattisesti
asettaa halutut arvot luotavan olion ominaisuuksiksi. Seuraavan esimerkin luokassa on nimen ja syntymävuoden asettava
alustaja. Pääohjelma käyttää olion luonnissa juuri laadittua alustajaa:

```python
class Koira:
    def __init__(self, nimi, syntymävuosi):
        self.nimi = nimi
        self.syntymävuosi = syntymävuosi

koira = Koira("Rekku", 2022)

print (f"{koira.nimi:s} on syntynyt vuonna {koira.syntymävuosi:d}." )
```

Python-kielen alustaja määritetään luokan sisällä kirjoittamalla funktio, jonka nimenä
on `__init__`. Funktion ensimmäiseksi parametriksi määritetään aina `self`. Tämän jälkeen määritellään
muut parametrit, jotka alustajalle halutaan antaa. Tässä tapauksessa ne ovat nimi ja syntymävuosi. Näin kirjoitettu
ja nimetty funktio tulkitaan ohjelmaa ajettaessa automaattisesti alustajaksi, ja se suoritetaan aina, kun uusi
olio luodaan. Alustajan loppuun ei kirjoiteta return-lausetta.

Alustajan sisällä on kaksi sijoituslausetta, joilla annetaan arvot luotavan olion ominaisuuksille.
Uuden olion ominaisuuksiin viitataan kirjoittamalla varattu sana `self`, minkä jälkeen tulee piste ja halutun
ominaisuuden nimi. Uuden olion ominaisuuden arvoksi annetaan tyypillisesti alustajan parametrina saatu arvo. Esimerkiksi
lause `self.nimi = nimi` antaa uuden olion nimi-ominaisuuden arvoksi nimi-parametrimuuttujan arvon.

Huomaa, että oliota luotaessa alustajan ensimmäinen parametri `self` ohitetaan kokonaan. Ei siis kirjoiteta:
```python
# Virheellinen luontilause
koira = Koira(self, "Rekku", 2022)
```
vaan kirjoitetaan:
```python
koira = Koira("Rekku", 2022)
```


## Metodit

Edellä opittiin määrittämään oliolle ominaisuuksia. Tämän lisäksi olioille halutaan usein määrittää toimintoja, joita 
kutsutaan metodeiksi. Kirjoitetaan alla Koira-luokkaan hauku-metodi, jota voidaan kutsua Koira-luokan ilmentymille eli
olioille. Esimerkin ohjelma luo kaksi Koira-oliota ja käskee niitä haukkumaan kyseiselle oliolle
tyypilliseen tapaan:

```python
class Koira:
    def __init__(self, nimi, syntymävuosi, haukahdus="Vuh-vuh"):
        self.nimi = nimi
        self.syntymävuosi = syntymävuosi
        self.haukahdus = haukahdus

    def hauku(self, kerrat):
        for i in range(kerrat):
            print(self.haukahdus)
        return


koira1 = Koira("Muro", 2018)
koira2 = Koira("Rekku", 2022, "Viu viu viu")

koira1.hauku(2)
koira2.hauku(5)
```

Alustajan parametreja on nyt kolme. Viimeiselle parametrille (`haukahdus`) on annettu oletusarvo, joka asetetaan
silloin, kun parametria ei oliota luetaessa anneta. Esimerkissä Muro-koira saa siis oletushaukahduksen.

Luokan sisään kirjoitettiin `hauku`-niminen metodi, jota voidaan kutsua mille tahansa olemassa olevalle Koira-luokan
ilmentymälle. Metodin ensimmäiseksi parametriksi asetetaan aina `self`. Tämän jälkeen luetellaan muut parametrit, joiden
arvo annetaan metodia kutsuttaessa.

Metodin kutsu tehdään siten, että kirjoitetaan olion nimi, sen jälkeen piste ja lopuksi metodin nimi kaarisulkeineen
ja mahdollisine parametreineen. Esimerkiksi kutsu `koira1.hauku(2)` kutsuu koira1-olion hauku-metodia. Metodikutsun parametrina
välitetään haukahdusten määrä (2). Metodin sisällä voidaan viitata olion omiin ominaisuuksiin siten,
että kirjoitetaan `self`, jota seuraa piste ja ominaisuuden nimi. Esimerkiksi ilmaisu `self.haukahdus` viittaa kulloisenkin
olion `haukahdus`-ominaisuuden arvoon.

## Luokkamuuttuja eli staattinen muuttuja

Aiemmassa esimerkissä koiran ominaisuuksina olivat nimi, syntymävuosi ja haukahdus. Olion ominaisuudet ovat tietenkin oliokohtaisia, eli yhdellä koiralla voi olla eri nimi kuin toisella koiralla.

Toisinaan on tarve tallentaa jokin koko luokkaa koskeva tieto, joka ei liity mihinkään yksittäiseen luokan olioon.
Esimerkiksi `Koira`-luokan tapauksessa tällainen ominaisuus voisi olla tieto siitä, montako koiraa (eli `Koira`-luokan ilmentymää) kaiken kaikkiaan on luotu. Tällainen tieto voidaan tallentaa luokkamuuttujaan eli staattiseen muuttujaan.

Seuraavassa esimerkissä on laadittu `tehty`-niminen luokkamuuttuja lukumäärän tallentamiseksi. Huomaa muuttujan sijoittaminen alustajan ulkopuolelle. Luokkamuuttujan määrityslauseeseen ei lisätä `self.`-etuliitettä. (Esimerkistä on jätetty pois aiempi haukkumistoiminnon toteutus.)

```python
class Koira:

    tehty = 0

    def __init__(self, nimi, syntymävuosi, haukahdus="Vuh-vuh"):
        self.nimi = nimi
        self.syntymävuosi = syntymävuosi
        self.haukahdus = haukahdus
        Koira.tehty = Koira.tehty + 1

koira1 = Koira("Muro", 2018)
koira2 = Koira("Rekku", 2022, "Viu viu viu")
print (f"Koiria on nyt {Koira.tehty}.")
```

Luokkamuuttujan arvoon viitataan kirjoittamalla sekä luokan että luokkamuuttujan nimi, esimerkissä siis `Koira.tehty`.

Ohjelma tuottaa seuraavan tulosteen:
```monospace
Koiria on nyt 2.
```
