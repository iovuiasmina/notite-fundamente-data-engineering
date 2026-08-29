FUNDAMENTE
The Big 3 - RSM
Reliability = Fiabilitate = omul de incredere, ca se va tine de cuvant
abilitatea sistemului de a livra ceea ce trebuie in timp
~ sunt o persoana reliable, de INCREDERE ca ma voi tine cuvant => astfel, pentru a ma tine de cuvant, fac tot posibilul sa obtin ceea ce trebuie => se cauta mentinerea unei STABILITATI, pentru a se evita evenimente care sa perturbe sistemul, se gestioneaza erorile, pentru a oferi user-ului o experienta cat mai simpla si "pazita" de ce este rau - reducerea probabilitatii aparitiei de leak-uri de date - practic, omul de CUVANT care face tot ce ii sta in putinta pentru a-si indeplini sarcina(source + more info: https://www.geeksforgeeks.org/system-design/reliability-in-system-design/)
Scalability = Scalabilitate = studentul care se descurca in sesiune sub stresul examenelor(nu poate adauga literalmente resurse de stocare, insa gestioneaza toti factorii, se motiveaza)
GESTIONEAZA sarcini de lucru/utilizatori/date in crestere FARA a afecta performanta
un sistem scalabil => extinde resurse precum servere/stocare/putere de procesare
TRAFIC MARE DE DATE => dezvoltarea sistemului
(source + more info: https://www.geeksforgeeks.org/system-design/what-is-scalability/)
Maintainability = Mentenabilitate = omul ninsat pe sectiunea lui, fara a interveni in sectiunile altora, astfel profesionist pe ramura lui
cat de usor poate fi MODIFICAT/ACTUALIZAT/IMBUNATATIT
imbunatatiri ale componentelor cu minimul de actiune asupra sistemului => MODULARIZAREA ajuta mult in aceasta situatie - lucru asupra unei singure componente FARA a afecta restul sistemului + TESTARE AUTOMATA
(source + more info: https://www.geeksforgeeks.org/system-design/maintainability-in-system-design/)
!Reminder: CPU = Central Processing Unit - componenta principala care face posibila executia instructiunilor de programe
De ce mai multe aplicatii sunt data-intensive decat compute-intensive? - un prim raspuns din DDIA: puterea CPU nu mai este un factor asa limitativ, insa volumul de date + complexitatea datelor + viteza de schimbare DA - are sens, intrucat mediile de business sunt in plina schimbare, oamenii tot mai conectati(medie de 3,6 dispozitive per locuitor conform Cisco Annual Internet Report pe 2018-2023 - e posibil sa fie si mai mare acuma) iar portalurile mari trebuie sa faca fata, sa nu pice
Componentele de baza ale unei aplicatii de tip data-intensive - aplicatie modularizata
Databases = stocarea datelor
Caches ~ tot utilizezi un material de pe web, asa ca lasi tab-ul deschis, nu il mai inchizi ca sa iti vina mai USOR urmatoarea data sa accesezi materialul => SCOPUL: imbunatatirea performantei + eficientei unui sistem prin reducerea timpului necesar pentru accesarea datelor accesate frecvent (source + more info: https://www.geeksforgeeks.org/system-design/caching-system-design-concept-for-beginners/)
Caught my eyes:
Exemplu: In Twitter, cand un tweet devine viral, un numar mare de clienti solicita acelasi tweet, asa ca, pentru a reduce numarul de apeluri catre baza de date, putem folosi memoria cache, iar tweet-urile pot fi furnizate mult mai rapid. => intrucat conceptul de caching consta in stocarea locala si temporara a unor date accesate frecvent, ma gandesc la faptul ca aceasta "stocare locala" se intampla la nivelul server-ului celui mai apropiat de dispozitiv; e interesant totusi la ce frecventa a cautarilor se pune acea informatie in cache, exista vreo regula? prin frecventa ma refer si la numarul de cautari, dar si la timp
Eficacitatea Cache-ului => locality of reference - Localitatea referintei = "termen din informatica utilizat pentru a descrie proximitatea temporala sau spatiala a accesarilor locatiilor de memorie in programele de calculator. Exista doua tipuri primare de localitate a referintei de memorie: temporala si spatiala" => imi atesta faptul ca m-am gandit bine la ce inseamna frecventa, nelasand pe afara vreuna din perspective - foarte bine!!
(source: https://ro.wikipedia.org/wiki/Principiul_de_localitate_(informatic%C4%83))
Totusi, conceptul de "Localty of reference" - ajuta memoria cache sa prezica ce informatii vor fi necesare in continuare, reducand astfel timpul mediu de acces la memorie si sporind eficienta generala a procesorului, fiind in acest mod un principiu de baza pentru tot ce inseamna Cache.
(source + more info: https://www.geeksforgeeks.org/computer-science-fundamentals/cache-memory/)
Search Indexes = Keywords
Indexarea in DB - foarte UTILA - permite cautarea mai rapida fara a scana intregul tabel - mana in mana cu Cache
(source + more info: https://www.geeksforgeeks.org/dbms/indexing-in-databases-set-1/)
Stream processing - procesarea CONTINUA a datelor pe masura ce sunt generate => lucreaza cu datele pe masura ce sosesc, fiind astfel posibila obtinerea de informatii, declansarea de actiuni si actualizarea INSTANTANEE a sistemelor => esentiala pentru aplicatiile care necesita analiza a datelor in timp real si raspunsuri imediate (ex: social media, aplicatii financiare etc) => Real-Time Processing + Continuous Data Flow
(source + more info: https://www.geeksforgeeks.org/data-engineering/what-is-stream-processing/)
Batch processing - practic ar fi opusul lui stream processing, intrucat presupune o prelucrare PERIODICA a datelor si nu instantanee - datele sunt adunate => VOLUM MARE DE DATE SIMULTAN
Utilizata atunci cand dimensiunea datelor este cunoscuta si finita, spre deosebire de stream processing unde dimensiunea datelor nu este cunoscuta, datele fiind prelucrate instant => batch processing dureaza putin mai mult, venind simultan un volum mai mare de date
Idee DDIA: Data systems - abstractizare cu succes - le folosim tot timpul, negandind prea mult

De multe ori alegem sa afirmam ca DB si cozile sunt foarte diferite, insa ele, intr-un mod superficial, se aseamana:
- ambele socheaza date pentru o perioada de timp
- difera pattern-urile de acces(ma gandesc ca la DB poti accesa orice informatie oricand si sub regula simpla de SELECT etc, insa la queue o accesezi doar dupa modelul FIFO) => caracteristici diferite precum performanta care numai astea duc la implementari si gestionari foarte diferite

De ce ar trebui sa le punem pe toate totusi in "aceeasi oala"? - un prim raspuns al meu: pai ele au sisteme de selectie, insertie, actualizare, stergere, urmarire etc distincte, care functioneaza dupa diferite principii(ce am spus mai inainte au mai multa referinta catre DB relationale), insa la baza au cuvantul cheie "data", practic lucrul cu date care in ultimii ani a crescut considerabil, nemaifiind suficient doar sa stochezi datele si sa le ai, ci sa le si optimizezi

* In ce consta scalarea *orizontala* si *verticala*? - raspunsul meu: cea *orizontala* apare in momentul in care dorim sa adaugam mai multe servere, intrucat TRAFICUL este MULT MAI MARE - ex: social media si exemplul cu tweet de mai sus pentru memoria Cache - practic, prin scalarea orizontala se cauta o multiplicare(daca tot vorbeam de ea la inceput) a componentei pe baza principiului: "VREM CA STIREA SA FIE DATA IN TOATA TARA"; in schimb, scalarea *verticala* as putea spune ca functioneaza pe baza regulii: "VREAU SA AJUNG SA FIU SUS, PRINTRE CEI MAI BUNI, ASA CA LUCREZ LA MINE PENTRU A FII CEA MAI BUNA VERSIUNE A MEA" - astfel, consta in actualizari ale componentelor hardware de regula pentru a creste CAPACITATEA - de regula la aplicatii mai micute, monolitice, fiind mai simplu de implementat

- (orizontal sau "scalarea in exterior"): crestrerea TRAFICULUI - accesibilitate mai mare("popularitate") - mai putine perioade de nefunctionare, usor de modelat si remodelat dupa propriile nevoi, potrivit pentru aplicatiile pe scara larga, toleranta la erori, insa introduce complexitate in proiectarea si getionarea sistemului, necesitand o arhitectura complexa, dificultate in mentinerea unei consistente puternice intre noduri, mai multe masini = mai multa retea, energie, intretinere + instrumente de orchestrare pentru gestiunea a mai multor servere
| (vertical): cresterea CAPACITATII - performanta mai mare("the best of the best") - gestiune mai usoara, simplu de implementat, nu necesita de regula sa se intervina asupra codului, insa scalarea necesita adesea repornirea sau inlocuirea serverului si poate duce la perioade de nefunctionare, un singur server primeste toate cererile, fapt care ar putea duce la timpi morti

Scalare orizontala	
- Adauga mai multe masini sau servere pentru a distribui volumul de lucru	
- Mai rentabil pentru sistemele la scara larga
- Foarte flexibil deoarece servere noi pot fi adaugate cu usurinta
- Toleranta mai buna la erori, deoarece volumul de lucru este distribuit pe mai multe masini
- Imbunatateste performanta prin distribuirea traficului pe servere
- Risc mai mic de defectiune a unui singur punct
- Mai complex de gestionat deoarece implica sisteme distribuite
- Potrivit pentru aplicatii care necesita scalabilitate masiva
- Necesita echilibrarea incarcarii pentru a distribui traficul intre servere
- Se bazeaza pe comunicarea in retea intre mai multe masini

Scalare verticala
- Creste capacitatea CPU, RAM sau stocarea unei singure masini
- Mai simplu la inceput, dar poate deveni scump in timp
- Flexibilitate limitata din cauza limitelor hardware
- Toleranta mai mica la erori, deoarece depinde de o singura masina
- Performanta se imbunatateste doar in limita capacitatii hardware-ului
- Risc mai mare de defectiune a unui singur punct
- Mai usor de gestionat, deoarece foloseste o singura masina
- Potrivit pentru aplicatii cu nevoi moderate de scalabilitate
- Echilibrarea incarcarii nu este de obicei necesara
- Foloseste in mare parte comunicarea in cadrul unei singure masini

(source + more info: https://www.geeksforgeeks.org/system-design/system-design-horizontal-and-vertical-scaling/)

Obs: am facut o scurta trecere in revista a ceea ce reprezinta up scalling si horizontal scalling, intrucat vreau sa clarific inca o data succint ce avem intre DB relationale si cele NoSQL(ma fascineaza, intrucat totul e dupa reguli mai kind, peacefull, nu ceva strict => mai multa libertate si cumva asta nu inteleg - momentan :) )

SGBDR - accent pe STRUCTURA, scheme FIXE, CONSISTENTA PUTERNICA
NoSQL - mana in mana cu scalarea orizontala, schme FLEXIBILE

SGBDR	
- Structura datelor: Structurat(bazat pe tabele)	
- Schema: Rigid(definit in prealabil)	
- Limbaj de interogare:	SQL(Standardizat)	
- Scalare:	Vertical(Adaugati alimentare la server)
- Relatii:	Sustinut prin JOIN-uri
- Tranzactii: ACID(Consistenta puternica)
- Cel mai bun pentru: Interogari complexe, sisteme financiare	Randament ridicat, date masive, agilitate

ACID: 
- Atomicitate: "totul sau nimic" - executie integrala sau deloc - COMMIT!! - bun pentru tranzactii bancare(ex: transferul bancare necesita 2 actiuni - scadere sold cont A si crestere sold cont B; daca intre timp pica serverul, ATOMICITATEA ANULEAZA TOT)
- Consistenta: "reguli stricte" - trecere dintr-o stare valida in alta stare valida - reguli, constrangeri de integritate trebuie OBLIGATORIU RESPECTATE(ex: creezi o factura pentru un client inexistent, sistemul blocheaza tranzactia)
- Izolare: "fiecare cu treaba lui" - tranzactii concomitent realizate, insa nu interfereaza niciuna cu cealalta(intrebare: pai si daca sunt 2 operatiuni asupra unui sold, cum se face? - raspuns: se folosesc mecanisme de blocare si niveluri de izolare pentru a preveni erori de tip *Race Condition* - pierderea unei actualizari; sistemul obliga tranzactiile sa se "aseze la coada", devenind astfel o EXECUTIE SECVENTIALA)

2 mecanisme de blocare

1. Blocarea Pesimista - "Primul pune lacatul"

Conflict probabil sa apara => sistemul blocheaza randul din tabela
ex: SELECT ... FOR UPDATE si la COMMIT se "elibereaza lacatul"

^ aceste info sunt la nivel de software engineer/backend dev/DB administrator(DBA), insa la nivel de data arhitect, se rezuma la SGBDR/NoSQL

Totusi, cum pune sistemul un "lacat" la nivel de arhitectura? - tine de RAM + modul in care SO gestioneaza firele de executie(threads) - raspuns: lacatul NU o bariera fizica, ci o STRUCTURA DE DATE(hashtable - REMINDER: structura de date utilizata pentru a insera, cauta si elimina rapid perechi cheie-valoare; functioneaza pe baza conceptului de hashing, unde fiecare cheie este tradusa de o functie hash intr-un index distinct intr-o matrice; indexul functioneaza ca o locatie de stocare pentru valoarea corespunzatoare; source + more info: https://www.geeksforgeeks.org/dsa/hash-table-data-structure/) gestionata de un modul dedicat *Lock Manager*

Cum functioneaza? - raspuns: 

1. Lock Manager: fiecare motor de DB(PostgreSQL, MySQL/InnoDB, SQL Server) are o componenta software in ram numita *Lock Manager* - tabela hash globala unde sunt stocate toate lacatele active din sistem - la dorinta realizarii unei tranzactii, NU SE MODIFICA DIRECT RANDUL, ci se TRIMITE O CERERE catre *Lock Manager*

Cheie Hash + valoarea(lista cu tranzactile care detin/asteapta un lacat pe acea cheie)

2. Cum se "incuie" usa in RAM: ipoteza: tranzactia A + B care vor sa modifice acelasi rand

a. solicitarea lacatului: tranz A ajunge PRIMA la randul cu soldul => apeleaza Lock Manager care verifica tabela hash din Ram pentru id-ul acelui rand + daca este gol, CREEAZA UN OBIECT DE TIP LOCK si il marcheaza ca fiind de tip *EXCLUSIVE (X LOCK)*, asoocind cu tranz A

b. blocarea fizica: imediat vine si tranz B care cere si ea un lacat exclusiv pe acelasi rand; Lock Manager verifica si spune "Randul este deja ocupat exclusiv de tranz A" => pune tranz B in starea de ASTEPTARE

* la invel de hardware + SO se foloseste un mecanism numit Mutex(Mutual Exclusion)/Semafor => tranz B este SUSPENDATA de catre procesor + pus in COADA DE ASTEPTARE din RAM legata de acel lacat

c. modif datelor in Buffer Pool: in acest timp, tranz A are cale libera; nu scrie direct pe hard disk(e prea lent), modificand valoarea in BUFFER POOL(zona mare din RAM unde DB pastreaza paginile de date pentru viteza ~ cache) + fisier de log pe disc(Write-Ahead Log - WAL) pentru siguranta

d. eliberarea si "trezirea"(The Wake-up Call): cand tranz A da COMMIT, datele sunr confirmate ca fiind salvate in siguranta, anunta *Lock Manager* ca a terminat, el sterge asocierea tranz A de pe acel rand din tabela de hash, se trimite un "semnal de trezire" catre tranz B, iar apoi tranz B primeste lacatul sau in tabela hash si poate executa operatiunea

Unde se pune mai exact acest lacat? - lasam pe discutii viitoare, intrucat e ceva mai complex

(source: recunosc, aici m-am ajuta de AI)

- Durabilitate: "scris in piatra" - odata ce o tranzactie a fost finalizata cu succes - COMMITTED - MODIFICARILE EI SUNT PERMANENTE si nu se vor pierde(modificari salvate pe un mediu de stocare non-volatil - hard disk/SSD)

NoSQL (nerelational)
- Structura datelor: Nestructurat(Document, Valoare-cheie, Grafic)
- Schema: Flexibil(Dinamic)
- Limbaj de interogare:	Variaza(UnQL - Limbaj de interogare Uninode, JSON, bazat pe API)
- Scalare:	Orizontal(Adaugati mai multe servere)
- Relatii:	Nu este puternic sustinut(adesea denormalizat)
- Tranzactii: BASE (Consistenta finala)
- Cel mai bun pentru: Randament ridicat, date masive, agilitate

UNQL este o structura JSON/Edgescript® pentru interogari de server.

O structura JSON de interogare arata astfel:

{
"edgeSpaces": [{ (opțional, matricea este utilizată pentru a impune ordinea de joncțiune)
"<Cod Edgespace>": {
"className": "<Nume clasă>"
"filtru": "<Filtru Edgescript®>" (opțional)
}, ...
}, ...]
"titlePath": <Calea marginii> (opțional)
"căi": [<Calea de margine, de ex. "\Asset.name" sau "\.name">, ...]
„orderPaths”: [<Edgepath>, ...] (opțional)
"filtre": ["<filtru Edgescript®>", ...] (opțional)
„isDistinct”: <true sau false> (opțional, implicit false)
"limită": <număr> (opțional, implicit 100)
"maxClassCount": <număr> (opțional, implicit 1)
"tree": { (opțional, utilizat pentru ierarhia arborelui intra-nivel)
"path": <Edgepath> (opțional, utilizat dacă părintele și copilul sunt stocate într-un alt tabel)
"părinte": <Cale de margine>
"copil": <Cale de margine>
}
„straturi”: [{ (opțional, folosit pentru straturi de date)
"path": <Edgepath> (opțional, calea către ID-ul stratului)
"parent": <Edgepath> (opțional, calea către ID-ul stratului părinte)
}, ...]
"levels": [{ (opțional, utilizat pentru interogări la nivel de arbore)
„isHidden”: <true sau false> (opțional, înregistrările pentru acest nivel sunt marcate cu „isHidden”: true)
"căi": [ (opțional, folosit pentru conectarea acestui nivel la următorul)
"părinte": <Cale de margine>
"copil": <Cale de margine>
, ...]
"query": [<query>, ...] (opțional, interogare pentru nivelul următor)
}, ...]
}
O structură JSON pentru o cerere arată astfel:

{
"lang": "<Cod limbă>"
"siteCode": "<Cod site>"
"packCode": "<Cod pachet>"
"orgCode": "<Codul organizației>"
"appCode": "<Cod aplicație>"
"interogare": <interogare>
}

Raspuns UNQL
La fel ca interogarea UNQL, raspunsul UNQL are un format JSON, deci poate fi gestionat de alti clienti decat clientii UNQL specifici.

O solutie ar fi ca raspunsul sa imite structura instantei claselor, dar acest lucru nu va functiona pentru structuri arborescente hoc sau scripturi, altele decat pentru acces pur la proprietati. Deoarece nu exista clase corespunzatoare rezultatelor, rezultatul nu poate fi verificat din punct de vedere al tipului.

Rezultatul trebuie sa poata gestiona referinte circulare.

Formatul raspunsului nu trebuie sa fie identic cu alte formate, cum ar fi GraphQL, SparQL, Neo4j/Cypher sau JSON-LD. Acestea sunt destul de versatile.

Edgescript®
UNQL foloseste limbajul de programare Edgescript® pentru diverse comportamente dinamice. Cititi mai multe despre Edgescript®

Edgespace
O cale de delimitare (edgepath) este o referinta la o proprietate a unui obiect. In mod normal, necesita un nume de clasa si un nume de proprietate, de exemplu \Asset.name.

Un spatiu de margine denumit poate fi utilizat intr-o cale de margine in locul numelui clasei, de exemplu \a.name, daca a este numele unui spatiu de margine. Spatiul de margine implicit nu are nume, iar calea de margine corespunzatoare ar arata ca \.name;

Retineti ca doua spatii de margine dintr-o interogare pot avea aceeasi clasa. De exemplu, spatiul de margine implicit poate avea clasa Asset, iar spatiul de margine "compare" poate avea clasa Asset si filtrul "\.id==\compare.id&\.date=='2022-10-01'". Aceasta ar duce la o jonctiune stanga a bazei de date, unde al doilea tabel Asset ar fi o comparatie cu acelasi asset la data "2022-10-01".

(source + more info: https://unql.org/)

Intrebari DDIA la care voi reusi sa raspund ulterior :):

Cum va asigurati ca datele raman corecte si complete, chiar si atunci cand lucrurile merg prost intern? 

Cum oferiti clientilor performante constante, chiar si atunci cand
parti ale sistemului dvs. sunt degradate? 

Cum scalati pentru a gestiona o crestere a incarcarii?

Cum arata o API buna pentru serviciu?

THE GODLY TRIO IN DATA SYSTEMS: RSM: Reliability - Scalability - Maintainability

##################################################################
### RELIABILITY
##################################################################

~ a functiona corect + a continua sa functioneze corect, chiar daca lucrurile merg gresit

Pentru software, asteptarile urmatoare sunt cele mai tipice:
- aplicatia face intocmai ce userul asteapta sa faca
- poate manageria/tolera greselile facute de user sau faptul ca foloseste aplicatia in mod diferit decat its purpouse + authority
- performanta suficienta pentru use case-ul afisat, cu volum mic de date si load lent
- sistemul previne orice acces si utilizare neautorizata

Ce poate merge rau = FAULT(~ defectiune) => sistemel care le pot anticipa si le pot gestiona se numesc FAULT-TOLERANT/RESILIENT - e cam imposibil, intrucat posibilitatea aparitiei unei defectiuni neasteptate este foarte mare(ex: cazul recent ANCPI) => tolerarea unor ANUMITE TIPURI

FAULT != FAILURE

*Fault(~ defectiune)* - apare atunci cand o componenta a unui sistem se abate de la specificatiile sale ~ defectiune interna, invizibila la ochiul liber
*Failure(~ eroare)* - apare atunci cand un sistem nu isi ofera serviciul utilizatorului sau ofera un serviciu degradat inacceptabil ~ user-ul nu mai poate utiliza sistemul

Intr-o lume ideala, nu exista faults, dar în lumea reala faults vor exista, dar failure este totusi inacceptabil.

(source + more info: https://medium.com/pyankit/fault-vs-failure-and-fault-tolerant-systems-60ec7dbfbe0d)

Astfel, probabilitatea unui fault poate fi redusa la 0 si ar fi indicat sa proiectam sisteme fault-tolerant pentru a preveni failures

In sistemele mari, este mai inteligent sa opresti intentionat si la intamplare componente(cum ar fi servere sau procese), FARA AVERTISMENT.

De ce se face asta? - raspuns: multe bug-uri apar din cauza gestionarii deficitare a erorilor; codul scris pentru a trata o problema rara este adesea netestat si esueaza cand apare un incident real; provocand defectiuni voluntar, fortezi sistemul sa isi foloseasca mecanismele de auto-reparare in fiecare zi; daca sistemul supravietuieste atacurilor tale controlate, ai garantia ca va supravietui si cand apar defectiuni reale, accidentale.

*The Netflix Chaos Monkey* 
- instrument open-source popular, dezvoltat de Netflix pentru implementarea principiilor Chaos Engineering in distributed systems

- conceput pentru a termina aleatoriu instantele si serviciile masinilor virtuale dintr-un mediu de infrastructura cloud => scopul principal: testarea proactiva a rezistentei unui sistem prin simularea defectiunilor si intreruperilor din lumea reala

- functioneaza prin selectarea aleatorie a instantelor masinilor virtuale si oprirea lor in timpul orelor de program; procedand astfel, ii obliga pe ingineri si dezvoltatori sa isi proiecteze sistemele avand in vedere redundanta si toleranta la erori

- daca sistemul este suficient de rezilient, acesta ar trebui sa poata face fata pierderii componentelor individuale fara a inregistra intreruperi semnificative sau intreruperi ale serviciului

##### Netflix Simian Army Tools
Chaos Monkey face parte din Simian Army de la Netflix, un grup de instrumente concepute pentru a testa fiabilitatea si rezistenta infrastructurii cloud. Fiecare instrument din Simian Army introduce diferite tipuri de erori pentru a evalua stabilitatea sistemului

Alte tool-uri importante din Simian Army includ:

- *Latency Monkey*: Introduce o latenta artificiala a retelei intre servicii pentru a testa cum se comporta aplicatiile atunci cand comunicarea devine lenta
- *Chaos Gorilla*: Simuleaza defectarea unei intregi zone de disponibilitate pentru a testa modul in care sistemele gestioneaza intreruperile de infrastructura la scara larga
- *Chaos Kong*: Simuleaza esecul unei intregi regiuni cloud pentru a evalua strategiile de recuperare in caz de dezastru
- *Conformity Monkey*: Verifica instantele si configuratiile pentru a se asigura ca respecta cele mai bune practici si standardele organizationale
- *Security Monkey*: Monitorizeaza configuratiile cloud si identifica vulnerabilitati de securitate sau incalcari ale politicilor

(source: recunosc, am folosit AI + more info: https://www.geeksforgeeks.org/system-design/what-is-netflixs-chaos-monkey/)

De regula se prefera tolerarea faults decat prevenirea faults, desi exista unele scenarii unde prevenirea e mai buna decat "leacul", pentru ca nu exista leac => aici SECURITATEA conteaza

Continuare RELIABILITY
Hardware Faults - cele mai probabile
ex: defectiuni ale hard disk-ului, RAM, blackout, eroare umana bazata pe o componenta hardware
"Se raporteaza ca hard disk-urile au un timp mediu de defectiune (MTTF) de aproximativ 10 pana la 50 de ani. Prin urmare, pe un cluster de stocare cu 10.000 de discuri, ar trebui sa ne asteptam, in medie, la o defectiune de un disc pe zi"
De regula, se au cel putin 2 componente care executa aceeasi functie astfel incat la defectiunea uneia, cealalta preia "controlul" ~ rendundanta - nu cea mai optima solutie, insa se dovedeste utila, mai ales in combintaie cu partea de backup
Insa, pe masura ce creste volumul de date si nr de aplicatii, poate deveni foarte costisitor, atat financiar, cat si ca parte de componente hardware(foarte multe!!)
Cazul AWS(Amazon Web Services) - cea mai cuprinzatoare si mai utilizata platforma cloud din lume unde platformele sunt proiectate pentru a prioritiza felxibilitatea mai mult decat functionalitatea - pot avea intreruperi fara avertismente :(
Beneficii ale utilizarii AWS
Accesati putere de calcul, stocare si baze de date la cerere
Eliminati nevoia de a cumpara, detine si intretine centre de date fizice
Plateste doar pentru ceea ce folosesti (modelul de plata pe masura ce utilizezi)
Scalare flexibila bazata pe nevoile afacerii
(source + more info: https://www.geeksforgeeks.org/cloud-computing/introduction-to-amazon-web-services/)
De regula, hardware faults - random + independente(afectezi un disk, insa cel de langa nu) - destul de improbabil sa existe dependenta intre masini
De-a lungul timpului, se constanta ca e mai bine to deal with software errors decat cele de hardware, motiv pentru care se utlizeaza in principiu tehnnici de tip software fault-tolerance, oferind astfel o serie de beneficii: single server cu un downtime planificat daca trebuie sa dai reboot la masina, functionarea server-ului si afectarea unui singur nod etc
Software Errors - bineinteles, mai greu de anticipat + cauzeaza in lant mai multe probleme decat problemele hardware
ex:
bug care da crash pentru fiecare apel al aplicatiei
=> Leap second on June 30, 2012, Linux kernel:
Pe 30 iunie 2012, introducerea unei secunde bisecte suplimentare (23:59:60 UTC) a declansat o eroare in subsistemele de gestionare a timpului si a cronometrelor de inalta rezolutie (hrtimer) din kernelul Linux => a provocat o crestere a utilizarii procesorului la 100% si a blocat simultan numeroase aplicatii multi-threaded
Ce a cauzat eroarea? - raspuns: secunda suplimentara - Timpul Universal Coordonat (UTC) a adaugat a 61-a secunda a minutului pentru a se sincroniza cu rotatia Pamantului; bucle infinite - in loc sa proceseze noua ora, firele de executie afectate au intrat in bucle continue si stranse => acest lucru a suprasolicitat nucleele procesorului la capacitate maxima, fara a efectua vreo sarcina utila
Impactul asupra aplicatiilor - Java si Node.js- aplicatiile bazate pe Java sau cele care depindeau puternic de cronometre de inalta rezolutie sau functii de time-out s-au blocat complet sau au incetinit drastic; intreruperi majore - site-uri si servicii web mari (inclusiv Reddit, LinkedIn, Yelp, Foursquare si Mozilla) au suferit degradari masive de performanta sau au picat de tot
Solutii rapide - administratorii de sistem au rezolvat temporar problema pe serverele active prin resetarea manuala a orei prin linia de comanda (folosind comanda date), fara a fi necesara o repornire (reboot) completa a sistemului
Pentru a evita blocajele masive ca cel din 2012, companii mari precum Google, Amazon (AWS) si Microsoft utilizeaza o metoda numita leap smearing => in loc sa adauge o secunda intreaga deodata, ele "impart" aceasta secunda pe o perioada mai lunga
Modul de functionare - serverele NTP (Network Time Protocol) incetinesc foarte putin ceasurile sistemului cu cateva zeci de microsecunde la fiecare secunda
Fereastra de timp - aceasta ajustare subtila se intinde de obicei pe o perioada de 12 pana la 24 de ore inainte si dupa momentul introducerii secundei bisecte
Rezultatul - la finalul ferestrei, sistemele sunt perfect sincronizate cu timpul UTC, iar kernelul Linux si aplicatiile nu observa nicio modificare brusca sau anormala a orei
(source: recunosc, am folosit AI)
proces care utilizeaza resurse comune
serviciu de care sistemul depinde si care e lent, unresponsive, corupt
failures in cascada
De regula trece mult timp pana aceste probleme sunt descoperite, intrucat pana nu sunt triggered de ceva din sistem, ele nu sunt vizibile - de acolo, software-ul ajunge sa faca presupuneri despre mediul sau
De asta nu exista solutii rapide, insa multe aspecte pot oferi un plus de ajutor:
thinking and debating despre presupunerile posibile => identificarea tuturor ramurilor use case
testare continua sau mai amanuntita
izolarea acelui proces specific
lasarea proceselor sa dea crash si sa isi dea restart(de multe ori e nevoie doar de un reapel al acelui proces pentru a reveni in parametri normali)
masurare + masurare + masurare a proceselor in productie(de preferat)!!!
Human Errors - oamenii sunt cunoscuti ca unreliable
poti avea intentii bune si sa gresesti, e firesc
"De exemplu, un studiu privind serviciile mari de internet a constatat ca
erorile de configurare ale operatorilor au fost principala cauza a intreruperilor de alimentare, in timp ce defectiunile hardware
(servere sau retea) au jucat un rol in doar 10-25% din intreruperi." - I mean, e normal, nu suntem roboti si nu intotdeauna putem vedea toate cazurile posibile(de asta e foarte fascinant sa ai discutii inainte cu cei din echipa si chiar cu userii finali sa vezi cate perspective are un singur proces!!! - dupa mine, ai rata de reusita net superioara)
Ce se face pentru a evita erorile umane?
design al sistemelor pentru a minimiza posibilitatea de eroare - destul de tricky si greu de obtinut
eliminarea locurilor in care oamenii gresesc frecvent sau pot face greseli in numar mare - crearea de sandbow environments(spatii de testare izolat care permite dev's si celor din securitate sa "experimenteze" FARA a afecta sistemul activ; este un mediu de testare securizat in care, chiar daca ceva nu merge bine, nu va afecta in mod direct masinile gazda, sistemele de operare, aplicatiile sau datele.)
(source + more info: https://builtin.com/software-engineering-perspectives/sandbox-environment)
testare peste testare, la FIECARE NIVEL - The holy automated testing
easy recovery pentru a minimiza impactul erorii - ma gandesc la backup rapid si s-ar lega cu COMMIT-urile si ROLLBACK-urile din DB
monitorizare detaliata si clara, cu precadere pentru metricile de performanta si ratele de erori - tine minte de telemetry(procesul automat de colectare a masuratorilor si datelor din surse indepartate sau inaccesibile si transmiterea acestora catre o statie receptoare pentru monitorizare si analiza - source + more info: https://www.britannica.com/technology/telemetry) - putem vedea prin monitorizare mult mai usor partea de warning-uri si presupuneri - tine cont ca in cazul aparitiei unei probleme, uneori, metricile pot fi fara valoare in diagnostic!! => nu te baza exclusiv pe ele!!!
good management + training
De ce e importanta partea de reliability? - raspuns: bugs, costuri(ca un sum up la toate efectele lipsei reliability), scaderea productivitatii + e componenta ce tine de incredere, responsabilitate pentru user => fara ea, scade credibilitatea noastra si astfel intram in declin(da, pe perioada productiei o poti reduce, insa in produsul final nu trebuie sa lipseasca)

SCALABILITY
Daca un sistem e reliable acum => NU inseamna ca va functiona exact lafel si in viitor, iar un factor extrem de simplu si common este creserea nr de useri => procesarea unor volume de date considerabil mai mari
Practic, scalability = capacitatea sistemului de a lucra cu un load crescut
!! Nu e o eticheta unidimensionala, pentru ca e destul de irelevant sa spunem ca "sistemul e scalabil" etc => raspunde foarte bine la intrebarile:
"Daca sistemul creste intr-un anumit mod, care sunt optiunile noastre de a gestiona cresterea?"
"Cum putem adauga resurse pentru a gestiona load-ul aditional?"
"Cum gestionezi milioane de cereri pe secunda fara sa blochezi sistemul?" !!!
Describing Load
Insa, pentru a vorbi de cresterea load-ului, trebuie mai intai sa stim unde ne situam: "care este load-ul curent?" - are foarte mult sens, pentru ca cea mai buna si indicata practica atunci cand vrei sa evoluezi in absolut orice, trebuie sa cunosti foarte bine de unde pleci, pe langa unde doresti sa ajungi - cunosti prezentul, astfel stii cum vrei sa arate viitorul si stii exact unde te situezi si ce ar trebui sa faci pentru a reusi sa prosperi
Load - poate fi descris prin cateva numere, practic prin cativa parametrii => nu are o valoare fixa, mereu fluctueaza si consider ca si acesti parametrii au la randul lor un grad de importanta, in special in functie de obiectivul fiecarei firme => cum spune si in DDIA, cea mai buna alegere de parametrii depinde de ARHITECTURA SISTEMULUI
ex de parametrii: requests/second pentru un server web, raportul dintre citiri si scrieri intr-o DB, nr de useri activi intr-un chat room, hit rate pentru cache etc
The "fan-out" concept - distribuirea datelor dintr-o singura sursa catre mai multe destinatii, unde fiecare destinatar poate primi informatii diferite in functie de cerintele sale specifice; aceasta abordare este extrem de eficienta in trimiterea de date PERSONALIZATE catre diferite noduri
Avantaje:
Optimizeaza latimea de banda prin trimiterea doar a datelor necesare catre fiecare nod
Permite echilibrarea incarcarii intre diferite noduri
Ofera flexibilitate prin furnizarea de date personalizate
Dezavantaje:
Complexitatea creste odata cu numarul de noduri si cu diferitele solicitari de date
Necesita un mecanism pentru gestionarea distributiei datelor personalizate
Potential de latenta crescuta daca mai multe noduri necesita date diferite
Aplicatii ale distributiei de date in fan-out:
Retele de livrare de continut (CDN) : Trimiterea de continut specific catre diferite servere in functie de locatia geografica sau de solicitarea utilizatorului
Echilibratoare de incarcare : Distribuirea diferitelor sarcini pe mai multe servere pentru o procesare eficienta
Arhitectura microserviciilor : Directionarea datelor relevante catre servicii specifice
Baze de date distribuite : Sincronizarea doar a datelor necesare cu diferite replici ale bazei de date
Deja suna foarte interesanta partea de DB distibuite :)
Daca tot am introdus conceptul de "fan-out", avem si partea de "broadcast" - implica trimiterea acelorasi date dintr-o singura sursa catre toti destinatarii conectati, indiferent de cerintele lor specifice; in acest caz, toate nodurile din retea primesc aceleasi informatii simultan
Avantaje:
Simplu si usor de implementat, in special pentru retele mici
Asigura consistenta datelor pe toate nodurile
Util pentru aplicatii in care toate nodurile au nevoie de aceleasi date in acelasi timp
Dezavantaje:
Irosi latime de banda deoarece toate nodurile primesc aceleasi date, chiar daca unele nu au nevoie de ele
Poate cauza congestie(o retea de calculatoare sau de comunicatii primeste mai multe date decat poate duce) in retea, in special in sistemele mari
Lipsa personalizarii pentru cerintele individuale ale nodurilor.
Aplicatii ale transmisiei de date:
Servicii de streaming : Difuzarea de materiale video sau audio catre mai multi utilizatori simultan
Fluxuri de date in timp real : Actualizari ale pietei bursiere sau scoruri sportive live trimise tuturor utilizatorilor
Retele IoT : Distribuirea datelor de la senzori catre toate nodurile dintr-o retea inteligenta
Actualizari de firmware : Difuzarea actualizarilor de software catre toate dispozitivele conectate
(source + more info: https://www.geeksforgeeks.org/system-design/data-fan-out-and-vs-broadcast-in-distributed-system/)
Explicatia pentru figura 1-3 - modelul istoric al Twitter-ului (2012–2017), conceput strict pentru un feed cronologic simplu ("cele mai noi tweet-uri de la cei pe care ii urmaresti")
In loc ca un utilizator sa astepte ca sistemul sa caute in baza de date toate postarile persoanelor pe care le urmareste atunci cand deschide aplicatia (citire scumpa), sistemul face munca grea in momentul in care se publica un tweet (scriere mai scumpa)
User posts tweet: Un utilizator scrie un tweet; sistemul primeste aproximativ 4.6k scrieri/secunda (media de tweet-uri noi postate global) => ajunge intr-o baza de date principala/coada cu toate tweet-urile (All tweets)
Fan-out: evenimentul (tweet-ul) este distribuit catre mai multe destinatii (cutiile postale/feed-urile urmaritorilor); cand postezi ceva, un serviciu de fundal ia tweet-ul tau si il introduce direct in "cutia postala" (inbox/home timeline cache) a fiecaruia dintre urmaritorii tai => multiplica numarul de operatii: de la 4.6k tweet-uri noi postate se ajunge la 345k scrieri/secunda in cache-urile utilizatorilor
Get home timeline: Utilizatorii deschid aplicatia (aprox. 300k citiri/secunda); pentru ca feed-ul fiecarui recipient este deja pre-calculat (listele Tweets for recipient 1, 2, 3), aplicatia doar citeste instant din memoria RAM (ex: Redis) => nu mai trebuie sa faca interogari complexe de tip JOIN pe baze de date mari
(source: recunosc, am folosit putin AI)
In momentul de fata, Twitter foloseste alt model, intrucat unul dintre motivele care performanta sistemului era afectata de existenta conturilor cu un numar foarte mare de urmaritori
ex: daca cineva cu 100 de milioane de followers posteaza, sistemul trebuia sa faca instant 100 de milioane de scrieri in memorie RAM => cozile se blocau (backpressure)
Solutia actuala - Model Hibrid:
Pentru utilizatori obisnuiti - schema(Fan-out on Write / Push)
Pentru conturi mari (cu peste ~10k–100k de followers) - NU Fan-out la scriere, ci tweet-ul se salveaza intr-un singur loc, iar cand deschizi aplicatia, feed-ul tau il preia prin imbinare la citire - Query (Fan-out on Read / Pull)
Totodata, in momentul de fata feed-ul nu mai e format din ultimele postari pe le care publica persoanele pe care le urmaresti, ci si din content posibil sa iti placa si de la oameni pe care nu ii cunosti
Astfel, schema din figura 1-3 presupune o simpla lista ordonata dupa timp (T1, T2, T3) => aplicatia foloseste acum tab-ul "For You" ca feed implicit, unde datele nu mai sunt doar stocate si citite, ci trecute prin modele de Machine Learning/AI :
In-Network vs Out-of-Network: Feed-ul contine acum ~50% postari de la oameni pe care nu ii urmaresti, dar care s-ar putea sa-ti placa
Heavy Ranker & Graph AI: In loc de o lista simpla in Redis, microserviciile extrag mii de tweet-uri candidate, le trec printr-un model neural (care evalueaza probabilitatea sa dai Like, Reply sau Retweet) si le sorteaza dinamic
Postare Tweet ──► Filtru (Numar Followers)
│
├── Urmaritori putini ──► Push in Cache (Figura 1-3)
│
└── Urmaritori multi  ──► Baza de date centrala (Pull la citire)
│
Deschidere App ──► Algoritm de Recomandare (ML) ──────┴──► Generare Feed "For You"
Informatiile de mai sus sunt mai avansate pentru aceasta etapa, insa nu imposibile!!(+ abia astept sa inteleg si mai bine ce e in spate, pentru ca e absolut fascinant)
Describing Performance
"Ce se intampla cand load-ul creste?" - 2 perspective:
cand cresti un parametru de load si pastrezi intacte resursele sistemului, cum e afectata performanta sistemului?
^ load + - resurse => cum e performanta?
cand cresti un parametru de load, cat trebuie sa cresti in resurse daca doresti vrei sa pastrezi aceeasi performanta?
^ load + - performanta => cat cresti resursele?
Obs: ^ = crestere, - = constant
Intr-un sistem de procesare in loturi, cum ar fi Hadoop, de obicei ne intereseaza randamentul - numarul de inregistrari pe care le putem procesa pe secunda sau timpul total necesar pentru a rula un job
pe un set de date de o anumita dimensiune
Obs: Intr-o lume ideala, timpul de executie al unui job batch este dimensiunea setului de date impartita la debit. In practica insa, timpul de executie este adesea mai lung, din cauza asimetriei (datele nu sunt distribuite uniform pe intregul proces al lucratorului) si a necesitatii de a astepta finalizarea celei mai lente sarcini
In sistemele online, ceea ce este de obicei mai important este
timpul de raspuns al serviciului - adica timpul dintre momentul in care un client trimite o solicitare si primirea unui raspuns
Din afirmatiile de mai sus rezulta ca totul pleaca de la SCOPUL pe care dorim sa il atingem!!!
Latenta != timpul de raspuns!!!
Latenta - din interiorul sistemului - durata in care o cerere asteapta sa fie gestionata - timpul mort in care o cerere sta la coada inainte sa fie efectiv preluata si procesata de un procesor
Timpul de raspuns - ceea ce vede clientul - pe langa timpul efectiv de procesare a cererii (timpul serviciului), acesta include intarzierile de retea si intarzierile de asteptare - incepe in secunda in care un utilizator apasa un buton in aplicatie si se termina cand ecranul s-a actualizat complet cu datele primite
Latenta = Timp de asteptare in coada
Timpul de Raspuns = Latenta + Timp de procesare + Intarzieri de retea (dus-intors)
ex: restaurant drive-thru:
Latenta: Timpul in care stai cu masina la coada, asteptand sa-ti vina randul la geam sa plasezi si sa-ti fie preluata comanda - bucatarul inca nu gateste nimic pentru tine, doar astepti serviciul
Timpul de procesare (Service Time): Cat timp ii ia bucatarului sa prepare mancarea si sa o puna in pachet
Timpul de raspuns: Toata experienta ta, de cand ai intrat cu masina pe banda drive-thru (asteptat la coada + gatit + inmanat pachetul la geam) pana cand ai primit mancarea in mana si poti pleca
Ar trebui sa vedem timpul de raspuns ca pe o distributie de valori pe care o poti masura si NU ca pe un simplu numar(difera de la cerere la cerere) - pot aparea fluctuatii care sunt influentate de diversi factori(server, background processes etc)
Outliers - puncte de date care difera semnificativ de restul setului de date si nu urmeaza modelul general(pot aparea din cauza erorilor, evenimentelor rare sau variabilitatii naturale a datelor)
(source + more info: https://www.geeksforgeeks.org/machine-learning/what-are-outliers-in-data/)
Slow request => mult mai expensive - de regula proceseaza mai multe date
Metrica de average/mean - nu cea mai buna pentru cel mai tipic response time, pentru ca nu exprima cati useri au experimentat asta
As putea spune ca metrica median ar fi o idee mai buna decat mean, pentru ca functioneaza mai bine pentru seturi de date asimetrice(necesita ordonare) - spune cam ce timp mediu asteapta userii(jum inainte, jum dupa) si face referire la un singur request
De asta, e mai bine de utilizat percentilele, intrucat impart setul de date in 100 de parti egale(median = p50), dar din nou, necesita sortare - reprezinta in esenta pragurile timpului de raspuns
ex: p95, p99, p90
daca p95 -> 1.5s => 95% din request-uri iau mai putin de 1.5s
High percentiles of response times = tail latencies - IMPORTANTE intrucat afecteaza direct UX
Cazul Amazon - legatura dintre arhitectura datelor, metricele de performanta si impactul lor direct asupra afacerii
De exemplu, Amazon descrie cerintele privind timpul de raspuns pentru serviciile interne in termeni de percentila 99,9, chiar daca afecteaza doar 1 din 1.000 de solicitari. Acest lucru se datoreaza faptului ca clientii cu cele mai lente solicitari sunt adesea cei care au cele mai multe date in conturile lor deoarece au facut multe achizitii - adica sunt cei mai valorosi clienti. Este important sa mentinem acesti clienti fericiti asigurandu-ne ca site-ul web este rapid pentru ei: Amazon a observat, de asemenea, ca o crestere de 100 ms a timpului de raspuns reduce vanzarile cu 1%, iar altii raporteaza ca o incetinire de 1 secunda reduce o metrica a satisfactiei clientilor cu 16%
Percentila 99.9 (P99.9) - masoara timpul de raspuns pentru cea mai lenta cerere din 1.000 (cel mai defavorizat 0.1% dintre utilizatori)
Ce inseamna asta pentru un Data Engineer?
Nu optimiza doar cazul mediu: Cand creezi un pipeline de date sau un query, trebuie sa testezi cum se comporta sistemul la pragurile de sus (edge cases si date extrem de mari / skewed data)
SLA-urile (Service Level Agreements) se construiesc pe percentile: In loc sa garantezi "timp mediu de raspuns: 50ms", vei garanta "P99 sub 200ms", asigurandu-te ca aproape nimeni nu experimenteaza un site blocat
(source: recunosc, am folosit putin AI)
Totusi, optimizarea timpilor de raspuns la percentile foarte mari este destul de costisitoare si de multe ori nu aduce un beneficiu, fiind dificil de implementat si usor afectate de evenimente random car nu tin de controlul nostru
De regula, percentilele sunt folosite in:
Service level objectives(SLOs) - promisiunea pe care o companie o face utilizatorilor cu privire la o anumita metrica, cum ar fi raspunsul la incidente sau timpul de functionare; exista in cadrul unui SLA ca promisiuni individuale continute in acordul complet cu utilizatorul => SLO-ul este obiectivul specific pe care serviciul trebuie sa il indeplineasca pentru a respecta SLA-ul; SLO-urile ar trebui sa fie intotdeauna simple, clar definite si usor de masurat pentru a determina daca obiectivul este indeplinit sau nu
Service level agreements(SLAs) - acord incheiat intre o companie si utilizatorii unui anumit serviciu; defineste diferitele promisiuni pe care compania le face utilizatorilor cu privire la anumite valori, cum ar fi disponibilitatea serviciilor => Acordurile de nivel de serviciu (SLA) sunt adesea redactate de echipa de afaceri sau juridica a unei companii
(source + more info: https://dev.to/karanpratapsingh/system-design-sla-slo-sli-446p)
Obs: aceste metrici seteaza asteptari pentru clientii serviciului si ofera clientilor "puterea" de a anunta cand ceva este incalcat
Head-of-line(HOL) blocking - apare atunci cand prima operatie dintr-o coada impiedica procesarea tuturor operatiunilor ulterioare, chiar daca acestea ar putea fi finalizate mai rapid => e important sa masuram timpii de raspuns pe partea clientului
Asadar, la generare de load artificial pentru a testa scalabilitatea sistemului, clientul load trebuie sa trimita request-uri independent de timpul de raspuns - daca asteapta finalizarea celui anterior, acel comportament de a mentine artificial cozile mai scurte in test decat ar fi in realiate, fapt care ofera un grad mare de neconcordanta a masuratorilor
High percentiles - foarte importante in partea de servicii backend => multiple backend calls
chiar daca un procent mic de request-uri sunt lente => probabilitatea de a initia un apel lent creste daca un request-ul necesita mai multe apeluri de backend => tail latency amplification
Am nevoie de lamurire la cadrul de pe pagina 16

Approaches for Coping with Load
"Cum mentinem o performanta buna chiar daca our load parameters cresc cu un anumit amount?" - practic, "popularea" progresiva a sistemului(nu neaparat liniara si lenta, ci poate fi si brusca)
!!Reminder: Load parameters - setari de configurare si variabile care controleaza modul in care datele sunt:
extrase
transformate
scrise intr-o destinatie tinta
Tipuri comune de load parameters:
Setari de conectare si acreditari: Nume de gazda ale bazei de date, porturi, ID-uri de utilizator, secrete sau siruri de conexiune care indica spre sursa si destinatie
Domeniu de aplicare si filtre de executie: Intervale de date, filigrane (cum ar fi last_loaded_timestamp) sau ID-uri specifice utilizate pentru a extrage date incrementale sau delta in loc sa se reincarce totul
Semnalizari de comportament de incarcare: Comutatoare care dicteaza daca o operatiune de incarcare efectueaza o operatiune APPEND, OVERWRITE, MERGE (upsert) sau o inlocuire completa a tabelului
Optiuni de performanta si optimizare: Dimensiuni de lot, numar de fire de executie paralele, intervale de validare sau limite de timeout
Reguli de schema si mapare: Nume de tabele tinta, formate de fisiere (Parquet, CSV) sau granule de agregare (cum ar fi rezumate saptamanale vs. lunare).
(source + more info: https://docs.oracle.com/cd/E63231_01/doc/BIACF/GUID-75D84990-12D5-4308-93A8-79282145CC8B.htm#BIACF10196)
Chiar daca o arhitectura este buna pentru un anumit nivel de load, asta nu garanteaza ca e bun si pentru un nivel de load mai incarcat - e posibil sa fie suficient, insa, in acelasi timp, cam imposibil + exista alte variante mai eficiente => de asta, o arhitectura nu poate fi in esenta proiectata sa raspunda "perfect" la fiecare nivel de load din prima - MEREU trebuie regandita si modelata pe nevoile si pozitia reala - load-ul curent de care am vorbit anterior!!!(plus ca scopul initial se poate modifica si el pe parcurs) - e captivant pentru ca trebuie sa gasesti o noua solutie si mai buna de fiecare data :) - astfel iti poti da seama atat de evolutia sistemului, cat si de evolutia ta, which is very fun :)
Dihotomia scaling up si scaling out - haha, am cautat-o acum cateva zile(pe 25.08.2026), e practic dualitatea scalarii pe verticala(add more CPU etc => moving to a more powerful machine) si cea pe orizontala(add more servers etc => distributing the load across multiple smaller machines)
Astfel, scalarea orizontala mai e cunoscuta si ca shared-nothing architecture(SNA) - arhitectura de calcul distribuita in care fiecare NOD functioneaza INDEPENDENT, cu propria memorie si stocare; nodurile comunica doar printr-o retea, eliminand resursele partajate si reducand blocajele sistemului
In acest mod, fiecare nod isi gestioneaza propriile resurse fara a partaja memorie sau stocare cu alte noduri - "I'm on my own and I can handle it!!"
Noduri noi pot fi adaugate cu usurinta, iar esecurile dintr-un nod nu le afecteaza direct pe celelalte - "It's only me vs me"
Caracteristici
Independenta: Fiecare nod functioneaza independent, avand propria memorie + spatiu de stocare; nodurile comunica intre ele(<=>) doar prin protocoale de retea
Scalabilitate: Arhitectura permite scalarea orizontala prin adaugarea de noi noduri; fiecare nod contribuie cu putere suplimentara de stocare si procesare
Izolarea defectiunilor: Defectiunile sunt izolate la noduri individuale si nu afecteaza direct alte noduri, acest lucru imbunatateste disponibilitatea si rezilienta sistemului
Distributia datelor: Datele sunt distribuite pe mai multe noduri folosind partitioning sau sharding techniques; fiecare nod gestioneaza un subset specific de date
Ce inseamna sharding? - raspuns: ajuta sistemul sa pastreze datele in diferite resurse in functie de procesul de partajare
Astfel, "shard" inseamna "o mica parte a unui intreg" => inseamna impartirea unei parti mai mari in parti mai mici; in DBMS(Database Management System), sharding este un tip de partitionare a bazelor de date in care o baza de date mare este impartita sau partitionata in date mai mici si noduri diferite => aceste partajari nu sunt doar mai mici, ci si mai rapide => usor de gestionat!!!
ex: luam o DB a unei facultati in care toate inregistrarile studentilor (prezente si trecute) din intreaga facultate sunt pastrate intr-o singura baza de date :( => ar contine un nr foarte mare de date(let's say around 100.000 de inregistrari)
Cand trebuie sa gasim un student din aceasta DB, de fiecare data trebuie efectuate aproximativ 100.000 de tranzactii pentru a gasi studentul => foarte, foarte costisitor :(
Acum, luam in considerare aceleasi inregistrari ale studentilor de la facultate, impartite in fragmente de date mai mici, in functie de ani
Fiecare fragment de date va avea doar inregistrari de aproximativ 1000-5000 de studenti => DB a devenit mult mai usor de gestionat + costul tranzactiilor de fiecare data se reduce cu un factor enorm <= FRAGMENTARE(sharding)
Cum functioneaza Sharding tho?
Intr-un sistem sharded, datele sunt partitionate in fragmente pe baza unui criteriu PREDETERMINAT
ex: putem imparti datele in functie de locatia geografica, ID-ul utilizatorului, perioada de timp etc
Odata ce datele sunt partitionate, acestea sunt distribuite pe mai multe servere sau noduri; fiecare server sau nod este responsabil pentru stocarea si procesarea unui subset de date
Ok, sounds interesting, insa cum accesam acele date? De unde stie sistemul ca noi suntem intr-o anumita regiune georgrafica si nu alta?? - raspuns: pentru a interoga date dintr-o sharded DB, sistemul trebuie sa stie care fragment contine datele necesare => acest lucru se realizeaza folosind o cheie de fragment(shard key) = IDENTIFICATOR UNIC utilizat pentru a mapa datele la fragmentul corespunzator
ex: shard key = country_code
User_1: { id: 101, name: "Ana", country_code: "RO" } Shard Romania
User_2: { id: 102, name: "John", country_code: "US" } Shard SUA
Cand este primita o interogare, sistemul utilizeaza shard key pentru a determina care shard contine datele necesare si apoi trimite interogarea catre serverul sau nodul corespunzator => sistemul mentine o tabela de rutare (numita adesea Shard Map sau administrata de un nod coordonator precum Router-ul din MongoDB sau Proxy-ul din baze de date SQL sharded):
Valoare Shard Key (country_code)        Nod Server (Shard Fizic)
RO                                      Server_Node_EU_East (IP: 192.168.1.10)
DE, FR                                  Server_Node_EU_West (IP: 192.168.1.11)
US, CA                                  Server_Node_US_East (IP: 192.168.1.12)
Caracteristici ale sharding-ului:
Sharding-ul reduce dimensiunea bazei de date
Sharding-ul face baza de date mai rapida
Sharding-ul face baza de date mult mai usor de gestionat
Sharding-ul poate fi uneori o operatiune complexa
Sharding-ul reduce costul tranzactiilor bazei de date
Fiecare shard citeste si scrie propriile date
Multe baze de date NoSQL ofera auto-sharding
Eroarea unui shard nu afecteaza procesarea datelor altor shard-uri
(source + more info: https://www.geeksforgeeks.org/dbms/what-is-sharding/)
Procesare paralela: Mai multe noduri pot procesa sarcini simultan pe diferite partitii de date => imbunatateste semnificativ performanta pentru aplicatiile la scara larga
Arhitectura Shared Nothing(SNA) joaca un rol semnificativ in proiectarea sistemelor, in special pentru sistemele distribuite, datorita numeroaselor sale avantaje si impactului asupra performantei, scalabilitatii si fiabilitatii:
Scalabilitate: Sistemele pot fi scalate cu usurinta prin adaugarea de noi noduri fara modificari arhitecturale majore; fiecare nod isi adauga propriile resurse de stocare si de calcul
Performanta: Volumul de lucru poate fi distribuit pe mai multe noduri pentru procesare paralela => imbunatateste performanta si reduce conflictele legate de resurse
Fiabilitate si toleranta la erori: Defectiunea unui nod nu afecteaza functionarea celorlalte noduri => asigura disponibilitate ridicata si fiabilitate a sistemului
Intretinere si administrare: Nodurile individuale pot fi actualizate, intretinute sau inlocuite independent => reduce timpul de nefunctionare si simplifica administrarea sistemului
Eficienta din punct de vedere al costurilor: Organizatiile pot incepe cu mai putine noduri si se pot extinde pe masura ce cererea creste => ajuta la optimizarea costurilor de infrastructura si a utilizarii resurselor
Flexibilitate: Diferite componente ale sistemului pot fi dezvoltate, testate si implementate independent => permite o dezvoltare mai rapida si actualizari de sistem mai usoare
(source + more info: https://www.geeksforgeeks.org/system-design/shared-nothing-architecture/)
Astfel, un sistem care poate rula pe o singura masina este deseori mai simplu, insa masinile ultracalitative pot deveni foarte scumpe => de asta se ajunge in majoritatea cazurilor la scaling out si chiar o mixtura intre cele 2
Sistemul "elastic" - pot adauga automat computing resources atunci cand detecteaza o crestere a load-ului, in timp ce alte sisteme sunt scalate manual(omul decide!!) - e de ajutor cand load-ul este unpredictable, insa scalarea manuala a sistemelor ofera mai multa simplitate si mai putine surprize operationale
sistemul scalat elastic - scalare automata + mai putin control + posibil o performanta mai buna + posibilitatea unor surprize neplacute
sistemul scalat manual - scalare manuala + mai mult control asupra actiunilor + mai putine surprize
Desi distribuirea pe mai multe noduri a serviciilor poate parea simpla, trecerea de la un single node la mai multe poate adauga o complexitate aditionala => pana de curand, sfatul era sa pastrezi DB pe un singur nod (scalare verticala) pana cand costurile de scalare sau cerintele de disponibilitate ridicata obligau trecerea la distribuita
Baza de date monolitica (Single Node / Vertical Scaling): Simplu de gestionat (tranzactii ACID garantate, interogari usoare fara sharding), dar extrem de scumpa la un moment dat (servere tot mai mari) si vulnerabila (un singur punct de esec).
Baza de date distribuita (Horizontal Scaling / Sharding): Rezolva scalabilitatea, dar aducea o complexitate arhitecturala masiva (gestionarea cheilor de sharding, lipsa tranzactiilor ACID complete, dificultati la JOIN-uri).
Care este verdictul actual totusi? - raspuns: pragul de trecere catre sisteme distribuite a scazut dramatic, datorita aparitiei a trei categorii majore de tehnologii:
Baze de date Distributed SQL / NewSQL (ex: CockroachDB, YugabyteDB, TiDB): Iti ofera scalabilitate orizontala automata (fara sa faci tu manual sharding geografic sau dupa ID), pastrand totodata garantiile ACID si interogarile SQL standard
Servicii Managed / Cloud-Native Serverless Databases (ex: AWS Aurora, GCP Spanner, Snowflake, BigQuery): Scalarea distribuita si stocarea separata de calcul (decoupled storage and compute) sunt gestionate complet de furnizorul de cloud; platesti doar ce consumi si nu mai administrezi tu nodurile fizice sau rutarea cererilor
Hardware ieftin si extrem de performant: Un singur server modern (ex: 128-256 vCPU, 1TB+ RAM, NVMe SSDs) poate duce zeci/sute de mii de operatii pe secunda => scale-up dureaza mult mai mult pana sa-si atinga limita decat in urma cu 10-15 ani
Strategia recomandata in prezent
Pentru start-up-uri / proiecte noi: Incepe cu un singur nod puternic (sau o baza cloud-managed precum Postgres/MySQL pe RDS) SAU o baza de date NewSQL nativ-distribuita din prima zi, fara sa-ti mai faci griji de sharding manual
Cand schimbi arhitectura: Nu mai astepti pana se prabuseste serverul unic; trecerea la un sistem distribuit se face proactiv, cand cerintele de disponibilitate (High Availability pe mai multe regiuni geografice) sau limitele financiare ale scalarii verticale o cer
(source: recunosc, am folosit AI)
"magic scaling sauce" - one-size-fits-all scalable arhitecture - Nu exista
Tipuri de probleme care pot aparea si care pot determina trecerea de la scaling-up la scaling-out:
volumul de citiri
volumul de scrieri
volumul de date de stocat
complexitatea datelor
response time etc
Practic, o arhitectura care scaleaza destul de bine o aplicatie particulara e construita in baza unor PRESUPUNERI cu ce operatiuni ar fi comune si care ar fi rare => load parameters => AICI AR FI POSIBIL CA ABSOLVENTUL DE INFO EC SA FIE CEL MAI POTRVIT, intrucat intelege in mare atat partea tehnica, cat si partea de business, actiunile principale ale user-ului
Intr-un stadiu incipient este de obicei mai important sa poti itera rapid pe caracteristicile produsului decat sa scalezi la o sarcina viitoare ipotetica => lucru suplimentar daca nu faci asta + resurse irosite
Desi sunt specifice pentru o aplicatie particulara, arhitecturile scalabile au la baza reguli si blocuri de cod generale, aranjate in pattern-uri similare

##### MAINTAINABILITY

Obs: se stie ca majoritatea costului software-ului nu e dezvoltarea initiala, ci MENTENANTA LUI:
- corectarea bugs
- pastrare operationala
- investigarea erorilor
- adaptare la noile platforme
- modificarea pentru noi use case-uri
- rambursarea datoriei tehnice
- adaugarea de noi features

Totusi, din pacate, multi oameni care lucreaza cu sisteme software nu apreciaza mentenanta asa-numitelor *legacy systems* - implica corectarea greselilor altora sau lucrul cu platforme care sunt acum invechite sau cu sisteme care au fost fortate sa faca lucruri pentru care nu au fost niciodata destinate; fiecare legacy system este neplacut in felul sau => dificil de oferit recomandari generale pentru a le gestiona

Ce reprezinta defapt un legacy system? - raspuns: programele mai vechi, dezvoltate cu zeci de ani in urma, sunt inca utilizate, efectuand modificari pentru a indeplini cerintele afacerii - cresterea rapida a acestor sisteme poate reprezenta un risc pentru organizatiile mai mari, deoarece acestea pot necesita hardware si sisteme de operare invechite

Un legacy system este un software, un limbaj de programare, o baza de date sau o infrastructura hardware *invechita*, care este inca folosita activ de o companie pentru ca indeplineste o functie critica de business, desi exista tehnologii moderne mult mai eficiente

*Piesa centrala* a unui legacy system nu este neaparat doar vechimea sa, ci *dificultatea si riscul de a-l inlocui*

Caracteristicile principale ale unui Legacy System:
- Limbaje si tehnologii depasite: Cod scris in COBOL, Fortran, VB6, baze de date vechi (Mainframes) sau aplicatii monolitice greu de modularizat

Reminder - arhitectura monolitica si aplicatiile monolitice:

*Arhitectura monolitica* - metodologie de proiectare software care combina toate componentele unei aplicatii intr-*o singura unitate inseparabila* => in cadrul acestei arhitecturi, interfata cu utilizatorul, logica de business si straturile de acces la date sunt create, puse in functiune si intretinute ca *o singura unitate unificata* - de asta, multe aplicatii mici utilizeaza acest tip de arhitectura, intrucat necesita de regula operatiuni si tranzactii asupra unei singure DB

Totusi, difera de arhitectura modulara prin simplul fapt ca, de ex, componenta factura poate accesa direct tabela de utilizatori; insa, in momentul in care in tabela de utilizatori se modifica un camp, toata aplicatia este data peste cap - in arhitectura modulara, componenta factura nu poate accesa direct tabela de utilizatori, necesitand instantierea unui obiect de tip utilizator care are o functie care genereaza proprietatile lui - interesant de studiat, pentru ca avem "trio-ul": monolitic - modular - microservicii

(source + more info: https://www.geeksforgeeks.org/system-design/monolithic-architecture-system-design/)

- Lipsa documentatiei si a specialistilor: Codul nu este documentat, fiind mentinut prin modificari superficiale (patch-uri)
- Probleme de integrare: Se conecteaza extrem de greu cu tehnologiile moderne (API-uri REST, microservicii, sisteme Cloud)
- Latenta si costuri mari de intretinere: Scalarea este scumpa, iar securizarea sistemului impotriva vulnerabilitatilor moderne necesita resurse mari

De ce le mai folosesc companiile totusi? - raspuns: desi sunt greu de gestionat, multe organizatii mari (banci, institutii guvernamentale, companii de aviatie, spitale) continua sa foloseasca legacy systems din doua motive principale:
- Garantia functionarii (*Daca functioneaza, nu atinge!*): Sistemul proceseaza deja miliarde de tranzactii corect de o perioada buna de timp => riscul ca un sistem nou sa aiba bug-uri si sa opreasca activitatea este considerat PREA MARE
- Costul masiv de migrare: Inlocuirea completa a unui legacy system (rip and replace) poate ajungi la costuri foarte mari si poate dura ani de implementare

(source + more info: https://www.geeksforgeeks.org/software-engineering/what-is-legacy-software/)

Totusi, software-ul poate fi proiectat astfel incat sa minimizeze "durerea" din timpul mentenantei => EVITAM CREAREA PROPRIE DE LEGACY SYSTEMS => 3 PRINCIPII DE DESIGN PENTRU SISTEMELE SOFTWARE:

The Godly OSE Design Principles:

1. *Operability(operabilitate)* - faciliteaza echipelor operationale mentinerea functionarii fara probleme a sistemului
2. *Simplicity(simplitate)* - faciliteaza intelegerea usoara a sistemului de catre noii programatori prin a elimina cat se poate de mult din complexitatea sistemului - personal, consider ca te ajuta foarte mult si pe tine, nu neparat pentru ceilalti(!!! aceasta simplitate e DIFERITA de cea UI)
3. *Evolvability(Evolutivitate - proprietatea unui sistem de a fi modificat cu usurinta pentru a integra noi functionalitati)* - faciliteaza programatorilor posibilitatea de a face modificari la sistem in viitor, adaptandu-l pentru cazuri de utilizare neprevazute pe masura ce cerintele se schimba - cunoscut si sub denumirea de *extensibilitate*, *modificabilitate* sau *plasticitate*

###### Descrierea fiecarei componente OSE

1. Operability: Making life easy for operations
"good operations can often work around the limitations of
bad (or incomplete) software, but good software cannot run reliably with bad operations" - practic, degeaba ai cea mai evoluata masina, cel mai bun soft daca tu nu stii sau il folosesti prost - degeaba achizitionezi o masina foarte scumpa joasa daca tu intri in gropi cu ea sau te apuci sa urci borduri cu ea - de asta e foarte important sa definim de la bun inceput ce intentii avem cu soft-ul nostru, pentru a stii cum sa-l modelam

Reminder: Automatizarea tine de oameni(atat setarea ei, cat si asigurarea ca functioneaza exact cum ne dorim)

Echipele operationale sunt vitale pentru mentinerea functionarii fara probleme a unui sistem software - are, de obicei, urmatoarele responsabilitati si multe altele:
- Monitorizarea starii de sanatate a sistemului si restabilirea rapida a serviciului daca acesta intra intr-o stare critica
- Urmarirea cauzei problemelor, cum ar fi defectiunile sistemului sau performanta degradata
- Mentinerea software-ului si a platformelor actualizate, inclusiv a patch-urilor de securitate
- Monitorizarea modului in care diferite sisteme se afecteaza reciproc, astfel incat o schimbare problematica sa poata fi evitata inainte de a provoca daune
- Anticiparea problemelor viitoare si rezolvarea acestora inainte ca acestea sa apara (ex: planificarea capacitatii)
- Stabilirea unor bune practici si instrumente pentru implementare, gestionarea configuratiei si multe altele
- Efectuarea unor sarcini complexe de intretinere, cum ar fi mutarea unei aplicatii de pe o platforma pe alta
- Mentinerea securitatii sistemului pe masura ce se fac modificari de configuratie
- Definirea unor procese care fac operatiunile previzibile si ajuta la mentinerea stabilitatii mediului de productie
- Pastrarea cunostintelor organizatiei despre sistem, chiar si atunci cand persoane vin si pleaca

O buna operabilitate inseamna facilitarea sarcinilor de rutina, oferind posibilitatea echipei operationale sa isi concentreze eforturile asupra activitatilor cu valoare ridicata => sistemele de date pot face diverse lucruri pentru a facilita sarcinile de rutina, inclusiv:
- Oferirea de vizibilitate asupra comportamentului in timpul executiei si a componentelor interne ale sistemului, cu o buna monitorizare
- Oferirea unui suport bun pentru automatizare si integrare cu instrumente standard
- Evitarea dependentei de masini individuale (oferind posibilitatea de scoatere a masinilor pentru intretinere, in timp ce sistemul in ansamblu continua sa functioneze neintrerupt)
- Oferirea unei documentatii bune si a unui model operational usor de inteles("Daca fac X, Y se va intampla")
- Oferirea unui comportament implicit bun, dar si oferirea administratorilor a libertatii de a suprascrie valorile implicite atunci cand este necesar
- Auto-reparare acolo unde este cazul, dar si oferirea administratorilor de control manual asupra starii sistemului atunci cand este necesar
- Prezentarea unui comportament previzibil, minimizand surprizele

2. Simplicity: Managing Complexity
Proiectele mici - de regula, cod simplu + expresiv
Proiectele mai mari - devin mai complexe si mai greu de inteles(stiu.. am experimentat asta, am avut si zile-saptamani intregi in care stateam si incercam sa inteleg "ce a vrut sa spuna autorul"..)

Asadar, cu cat creste proiectul, cu cel putin atat creste si complexitatea care bineinteles incetineste pe toata lumea care lucreaza la sistem => creste costul mentenantei

*Big ball of mud* - proiect care e "imbibat" in complexitate

Exista diverse simptome posibile ale complexitatii:
- explozia spatiului de stari
- cuplarea stransa a modulelor
- dependente incalcite
- denumire si terminologie inconsistente
- trucuri care vizeaza rezolvarea problemelor de performanta 
- cazuri speciale pentru a rezolva problemele din alte parti etc altele. 

Complexitatea ridicata => creste Mentenanta => bugete + timpi de lucru suprascrisi :(

De ar fi doar atat..

Insa, complexitatea introduce si un *risc major de introducere a erorilor la realizarea unei modificari* => presupuneri ascunse, consecinte neintentionate, interactiuni unexpected - deja cunosc prea bine...(thank God ca nu am ajuns sa fac vreun DELETE *)

Asadar, toate aceste aspecte negative legate de complexitate ar putea fi evitate daca REDUCEM COMPLEXITATEA, simplitatea devenind astfel un key goal pentru design-ul sistemelor

!!ATENTIE: daca reducem complexitatea != reducerea functionalitatilor - ci ar putea fi chiar o reducere a unei complexitati aditionale

Moseley si Marks(source: "Out of the Tar Pit" (2006)) definesc complexitatea "ca accidentala" daca nu este inerenta problemei pe care o rezolva software-ul (asa cum este vazuta "de utilizatori"), ci apare doar din implementare => face o distinctie fundamentala intre doua tipuri de complexitate in dezvoltarea de software: *essential complexity* si *accidental complexity*

Cele doua tipuri de complexitate
- Complexitatea Esentiala (Inerenta): Este complexitatea problemei reale de business pe care incerci sa o rezolvi

ex: Intr-o aplicatie bancara, regulile de calcul ale dobanzilor, legile fiscale si pasii de aprobare ai unui credit reprezinta complexitate esentiala => nu le poti elimina fara sa schimbi natura aplicatiei

- Complexitatea Accidentala (Implementare): Este complexitatea creata de instrumentele, limbajele, arhitecturile sau deciziile de cod alese de ingineri

ex: Gestionarea manuala a memoriei, sincronizarea firelor de executie (multithreading locks), formatarea manuala a datelor JSON, bug-urile de stare (state management) sau structura complicata de baze de date

(source: recunosc, am folosit AI)

Siii, THE MASTER "KEY"(IT'S A TOOL, BUT LET IT LIKE THIS) OF REMOVING ACCIDENTAL COMPLEXITY: ABSTRACTIZAREA(dear old friend, I missed you <3 ) - ascunde detaliile interne de implementare si expune doar o interfata simpla, clara si functionala

Abstractizarea elimina complexitatea accidentala prin reducerea cantitatii de informatie pe care un programator trebuie sa o retina in memorie la un moment dat

Principalele motive pentru care abstractizarea functioneaza
- Izolarea detaliilor: nu trebuie sa stii cum functioneaza un motor cu ardere interna ca sa poti conduce o masina; ai nevoie doar de volan si pedale => in mod similar, o abstractizare ofera un "volan" pentru cod
- Separarea responsabilitatilor: aplicatia este impartita in layers; fiecare strat se ocupa de o singura problema si comunica cu celelalte doar prin interfete bine definite (API-uri, clase abstracte)
- Compozabilitate si Reutilizabilitate: partile abstractizate pot fi imbinate ca piesele de LEGO :) => poti schimba implementarea din spate fara sa strici restul sistemului

O abstractizare buna poate ascunde o multime de detalii de implementare in spatele unei fatade curate, usor de inteles + poate fi utilizata si pentru o gama larga de aplicatii diferite

Nu numai ca aceasta reutilizare este mai eficienta decat reimplementarea unui lucru similar de mai multe ori, dar duce si la software de calitate superioara, deoarece imbunatatirile calitatii componentei abstractizate aduc beneficii tuturor aplicatiilor care o utilizeaza

Practic, abstractizarea ne ajuta sa "ascundem"(sa nu folosim direct) machine code, intrucat ne "salveaza" de a fi nevoiti sa ne gandim la el

Totusi, gasirea unor metode de abstractizare bune poate deveni dificila :(

Desi, in ceea ce priveste sistemele distribuite, exista multi algoritmi buni, este destul de neclar cum ar trebui impachetati in abstractizari pentru a mentine complexitatea sistemului la un nivel manageable

3. Evolvability: Making Change Easy
Cam imposibil ca nevoile sistemului sa ramana neschimbate pentru totdeauna - mult mai probabil sa fie intr-un flux constant:
- inveti noi informatii 
- cazuri neanticipate anterioare ies la iveala
- se modifica prioritatile business-ului
- noi cereri/features etc
- platforme noi inlocuiesc pe cele vechi
- se modifica reglementarile legale
- cresterea sistemului determina o modificare fortata a schimbarilor arhitecturale etc

Aici, metodologia Agile castiga!! - e framework adaptat pe schimbari, comparativ cu metodologia Cascada => a dezvoltat tool-uri si pattern-uri utile pentru dezvoltarea software in medii frecvent modificabile, cum ar fi:
- *test-driven development(TDD)* - metoda de dezvoltare software in care se scriu teste de automatizare inainte de inceperea procesului de dezvoltare propriu-zis, adica programarea; aceasta abordare utilizeaza cicluri de dezvoltare scurte care se repeta pentru a verifica calitatea si corectitudinea

TDD inseamna pur si simplu o metoda de codare in care mai intai scrii un test, iar acesta esueaza, apoi scrii codul pentru a trece testul de dezvoltare si curati codul; acest proces este reciclat pentru o noua functionalitate sau modificare => in loc de procesul clasic (Scrie cod -> Testeaza manual -> Repara bug-uri), TDD inverseaza complet ordinea si ghideaza designul aplicatiei prin teste

    ┌─────────────────────────────────────────┐
    │                                         │
    ▼                                         │
[ 1. RED ] ──► [ 2. GREEN ] ──► [ 3. REFACTOR ]
(Scrie test)    (Cod minim)      (Curata codul)

TDD este o tehnica in care sunt utilizate testele unitare automate si urmeaza un ciclu repetitiv numit Red-Green-Refactoring

1. RED (Rosu - Testul pica):
- scrii un test automatizat scurt pentru o functionalitate care nu exista inca
- rulezi testul; acesta trebuie sa esueze (sa fie rosu) - astfel confirmi ca testul functioneaza si verifica exact ceea ce lipseste

2. GREEN (Verde - Testul trece):
- scrii doar cantitatea minima de cod necesara pentru ca testul sa treaca (sa devina verde)
- nu iti faci griji in acest pas pentru cod elegant, performanta sau bune practici; *singurul scop este sa treci testul*

3. REFACTOR (Optimizare & Curatare):
- Cureti si reorganizezi codul scris (elimini duplicarea, imbunatatesti denumirile, aplici design patterns, abstractizezi)
- Rulezi din nou testele pentru a fi sigur ca optimizarile tale nu au stricat nimic

De fiecare data cand scriem un test nou, codul devine mai bun si mai fiabil, ceea ce face ca software-ul in ansamblu sa fie mai puternic

Abordari ale Dezvoltarii Basate pe Teste (TDD) - exista doua abordari principale ale TDD: *Inside Out* si *Outside In*:

1. *Inside Out*: se incepe prin testarea celor mai mici unitati de cod, cum ar fi functii sau metode individuale

Abordarea "Inside Out" este cunoscuta si sub numele de Detroit School of TDD sau Classicist

- se concentreaza pe testarea mai intai a celor mai mici unitati si pe construirea de acolo
- arhitectura software-ului apare natural pe masura ce testele sunt scrise
- designul si arhitectura sunt rafinate in timpul etapei de refactorizare, ceea ce poate duce uneori la schimbari semnificative
- mai usor de invatat pentru incepatori
- minimizeaza utilizarea simularilor
- ajuta la prevenirea over-engineering

2. *Outside In*: cunoscuta sub numele de London School of TDD sau Mockist, se concentreaza pe testarea comportamentului si interactiunilor utilizatorilor

- testarea incepe la nivelul cel mai exterior, cum ar fi interfata cu utilizatorul, si lucreaza spre detalii
- se bazeaza in mare masura pe mock-uri si stub-uri pentru a simula dependentele externe
- mai greu de invatat, dar asigura faptul ca codul indeplineste nevoile generale ale afacerii
- designul este luat in considerare in etapa rosie, aliniind testele cu cerintele afacerii inca de la inceput

TDD vs. Testarea Traditionala
- Abordare: *TDD* este o modalitate de a crea software in care *testele sunt scrise mai intai dupa ce este scris codul*; in *testarea traditionala*, este invers, *se creeaza mai intai codul si apoi se incepe testarea in el*

- Sfera testarii: *TDD* verifica *parti mici ale codului una cate una*; *testarea traditionala* verifica *intregul sistem*, inclusiv modul in care diferite parti functioneaza impreuna

- Iterativa: *TDD* functioneaza in *pasi mici*; se scrie un cod mic si se testeaza, apoi se imbunatateste regulat codul pana cand acesta trece toate testele necesare; *testarea traditionala* testeaza codul *o singura data* si apoi remediaza orice problema gasita

- Depanare: *TDD* va incerca sa gaseasca *greseli la inceputul procesului de codare*, ceea ce face mai usoara remedierea lor; *testarea traditionala* va gasi *greselile pentru mai tarziu*, ceea ce poate fi mai dificil de remediat in viitor

- Documentatie: *TDD* se va concentra pe *documentarea testelor si a rezultatelor acestora*; *testarea traditionala ar fi putut oferi informatii mai clare* despre modul in care a fost efectuata testarea si despre modul in care sistemul va fi testat

(source + more info: https://www.geeksforgeeks.org/software-engineering/test-driven-development-tdd/)

- refactoring - proces sistematic de imbunatatire a codului existent, fara a adauga functionalitati noi sau a modifica comportamentul extern al codului

Scopul: de a schimba implementarea, definitia si structura codului fara a schimba functionalitatea software-ului 

De ce ar trebui sa refactorizam codul nostru atunci cand functioneaza corect? - raspuns: scopul refactorizarii nu este de a adauga functionalitati noi sau de a elimina una existenta, ci de a face codul mai usor de intretinut in viitor si de a combate datoriile tehnice => facem refactorizare deoarece intelegem ca este dificil sa obtineti un design corect de la prima incercare si, de asemenea, obtineti urmatoarele beneficii in urma refactorizarii:

- dimensiunea codului este adesea redusa
- codul este restructurat intr-un cod mai simplu

Ambele beneficii de mai sus imbunatatesc considerabil mentenabilitatea, ceea ce este necesar deoarece cerintele se schimba mereu

Cand refactorizam? - raspuns: 
- inainte de a adauga noi functionalitati, intrucat trebuie sa ne asiguram ca designul si codul actual sunt "bune"
- cand trebuie remediata o eroare
- cand facem o evaluare inter pares(peer review - proces de control al calitatii prin care expertii din acelasi domeniu analizeaza o lucrare stiintifica inainte ca aceasta sa fie publicata)
- in timpul unei revizuiri de cod

Cum se identifica codul care trebuie refactorizat? - raspuns: Martin Fowler a propus utilizarea "code smells" pentru a identifica cand si unde trebuie refactorizat 

Code smells sunt lucruri negative facute in cod, lafel ca modelele negative din cod => refactorizarea si code smells sunt cateva tehnici care ne ajuta sa identificam problemele in proiectare si implementare, ajutand de asemenea la aplicarea unor solutii cunoscute la aceste probleme

Obs: exista peste 70 de tehnici de refactorizare :()

(source + more info: https://www.geeksforgeeks.org/software-engineering/refactoring-introduction-and-its-techniques/)

Majoritatea discutiilor despre aceste tehnici Agile se concentreaza la o scara locala destul de mica (cateva fisiere cu cod sursa in cadrul aceleiasi aplicatii)

De exemplu, cum ati "refactoriza" arhitectura Twitter pentru asamblarea cronologiilor de acasa de la abordarea 1 la abordarea 2? - raspuns: momentan nu am un raspuns

Usurinta cu care poti modifica un data system si sa il adaptezi la cerintele si nevoile schimbate este destul de stransa cu simplitatea si abstractizarea => sisteme simple si usor de inteles sunt de obieci mai simplu de modificat decat cele complexe

##### SUMMARY
Un sistem are cerinte:
- *functionale*(ce ar trebui sa faca, allowing data sa fie stocata, accesata, cautata, procesata)
- *nonfunctionale*(securitate, reliability, compliance, scalability, compatibility, maintainability)