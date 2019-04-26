# ﻿Progetti in ambito IT

Il seguente documento ha lo scopo di tenere traccia dei progetti a sfondo informatico portati avanti nel Dipartimenti di Ingegneria e Scienza dell’informazione.

## PovoMap (mappatura interna dell’università)

### Componenti

1. Matteo Filippini
2. Mattia Simone
3. Simone Degiacomi

### Breve descrizione del progetto

Il progetto consiste nell’implementazione di un sistema di localizzazione interna per
gli edifici di unitn e la biblioteca BUC.
Una volta implementato il sistema è possibile applicarlo per risolvere vari problemi,
di seguito una breve lista:

1. Ricerca libri geolocalizzata: ricerca dei volumi per posizione negli scaffali/piani ecc…
2. Trovare aule ed uffici Professori
3. Collezione ed analisi dei dati sulla posizione degli studenti/utenti

### Tecnologie utilizzate

Il sistema consiste principalmente in due componenti: dispositivi Android dell’utente
(front-end) e server, a cui vengono inviate le liste delle scansioni Wi-Fi dei dispositivi e viene
effettuata la trilaterazione della posizione.

### Tecnologie frontend

- Android Studio

### Tecnologie backend

- Golang per la realizzazione del server
- MySQL per contenere la lista e le posizioni degli access point
- Vue.js per la realizzazione di un’interfaccia di amministrazione dei dati contenuti nel
- database (coordinate di aule e access point)

### Parte implementata

- Applicazione android che si collega al server attraverso websocket e invia a intervalli di circa 5 secondi la lista delle wifi. L’applicazione rimane in attesa del risultato della trilaterazione dal server. Quando questa viene ricevuta viene mostrata la mappa con la posizione calcolata
- Server che riceve la lista delle wifi e utilizzando i dati nel db prova a trilaterare una posizione dell’utente.
- Interfaccia web base per la creazione di mappe e inserimento di access point
Parte da implementare
- Sistemare e ottimizzare l’algoritmo di trilaterazione, in particolare la conversione dal livello di segnale del wifi (db) in metri (distanza tra dispositivo e access point)
- Creare/ottenere mappe degli edifici
- Tutte le possibili applicazioni

---

## Sistema Gestione orari-Aule (Concept) (Estensione t.me/Ports_Bot)

### Componenti

1. Giovanni Ferronato
2. Luca Scotton
3. Matteo Tadiello
4. Rupert Gobbler

### Breve descrizione del progetto

Un sistema per la gestione degli orari e delle aule. Più in specifico unificare e centralizzare in un unico progetto la gestione degli orari delle aule (ad ora molto confusionario e gestito singolarmente dalle varie facoltà universitarie). Il sistema prevede la suddivisione in tre-quattro macro categorie: l'applicativo per studenti e professori(per la visualizzazione delle aule, degli orari, degli avvisi di dipartimento, variazioni di orario ed eventualmente richieste di prenotazioni aule), l'applicativo per la segreteria, il server con cui l'applicativo può reperire informazioni, il database su cui verranno memorizzate le aule e la struttura dell'università in modo gerarchico (da vedere in fase finale se può essere utile fare confluire il database con il database gestito dall'università).

### Tecnologie utilizzate

- Webapps: con vari user mode (log-in professore, log-in studente, sessione segreteria) e interfacce personalizzate;
- Server: in fase di progettazione;
- Database: gestione piramidale della struttura universitaria:
POLO → EDIFICIO → PIANO → AULA, con gestione della relazione aule, orario lezioni.

### Tecnologie frontend

### Tecnologie backend

### Parte implementata

- Ingegneria del software sul progetto (concept e features da implementare), idee di base, obiettivi, da revisionare prima dell'inizio della fase di implementazione.
Parte da implementare

---

## UniMeal (iOS)

### Componenti

1. Edoardo Meneghini

### Breve descrizione del progetto

UniMeal è un’applicazione al servizio degli utenti delle mense universitarie di Trento, che permette di consultarne prezzi, menu, informazioni e webcam in tempo reale delle mense di Povo, Mesiano e Trento.

### Tecnologie utilizzate

L’applicazione è scritta interamente Swift 3 ed implementa alcune librerie esterne. Il parsing dei menù avviene attraverso un file Json collocato sul Firebase di David Marinangeli.

### Tecnologie frontend

- Xcode 8
- UIKit

### Tecnologie backend

- Swift 3
- Firebase

### Parte implementata

- Informazioni sui menù, Mappa, Webcams.

### Parte da implementare

Essendo un progetto collaborativo con i servizi per gli universitari di Trento, le parti da implementare devono essere approvate dall’Opera Universitaria.

Per ora, le parti da implementare in un futuro prossimo riguardano un sistema robusto di votazioni dei menù.
In un futuro più remoto, si parlerà probabilmente di poter controllare il credito residuo sul proprio badge universitario direttamente dall’applicazione.

---

## Statistica dell’Occupazione della Mensa Universitaria

Webcam Mensa

### Componenti

1. Francesco Gazzetta
2. Giulio Migani
3. Nicola Sartorato
4. Mattia Carolo

### Breve descrizione del progetto

Il progetto ha il compito di andare a calcolare la percentuale di occupazione della mensa scolastica attraverso le webcam che sono state rese disponibili dall’Opera Universitaria.

### Tecnologie utilizzate

- openCV
- chart js

### Tecnologie frontend

### Tecnologie backend

### Parte implementata

- Algoritmo (di prova) della percentuale di occupazione della mensa
- Statistica dell’occupazione delle mense in visione settimanale

### Parte da implementare

- Notifiche con i Service Worker (se verrà fornito un certificato TLS)
- Implementare delle maschere di sensibilità personalizzate per ogni telecamera
- Database (per gestire più agilmente la statistica settimanale)

### Richieste al servizio IT

- Migliorie alle webcam in modo da prestarsi per una più completa visione delle persone in fila.
- Aggiunta di una webcam a povo 0.

---

## UNITNCAL

Gestione del calendario di Ateneo

### Componenti

1. Francesco Gazzetta
2. Nicola Sartorato

### Breve descrizione del progetto

Il progetto è open-source ed il codice è disponibile su https://github.com/fgaz/unitncal.

Un servizio che fornisce il calendario dei corsi in formato standard iCal/ics, quindi sincronizzabili con qualsiasi dispositivo in maniera nativa, senza app aggiuntive.

### Tecnologie utilizzate

### Tecnologie frontend

Lato server in Haskell/servant, esegue lo scraping di unitn/Orari, converte il formato json custom in iCal standard e lo serve sotto permalink listati in homepage, pronti per essere inseriti nel calendario (ci sono le guide in proposito).

### Tecnologie backend

Non c'è bisogno di client appositi, dato che ical è uno standard supportato dalla maggior parte dei dispositivi.

### Parte implementata

Tutte le funzionalità programmate per la 2a versione (http://beta.unitncal.fgaz.me) (accessibile solo dalla vpn universitaria per ora), in particolare i calendari personalizzati stateless.

In particolare:

1. scraping periodico
2. permalink per gli ical dei corsi
3. gestione degli errori
   1. ora il server non può crashare
1. scraping della lista dei corsi
   1. il servizio è totalmente autonomo, anche tra un anno e l'altro (eccetto variazioni nel formato)
1. server web integrato
   1. dati memorizzati in ram, massime performance
   2. configurato il reverse proxy
1. calendari personalizzati
   1. creazione di url per raggruppare più corsi a piacere
      1. per chi è indietro coi corsi
      2. per chi ha più corsi opzionali
   1. niente account o database, l'url contiene tutte le informazioni
      1. sistema stateless

### Parte da implementare

- Rifiniture varie, pulizia del codice, struttura nei log, retrocompatibilità con la versione 1 da mantenere per quest'anno, merging di scraping incompleti, generazione di html da haskell o template.
- Forse un video passo passo oltre che le istruzioni scritte/screenshot.
- Niente di breaking a lato utente, anzi dall'esterno il servizio dovrebbe apparire esattamente uguale.

### Richieste al servizio IT

- Un IP pubblico, già chiesto noi via email, dovrebbero attivarlo a breve.
- Link al servizio nel sito principale di unitn e/o in Orari.
- Un API stabile, versionata e consistente per gli orari.
