## 3.1 AND (20.8.2024)

Esimerkki 3.1: Levyjen hakeminen vuosilta 1988-1999

SELECT   * 
FROM     Albumit
WHERE    AlbumitJulkaisuvuosi >= 1988 AND AlbumitJulkaisuvuosi <= 1999

Esimerkki 3.2: Levyjen hakeminen useisiin kriteereihin perustuen

SELECT   * 
FROM     Albumit
WHERE    AlbumitArtisti = 'Metallica' AND AlbumitJulkaisuvuosi >= 2000

## 3.2 OR


Esimerkki 3.3: Tiedon hakua OR-operaattorin avulla

SELECT   *
FROM     Albumit 
WHERE    AlbumitJulkaisuvuosi = 1972 OR AlbumitJulkaisuvuosi = 1974 OR AlbumitJulkaisuvuosi = 1988

## 3.3 AND ja OR samassa kyselyssä

Esimerkki 3.4: AND ja OR samassa kyselyssä

SELECT   * 
FROM     Albumit 
WHERE    AlbumitJulkaisuvuosi >= 1960 AND AlbumitJulkaisuvuosi < 1970 OR AlbumitJulkaisuvuosi > 1999

## 3.4 BETWEEN-AND

Esimerkki 3.6: Arvoalueen määrittely BETWEEN-AND operaattorilla

SELECT   * 
FROM     Albumit 
WHERE    AlbumitJulkaisuvuosi BETWEEN 1988 AND 1999

## 3.4 LIKE

Esimerkki 3.7: Kirjaimella "t" alkavat albumit

SELECT   * 
FROM     Albumit 
WHERE AlbumitAlbuminNimi LIKE 't%'

Esimerkki 3.8: Kirjaimeen "t" päättyvät albumit

SELECT   * 
FROM     Albumi
WHERE    AlbumitAlbuminNimi LIKE '%t'

Esimerkki 3.9: Albumit, joissa kirjaimet "uppet"

SELECT   AlbumitAlbuminNimi 
FROM     Albumit 
WHERE    AlbumitAlbuminNimi LIKE '%uppet%'

-> AlbuminNimi
Master of puppets	


Esimerkki 3.10: Monimutkaisempi merkkijonohaku

SELECT   AlbumitAlbuminNimi 
FROM     Albumi 
WHERE    AlbumitAlbuminNimi LIKE '%e%mi%'

->Koska kyselyssä jokainen %-merkki voi olla mikä tahansa yhdistelmä kirjaimia, haku täsmäisi esimerkiksi albumiin "Nevermind".