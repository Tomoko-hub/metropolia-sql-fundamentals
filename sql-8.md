## 8. AS (22.8)

-Kenttien ja taulujen uudelleen nimeäminen
-Kyselyn tuloksessa olevien kenttien väliin lisätyn tekstin nimeäminen
-Laskutoimitusten tuloksena saatujen kenttien uudelleen nimeäminen
-COALESCE-funktiolla määritellyn tuloskentän uudelleen nimeäminen

8.1 Kenttien uudelleen nimeäminen

Esimerkki 8.1: AS kenttien nimeämisessä
 SELECT   LainaajatEtunimi AS Etunimi, LainaajatSukunimi AS Sukunimi 
 FROM     Lainaajat

8.2 Tekstin lisääminen kenttien väliin


Esimerkki 8.2: AS tekstin lisäämisessä
 SELECT   AlbumitArtisti, 'on julkaissut albumin' AS Apukentta, AlbumitNimi 
 FROM     Albumit

8.3 Funktioiden ja laskutoimitusten tulosten nimeäminen
Esimerkki 8.3: Funktiokentän uudelleen nimeäminen
 SELECT   AlbumitArtisti AS Artisti, COUNT(*) AS AlbumienLkm 
 FROM     Albumit 
 GROUP BY AlbumitArtisti

Esimerkki 8.4: Laskutoimituksen tuloksen nimeäminen
 SELECT   AlbumitNimi, 2002 - AlbumitJulkaisuvuosi AS AlbuminIka 
 FROM     Albumit

8.3 AS ja COALESCE
Esimerkki 8.5: tyhjiä arvoja tuloksessa
 SELECT   LainaajatEtunimi AS Etunimi, LainaajatSukunimi AS Sukunimi, LainaajatEmail AS Email 
 FROM     Lainaajat

->
Etunimi  Sukunimi     Email	
-------  --------     -----	
Esko     Tahvanainen  esko@email.com	
Kalevi   Härmä	
Maija    Meikalainen  maija.meikalainen@meikamanne.com	
Marko    Meikalainen  make@hotmail.com	
Tero     Teräväinen			
Liisa    Virtanen			


Esimerkki 8.6: tyhjien arvojen korvaaminen
 SELECT   LainaajatEtunimi AS Etunimi, 
         LainaajatSukunimi AS Sukunimi, 
         COALESCE (LainaajatEmail, 'ei sähköpostiosoitetta') AS Email 
 FROM     Lainaajat

->
Etunimi  Sukunimi     Email	
-------  --------     -----	
Esko     Tahvanainen  esko@email.com	
Kalevi   Härmä        ei sähköpostiosoitetta
Maija    Meikalainen  maija.meikalainen@meikamanne.com	
Marko    Meikalainen  make@hotmail.com	
Tero     Teräväinen   ei sähköpostiosoitetta	
Liisa    Virtanen     ei sähköpostiosoitetta	


-CAST :
なぜCASTを使うのか？
データ型の統一: データベースの列に異なる型のデータが混在している場合、CASTを使って一貫したデータ型に変換できます。

演算時の正確性: たとえば、文字列として保存されている数値を数値として計算したい場合、CASTを使って文字列を数値型に変換できます。これにより、数値としての演算が可能になります。

kirjat_hintaはデータベース内で浮動小数点型（例: FLOATやDOUBLE）で保存されています。浮動小数点型は計算精度においてわずかな誤差が生じることがあります。CAST(kirjat_hinta AS NUMERIC)によって、この値をより精度の高いNUMERIC型（固定小数点型）に変換します。
つまり、CASTを使うことで、kirjat_hintaの値をより正確な数値として扱い、それをROUNDで丸めて表示しているのです。