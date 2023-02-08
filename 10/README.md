```sql
1)
mysql> SELECT Etunimi, Sukunimi, Nimi, Arvosana
    -> FROM Opiskelija
    -> JOIN Arvosana ON Arvosana.idOpiskelija = Opiskelija.idOpiskelija
    -> JOIN Opintojakso ON Opintojakso.idOpintojakso = Arvosana.idOpintojakso
    -> WHERE Arvosana.Arvosana = 0;
+---------+----------+----------+----------+
| Etunimi | Sukunimi | Nimi     | Arvosana |
+---------+----------+----------+----------+
| Roope   | Ankka    | Biologia |        0 |
| Iines   | Ankka    | Fysiikka |        0 |
+---------+----------+----------+----------+
2 rows in set (0.00 sec)


2)
mysql> SELECT Etunimi, Sukunimi, Nimi, Arvosana
    -> FROM Opiskelija
    -> JOIN Arvosana ON Arvosana.idOpiskelija = Opiskelija.idOpiskelija
    -> JOIN Opintojakso ON Opintojakso.idOpintojakso = Arvosana.idOpintojakso
    -> WHERE Arvosana.Arvosana != 0 AND Nimi = 'Fysiikka';
+---------+----------+----------+----------+
| Etunimi | Sukunimi | Nimi     | Arvosana |
+---------+----------+----------+----------+
| Aku     | Ankka    | Fysiikka |        4 |
+---------+----------+----------+----------+
1 row in set (0.00 sec)


3)
mysql> SELECT Etunimi, Sukunimi, Nimi
    -> FROM Opiskelija
    -> JOIN Arvosana ON Arvosana.idOpiskelija = Opiskelija.idOpiskelija
    -> JOIN Opintojakso ON Opintojakso.idOpintojakso = Arvosana.idOpintojakso
    -> WHERE Opiskelija.Etunimi = 'Hessu';
+---------+----------+----------+
| Etunimi | Sukunimi | Nimi     |
+---------+----------+----------+
| Hessu   | Hopo     | Englanti |
+---------+----------+----------+
1 row in set (0.00 sec)


4)
mysql> SELECT Etunimi, AVG(Arvosana) AS Keskiarvo
    -> FROM Opiskelija
    -> JOIN Arvosana ON Arvosana.idOpiskelija = Opiskelija.idOpiskelija
    -> WHERE Opiskelija.Etunimi = 'Aku'
    -> GROUP BY Opiskelija.Etunimi;
+---------+-----------+
| Etunimi | Keskiarvo |
+---------+-----------+
| Aku     |    3.7500 |
+---------+-----------+
1 row in set (0.00 sec)


5)
mysql> SELECT Nimi
    -> FROM Opintojakso
    -> LEFT JOIN Arvosana
    -> ON Arvosana.idOpintojakso = Opintojakso.idOpintojakso
    -> WHERE Arvosana IS NULL;
+-------+
| Nimi  |
+-------+
| Kemia |
+-------+
1 row in set (0.00 sec)
```