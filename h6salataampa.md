<h1>h6 Salataampa</h1>
<h2>Tiivistykset artikkeleista:</h2>
<h3>How it Works - Let's Encrypt</h3>

- ACME client todistaa domainin hallinnan CA:lle
- Asiakas voi hallita sertiikaatteja (pyytää, uusia tai peruuttaa)
- Asiakkaan tunnistaminen tapahtuu julkisen avaimen perusteella
- CA:n haasteita DNS-tietueen lisääöminen tai HTTP-resurssin lisääminen
- Client toteuttaa yhden annetuista haasteista ja ilmoittaa valmiudestaan
- Hyväksynnän jälkeen client valtuutetaan domainin sertifikaattien hallinnoijaksi
- client luo Certificate Signing Requestin (sisältää domainin, julkisen avaimen)
- CSR signataan tilin avaimella sekä domainin avaimella
- CA tarkistaa ja sen jälkeen myöntää sertifikaatin
- CA myös lisää sertifikaatin julkisiin CT-lokeihin
- Peruutus: client signaa peruutuspyynnön tilin avaimella
- CA tarkistaa peruutuspyynnön sekä julkaisee tiedon CRL-listoihin
[3]https://letsencrypt.org/how-it-works/

<h3>Apache - SSL/TLS Strong Encryption: How-To</h3>

LoadModule ssl_module modules/mod_ssl.so

Listen 443
<VirtualHost *:443>
    ServerName www.example.com
    SSLEngine on
    SSLCertificateFile "/path/to/www.example.com.cert"
    SSLCertificateKeyFile "/path/to/www.example.com.key"
</VirtualHost>
[2]

<h2>A-tehtävä, Let's</h2>
Avasin virtaalikoneen ja potkaisin demonia. Testasin ensin nettisivuni toimivuuden. Nettisivu toimi. Avasin myös http eli 80/tcp sekä https eli 443/tcp. [1]
Kuvakaappaukset:
<img width="344" height="104" alt="image" src="https://github.com/user-attachments/assets/e4cd1209-cba5-48b0-9e96-5a3470f8a314" />
<img width="318" height="102" alt="image" src="https://github.com/user-attachments/assets/18919a2c-b77c-4349-94b6-32527d803c4f" />
<h2>Seuraavaksi hankitaan ja asennetaan TLS-sertifikaatti Let's Encryptiltä:</h2>
Asensin Certbotin komennolla 'sudo apt-get install certbot python3-certbot-apache'.
Kuvakaappaus:
<img width="754" height="116" alt="image" src="https://github.com/user-attachments/assets/f28b3ab4-c335-40db-a5a7-d782adcc83be" />
Ajoin komennon 'sudo certbot --apache --domains veikkah.live,www.veikkah.live', ja jotain meni pieleen. Vastaus oli seuraava:
<img width="1122" height="400" alt="image" src="https://github.com/user-attachments/assets/5142d902-f9b6-460d-900a-5849ca223a0c" />
Testasin useita eri vaihtoehtoja ChatGPT:n avulla ja yritin etsiä ongelmaa 'sudo less /var/log/letsencrypt/letsencrypt.log' -komennolla tuloksetta.
Testasin vielä kertaalleen tarkistaa, pystyykö Apache palvelemaan tiedostoja polusta komennoilla 'sudo mkdir -p /var/www/html/.well-known/acme-challenge'
'echo "test" | sudo tee /var/www/html/.well-known/acme-challenge/test.txt'

Curl kuitenkin edelleen sanoo 404:
<img width="964" height="224" alt="image" src="https://github.com/user-attachments/assets/b3fb57f3-0039-4d49-81b9-f3294e728474" />
Tässä vaiheessa aika tehtävän suorittamiwseen loppui kesken. Muokkaan raporttia, kun ongelma on saatu ratkaistua.

SSL Labs tulos oli odotetunlainen:
<img width="1106" height="284" alt="image" src="https://github.com/user-attachments/assets/6d45ee43-06e1-4c1d-825a-7a9a6f3409dd" />

<h2>Lisäys:</h2>
Lisäyksenä: Asensin Snap-kokonaisuuden ja yritin aktivoida Certbotin sitä kautta.
Vastaus oli kuitenkin sama, kuin aiemminkin:
Kuvakaappaus:
<img width="1178" height="64" alt="image" src="https://github.com/user-attachments/assets/bdab80eb-a720-4a82-a8c6-7b66f57481fa" />


<h2>Lähteet:</h2>

Karvinen, Tero 2025: Linux Palvelimet 2025 alkusyksy: https://terokarvinen.com/linux-palvelimet/#aikataulu [1]
Apache 2025: SSL_TLS Strong Encryption: How-To: https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html#configexample [2]
Let's Encrypt 2025: https://letsencrypt.org/how-it-works/ [3]
ChatGPT:ltä kysytty "Miten asennan ja otan käyttöön TLS-sertifikaatin Let's Encryptiltä debian 13 virtuaalikoneelleni (apache)". Vastaus ei ollut hyödyllinen tehtävää varten.

