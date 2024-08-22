## 9. Taulujen väliset liitokset: useisiin tauluihin kohdistuvat kyselyt (22.8)

9.1 Taulujen välisistä suhteista

INNER JOIN
[taulu1] INNER JOIN [taulu2] ON [kenttä1] = [kenttä2]

Esimerkki 9.1: Lainatut albumit ja lainaajien nimet

 SELECT      LainaajatEtunimi, LainaajatSukunimi, LainauksetAlbumit_ID 
 FROM        Lainaajat 
 INNER JOIN  Lainaukset ON Lainaajat_ID = LainauksetLainaajat_ID

Esimerkki 9.2: Lainaajien ja lainattujen albumien nimet
 SELECT      LainaajatEtunimi, LainaajatSukunimi, AlbumitNimi
 FROM        (Lainaajat INNER JOIN  Lainaukset ON Lainaajat_ID = LainauksetLainaajat_ID)
 INNER JOIN  Albumit ON Albumit_ID = LainauksetAlbumit_ID

9.4 OUTER JOIN

LEFT OUTER JOIN

Esimerkki 9.3: Lainaajat ja mahdolliset lainatut albumit
 SELECT   LainaajatEtunimi, LainaajatSukunimi, LainauksetAlbumit_ID
 FROM     Lainaajat 
 LEFT OUTER JOIN   Lainaukset ON Lainaajat_ID = LainauksetLainaajat_ID

Esimerkki 9.4: Lainattujen albumien lukumäärä henkilöittäin
 SELECT   LainaajatEtunimi, LainaajatSukunimi, COUNT(LainausAlbumi_ID) AS LainattujaAlbumeja
 FROM     Lainaajat
 LEFT OUTER JOIN Lainaukset ON Lainaajat_ID = LainauksetLainaajat_ID
 GROUP BY LainaajatEtunimi, LainaajatSukunimi
->
LainaajatEtunimi  LainaajatSukunimi  LainauksetAlbumit_ID	
----------------  -----------------  --------------------
Esko              Tahvanainen        NULL	
Kalevi            Härmä              1	
Kalevi            Härmä              2	
Maija             Meikäläinen        3	
Marko             Meikäläinen        NULL	
Tero              Teräväinen         NULL	
Liisa             Virtanen           NULL	


->
LainaajatEtunimi  LainaajatSukunimi  LainattujaAlbumeja	
----------------  -----------------  ------------------	
Esko              Tahvanainen        0	
Kalevi            Härmä              2	
Liisa             Virtanen           0	
Maija             Meikäläinen        1	
Marko             Meikäläinen        0	
Tero              Teräväinen         0	


9.4.1 OUTER JOIN: RIGHT OUTER JOIN ja FULL OUTER JOIN

Esimerkki 9.4: Pistenotaatio eri taulujen saman nimisten kenttien viittauksissa
 SELECT      LainaajatEtunimi, LainaajatSukunimi, LainauksetAlbumit_ID
 FROM        Lainaajat
 INNER JOIN  Lainaukset ON Lainaajat.Lainaaja_ID = Lainaukset.Lainaaja_ID

9.6 WHERE-ehto liitoksissa
 SELECT      LainaajatEtunimi, LainaajatSukunimi
 FROM        (Lainaajat INNER JOIN Lainaukset ON Lainaajat_ID = LainauksetLainaajat_ID)
 INNER JOIN  Albumit ON Albumit_ID = LainauksetAlbumit_ID
 WHERE       AlbumitNimi = 'Master of puppets'

LainaajatEtunimi  LainaajatSukunimi	
----------------  -----------------	
Maija             Meikäläinen

**INNER JOIN**は、2つのテーブルを結合する際に、両方のテーブルに共通するキー（または列）の値が一致するレコードだけを結果に含めます。
つまり、結合されたテーブルの中には、両方のテーブルで一致するデータのみが含まれます。もし、片方のテーブルに一致するデータが存在しなければ、そのデータは結果セットに含まれません。

**LEFT OUTER JOIN**
LEFT OUTER JOIN: 左側のテーブル（最初のテーブル）のすべてのレコードを含み、右側のテーブル（結合されるテーブル）に一致するレコードがない場合はNULLを返します。

**RIGHT OUTER JOIN**
RIGHT OUTER JOIN: 右側のテーブル（結合されるテーブル）のすべてのレコードを含み、左側のテーブルに一致するレコードがない場合はNULLを返します。

**FULL OUTER JOIN**
FULL OUTER JOIN: 左側と右側の両方のテーブルのすべてのレコードを含みます。一致するレコードがない場合はNULLが返されます。

SELECT AlbumitNimi FROM Albumit INNER JOIN Lainaukset ON Albumit_ID = LainauksetAlbumit_ID WHERE LainauksetPvm = '2002-12-17'

SELECT Autot.Valmistaja, Henkilot.Nimi FROM Autot INNER JOIN Henkilot ON Autot.Omistaja_ID = Henkilot.Henkilo_ID