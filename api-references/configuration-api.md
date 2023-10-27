# API configureren

### API's configureren in Dastra&#x20;

API staat voor _**Application Programming Interface**_;

API's maken het mogelijk om het Dastra platform te verbinden met andere externe tools;

De mogelijkheden zijn legio: koppeling met CRM-software om stakeholders automatisch op te halen, synchronisatie van een rechtenmanagementtool met de Dastra-module, etc.

Dastra is gebaseerd op de **API-Rest** standaard en in het bijzonder op de volgende HTTP requests:&#x20;



| URI | GET | POST | PUT | PATCH | DELETE |
| --------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| Resource collection, zoals `http://api.exemple.com/collection/` | _Fetch_ de URI's van de member resources in de resource collection uit de respons body. |_Create_ een member resource in de resource collection met behulp van de statements in de request body. De URI van de aangemaakte member resource wordt _auto-toegewezen_ en teruggezonden in het _Location_ headerveld van het antwoord. Vervang_ alle representaties van de member resources in de resourceverzameling door de representatie in de request body, of _maak_ de resourceverzameling aan als deze niet bestaat. | Update_ alle representaties van de resource-leden van de resourceverzameling met behulp van de verklaringen in de verzoektekst, of _creëer_ de resourceverzameling als deze niet bestaat. Verwijder alle representaties van de resource-leden van de resourceverzameling.
| Haalt_ een representatie van de lidbron op uit de respons body. Creëert_ een lidbron in de lidbron met behulp van de verklaringen in de request body. De URI van de aangemaakte member resource wordt _auto-toegewezen_ en teruggezonden in het _Location_ headerveld van het antwoord. Vervang_ alle representaties van de member resource, of _creëer_ de member resource als deze niet bestaat, met de representatie in de request body.                               | Werk alle representaties van de lidbron bij, of _maak_ de lidbron aan als deze niet bestaat, met behulp van de instructies in de verzoektekst. Verwijder alle representaties van de lidbron.

Bron : [_wikipedia_](https://fr.wikipedia.org/wiki/Representational);



Verschillende API's kunnen worden geconfigureerd met Dastra. De lijst met API's is hier beschikbaar: [https://api.dastra.eu/swagger/index.html](https://api.dastra.eu/swagger/index.html)

### Beperkingen&#x20;

Een http-verzoeklimiet is ingesteld op 500/min of 10000/10min.

Beveiligingsopties (met name IP-filtering) zijn niet van toepassing op API's &#x20;

### Blootstelling van aangepaste velden in de Dastra API&#x20;

In Dastra is het mogelijk om in de API [aangepaste velden](../features/generalites/custom-fields.md) te tonen die ontworpen zijn vanuit je Dastra-workspace.&#x20;

Aangepaste velden zijn specifiek voor elke werkruimte. Om ze mee te nemen in de Dastra API, moet je eerst de naam van hun variabele definiëren in de aangepaste velddefinitie:&#x20;

<figure><img src="../.gitbook/assets/image (276).png" alt=""><figcaption></figcaption></figure>

{% content-ref url="../features/generalites/custom-fields.md" %}
[custom-fields.md](../features/generalites/custom-fields.md)
{% endcontent-ref %}

De meeste entiteiten die via de API gewijzigd kunnen worden, hebben een veld met de naam "**customFields**" dat je kunt wijzigen &#x20;

Als je velden definieert met de volgende variabele namen binnen je werkruimte:&#x20;

* my_field_string: een "Tekst" veld
* my_field_booleen: een "aankruisvakje" veld
* mijn_veld_numeriek : een "Nummer" veld
* my_field_checkbox: een "Checkbox" veld

Het is mogelijk om deze informatie als volgt aan te passen

```json
{ 
  "label: "Google Analytics 4",
  ...
  "customFields": {
     "my_field_string": "Waarde van mijn veld",
     "my_field_booleen": waar
     "my_field_numeric": 1.,
     "my_checkbox_field":["Appel", "Banaan"],
     ...a
  }
}
```

### Tags

Om tags bloot te leggen in de Dastra API, moet je ze zoeken in het tags eindpunt voordat je ze toevoegt: /v1/ws/{workspaceId}/Tags

###

{% hint style="info" %}
**TIP**: gebruik alleen API's als je weet wat je doet!
{% endhint %}



Je kunt de API beheerinterface in Dastra vinden op dit adres: [https://app.dastra.eu/general-settings/api](https://app.dastra.eu/general-settings/api)





