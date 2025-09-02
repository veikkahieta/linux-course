<h1>h2 Komentaja pingviini</h1>

Tiivistelmä Command line basics revisited:

- pwd: nykyinen hakemisto
- ls: listaa tiedostot
- cd nimi/: siirry hakemistoon, cd .. siirtää ylähakemistoon.
- less tiedosto: selaa tiedostoa sivu kerrallaan.
- komento | less: putkitus selattavaksi.

- nano-tiedosto: tekstieditori.
- mkdir: luo hakemisto.
- mv: siirrä/nimeä
- cp -r: kopioi tiedosto tai hakemisto, rmdir poistaa tyhjän hakemiston.
- rm: poista tiedosto tai hakemisto. Ei roskakoria.

- ssh käyttäjä@palvelin: kirjautuminen etäkoneelle, exit=poistu
- scp -r kansio käyttäjä@palvelin:polku/: kopioi etäkoneelle

- man: manuaali, --help, tab täydentää, nuolinäppäimet, history, ctrl+R: haku historiasta.

- /: juurihakewmisto
- /home/: käyttäjän kotihakemistot
- /etc/: järjestelmän asetukset
- /media/: irtolaitteet (esim. /media/usbdisk/)
- var/log/: lokitiedostot

- sudo apt-get update: päivitä listaus paketeista
- apt-cache search hakusana: pakettien etsimiseen
- sudo atp-get install paketti: ohjelman asentamiseen
- dpkg --listfiles paketti: kertoo mitä asennettiin
- sudo apt-get purge paketti: ohjelman poistamiseen, asetukset





Asensin micron jälkeen cbonsain, cmusin ja emacsin. Jokainen oli minulle uusi ja asensin ne erikseen. Tiedän myös apt-get -komennon, jolla olisin voinut asentaa halutessani kaikki ohjelmat samalla kerralla.

Kuvakaappaus micro: <img width="1269" height="872" alt="image" src="https://github.com/user-attachments/assets/32697969-bba3-4fe6-8da8-1258bc46446c" />

Kuvakaappaus cbonsai: <img width="1273" height="876" alt="image" src="https://github.com/user-attachments/assets/4ea3afbe-9b29-4566-9bfc-0808093dd1a1" />

Kuvakaappaus cmus: <img width="1262" height="869" alt="image" src="https://github.com/user-attachments/assets/43723c8a-fcd7-47e8-a7ce-c6bad31ab7b0" />

Kuvakaappaus emacs: <img width="1265" height="873" alt="image" src="https://github.com/user-attachments/assets/ca85849f-8397-4d32-b396-621cee4a1f6c" />



ls /: <img width="818" height="503" alt="image" src="https://github.com/user-attachments/assets/e15b484b-b3d8-48e1-9c90-da7ce2d1009a" />

ls /home/: <img width="1266" height="871" alt="image" src="https://github.com/user-attachments/assets/f5e42c81-ab84-4c53-b31b-9f2aed43dfa0" />

ls /home/käyttäjä/: <img width="1273" height="877" alt="image" src="https://github.com/user-attachments/assets/d2258134-dba9-437b-9752-621c79c52f4b" />

ls /etc/: <img width="1258" height="784" alt="image" src="https://github.com/user-attachments/assets/ce1365f9-d2f9-4c84-8588-02d84a69fbac" />

ls /media/: <img width="1268" height="874" alt="image" src="https://github.com/user-attachments/assets/e87b8bd6-4758-4e2d-88e6-5a058f35ecd4" />

ls/var/log/: <img width="1274" height="876" alt="image" src="https://github.com/user-attachments/assets/f65d8851-d1e0-480f-96d6-bbd18a741836" />

cd /etc/ssh/: <img width="1269" height="870" alt="image" src="https://github.com/user-attachments/assets/628633e2-13b2-4af6-9710-03cc09a70baf" />


Esimerkit grep-komennosta:

1. grep root /etc/passwd etsii kaikki rivit, joissa esiintyy sana "root".

Kuvakaappaus: <img width="1266" height="872" alt="image" src="https://github.com/user-attachments/assets/59c43c74-e111-412d-af5c-88cc2a306ac3" />


2. Laskee montako riviä sisältää sanan "sshd". Tässä tapauksessa 0.

<img width="1263" height="872" alt="image" src="https://github.com/user-attachments/assets/630b8557-be1a-441f-aac0-38a7ebe9b985" />


3. grep -r bash /etc etsii kaikki sanan "bash" sisältävät tiedostot kohteessa /etc.

<img width="1265" height="875" alt="image" src="https://github.com/user-attachments/assets/c2230e63-9326-4d76-97ec-f1706616e554" />



Esimerkki putkista (|):

ls /bin | grep sh listaa kaikki /bin -hakemiston tiedostot, joiden nimessä esiintyy "sh".
ls listaa tiedostot ja grep sh suodattaa tiedostoista näkyviin ainoastaan ne, joiden nimessä on "sh".

<img width="1266" height="867" alt="image" src="https://github.com/user-attachments/assets/b6647d59-abbd-4f4a-81f2-75f41d0c6376" />



Koneen raudan listaus:

sudo lshw -short -sanitize kuvakaappaus: <img width="1268" height="871" alt="image" src="https://github.com/user-attachments/assets/cb353bf0-a9b8-4bfe-a547-84f9bbc02112" />

H/W path kertoo päätelmieni mukaan laitteiden sijainnista laitehierarkiassa. Device-osiossa kerrotaan jokaisen laitteen tunnukset, mikäli sellaisia on ja class kertoo minkälainen laite on kyseessä (esim. processor). Description on kuvaus laitteesta.
Listauksessa kerrotaan prosessorin ytimien määrä, RAM-muistin ja kampojen määrä sekä esimerkiksi levyn koko ja liitäntä. Koneessa on prosessorina Intel Core i5-7300HQ kahdella ytimellä.


Lähteet:

Karvinen, Tero 2020: Command Line Basics Revisited Linkki: https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited

Heinonen Johanna 2025: Linux Commands Linkki: https://github.com/johannaheinonen/johanna-test-repo/blob/main/linux-27082925.md
