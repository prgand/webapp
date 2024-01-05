Opis projekta:
Osobna web stranica - Andreas Prgić
Ovo je moja osobna web stranica koja služi kao portfolio i informacijsko mjesto o meni. Sadrži informacije o mom obrazovanju, projektima na kojima radim, vještinama i interesima. Mojoj web stranici možete pristupiti na jednoj od ove dvije adrese: https://mojwebapp1.azurewebsites.net ili www.andreas-prgic.from.hr . Mom Docker image-u možete pristupiti na ovoj adresi: https://hub.docker.com/r/prgicandreas/webappimage .

Što vam je potrebno od programa/softvera da napravite ovakvu web aplikaciju?
Docker Hub
-za to vam je potreban korisnički račun na Docker Hub-u kojeg možete napraviti na ovom linku https://hub.docker.com/signup

Visual Studio Code (meni osobno najdraži editor koji ima raznovrsne mogućnosti)

Web preglednik (Google Chrome, Firefox, Safari, Brave itd.)

Ova aplikacija je napravljena pomoću Flask-a. Flask je popularni Python web framework zbog nekoliko razloga:

1.Jednostavnost: Flask je jednostavan za naučiti i koristiti. Njegova sintaksa je čista i intuitivna, što olakšava izgradnju web aplikacija.

2.Fleksibilnost: Omogućava izgradnju malih i velikih aplikacija. Nudi osnovne alate potrebne za razvoj web aplikacija, ali isto tako dozvoljava proširenje funkcionalnosti pomoću raznih dodataka.

3.Laganost i skalabilnost: Flask je lagan i ne nameće stroga pravila strukture aplikacije. To omogućava razvoj aplikacija prema vlastitim potrebama, čime se olakšava skaliranje aplikacija.

4.Veličina i performanse: Flask je mali i ne opterećuje aplikaciju nepotrebnim funkcijama. To može rezultirati bržim izvršavanjem aplikacije.

5.Veličina zajednice i dokumentacija: Flask ima aktivnu zajednicu korisnika s obiljem dostupne dokumentacije, tutorijala i resursa. To olakšava rješavanje problema i učenje. 

Za osobnu web stranicu ili manje aplikacije poput ove, Flask je odličan izbor zbog svoje jednostavnosti, fleksibilnosti i brzine razvoja. Omogućuje izgradnju dinamičnih web stranica s minimalnim naporom, čime je idealan za početnike ili manje projekte.

Sve datoteke su dostupne i na GitHub-u koje možete preuzeti na sljedećem link-u: https://github.com/prgand/webapp.git

Koraci za izgradnju web aplikacije:


Izgradnja Dockerfile-a:

# Ovo je primjer Dockerfile-a za izgradnju Docker image-a za Python Flask aplikaciju.
FROM python:3.9

# Autor Dockerfile-a
LABEL author="Vaše ime"

# Postavljanje radnog direktorija
WORKDIR /app

# Kopiranje aplikacijskih datoteka
COPY . /app

# Instalacija potrebnih paketa
RUN pip install -r requirements.txt

# Izlaganje porta na kojem će aplikacija biti dostupna
EXPOSE 5000

# Pokretanje aplikacije
CMD ["python", "app.py"]

# Detaljan opis image-a
# Ovaj image pokreće Python Flask aplikaciju.
# Prvo se koristi osnovni image Pythona, zatim se kopira aplikacijski kod i instaliraju se potrebni paketi.
# Na kraju, aplikacija se pokreće unutar Docker kontejnera na portu 5000.

Nakon što smo izgradili Dockerfile, prelazimo na implementaciju Flask-a u datoteci "app.py". Kako bi instalirali Flask, potrebno je otvoriti CMD(naredbeni redak u Windows-u) ili Terminal(u Linux-u) te unijeti sljedeću naredbu:

pip install Flask

Ova naredba će preuzeti i instalirati Flask na vaše računalo. Nakon što je Flask uspješno instaliran, pozicionirajte se u datoteku app.py te u tu datoteku unesite ovaj kod:

from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def index():
    return render_template('index.html')

if __name__ == '__main__':
    app.run(debug=True, host='0.0.0.0')

Spremite datoteku s ovim kodom te pokrenite aplikaciju. Ukoliko radite u Visual Studio Code-u, potrebno je pokrenuti aplikaciju tako što pritisnemo na ikonu play (nalazi se u gornjem desnom kutu) koja nam kaže "Run Python file" ili možete otvoriti terminal te unijeti ovu naredbu:

python app.py

Ukoliko je sve u redu, aplikacija će se pokrenuti i biti će dostupna na adresi http://127.0.0.1:5000/ ili http://localhost:5000/.
Pošto koristimo Flask, vrlo je bitno da u direktoriju gdje se nalazi app.py, postoje još dva direktorija static i templates. Flask ima konvenciju koja olakšava organizaciju projekata. Kada se radi o web aplikacijama, razdvajanje HTML datoteka, CSS-a, JavaScript-a i drugih statičkih resursa u odvojene direktorije kao templates i static često se koristi radi bolje organizacije i efikasnijeg razvoja.

Templates direktorij (templates/): Ovdje se obično nalaze HTML datoteke. Flask očekuje da će sve HTML datoteke koje se koriste kao predlošci za generiranje stranica biti pohranjene u ovom direktoriju. Flask koristi Jinja2 template engine kako bi olakšao dinamičko generiranje HTML-a i njegovo povezivanje s podacima koje šalješ iz Pythona.

Static direktorij (static/): Ovdje se pohranjuju statički resursi poput CSS datoteka, JavaScript-a, slika, fontova itd. Flask će posluživati ove datoteke kao statičke resurse direktno s web servera kada ih pozoveš u HTML-u. To znači da možeš koristiti relativne putanje kako bi u HTML-u referencirao ove datoteke, a Flask će se brinuti za posluživanje tih resursa prilikom zahtjeva.

Korištenjem ovog organizacijskog obrasca, lakše je održavati projekte jer je struktura jasna i jednostavna za razumjeti. Flask automatski prepoznaje ove direktorije ako su pravilno nazvani ('templates' i 'static') i koristi ih za odgovarajuće svrhe prilikom generiranja web stranica i posluživanja statičkih datoteka.

Potrebno je napraviti web aplikaciju (u ovom slučaju web stranicu) koristeći bilo koji programski jezik i framework. Prilikom izrade aplikacije, uključivanje određenih elemenata u HTML je drugačije nego inače jer se koristi Flask. Uključivanje CSS-a izgleda ovako:

<link rel="stylesheet" href="{{ url_for('static', filename='stil.css') }}" />

Uključivanje slike izgleda ovako:

<img src="{{ url_for('static', filename='/images/nazivslike.ekstenzija') }}"  />

Uključivanje JavaScript-a u HTML dokument:

<script src="{{ url_for('static', filename='script.js') }}"></script>


Ako želite vidjeti kako vam izgleda stranica, potrebno je pokrenuti app.py te nakon pokretanja aplikacije, stranici možete pristupiti na jednoj od ove dvije adrese kao što je to već prethodno spomenuto: http://127.0.0.1:5000/ ili http://localhost:5000/ .
Možete aplikaciju ostaviti da bude pokrenuta cijelo vrijeme te bilo koje promjene da napravite u vašem kodu, spremite ih, ponovno učitajte stranicu u web pregledniku i promjene će biti vidljive ukoliko ste ispravno unijeli promjenu.

