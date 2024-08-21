## 6. Kooste- ja skalaarifunktioita (21.8)

Esimerkki 6.1: Laskutoimitus tiedon haussa

Esimerkki 6.1: Laskutoimitus tiedon haussa (CD-levyarkistosta voimme hakea albumeita, jotka on julkaistu yli kymmenen vuotta sitten)

 SELECT   * 
 FROM     Albumit 
 WHERE    (2002 - AlbumitJulkaisuvuosi) > 10

6.1 SQL-funktiot: AVG

Esimerkki 6.2: Albumien keskimääräinen kesto
 SELECT   AVG(AlbumitKesto) 
 FROM     Albumit

Esimerkki 6.3: Halutun artistin albumien keskimääräinen pituus
 SELECT   AVG(AlbumitKesto) 
 FROM     Albumit 
 WHERE    AlbumitArtisti = 'Metallica'

6.2 SQL-funktiot: MAX

Esimerkki 6.4: CD-levyarkiston pisin albumi
 SELECT   MAX(AlbumitKesto) 
 FROM     Albumit

6.3 SQL-funktiot: MIN

Esimerkki 6.5: CD-levyarkiston lyhyin albumi
 SELECT   MIN(AlbumitKesto) 
 FROM     Albumit

6.4 SQL-funktiot: SUM

Esimerkki 6.6: Albumien kestot yhteensä
 SELECT   SUM(AlbumitKesto) 
 FROM     Albumi

6.5 SQL-funktiot: ABS

Esimerkki 6.7: Luettelo lukujen itseisarvoista
 SELECT   ABS(LuvutLuku) 
 FROM     Luvut

6.6 SQL-funktiot: MOD

Esimerkki 6.8: Luettelo lukujen jakojäännöksistä kun jakaja on 2
 SELECT   MOD(LuvutLuku, 2) 
 FROM     Luvut

6.7 SQL-funktiot: ROUND ROUND(数値、精度)


Esimerkki 6.9: ROUND-funktiolla pyöristettyjä lukuja
 SELECT   ROUND(LuvutLuku, 2) 
 FROM     Luvut

Jos halutaan pyöristää lukuja, jotka eivät ole tietotyypiltään NUMERIC, täytyy pyöristettävälle luvulle tehdä tyyppimuunnos. Tähän voi käyttää CAST-funktiota.

Esimerkki 6.10: CAST-funktion käyttäminen
 SELECT   ROUND(CAST(LuvutLuku AS NUMERIC), 2) 
 FROM     Luvut

-----

SELECT * FROM Henkilot WHERE MOD(HenkilotSyntymavuosi, 2) = 0

Hakee tiedot "Henkilot" taulun tietueista, joissa kenttä "HenkilotSyntymavuosi" sisältää parillisen arvon.