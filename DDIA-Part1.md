04/08/2026 - DDIA

FUNDAMENTE

The Big 3 - RSM

Reliability = Fiabilitate = omul de incredere, ca se va tine de cuvant
- abilitatea sistemului de a livra ceea ce trebuie in timp 
~ sunt o persoana reliable, de INCREDERE ca ma voi tine cuvant => astfel, pentru a ma tine de cuvant, fac tot posibilul sa obtin ceea ce trebuie => se cauta mentinerea unei STABILITATI, pentru a se evita evenimente care sa perturbe sistemul, se gestioneaza erorile, pentru a oferi user-ului o experienta cat mai simpla si "pazita" de ce este rau(source + more info: https://www.geeksforgeeks.org/system-design/maintainability-in-system-design/) 

Scalability = Scalabilitate = studentul care se descurca in sesiune sub stresul examenelor(nu poate adauga literalmente resurse de stocare, insa gestioneaza toti factorii, se motiveaza)   
- GESTIONEAZA sarcini de lucru/utilizatori/date in crestere FARA a afecta performanta
- un sistem scalabil => extinde resurse precum servere/stocare/putere de procesare
- TRAFIC MARE DE DATE => dezvoltarea sistemului
(source + more info: https://www.geeksforgeeks.org/system-design/what-is-scalability/)

Maintainability = Mentenabilitate = omul ninsat pe sectiunea lui, fara a interveni in sectiunile altora, astfel profesionist pe ramura lui
- cat de usor poate fi MODIFICAT/ACTUALIZAT/IMBUNATATIT 
- imbunatatiri ale componentelor cu minimul de actiune asupra sistemului => MODULARIZAREA ajuta mult in aceasta situatie - lucru asupra unei singure componente FARA a afecta restul sistemului + TESTARE AUTOMATA 
(source + more info: https://www.geeksforgeeks.org/system-design/maintainability-in-system-design/)

!Reminder: CPU = Central Processing Unit - componenta principala care face posibila executia instructiunilor de programe

De ce mai multe aplicatii sunt *data-intensive* decat *compute-intensive*? - un prim raspuns din DDIA: puterea CPU nu mai este un factor asa limitativ, insa **volumul de date** + **complexitatea datelor** + **viteza de schimbare** DA - are sens, intrucat mediile de business sunt in plina schimbare, oamenii tot mai conectati(medie de 3,6 dispozitive per locuitor conform Cisco Annual Internet Report pe 2018-2023 - e posibil sa fie si mai mare acuma) iar portalurile mari trebuie sa faca fata, sa nu pice

Componentele de baza ale unei aplicatii de tip *data-intensive* - aplicatie modularizata
- Databases = stocarea datelor 
- Caches ~ tot utilizezi un material de pe web, asa ca lasi tab-ul deschis, nu il mai inchizi ca sa iti vina mai USOR urmatoarea data sa accesezi materialul => SCOPUL: imbunatatirea *performantei* + *eficientei* unui sistem prin reducerea timpului necesar pentru accesarea datelor accesate frecvent (source + more info: https://www.geeksforgeeks.org/system-design/caching-system-design-concept-for-beginners/)

Caught my eyes: 
Exemplu: In Twitter, cand un tweet devine viral, un numar mare de clienti solicita acelasi tweet, asa ca, pentru a reduce numarul de apeluri catre baza de date, putem folosi memoria cache, iar tweet-urile pot fi furnizate mult mai rapid. => intrucat conceptul de caching consta in stocarea locala si temporara a unor date accesate frecvent, ma gandesc la faptul ca aceasta "stocare locala" se intampla la nivelul server-ului celui mai apropiat de dispozitiv; e interesant totusi la ce frecventa a cautarilor se pune acea informatie in cache, exista vreo regula? prin frecventa ma refer si la numarul de cautari, dar si la timp

Eficacitatea Cache-ului => locality of reference - Localitatea referintei = "termen din informatica utilizat pentru a descrie proximitatea **temporala** sau **spatiala** a accesarilor locatiilor de memorie in programele de calculator. Exista doua tipuri primare de localitate a referintei de memorie: temporala si spatiala" => imi atesta faptul ca m-am gandit bine la ce inseamna frecventa, nelasand pe afara vreuna din perspective - foarte bine!!

(source: https://ro.wikipedia.org/wiki/Principiul_de_localitate_(informatic%C4%83))

Totusi, conceptul de "Localty of reference" - ajuta memoria cache sa prezica ce informatii vor fi necesare in continuare, reducand astfel timpul mediu de acces la memorie si sporind eficienta generala a procesorului, fiind in acest mod un principiu de baza pentru tot ce inseamna **Cache**.

(source + more info: https://www.geeksforgeeks.org/computer-science-fundamentals/cache-memory/)

- Search Indexes = Keywords
Indexarea in DB - foarte UTILA - permite cautarea mai rapida fara a scana intregul tabel

(source + more info: https://www.geeksforgeeks.org/dbms/indexing-in-databases-set-1/)

- Stream processing - procesarea CONTINUA a datelor pe masura ce sunt generate => lucreaza cu datele pe masura ce sosesc, fiind astfel posibila obtinerea de informatii, declansarea de actiuni si actualizarea INSTANTANEE a sistemelor => esentiala pentru aplicatiile care necesita analiza a datelor in timp real si raspunsuri imediate (ex: social media, aplicatii financiare etc) => *Real-Time Processing* + *Continuous Data Flow*

(source + more info: https://www.geeksforgeeks.org/data-engineering/what-is-stream-processing/)

- Batch processing - practic ar fi opusul lui stream processing, intrucat presupune o prelucrare PERIODICA a datelor si nu instantanee - datele sunt adunate => VOLUM MARE DE DATE SIMULTAN

Utilizata atunci cand dimensiunea datelor este *cunoscuta* si *finita*, spre deosebire de **stream processing** unde dimensiunea datelor nu este cunoscuta, datele fiind prelucrate instant => batch procesiing dureaza putin mai mult, venind simultan un volum mai mare de date

Idee DDIA: Data systems - abstractizare cu succes - le folosim tot timpul, negandind prea mult

-- AM RAMAS LA pag. 4