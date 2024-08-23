## 10. CREATE, ALTER ja DROP (23.8)

10.1 Tietokannan luominen ja poistaminen

Esimerkki 10.1: Tietokannan luominen
 CREATE DATABASE CD_kanta

Esimerkki 10.2: Tietokannan poistaminen
 DROP DATABASE CD_kanta

10.2 Taulun luominen tietokantaan
 CREATE TABLE [taulun_nimi] (
  [kenttä1] [määreet],
  [kenttä2] [määreet],
  ...
  [kenttäN] [määreet]
)

Esimerkki 10.3: Henkilot-taulun muodostaminen
 CREATE TABLE Henkilot(
   Henkilot_ID       INTEGER       PRIMARY KEY,
   HenkilotEtunimi   VARCHAR(32),
   HenkilotSukunimi  VARCHAR(64)
)

10.2.1 Kenttien tietotyypit
 Tietotyyppi	Aliakset (vaihtoehtoinen nimi)	Kuvaus
 boolean	bool	Boolean-arvo (tosi/epätosi)
 character(x)	char(x)	Kiinteän pituinen merkkijono. (X = haluttu merkkien määrä)
 character varying(x)	varchar(x)	Vaihtelevan pituinen merkkijono. (X = haluttu merkkien määrä)
 date	 	Kalenteripäivä (vuosi, kuukausi, päivä)
 integer	int, int4	4-tavuinen kokonaisluku
 real	float4	4-tavuinen liukuluku
 serial	serial4	Automaattisesti kasvava 4-tavuinen kokonaisluku

10.2.2 Kenttien määreet: PRIMARY KEY ja FOREIGN KEY
Esimerkki 10.4: Taulun ja sen avaimien muodostaminen
 CREATE TABLE Henkilot(
   Henkilot_ID      INTEGER      PRIMARY KEY,
   HenkilotEtunimi  VARCHAR(32),
   HenkilotSukunimi VARCHAR(64),
   HenkilotOsoite   INTEGER,
   FOREIGN KEY(HenkilotOsoite)   REFERENCES Osoitteet(Osoitteet_ID)
)

Esimerkki 10.6: DEFAULT-arvon määritteleminen
CREATE TABLE Henkilot(
   Henkilot_ID         INTEGER      PRIMARY KEY,
   HenkilotEtunimi     VARCHAR(32)  NOT NULL,
   HenkilotSukunimi    VARCHAR(64)  NOT NULL,
   HenkilotSyntymaPvm  DATE         NOT NULL  DEFAULT '0000-00-00',
   HenkilotOsoite      INTEGER,
   FOREIGN KEY(HenkilotOsoite)      REFERENCES Osoitteet(Osoitteet_ID)
)

10.3 Taulun rakenteen muokkaaminen
 
Esimerkki 10.7: Kentän lisääminen tauluun Osoitteet
 ALTER TABLE   Osoitteet 
 ADD COLUMN    Email VARCHAR(64)


Esimerkki 10.8: Kentän poistaminen taulusta Osoitteet
 ALTER TABLE   Osoitteet 
 DROP COLUMN   Email RESTRICT


Esimerkki 10.9: Kentälle DEFAULT-arvo
 ALTER TABLE   Henkilot 
 ALTER COLUMN  SyntymaPvm SET DEFAULT '0000-00-00'

10.4 Taulun poistaminen tietokannasta
 -taulun poistaminen viite-eheysmääreistä riippumatta
 -taulun poistaminen jos viite-eheysmääreitä ei ole
 -taulun ja sen sidostaulujen poistaminen


Esimerkki 10.10: Taulun poistaminen
 DROP TABLE   Osoitteet


-前文に "RESTRICT "という修飾語が加えられている場合、そのテーブルが他のテーブルから参照されていても削除されない：
Esimerkki 10.11: Taulun poistaminen (RESTRICT)
 DROP TABLE   Osoitteet RESTRICT

-テーブルと、削除するテーブルの参照コンテキストにあるテーブルを削除したい場合は、"CASCADE "属性を使用することができます：

Esimerkki 10.12: Taulun poistaminen (CASCADE)
 DROP TABLE   Osoitteet CASCADE

Millä seuraavista tiedonhallintajärjestelmälle syötettävistä komennoista voidaan poistaa Levyarkisto-niminen tietokanta tiedonhallintajärjestelmästä?
->DROP DATABASE Levyarkisto
(Tarkista ensin poistetaanko tietokanta vai taulu.)

範囲: DROP DATABASE はデータベース全体を削除しますが、DROP TABLE はデータベース内の特定のテーブルのみを削除します。

影響: DROP DATABASE は非常に広範囲で破壊的な影響がありますが、DROP TABLE は特定のテーブルにのみ影響を与えます。

使用状況: データベース全体を完全に削除したい場合は DROP DATABASE を使用し、特定のテーブルのみを削除したい場合は DROP TABLE を使用します。

