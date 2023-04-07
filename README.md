# home-assistant-wastehero
Simple pickup info from wastehero

Få dine tømninger automatisk fra wastehero.

Hvis du bor i Guldborgsund eller Lolland kommune er det REFA der henter dit affald,
 de bruger wastehero, og login til refas selvbetjening er: https://refa-portal.wastehero.io/
 
 Hvis du bor i en anden kommune der også bruger wastehero,
  må det antages at det her også vil virke, der er dog ingen garantier.  
  
Brug er dog under alle omstendigheder på eget ansvar.

## krav

- At du kan bruge konsollen i din browser  
- HACS  
- at du bor et sted hvor de bruger wastehero


## sådan gør du

### opsætning af sensor

Login på din portal
![login](https://github.com/0rsted/home-assistant-wastehero/raw/main/login.PNG)

Åben konsollen, (det afhænger af dit os og browser), og vælg "netværk"

Klik på Tømningsoversigt
![collections](https://github.com/0rsted/home-assistant-wastehero/raw/main/click_here.PNG)

Find et punkt i listen der hedder "collections", og klik på den  
Derinde skal du finde to værdier.  

Den grønne værdi er dit location_id, den skal indsættes i sensor.yaml i stedet for [ YOUR ID! ]  
Den lilla værdi er din api nøgle, den skal indsættes i sensor.yaml i stedet for [ YOUR API KEY ]  
![show values](https://github.com/0rsted/home-assistant-wastehero/raw/main/copy_values.PNG)


sensor.yaml skal nu tilføjes til din config,
 jeg har min liggende i en mappe med andre sensorer,
 hvordan du gør er op til dig.



### opsætning af kort

Jeg bruger Thomas Lovéns fantastiske template-entity-row,
 den sørger for at man kun kan se de elementer der har en værdi.  
Så start med at installere den: https://github.com/thomasloven/lovelace-template-entity-row

Derefter er det reelt bare at copy-paste card.yaml ind i card-editoren i lovelace


Så ender du med et kort der ser sådan her ud:  
![card](https://github.com/0rsted/home-assistant-wastehero/raw/main/card.PNG)



## afsluttende noter

Der er, uden tvivl, bedre måder at gøre det her på, jeg har bare fundet noget der virker.  
Jeg overvejer at finde ud af hvordan jeg får de "rigtige" ikoner der viser affaldsfraktionen ind, nice-to-have, ikke need-to-have.  
Outputtet fra wastehero er omvendt, så det sidste punkt i listen, er den første afhentning affald,
 hvorfor aner jeg ikke.  
Hvis du vil have mulighed for at hente flere afhentninger (den her opsætning henter op til 6), 
 kan det gøres ved at kopiere flere sensorer ind, og skifte værdierne i name, value_template, og json_attributes_path.  
Derefter skal du opdatere dit kort, husk at grundet den baglens rækkefølge i wasteheros output, skal nye linier tilføjes ovenover de gamle.  
Opdater værdierne alle steder hvor sensoren bliver nævnt, så de matcher navnet på din nye sensor.
