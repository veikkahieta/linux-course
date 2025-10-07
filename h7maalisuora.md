<h1>h7 Maalisuora</h1>

<h2>a) Kirjoita ja aja "Hei maailma" kolmella kielellä.</h2>
Ajoin komennot 'nano helloworld.sh' ja lisäsin tiedostoon sisältöä. Seuraavana ajoin 'ls -l helloworld.sh' ja chmod ugo+x helloworld.sh'. Lopuksi uudelleen vielä 'ls -l helloworld.sh'. Tämä tehtiin, jotta scriptien ajaminen on mahdollista.
<img width="624" height="214" alt="image" src="https://github.com/user-attachments/assets/8280c825-fe37-449c-84a7-bd4797b50d71" />

Aloitin scriptin ajamisen komennolla 'pwd'. Seuraavana ajoin komennon 'echo $PATH' ja './helloworld.sh'.
Ajoin myös 'export PATH="$PATH:$HOME/bin"'. Reloadasin myös .profile -tiedoston komennolla 'source ~/.profile'.
<img width="700" height="58" alt="image" src="https://github.com/user-attachments/assets/4164933f-56f2-4dc3-8cf3-8d173a274f71" />

Ajoin "Hei, maailma!" kolmella eri kielellä Pythonilla:
<img width="648" height="158" alt="image" src="https://github.com/user-attachments/assets/e39e7ec1-8bdf-4f7f-af97-c64e30594a3f" />

<h2>b) Lähdeviitteet</h2>
Tarkastin aiempien raporttien lähteet ja ne olivat kunnossa. [1]

<h2>c) Laita Linuxiin uusi, itse tekemäsi komento niin, että kaikki käyttäjät voivat ajaa sitä.</h2>

Tehdään komento 'moi', joka tulostaa kaikille 'Terve!'.
Loin tiedoston 'sudo nano /usr/local/bin/moi'. Kirjoitin tiedostoon '#!/bin/bash'
'echo "Terve!"'.
<img width="554" height="90" alt="image" src="https://github.com/user-attachments/assets/a4bf2465-6ea5-4022-826c-32bc20210aeb" />
Ajoin seuraavaksi komennon 'sudo chmod +x /usr/local/bin/moi', jotta teen komennosta suoritettavan. Testasin 'moi' -komentoa ja kaikki toimii.

<img width="554" height="80" alt="image" src="https://github.com/user-attachments/assets/6b37ea43-e8df-4f1d-a878-ecae276423d3" />

Tajusin myöhemmin, että olisin voinut tehdä tehtävän Pythonillakin, aikalailla samalla tavalla.
<h2>d) Ratkaise vanha arvioitava laboratorioharjoitus soveltuvin osin.</h2>
Löysin Teron sivuilta vanhan "Hello Go world – Install and Run Go in Less Than a Minute on Ubuntu 16.04 LTS" -artikkelin/tehtävän ja tahdon tehdä sen. Minua kiinnosti erityisesti se, että Tero Karvinen on sanonut artikkelissa vuonna 2017 "Go":n olevan uusi ohjelmointikieli, joka on C++ kanssa samankaltainen. Se pyrkii kuitenkin yksikertaisenpaan ja turvallisempaan toteuttamiseen.
<h3>Joten ladataan Go:</h3>
Ensin 'sudo apt-get update' sekä 'sudo apt-get -y install golang'. Lataamisen jälkeen 'mkdir helloveikka/' ja 'cd helloveikka'. "helloveikka"-directoryssä 'nano helloveikka.go':
<img width="556" height="50" alt="image" src="https://github.com/user-attachments/assets/625481c3-c899-4987-9249-e8cdda8bb801" />
Lisäsin helloveikka.go -tiedostoon sisältöä:
'package main
import "fmt"
func main() {
     fmt.Printf("Moro Veikka!\n")
}'
Lopuksi vielä 'go build', jonka jälkeen './helloveikka' tulostaa "Moro Veikka!":
<img width="480" height="56" alt="image" src="https://github.com/user-attachments/assets/99ce2e41-4e8d-47fa-a1f1-b543e5c43852" />


<h2>Lähteet:</h2>
Karvinen, Tero 2025: Linux palvelimet 2025 alkusyksy: https://terokarvinen.com/linux-palvelimet/#aikataulu [1]
Heinonen, Johanna 2025: Linux Shells Scripting Basics: https://github.com/johannaheinonen/johanna-test-repo/blob/main/linux-01102025.md
Karvinen, Tero 2017: Hello Go world – Install and Run Go in Less Than a Minute on Ubuntu 16.04 LTS: https://terokarvinen.com/2017/hello-go-world-install-and-run-go-in-less-than-a-minute-on-ubuntu-16-04-lts/?


