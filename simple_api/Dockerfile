# Image de base imposée par POZOS
FROM python:3.13-slim

# Maintainer
LABEL maintainer="Alvirra <alvirra@example.com>"

# Prérequis système pour Flask / LDAP / SASL
RUN apt-get update -y && apt-get install -y \
    gcc \
    python3-dev \
    libsasl2-dev \
    libldap2-dev \
    libssl-dev \
    && rm -rf /var/lib/apt/lists/*

# Copie du code source de l'API à la racine du conteneur
COPY . /

# Installation des dépendances Python
RUN pip3 install --no-cache-dir -r /requirements.txt

# Dossier de données persistantes (monté en volume au lancement)
RUN mkdir -p /data
VOLUME ["/data"]

# Port d'écoute de l'API
EXPOSE 5000

# Lancement de l'API au démarrage du conteneur
CMD ["python3", "./student_age.py"]
