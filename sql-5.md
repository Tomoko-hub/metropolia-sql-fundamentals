## 5. INSERT, UPDATE & DELETE

5.1 INSERT
Esimerkki 5.1: Yksinkertainen INSERT-lause
 INSERT INTO   Lainaajat 
 VALUES        (1, 'Esko', 'Tahvanainen', '0503787843', 'esko@email.com')


Esimerkki 5.2: kenttien jättäminen tyhjäksi INSERT-lauseessa
 INSERT INTO   Lainaajat (Lainaajat_ID, LainaajatEtunimi, LainaajatSukunimi) 
 VALUES        (1, 'Esko', 'Tahvanainen')

Esimerkki 5.3: kenttien järjestys INSERT-lauseessa
 INSERT INTO   Lainaajat (LainaajatSukunimi, LainaajatEtunimi, Lainaajat_ID) 
 VALUES        ('Tahvanainen', 'Esko', 1)

5.2 UPDATE
Esimerkki 5.4: Eskolle uusi sähköpostiosoite

 UPDATE   Lainaajat 
 SET      LainaajatEmail = 'esko.tahvanainen@email.com'
 WHERE    LainaajatEtunimi= 'Esko' AND LainaajatSukunimi = 'Tahvanainen'


Esimerkki 5.5: Kenttien arvojen muuttaminen matemaattisin operaatioin
 UPDATE   Taulu 
 SET      Kentta1 = Kentta1 + 1

UPDATE Henkilot SET HenkilotEmail = 'matti.meikalainen@mail.com'
-> Päivittää Henkilot-taulun sisältämien tietueiden HenkilotEmail-kentät osoitteella: "matti.meikalainen@mail.com"

5.3 DELETE
Esimerkki 5.6: Tietueen poistaminen
 DELETE FROM   Henkilot 
 WHERE         HenkilotEtunimi = 'Esko' AND HenkilotSukunimi = 'Tahvanainen'
