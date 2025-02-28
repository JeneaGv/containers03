# Utilizarea containerelor ca medii de execuție

# Scop

Această lucrare de laborator are ca scop familiarizarea cu comenzile de bază ale OS Debian/Ubuntu. De asemenea, aceasta va permite să vă familiarizați cu Docker și comenzile sale de bază.

# Sarcina

Pornind de la imaginea oficială a sistemului de operare Ubuntu, să se creeze un container care să conțină un server web Apache. Să se creeze o pagină web care să conțină textul "Hello, World!" și să se afișeze într-un browser.

# Executare

-Intram pe GitHub si cream repozitoriu nou
-Clonam acesta cu ajutorul git clone URL
-Urmeaza pornirea si testarea 
1.Deschidem terminalul si schimbam directorul curent pe cel creat(prin clonare) si executam comanda

docker run -ti -p 8000:80 --name containers03 ubuntu bash 

Astfel rulam un container bazat pe imaginea ubuntu(O descarcam din depozitor)
Expunem portul 80 din container pe portul 8000 a gazdei 
Deschidem terminalul Bash pentru a executa comenzile in container 

![image](https://github.com/user-attachments/assets/86fdf4dd-9d5d-48e2-b039-e73619f0f41b)

2.In fereastra deschisa executam urmatoarele comenzi 

apt update -actualizam lista de pachete disponibile în sistemul de gestionare a pachetelor APT (Advanced Package Tool) utilizat în distribuțiile Debian și Ubuntu.

![image](https://github.com/user-attachments/assets/4be44490-a0b1-4fc2-88ad-dd3513ee8643)

apt install apache2 -y -instalam serverul web Apache2,-y confirma automat instalarea evitand intrebarile de confirmare 

![image](https://github.com/user-attachments/assets/5047fbc1-cfa5-4570-95ee-d5935c3434f0)

service apache2 start -pornim serviciul Apache2

![image](https://github.com/user-attachments/assets/badd523b-1c96-4dab-aa51-df4aa80ceff7)

Deschidem browserul si plasam http://localhost:8000 in bara de adrese 

Observam pagina implicita 

![image](https://github.com/user-attachments/assets/6d237e4e-6269-48e5-9851-153d17d210a6)

Executam următoarele comenzi:

ls -l /var/www/html/ 

observam existenta fisierului index.html ce ocupa 12KB memorie si are anumite drepturi de acces 

Pentru proprietar(root) de scriere si citire

Pentru Grupa(root) de citire

Pentru alti utilizatori de citire 

![image](https://github.com/user-attachments/assets/18d573b2-d469-45c7-a11c-c9dcd757a061)

echo '<h1>Hello, World!</h1>' > /var/www/html/index.html

pentru a afisa rezultatul comenzii in fisierului index.html(va fi afisat Hello, World! ca titlu de nivelul 1(Cel mai mare) )

![image](https://github.com/user-attachments/assets/269d109e-24bd-422a-bd1e-3064b3305780)

Schimbam directorul curent  cu ajutorul comenzii:

cd /etc/apache2/sites-enabled/

Afisam continutul fisierului 000-default.conf cu ajutorul comenzii :

cat 000-default.conf

observam urmatorul continut 

![image](https://github.com/user-attachments/assets/bb0e1f4b-423f-42ca-ab2e-821e5e0170d3)

Observam configurația implicită a Apache pentru site-ul web pe portul 80, 

cu directorul rădăcină /var/www/html, log-urile setate în /var/log/apache2/, 

și câteva directive comentate ce pot fi activate la nevoie

Folosim comanda docker ps -a pentru a vizualiza toate conainerele inclusiv cele oprite 

![image](https://github.com/user-attachments/assets/f0f2ba3d-0dd9-4c87-9edd-993d8d26ba05)

Stergem containerul containers03 cu ajutorul comenzii docker rm containers03 
