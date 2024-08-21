## 7. GROUP BY (21.8)

GROUP BY ryhmittelymääreen sisältävän SQL-lauseen yleinen muoto on seuraava:

SELECT [kenttä], FUNKTIO(kenttä) FROM [Taulu] GROUP BY [kenttä]

Esimerkki 7.1: Artistien albumien kestot yhteensä

 SELECT   AlbumitArtisti, SUM(AlbumitKesto) 
 FROM     Albumit 
 GROUP BY AlbumitArtisti

 -> AlbumitArtisti  SUM(AlbumitKesto)	
--------------  --------------------
Metallica       157.920001983643	
Nirvana         44.2299995422363	
Pearl jam       70.2300033569336	

7.1 GROUP BY - HAVING
HAVING-määreen avulla voidaan muodostaa WHERE-määreen kaltaisia ehtoja kyselyihin, jotka kohdistuvat jonkin koostefunktion tulokseen. 

Esimerkki 7.2: Artistit ja albumien kestot yhteensä (joilla vähintään 60 minuuttia musiikkia)

 SELECT   AlbumitArtistit, SUM(AlbumitKesto)
 FROM     Albumit 
 GROUP BY AlbumitArtistit 
 HAVING   SUM(AlbumitKesto) > 60

-> AlbumitArtisti  SUM(AlbumitKesto)
--------------  -----------------
Metallica       157.920001983643
Pearl jam       70.2300033569336

Esimerkki 7.3: Virheellinen koostefunktion sisältävä lause

 SELECT   AlbumitArtistit, SUM(AlbumitKesto)
 FROM     Albumit 
 GROUP BY AlbumitArtistit 
 WHERE    SUM(AlbumitKesto) > 60

On siis syytä muistaa, ettei koostefunktioita voida käyttää SELECT-lauseen WHERE-osassa.

7.2 GROUP BY ja COUNT

Luvussa 4. esiteltiin COUNT-funktio, jonka avulla voidaan laskea yhteen kenttien lukumääriä. Havainnollistimme COUNT-funktiota esimerkillä, jossa laskettiin yhteen "Metallica" nimisen yhtyeen albumit:


Esimerkki 7.4: Metallican albumien määrä yhteensä
 SELECT   COUNT(*) 
 FROM     Albumi 
 WHERE    Artisti = 'Metallica'

Esimerkki 7.5: Artistien albumien lukumäärät
 SELECT   AlbumitArtisti, COUNT(*) 
 FROM     Albumit 
 GROUP BY AlbumitArtisti

