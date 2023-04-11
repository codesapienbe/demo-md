## 3\. Resource methoden

Een ander belangrijk ding in verband met REST is **resource methoden**. Deze bronmethoden worden gebruikt om de gewenste overgang tussen twee statussen van een bron uit te voeren.

Een groot aantal mensen relateert bronmethoden ten onrechte aan [HTTP-methoden][1] (d.w.z. GET / PUT / POST / DELETE). Roy Fielding heeft nooit een aanbeveling genoemd rond welke methode in welke toestand moet worden gebruikt. Het enige wat hij benadrukt is dat het een **uniforme interface** moet zijn.

Als we bijvoorbeeld besluiten dat de toepassings-API's HTTP POST zullen gebruiken voor het bijwerken van een bron - in plaats van dat de meeste mensen HTTP PUT aanbevelen - is het goed. Toch zal de applicatie-interface RESTful zijn.

Idealiter maakt alles wat nodig is om de bronstatus over te zetten deel uit van de bronrepresentatie - inclusief alle ondersteunde methoden en welke vorm ze de vertegenwoordiging zullen verlaten.

> We moeten een REST API invoeren zonder voorkennis buiten de initiële URI (een bladwijzer) en een set gestandaardiseerde mediatypen die geschikt zijn voor het beoogde publiek (d.w.z. naar verwachting worden begrepen door elke client die de API zou kunnen gebruiken).
> 
> Vanaf dat moment moeten alle overgangen van de toepassingsstatus worden aangestuurd door de clientselectie van door de server verstrekte keuzes die aanwezig zijn in de ontvangen representaties of worden geïmpliceerd door de manipulatie van die representaties door de gebruiker.
> 
> De overgangen kunnen worden bepaald (of beperkt door) de kennis van de klant van mediatypen en communicatiemechanismen voor bronnen, die beide on-the-fly kunnen worden verbeterd (bijv. _code-on-demand_). \[Falen hier impliceert dat out-of-band informatie interactie stimuleert in plaats van hypertekst.\]

[1]: https://restfulapi.net/http-methods/