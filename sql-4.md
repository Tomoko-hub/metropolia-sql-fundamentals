## 4.1 ORDER BY ja DESC (20.8.2024)

Esimerkki 4.1: Tuloksen järjestäminen sukunimen mukaan

SELECT   LainaajatEtunimi, LainaajatSukunimi 
FROM     Lainaaja 
ORDER BY LainaajatSukunimi


Esimerkki 4.2: Albumien nimet järjestettynä julkaisuvuoden mukaan (nouseva järjestys)

SELECT   AlbumitAlbuminNimi 
FROM     Albumi 
ORDER BY AlbumitJulkaisuvuosi

Esimerkki 4.3: Albumien nimet järjestettynä julkaisuvuoden mukaan (laskeva järjestys)

SELECT   AlbumitAlbuminNimi, AlbumitJulkaisuvuosi 
FROM     Albumi 
ORDER BY AlbumitJulkaisuvuosi DESC
(大きい方から順に)

 Lyhenteet ASC ja DESC tulevat englanninkielisistä sanoista "ascending" ja "descending". Lisäämällä DESC-määreen edelliseen esimerkkiin, saamme tuloksen lajiteltuna laskevassa järjestyksessä


AlbumitAlbuminNimi  AlbumitJulkaisuvuosi	
------------------  --------------------	
Nevermind           1991
Ten                 1988
Master of puppets   1986
Ride the lightning  1984
Kill em all         1981

Esimerkki 4.4: Lainaajien tiedot lajiteltuna suku- ja etunimen mukaan

SELECT   * 
FROM     Lainaajat 
ORDER BY LainaajatSukunimi, LainaajatEtunimi


Esimerkki 4.5: Lainaajien tiedot (sukunimi laskevassa ja etunimi nousevassa järjestyksessä)

SELECT   * 
FROM     Lainaajat 
ORDER BY LainaajatSukunimi DESC, LainaajatEtunimi

## 4.2 DISTINCT
DISTINCT-määreen avulla voimme jättää pois kyselyn tuloksessa toistuvat arvot.


Esimerkki 4.6: CD-levyarkiston artistit (haku 1)

SELECT   AlbumitArtisti 
FROM     Albumit 
ORDER BY AlbumitArtisti


Esimerkki 4.7: CD-levyarkiston artistit (haku 2)

SELECT   DISTINCT AlbumitArtisti 
FROM     Albumit 
ORDER BY AlbumitArtisti

## 4.3 COUNT

COUNT-funktiota käytetään erilaisten tietueiden tai kenttien lukumäärien laskemiseen

Esimerkki 4.8: Albumien lukumäärä

SELECT   COUNT(*) 
FROM     Albumit
 COUNT -> 5

Esimerkki 4.9: Metallican albumien lukumäärä

SELECT   COUNT(*) 
FROM     Albumit 
WHERE    AlbumitArtisti = 'Metallica'
 -> COUNT -> 3