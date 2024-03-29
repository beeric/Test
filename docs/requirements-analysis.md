#Requirements and Analysis Document for OH-Haiku

#1 Introduction

###1.1 Purpose of application

Twitter-användare har efterfrågat en applikation som avgör om en text är skriven enligt diktformen Haiku. Handledaren för projektet har utvecklat en applikation innehållande en enkel algoritm för att kontrollera detta, vilken har laddats ner tillräckligt många gånger för att påvisa att ett behov finns.

###1.2 General characteristics of application
# 2 Proposed application
Haiku-app
### 2.1 Overview
### 2.2 Functional requirements
Övergripande funktionella krav
#### 2.2.1 Algoritm som räknar stavelser
1.	Kunna identifiera och räkna stavelser i en text
#### 2.2.2 Haiku-algoritm
1.	Kunna avgöra om texten uppfyller kraven för en haiku
2.	Kunna beräkna någon form av poäng för hur haikun, kanske på basis av hur nära den är en “korrekt” haiku
3.	Kunna berätta vilken rad som innehåller för många eller för få stavelser
4.	Kunna räkna stavelser i realtid
5.	Kunna fungera för språken engelska och svenska 

####2.2.3 Twitter
	
7.	Kunna tweeta texten med haikupoängen
8.	Kunna skriva ut Certified Haiku på Twitter i fallet att texten är en fullständig Haiku
9.	Kunna logga in med sina Twitter-credentials
10.	Kunna komma ihåg Twitter-användaruppgifter
11.	Kunna analysera användare på Twitter. Hur många procent av tweetsen är Haikus? Hur Haiku är en användare?

####2.2.4 Övrigt

12.	Kunna använda applikationen utan Twitter-konto
13.	Kunna kontrollera om en användares sms är en Haiku
14.	Kunna dela via sms och mail
15.	Kunna spara en Haiku
16.	Kunna ta bort en sparad Haiku
	
###2.3 Non-functional requirements
Rubriken avser applikationens kvalitativa mått

####2.3.1 Usability

- Ett smidigt och trevligt GUI
- Ta asiatiska influenser i beaktning vid utformning av grafiskt gränssnitt
- Ge trevlig ljud-feedback
- Snygg ikon
- Låsa GUI:t så lite som möjligt 
- Asynkrona requests där det är lämpligt
- Enkel att använda för personer som inte är helt insatta i Haiku

####2.3.2 Reliability

- Enkel funktion, skall därav aldrig behöva faila
- Sparade Haikus ska inte kunna gå att ta bort av misstag 
- Haikun ska inte försvinna om åtkomst till Twitter eller Internet saknas 

####2.3.3 Performance

- Snabb respons
- Robust
- Resurssnål, i enlighet med Androids krav
- Skall kunna kontrollera om texten är en Haiku utan tillgång Internet
- Skall kunna spara en Haiku utan tillgång till Internet

####2.3.4 Scalability, Extensibility

- Logik som beräknar stavelser ska separeras från Haikulogiken
- Ett interface ska utarbetas som gör det möjligt att koppla på andra sätt att poängsätta strängar på basis av stavelseuppsättningen i dem. På detta sätt skulle man kunna lägga till andra regelbestämda diktformer senare.
- Design skall enkelt kunna ändras för att regelalgoritmen skall kunna användas i andra applikationer

####2.3.5 Packaging and Installation

- Skall paketeras som en android-applikation och släppas på google-play
- Skall ha en säljande beskrivning på google-play

####2.3.6 Accessibility

- Enkel att använda för personer som inte är helt insatta i Haiku

####2.3.7 Maintainability

- En tydlig kanal för att ta emot feedback vid eventuella buggar
- Vid stor efterfrågan uppgraderas applikationen kontinuerligt
- En trigger med meddelande om att applikationen inte är den senaste versionen skall presenteras vid start

####2.3.8 Legal
- Skall använda en lämplig licens. MIT-licensen används om inga konflikter uppstår till exempel på grund av externa bibliotek. Projektet kan komma att läggas under en GPL-licens om så krävs.

###2.4 Application models 
####2.4.1 Scenarios 
####2.4.2 Use case model Use cases priority 
####2.4.3 Static model 
####2.4.4 Dynamic model
####2.4.5 User interface
####2.5 Test cases
####2.6 Possible future directions
####2.7 References

 





#3 Architecture
Arkitekturen kommer att följa MVC-mönstret (Model - View - Controller) vilket innebär att data och presentation separeras. 
Data enkapsuleras i en modell. Vyn presenterar data från modellen. Kontrollern förmedlar händelser i vyn till modellen och förändringar i modelldata till vyn.
På så vis kan till exempel databasmotorn eller hela lagringslösningen bytas ut utan att det påverkar vyn. I gengäld kan även presentationen av data förändras utan att modellen behöver skrivas om. 

#4 Design
Färdiga stavelseräknande algoritmer ska undersökas. Ett möjligt alternativ är att använda sig av en algoritm som används i LaTeX. Den finns beskriven i en doktorsavhandling. Färdiga implementationer finns släppta under GPL-licens. Val av den implementationen skulle alltså föranleda ett byte av licens.
Även vad gäller Twitter-integrationen skall färdiga bibliotek undersökas. Twitter4J är ett möjligt alternativ. Biblioteket skötet auktorisering och autentisering mot Twitter via OAuth. Licensen är Apache, vilken torde vara kompatibel med MIT.