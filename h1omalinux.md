# h1 Oma Linux

## Raportin kirjoittaminen

- Raportin kirjoittamisen ohjeet ovat pätevät jokaiseen teknisten testien toteutusympäristöön. [2]

- Raporttia kirjoitetaan jatkuvasti samalla, kun testejä toteutetaan. [2]

- Raportin tulee olla täsmällinen ja yksityiskohtainen. [2]

- Raporttia voi hyödyntää pohjana ohjeita laatiessa.  [2]

- Myös ympäristön raportoiminen on tärkeää. [2]

- Esimerkiksi kellonajan kertominen voi olla ratkaisevaa, mikäli myöhemmin ilmenee laajempia verkon laajuisia ongelmia. [2]

- Raportoi kaikki odotetut ja odottamattomat tulokset ylös. Mahdolliset ongelmat on myös hyvä tiedostaa. [2]

- Käytä väliotsikoita ja oikeanlaista kieltä. [2]

- Loppuun voi kirjoittaa tiivistelmän. [2]

- Viittaa lähteisiin selkeästi. [2]

- Kirjoita tekstisi itse ja käytä ainoastaan luvallisia kuvia. [2]

- Ilmoita aina lähteet. [2]




# Linuxin asennus virtuaalikoneelle

Tein harjoituksen kotonani 25.8.2025 17.30 käyttäen kotonani olevaa pöytätietokonetta (Windows).

17.32: Avasin Oracle VirtuualBox Manager -sovelluksen ja lisäsin uuden virtuaalikoneen. Virtuaalikonetiedoston (test-debian-live-13.0.0-amd64-xfce.iso) [1].

17.39: Tarkistin arvojen olevan samat, kuin artikkelissa [1] mainitut. Virtuaalikone on luotu 2048 Mt välimuistilla, kahdella prosessorilla sekä 20 Gt tallennustilalla, kuten artikkelissa [1] viitearvoiksi mainitaan.
Tässä näyttökuva: <img width="1115" height="694" alt="image" src="https://github.com/user-attachments/assets/97901f90-8c9e-45b0-8f40-954e83b64117" />

17.46: Käynnistin virtuaalikoneen ja valitsin artikkelin [1] mukaisesti Live System (amd64).

17.57: Testasin internetin toimivuuden käynnistämällä Mozilla  Firefox -sovelluksen ja hakemalla Google -hakukoneella "iltalehti". Tämä onnistui. Testasin myös komentorivillä komentoja ls ja cd, nämä toimivat.
Tässä näyttökuvat: <img width="1917" height="1077" alt="image" src="https://github.com/user-attachments/assets/576a29f3-eeed-42c5-b59f-c7df14494f69" />
<img width="1259" height="855" alt="image" src="https://github.com/user-attachments/assets/72b76ec9-90c3-43e3-b3d3-b3405576c1ab" />

18.02: Käynnistin järjestelmän uudelleen komennolla "sudo reboot", kuten artikkelissa [1] ohjeistetaan. Tämän jälkeen VirtualBox antoi virheilmoituksen bootauksen epäonnistumisesta. Valitsin valikosta virtuaalikonetiedoston ja se käynnistyi.
Tässä näyttökuva: <img width="1919" height="1028" alt="image" src="https://github.com/user-attachments/assets/8b497e58-bffe-4de0-b184-3e01d19c0de3" />

18.06: Valitsin Debianin "Start installer" -vaihtoehdon, jonka jälkeen valitsin kieleksi englannin, maaksi Suomen, en-US.UTF-8 ja näppäimistön kieleksi suomen. Valitsin hostnameksi "linux-test" ja domainiksi "example.com", kuten artikkelissa [1] kerrottiin.

18.12: En asettanut root passwordia. Laitoin "full name of the new user" -kohtaan koko nimeni, "username" -kohtaan etunimeni ja loin vahvan salasanan, kuten artikkelissa [1] kerrottiin.

18.14: Valitsin "partition method" -kohtaan "guided - use entire disk", valitsin virtuaalikonetta varten luomani virtuaalilevyn, "partitioning scheme" -kohtaan "all files in one partition (recommended for new users)" sekä "partitioning disks" -kohtaan "finish partitioning and write changes to disk", kuten artikkelissa [1] kerrotaan. Tämän jälkeen järjestelmä kysyi varmistuskysymyksen formatoinnista, johon vastasin "Yes"

18.25: Asennus onnistui ja järjestelmä kysyi GRUB:in asentamisesta. Valitsin "Yes" ja valitsin käyttämäni partitionin.
Tässä näyttökuva: <img width="1275" height="868" alt="image" src="https://github.com/user-attachments/assets/b22ded0c-9ec7-4e91-a1bb-9d545348cb3b" />

18.30: GRUB-asennus onnistui ja valitsin "Finish the installation" -kohdasta "Continue" rebootia varten. Kirjauduin Debianiin sen käynnistyttyä. 

18.52: Pyrin muuttamaan sources.list-tiedoston sisältöä jotta voisin ajaa komennon "apt-get update" järjestelmän saatavien pakettien päivittämiseksi. Tiedoston muokkaaminen ei onnistunut. Järjestelmä sanoo tiedoston olevan vain-luku -tilassa. Sisältö, jota yritin kirjoittaa tekstitiedostoon oli seuraava:
```
deb https://deb.debian.org/debian trixie main non-free-firmware
deb-src https://deb.debian.org/debian trixie main non-free-firmware

deb https://security.debian.org/debian-security trixie-security main non-free-firmware
deb-src https://security.debian.org/debian-security trixie-security main non-free-firmware

deb https://deb.debian.org/debian trixie-updates main non-free-firmware
deb-src https://deb.debian.org/debian trixie-updates main non-free-firmware
```
Artikkelin [1] mukaisesti.

18.58: Kokeilin muokata tiedoston sisältöä avamaalla sen komentoriviltä "nano" -tekstieditorissa "sudo" -oikeuksilla. Tallennus vaikutti onnistuneen.

19.02: Yritin ajaa apt-get update -komentoa, mutta pakettien etsiminen ei onnistunut. Käynnistin virtuaalikoneen uudelleen.

19.10: Ajoin apt-get update -komennon sudo-oikeuksilla terminaalissa ja se onnistui.
Tässä näyttökuva: <img width="1268" height="872" alt="image" src="https://github.com/user-attachments/assets/8c63f9b5-8abf-4aae-9f03-2b4bf0970571" />





Lähteet:

[1] Heinonen, Johanna 2025: How To Install Linux To Virtualbox (https://github.com/johannaheinonen/johanna-test-repo/blob/main/linux-20082025.md)
[2] Karvinen, Tero 2025: Linux Palvelimet 2025 alkusyksy (https://terokarvinen.com/linux-palvelimet/#h1-oma-linux)
