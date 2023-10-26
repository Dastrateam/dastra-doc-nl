---
description: >-
  Deze pagina legt uit hoe u de interne identifiers van de organisatie kunt traceren
  in de toestemmingsbewijzen
---

# Gebruikersidentificatie

## Hoe het werkt

Het principe is als volgt: u stuurt de **unieke identifier van de geauthenticeerde gebruiker** in uw intranet naar de dastra widget en deze zal deze id versturen bij het verzamelen van de toestemming van de gebruiker. Het is dan mogelijk om het bewijs van toestemming te koppelen aan de klantendatabase (CRM, klantendatabase, klantendatabase, etc.). Eenmaal in het weergavegebied van de toestemmingsbewijzen wordt de geduwde gebruikers-ID weergegeven.

## Stap 1: Kies de gebruikers-ID

Hiervoor moet je een variabele kiezen die je naar de widget wilt overbrengen. Je kunt het base64 gehashte e-mailadres van de gebruiker, een interne klant-ID of een CRM ID gebruiken. Deze variabele moet beschikbaar zijn op de webpagina en wordt in duidelijke tekst doorgegeven. Het mag geen persoonlijke informatie over de gebruiker bevatten (achternaam, voornaam, ongecodeerd e-mailadres). &#x20;

{% hint style="info" %}
&#x20;Als u een base64 gecodeerde string verstuurt, wordt deze automatisch gedecodeerd wanneer de toestemming van de gebruiker wordt ontvangen in de Dastra database.
{% endhint %}

## Stap 2: Pas de integratiecode aan

markup
<div id="cookie-toestemming"></div>
<script src="https://cdn.dastra.eu/sdk/dastra.js?key={UW OPENBARE KEY HIER}" async></script>
<script>

// Dastra's array's initialisatie
window.dastra = window.dastra || [];

// Laad de cookie-toestemming in de pagina
dastra.push(['loadCookieConsent', {
    widgetId: {Plak hier uw widgetId (cijfer)},
    selector: '#cookie-toestemming',
    userId: {De variabele van de userId (e-mail 64bits hash of wat dan ook...)}).
}]);
</script>
```

Je kunt ook de "set"-methode gebruiken

```opmaak
<div id="cookie-consent"></div>
<script src="https://cdn.dastra.eu/sdk/dastra.js?key={UW OPENBARE KEY HIER}" async></script>
<script>

// Dastra's array's initialisatie
window.dastra = window.dastra || [];

// Laad de cookie-toestemming in de pagina
dastra.push(['loadCookieConsent', {
    widgetId: {Plak hier uw widgetId (cijfer)},
    selector: '#cookie-toestemming'.
}]);

// Stuur de userId naar de cookies van dastra
// Het moet gepushed worden na de loadCookieConsent methode
dastra.push(['set','cookie:userId',{De variabele van de userId (e-mail 64bits hash of wat dan ook...)}])
</script>
```