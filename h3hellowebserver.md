<h1>h3 Hello web server</h1>

<h2>Tiivistys artikkelista The Apache Software Foundation 2023: Apache HTTP Server Version 2.4 Documentation: Name-based Virtual Host Support [1]:</h2>


- IP-pohjaiset virtuaalipalvelimet vaativat eri IP-osoitteet jokaiselle sivustolle

- Nimiin perustuva tapa suositeltavampaa, koska se on helpompaa konfiguroida ja säästää IP-osoitteita

- Jos samalla IP-osoitteella ja portilla on useita virtuaalipalvelimia, tarkistetaan ServerName ja ServerAlias

- Tärkeää on määrittää ServerName

- Jokaiselle sivustolle määritetään oma VirtualHost-lohko

- Kannattaa aina tehdä default vhost ensimmäisenä

- DNS täytyy olla konfiguroitu, jotta nimet osoittaa palvelimen IP:hen


<h2>Tiivistys artikkelista Name based Virtual Hosts on Apache - Multiple Websites to Single IP Address [2]:</h2>

- Yhdellä IP-osoitteella voi palvella useita verkkotunnuksia, kuten terokarvinen.com, botbook.com. Tämä tapahtuu nimiin perustuvilla virtuaalipalvelimilla Apachella.

- Asennus ja oletussivu: sudo apt-get -y install apache2, echo "default" | sudo tee /var/www/html/index.html

- Uuden konfiguraatiotiedoston luominen /etc/apache2/sites-available/pyora.example.com.conf

- Käyttöönotto ja restart: sudo a2ensite pyora.example.com, sudo systemctl restart apache2

- Sivun luo+minen normaalikäyttäjänä: mkdir -p /home/xubuntu/publicsites/pyora.example.com/, ECHO pyora > /home/xubuntu/publicsites/pyora.example.com/index.html

- Testaus curl -H 'Host: pyora.example.com' localhost, curl localhost

- Firefoxilla http://localhost, http://pyora.example.com




Avasin virtuaalikoneen ja asensin Apachen komennolla "sudo apt-get update" ja "sudo apt-get install -y apache2". Vaihdoin myös oletuksena olevan weppisivun komennolla "echo "Default"|sudo tee /var/www/html/index.html".

Kuvakaappaukset: 
<img width="823" height="75" alt="image" src="https://github.com/user-attachments/assets/85957411-1388-425e-aa44-32d5b223c160" />
<img width="826" height="353" alt="image" src="https://github.com/user-attachments/assets/078259a3-1023-4740-bec3-43076446092b" />

Testasin, että weppipalvelimeni vastaa localhost-osoitetta, selaimella http://localhost sekä terminaalissa "curl localhost" -komennolla.
kuvakaappaukset: 
<img width="850" height="578" alt="image" src="https://github.com/user-attachments/assets/9d0d29c1-8121-402a-a88e-972f3385e1ed" />
<img width="1253" height="777" alt="image" src="https://github.com/user-attachments/assets/52031d3e-f652-4884-8fbf-ba982e0f911c" />

Avasin access.login, ja päättelin lokissa näkyvästä kellonajasta, että alin rivi tuli viimeisimmän curlin seurauksena.
Rivin alussa (: :1) kerrotaan IPv6-osoite (IPv4:ssä 127.0.0.1). Ensimmäinen - viittaa siihen, että Apache voisi käyttää ident-protokollaa kysyäkseen käyttäjän identiteettiä, mutta sitä ei käytetä. Toinen - viittaa siihen, että kirjautumista ei ole tapahtunut. [3]
Seuraavana lokirivillä kerrotaan tapahtuman ajankohta sekä aikavyöhyke. "GET / HTTP/1.1" tarkoittaa, että client on pyytänyt palvelimelta juurisivua GET-metodilla ja HTTP/1.1 -protokollalla. Seuraavana ilmoitettu 200 233 tarkoittaa, että pyyntö onnistui ja palvelin on lähettänyt 2333 tavua takaisin. 200 233 kertoo siis statuksen. [3]
"-" kertoo, mikä oli HTTP-pyynnön Referer-headerin arvo, eli miltä sivulta käyttäjä on tullut. Tässä tapauksessa pyyntö on siis tullut suoraan, eikä linkin kautta. [3]
Viimeisenä rivillä oleva "curl/8.14.1" kertoo, mikä ohjelma tai selain pyynnön on tehnyt. Pyyntö tehtiin siis curl-ohjelmalla jonka versio on tässä tapauksessa 8.14.1.
Kuvakaappaus: 
<img width="810" height="461" alt="image" src="https://github.com/user-attachments/assets/510df402-3bbb-4aa8-b55f-2d341437ef3f" />



Tein uuden name based virtual hostin, jonka nimi on hattu.example.com. Tein tarvittavat konfiguraatiot ja poistin aiemmat palvelimet käytöstä a2dissite-komennolla. Sivu kuitenkin avautuessaan ilmoitti "Forbidden". ALoitin alusta ja tein kaiken uudelleen erityisellä tarkkuudell, mutta en valitettavasti onnistunut muuttamaan lopputulosta.
Reloadasin myös apachen useampaan otteeseen, mutta sekään ei auttanut. 
Kuvakaappaukset: 
<img width="1266" height="858" alt="image" src="https://github.com/user-attachments/assets/3abdf4fb-fd59-417f-a194-3c0773585ffe" />
<img width="1267" height="868" alt="image" src="https://github.com/user-attachments/assets/72ec5bbe-3bb4-4152-81d7-b3ded9014b29" />

Lopulta huomasin, että <Directory> sekä DocumentRoot osoittivat väärään paikkaan nano-tiedostossa, käytännössä kyseessä oli siis kirjoitusvirhe. Nyt sivu toimii oikealla tavalla.
Kuvakaappaukset:
<img width="1272" height="897" alt="image" src="https://github.com/user-attachments/assets/822d585b-ebd7-4a90-aaaf-66cb9b1f9996" />
<img width="1277" height="900" alt="image" src="https://github.com/user-attachments/assets/bea2ef77-5329-47b7-949a-739e79b3e7fe" />
<img width="815" height="546" alt="image" src="https://github.com/user-attachments/assets/a9d249c5-1d7e-49fd-8521-0efa9120b2b5" />
(validi HTML5-sivu)


Curl-komennolla voi hakea hakea verkkosivun sisältöä. Esimerkiksi komento "curl http://localhost/" näyttää terminaalissa sivun sisällön, kuten ylempänä kuvassa. Curl -I hakee ainoastaan http-protokollan response headerit.
Kuvakaappaus:
<img width="1261" height="897" alt="image" src="https://github.com/user-attachments/assets/851b36b4-556f-4da4-bdc0-756d113098ae" />
Curl -I -komennon tuottamat otsakkeet kertovat esimerkiksi, että palvelin on vastannut onnistuneesti (ensimmäinen rivi, HTTP/1.1 200 OK) sekä palvelimen vastajan (toinen rivi, Date). Otsakkeissa kerrotaan myös mikä ohjelmisto vastasi (Apache/2.4.65) sekä ETagin, joka on tunniste tiedoston versiolle. Otsakkeissa ilmoitetaan myös vastauksen bodyn koko tavuina sekä että sisältö on html-tekstiä.


<h2>Lähteet:</h2>

The Apache Software Foundation 2023: Apache HTTP Server Version 2.4 Documentation: Name-based Virtual Host Support: https://httpd.apache.org/docs/2.4/vhosts/name-based.html [1]

Karvinen, Tero 2018: Name based Virtual Hosts on Apache - Multiple Websites to Single IP Address: https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/ [2]

https://stackoverflow.com/questions/9234699/understanding-apaches-access-log [3]



