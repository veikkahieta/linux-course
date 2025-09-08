




Avasin virtuaalikoneen ja asensin Apachen komennolla "sudo apt-get update" ja "sudo apt-get install -y apache2". Vaihdoin myös oletuksena olevan weppisivun komennolla "echo "Default"|sudo tee /var/www/html/index.html".

Kuvakaappaukset: <img width="823" height="75" alt="image" src="https://github.com/user-attachments/assets/85957411-1388-425e-aa44-32d5b223c160" />
<img width="826" height="353" alt="image" src="https://github.com/user-attachments/assets/078259a3-1023-4740-bec3-43076446092b" />

Testasin, että weppipalvelimeni vastaa localhost-osoitetta, selaimella http://localhost sekä terminaalissa "curl localhost" -komennolla.
kuvakaappaukset: <img width="850" height="578" alt="image" src="https://github.com/user-attachments/assets/9d0d29c1-8121-402a-a88e-972f3385e1ed" />
<img width="1253" height="777" alt="image" src="https://github.com/user-attachments/assets/52031d3e-f652-4884-8fbf-ba982e0f911c" />

Avasin access.login, ja päättelin lokissa näkyvästä kellonajasta, että alin rivi tuli viimeisimmän curlin seurauksena.
Rivin alussa (: :1) kerrotaan IPv6-osoite (IPv4:ssä 127.0.0.1). Ensimmäinen - viittaa siihen, että Apache voisi käyttää ident-protokollaa kysyäkseen käyttäjän identiteettiä, mutta sitä ei käytetä. Toinen - viittaa siihen, että kirjautumista ei ole tapahtunut.
Seuraavana lokirivillä kerrotaan tapahtuman ajankohta sekä aikavyöhyke. "GET / HTTP/1.1" tarkoittaa, että client on pyytänyt palvelimelta juurisivua GET-metodilla ja HTTP/1.1 -protokollalla. Seuraavana ilmoitettu 200 233 tarkoittaa, että pyyntö onnistui ja palvelin on lähettänyt 2333 tavua takaisin. 200 233 kertoo siis statuksen.
"-" kertoo, mikä oli HTTP-pyynnön Referer-headerin arvo, eli miltä sivulta käyttäjä on tullut. Tässä tapauksessa pyyntö on siis tullut suoraan, eikä linkin kautta.
Viimeisenä rivillä oleva "curl/8.14.1" kertoo, mikä ohjelma tai selain pyynnön on tehnyt. Pyyntö tehtiin siis curl-ohjelmalla jonka versio on tässä tapauksessa 8.14.1.
Kuvakaappaus: <img width="810" height="461" alt="image" src="https://github.com/user-attachments/assets/510df402-3bbb-4aa8-b55f-2d341437ef3f" />



Tein uuden name based virtual hostin, jonka nimi on hattu.example.com. Tein tarvittavat konfiguraatiot ja poistin aiemmat palvelimet käytöstä. Sivu kuitenkin avautuessaan ilmoitti "Forbidden". ALoitin alusta ja tein kaiken uudelleen erityisellä tarkkuudell, mutta en valitettavasti onnistunut muuttamaan lopputulosta.
Reloadasin myös apachen useampaan otteeseen, mutta sekään ei auttanut. 
Kuvakaappaukset: <img width="1266" height="858" alt="image" src="https://github.com/user-attachments/assets/3abdf4fb-fd59-417f-a194-3c0773585ffe" />
<img width="1267" height="868" alt="image" src="https://github.com/user-attachments/assets/72ec5bbe-3bb4-4152-81d7-b3ded9014b29" />









