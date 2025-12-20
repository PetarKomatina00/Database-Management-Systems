# Optimizacija upita u PostgreSQL-u

## Opis projekta
U ovom projektu objašnjene su strukture podataka koje PostgreSQL može koristiti za optimizaciju upita, kao i osnovni algoritmi za njihovo izvršavanje. Analiziran je na?in skladištenja podataka, struktura i funkcionalnost indeksa, kao i troškovi različitih JOIN algoritama koje planer može da izabere.

Teorijski deo realizovan je kroz dva ilustrovana primera nad realnim skupom podataka.

U okviru projekta korišćena je literatura PostgreSQL Query Optimization: The Ultimate Guide to Building Efficient Queries (Henrietta Dombrovskaza, Boris Novikov, Anna Bailliekova 1st ed.). 

---

## Skup podataka
Baza podataka preuzeta je sa javno dostupnog IMDB repozitorijuma:  
https://datasets.imdbws.com/

U projektu su korišćene sledeće datoteke:
- `name.basics.tsv.gz` � podaci o osobama koje su učestvovale u filmu  
- `title.basics.tsv.gz` � osnovni podaci o filmovima  
- `title.principals.tsv.gz` � relacija između filmova i osoblja  
- `title.ratings.tsv.gz` � ocene filmova  

---

## Priprema podataka
Potrebno je napomenuti da tabele nisu u potpunosti konzistentne, da je većina polja tipa `TEXT`, kao i da veliki broj vrednosti ima `NULL` vrednost.

Konzistentnost se postiže izvršavanjem SQL komande prikazane na slici 17, kojom se brišu nekonzistentni podaci između tabela `ucesnici` i `naziv_osoblja`. Odgovarajući upit potrebno je primeniti i na preostale tabele.

Takođe, neophodno je definisati strane ključeve preko kojih su tabele međusobno povezane.

---

## ER Dijagram
![ER dijagram](images/ER_diagram.png)