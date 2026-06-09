FROM ubuntu:22.04

RUN apt-get update && apt-get install -y \
    curl \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY ./meine_datei.txt .

ENV INFO="Hallo aus Aufgabe 1.5"

CMD ["echo", "Container gestartet!"]
