## 6. Kooste- ja skalaarifunktioita

Esimerkki 6.1: Laskutoimitus tiedon haussa

Esimerkki 6.1: Laskutoimitus tiedon haussa (CD-levyarkistosta voimme hakea albumeita, jotka on julkaistu yli kymmenen vuotta sitten)

 SELECT   * 
 FROM     Albumit 
 WHERE    (2002 - AlbumitJulkaisuvuosi) > 10

