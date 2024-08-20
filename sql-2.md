## SQL Lesson 2 18.8.2024

SELECT  LainaajatEtunimi, LainaajatSukunimi 
FROM    Lainaajat

SELECT   LainaajatSukunimi 
FROM     Lainaajat

SELECT   * 
FROM     Lainaajat

SELECT   * 
FROM     Lainaajat 
WHERE    LainaajatSukunimi = 'Meikäläinen'

SELECT [kentät] FROM [taulut] WHERE [ehto]

OPERAATTORI	SELITE
=	yhtäsuuri kuin
>	suurempi kuin
<	pienempi kuin
>=	suurempi tai yhtäsuuri kuin
<=	pienempi tai yhtäsuuri kuin
<>	erisuuri kuin

SELECT   * 
FROM     Lainaukset 
WHERE    LainauksetLainausPvm < '2002-11-27'

Esimerkiksi CD-levyarkiston "Albumit" taulun kenttää "Julkaisuvuosi" voidaan käyttää 
sellaisten albumien hakemiseen, jotka on julkaistu yli kaksikymmentä vuotta sitten:

Esimerkki 2.6: Laskutoimitus tiedon haussa
SELECT   * 
FROM     Albumit 
WHERE    2002 - Julkaisuvuosi > 20

Monimutkaisia laskutoimituksia laadittaessa voidaan käyttää sulkuja, jolloin 
kyselyn luettavuutta voidaan parantaa. Edellisen esimerkin olisimme voineet laatia 
myös seuraavasti:

Esimerkki 2.7: Sulkeiden käyttö laskutoimituksissa
SELECT   * 
FROM     Albumit 
WHERE    (2002 - Julkaisuvuosi) > 20

Operaattori	Merkitys
+	yhteenlasku
-	vähennyslasku
*	kertolasku
/	jakolasku
