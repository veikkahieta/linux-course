#h4 Maailma kuulee

##Tiivistelmä artikkelista [1](https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/):

-Vuokraa ja asenna pilvipalvelin

- Suojaa palvelin palomuurin avulla ssh-palvelimelle tehdyn reiän jälkeen

- Koneelle Apache

- Korvataan olemassaoleva testisivu

- Kokeile toimivuus eri laitteella, esim. puhelin

- Kotisivut normaalina käyttäjänä public_html/ alle

- Päivitä palvelimen ohjelmat

##Tiivistelmä artikkelista [2](https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/):

- Aina vahvat salasanat

- Luodaan uusi virtuaalipalvelin

- Datakeskus mahdollisimman lähelle käyttäjiä (Eurooppaan)

- Kirjaudutaan ainoastaan ensimmäisellä kerralla root-käyttäjänä, vaihdetaan salasana

- Tehdään reikä SSH-palvelimelle ennen palomuurin aktivoimista

- Luodaan oma käyttäjä ja lisätään se sudo-ryhmään

- Testataan kirjautuminen uudella käyttäjällä

- Lukitaan root sekä estetään root-kirjautuminen SSH:ssa

- päivitetään ohjelmistot (apt-get update, apt-get upgrade)

- Kun asennetaan palveluita, kuten Apahce, avataan vastaava portti palomuurissa

- IP-osoitteen sijaan on kätevämpää käyttää verkkotunnusta


##Virtuaalipalvelimen vuokraaminen sekä asennus


Vuokrasin virtuaalipalvelimen GitHub Educationin avulla DigitalOceanilta. Valitsin virtuaalipalvelimen käyttöjärjestelmäksi Debian 13. Valitsin tavallisen prosessorin SSD:llä, ja prosessorin kooksi valitsin 1GB sekä kovalevyn kooksi 25GB. Tämä oli toiseksi halvin vaihtoehto, jonka valitsin koska epäilin halvimman vaihtoehdon olevan mahdollisesti liian heikko spekseiltään.
Kuvakaappaus:
<img width="1879" height="1014" alt="image" src="https://github.com/user-attachments/assets/d860a6ee-ac04-4e5f-8083-d1c65e37f76d" />

Valitsin Authenticationiksi salasanan ja loinkin todella vahvan salasanan, jota en käytä missään muualla. Asetin hostnameksi "veikkah".


Seuraavana siirryin tekemään alkutoimet virtuaalikoneelleni. Pääsin sisään, mutta jouduin välissä poistamaan aiemman palvelimen ja tekemään uuden, todennäköisesti aiemmassa palvelimessa oli jäänyt SSH päälle, vaikka valitsin salasanan.
Kuvakaappaus:
<img width="1264" height="868" alt="image" src="https://github.com/user-attachments/assets/730553fb-de94-4634-94ee-778de45d20a8" />

Seuraavana asennetaan palomuuri 'sudo apt-get install ufw', tehdään siihen reikä 'sudo ufw allow 22/tcp' sekä laitetaan se päälle 'sudo ufw enable'. [2](https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/)
Kuvakaappaus:
<img width="1090" height="729" alt="image" src="https://github.com/user-attachments/assets/0eb5e5af-44ef-4e85-b6dd-57c769085d47" />

Seuraavana loin käyttäjän. Laitoin koko nimeksi "veikka"  ja muut kentät jätin tyhjäksi.
Kuvakaappaus:
<img width="803" height="463" alt="image" src="https://github.com/user-attachments/assets/ca7d7082-22c9-41e0-95da-b129b49e7d83" />

Tämän jälkeen annoin käyttäjälle oikeuksia 'sudo adduser veikka sudo' 'sudo adduser veikka adm' 'sudo adduser veikka admin'. Näistä viimeistä ei ole olemassa (admin). [2](https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/)
Kuvakaappaus:
<img width="809" height="505" alt="image" src="https://github.com/user-attachments/assets/70ad1925-f812-4493-a604-59f1d5b9ffd5" />

Ajoin virtuaalikoneelle rebootin 'reboot', jonka jälkeen ajoin 'apt-get update' sekä esimerkiksi 'whoami' -komennot.
Kuvakaappaus:
<img width="1266" height="872" alt="image" src="https://github.com/user-attachments/assets/0828f53d-cbb8-4f89-9f31-7a2b67b51410" />

Seuraavana suljin rootin SSH-yhteyden. Jotta root-salasana saadaan pois, täytyy käyttää 'sudo usermod --lock root' -komentoa. Tämän jälkeen menin 'sudoedit /etc/ssh/sshd_config' -konfiguraatiotiedostoon, ja muutin "PermitRootLogin" -kohdan pois päältä, eli "no".
Kuvakaappaukset:
<img width="489" height="90" alt="image" src="https://github.com/user-attachments/assets/5a942977-7d83-4444-8931-3c3e462900bd" />
<img width="191" height="114" alt="image" src="https://github.com/user-attachments/assets/450a64be-808c-40c9-8b12-904361f3f896" />

Seuraavaksi ajoin komennot 'sudo apt-getupdate', 'sudo+ apt-get upgrade' sekä 'sudo apt-get dist-upgrade'.

Latasin Apachen komennolla 'sudo apt-get install apache2. Tämän jälkeen tarkistin Apachen tilan.
Kuvakaappaus:
<img width="794" height="471" alt="image" src="https://github.com/user-attachments/assets/69695985-83b1-4a3d-ba92-566a9fafb9f7" />

Tein reiän palomuuriin: [2](https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/)
<img width="797" height="90" alt="image" src="https://github.com/user-attachments/assets/8901a2c9-025f-4885-9af6-ae29bb8e5769" />

Ajoin seuraavat komennot: 'echo Testi|sudo tee /var/www/html/index.html' sekä 'sudo systectl restart apache2'.
Tämän jälkeen testasin avata sivun puhelimella Safarissa, sekä Windowsilla. Sivulla lukee nyt "Testi".
Kuvakaappaus:
<img width="348" height="87" alt="image" src="https://github.com/user-attachments/assets/c00e1b07-a32a-4800-914e-df3a1882f14f" />

##Lähteet
Lehto, Susanna 2022: Teriasta käytäntöön pilvipalvelimen avulla [1]:
https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/

Karvinen, Tero 2012: First Steps on a New Virtual Private Server - an Example on DigitalOcean and Ubuntu 16.04 LTS [2]:
https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/
