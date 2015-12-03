# Hack The Future 2015 [![Build Status](https://travis-ci.org/connery0/controlcenter.svg)](https://travis-ci.org/connery0/controlcenter)
> *Het is 2277, 3 jaar na de fallout en jullie verlaten de bunker om voorraad te verzamelen. Anderen liggen
echter op de loer om jullie bunker aan te vallen. Jullie ontwikkelen ControlCenter, een webapplicatie die het mogelijk maakt om vanop 
afstand de bunker in de gaten te houden en te beschermen.*

![HackTheSFuture](HackTheFuture.png)

Item | Omschrijving
------------- | -------------
ControlCenter  | Webapplicatie die jullie laten draaien op IBM Bluemix.
Bluemix | Bluemix is een [Platform as a service](https://en.wikipedia.org/wiki/Platform_as_a_service) oplossing van IBM, gebaseerd op [Cloud Foundry](https://www.cloudfoundry.org/)
IOT Foundation | De [IoT Foundation](https://www.ng.bluemix.net/docs/#services/IoT/index.html) fungeert als message broker.
Android App | Jullie ontwerpen een Android applicatie die de berichten via MQTT leest en instructies doorstuurt naar Ollie via de [Android SDK for Sphero](https://github.com/orbotix/Sphero-Android-SDK)
Ollie | [Ollie](http://www.sphero.com/ollie) is de beschermer van jullie vault. 

## Start de applicatie
Om van start te kunnen gaan, hebben we 2 kleine applicaties gemaakt. Eén op basis van [Spring Boot](http://projects.spring.io/spring-boot) en één op basis van [ExpressJs](http://expressjs.com). Kies één van beiden en start deze lokaal op. 

### Gebruik de Java applicatie:
1. Installeer [Apache Maven](https://maven.apache.org/install.html)
2. Open terminal en voer volgende commando's uit:

   ```sh
   cd controlcenter-java
   mvn clean install
   mvn spring-boot:run
   ```

3. Ga naar http://localhost:8080

### Gebruik de NodeJS applicatie:
1. Installeer [NodeJS](https://nodejs.org/en/download/)
2. Open terminal en voer volgende commando's uit:

   ```sh
   cd controlcenter-nodejs
   npm install
   npm start
   ```
   
3. De applicatie geeft aan in de terminal op welke poort hij gestart is.

## Breng ControlCenter naar de cloud
1. Maak [een IBM Bluemix-account](https://console.ng.bluemix.net/registration/) aan
2. Download de [Cloud Foundry CLI](https://github.com/cloudfoundry/cli#downloads)
3. De naam van jullie applicatie moet uniek zijn. Ga daarom naar de `manìfest.yml`file en verander de bij name *myteam* door de naam van jullie team. 
4. Open terminal en voer volgende commando's uit:

   ```sh
   cf api https://api.eu-gb.bluemix.net
   cf login # geef hierna je emailadres en wachtwoord in en selecteer space 'dev'
   cf push
   ```
5. Ga naar http://htf-controlcenter-*myteam*.eu-gb.mybluemix.net

## Voeg 'Internet Of Things Foundation' service toe
1. Login op het [Bluemix Dashboard](https://console.eu-gb.bluemix.net)
2. Ga naar het detail van de applicatie htf-controlcenter-*myteam*
3. Klik 'Add a service or api' en zoek naar 'Internet Of Things Foundation'
4. Klik op 'View more', behoudt de default waarden en klik op 'Create'
5. De applicatie zal vragen om te restagen. Klik 'Restage'. 
6. Wacht enkele momenten en ga dan terug naar het detail van de applicatie. Je ziet nu dat de service is toegevoegd. Klik op 'show credentials' om de credentials van de service te bekijken.

## Challenges
Jullie hebben nu een eerste versie van de webapplicatie naar de cloud gebracht. Nu kunnen jullie starten met het uitvoeren van de challenges. Kies zelf welke challenges jullie proberen uit te voeren en in welke volgorde. 

- Download [Eclipse Mars](http://www.eclipse.org/downloads), importeer jullie project en push een wijziging naar Bluemix.

- Maak met [Android Studio](http://developer.android.com/sdk/index.html) een android toepassing die Ollie kan besturen adhv de [Android SDK for Sphero](https://github.com/orbotix/Sphero-Android-SDK)

- Bestuur Ollie via ControlCenter dmv MQTT. Gebruik hiervoor [Eclipse Paho](https://www.eclipse.org/paho). Verstuur een bericht van ControlCenter naar de IoT Foundation op Bluemix. Lees vervolgens het bericht uit via de android applicatie en spreek vervolgens de SDK for Sphere aan. 	

- Lees het huidige batterijpercentage uit van je android toestel en toon het (via [MQTT](http://hivemq.com/blog/how-to-get-started-with-mqtt)) op het ControlCenter

- Gebruik [Git](https://git-scm.com/downloads) en werk samen op Github, fork het project en koppel de repository aan [Travis CI](https://travis-ci.org) voor continuous integration.

- Voorzie een responsive [pipboy](http://vignette3.wikia.nocookie.net/fallout/images/7/76/Pip-Boy_3000.jpg/revision/latest?cb=20110712154420) layout voor ControlCenter

- Laat Ollie rood kleuren wanneer er een tweet binnenkomt met #craftworkzalert
