# Ovo je primjer Dockerfile-a za izgradnju Docker image-a za Python Flask aplikaciju.
FROM python:3.9

# Autor Dockerfile-a
LABEL author="Andreas Prgić"

# Postavljanje radnog direktorija
WORKDIR /app

# Kopiranje datoteka
COPY requirements.txt /app
COPY Webapp /app

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