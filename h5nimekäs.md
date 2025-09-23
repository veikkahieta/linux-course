<h1>h5 Nimekäs</h1>

Tilasin domainin veikkah.live name.comista, koska sen sai ilmaiseksi GitHub Educationin kautta. Lisäsin A-tietueet.
Kuvakaappaus:
<img width="1266" height="510" alt="image" src="https://github.com/user-attachments/assets/975be0cf-6469-4754-a443-412a6361a26e" />
Loin hakemiston sivustolle 'sudo mkdir -p /var/www/veikkah.live/public_html' ja 'sudo chown -R veikka:veikka /var/www/veikkah.live/public_html' -komennoilla.
Kuvakaappaus:
<img width="800" height="134" alt="image" src="https://github.com/user-attachments/assets/ed4afd3a-160f-4042-9da2-3d067966b993" />

Loin VirtualHost-konfiguraatiotiedoston, jonka sisältö oli seuraavanlainen: 
'<VirtualHost *:80>
    ServerName domainisi.fi
    ServerAlias www.domainisi.fi
    DocumentRoot /var/www/domainisi.fi/public_html

  <Directory /var/www/domainisi.fi/public_html>
  Options Indexes FollowSymLinks
  AllowOverride All
  Require all granted
  </Directory>

  ErrorLog ${APACHE_LOG_DIR}/domainisi.fi-error.log
  CustomLog ${APACHE_LOG_DIR}/domainisi.fi-access.log combined
</VirtualHost>'

Seuraavaksi otin uuden sivuston käyttöön komennoilla 'sudo a2ensite veikkah.live.conf' ja 'systemctl reload apache2'.
Sivu toimii nyt domainilla veikkah.live ja sanoo "Testi".
Kuvakaappaus:
<img width="330" height="108" alt="image" src="https://github.com/user-attachments/assets/02afacd0-9de7-4ee8-9c97-115d0452b66a" />

Lisäsin kaksi alidomainia, testi.veikkah.live sekä toinen.veikkah.live osoittamaan samaan, kuin päädomain.
Kuvakaappaus:
<img width="1268" height="138" alt="image" src="https://github.com/user-attachments/assets/1b918395-18da-4932-93c7-610d7580bc6d" />

Tein alidomaneille samanlaiset .conf-tiedostot ja otin sivut käyttöön a2ensite -komennolla. sivut osoittavat nyt samaan, kuin päädomain veikkah.live.
Kuvakaappaus:
<img width="364" height="108" alt="image" src="https://github.com/user-attachments/assets/ace49c0b-96dd-4740-8b1a-c6efbb357113" />
<img width="354" height="138" alt="image" src="https://github.com/user-attachments/assets/d8594748-c1ef-4569-b0c0-9859ae8f9746" />


<h2> Tutki jonkin nimen DNS-tietoja 'host' ja 'dig' -komennoilla:</h2>

host-komento kuuluu Debianissa pakettiin dnsutils, joten latasin sen komennolla sudo apt 'install dnsutils -y', jotta voin käyttää host-komentoa.

host kertoo IP-osoitteen. Juuri luomillani sivuilla IP-osoite on alidomaineissa sama kuin päädomainissa. Dig-komennolla 'dig veikkah-live' 

Kuvakaappaukset:
<img width="496" height="138" alt="image" src="https://github.com/user-attachments/assets/a2c187cb-38d6-4a3b-b919-5bdebc2a76a3" />
<img width="800" height="702" alt="image" src="https://github.com/user-attachments/assets/f0b068fd-28d0-43ac-b205-7061cd8cd194" />

Verratessa veikkah.live ja name.com tulokset ovat samankaltaisia. A-tietueissa siis samat IP-osoitteet. Prioriteetit N/A eli ei ole.
Ajoin dig-komennon myös microsoft.comille sekä paljekirppis.fille:
<img width="690" height="378" alt="image" src="https://github.com/user-attachments/assets/8630d244-ab6c-463d-8b90-0caf824582bb" />

<img width="704" height="404" alt="image" src="https://github.com/user-attachments/assets/a2953b32-889c-4747-aeb7-db476cd5176c" />



Lähteet:

https://terokarvinen.com/linux-palvelimet/
Kysytty ChatGPT:ltä "Miksi "host: commant not found". Vastaukseksi saatiin Aha, tuo kertoo, että host-komentoa ei ole asennettu Debian 13 -palvelimellasi.
host kuuluu pakettiin nimeltä bind-utils tai Debianissa tarkemmin dnsutils."



