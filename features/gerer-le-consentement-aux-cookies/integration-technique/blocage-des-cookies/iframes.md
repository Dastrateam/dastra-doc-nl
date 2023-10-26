---
description: >-
  Veel sites gebruiken iframes om video's, tweets, enz. weer te geven.
  tweets... Het is daarom noodzakelijk om gebruikers om toestemming te vragen
  voordat de iframe-inhoud wordt geladen.
---

# Iframes blokkeren (twitter/youtube...)

## Voorbeelden van diensten die iframes gebruiken

Videospelers: Youtube, Vimeo, DailyMotion, enz.

Sociale netwerken: Twitter, Facebook, enz.

Podcast spelers &#x20;

Audiospelers &#x20;

## Methode 1: De SDK gebruiken

Met onze SDK kun je alle iframes op de pagina blokkeren door een aanpasbaar blokkeerbericht weer te geven:

![](<../../../.gitbook/assets/image (184).png>)

Door op "Ik accepteer" te klikken wordt automatisch toestemming gegeven voor de specifieke dienst. Het systeem maakt het ook mogelijk om een weigering van cookies vast te leggen in het Dastra CMP.

Een eenvoudig voorbeeld met youtube video player iframes:

``markering
<iframe width="560" height="315" src="https://www.youtube.com/embed/aJ1qDx8lv2Y" allowfullscreen></iframe>
<script>
  // Youtubeframe blokkeren instellen
  dastra.push(['iframeBlock', {
    selector: 'iframe[src*="youtube.com"]',
    service: 'youtube', // service slug (Controleer uw Dastra cmp-configuratie)
    body:'<p>Door te klikken op "I accept" worden de trackers gedeponeerd en kun je de video bekijken. Je kunt je toestemming op elk moment intrekken :</p>',
    buttonLabel:'Ik accepteer',
    buttonClass: 'btn btn-primary'.
  }])
</script>
```

{% hint style="info" %}
Het is mogelijk om het uiterlijk van het bericht (achtergrond, lettertypen...) aan te passen met je css-sheet. Het blokkeringsbericht wordt geïntegreerd in de pagina DOM met een ".datra-blocking-iframe" klasse.&#x20;
{% endhint %}

## Methode 2: Handmatige implementatie&#x20;

Je kunt ook je eigen logica implementeren

opmaak
<script>
  // Selecteer alle youtube iframes 
  var iframes = document.querySelectorAll('iframe[src*="youtube.com"]');

  // Schakel voor elk iframe het iframe uit door het kenmerk "src" te transformeren naar "data-blocked-src".
  iframes.forEach(function(iframe){
    var iframeSrc = iframe.getAttribute('src');
    iframe.setAttribute('data-blocked-src', iframeSrc );
    iframe.setAttribute('src','about:blank');
    var divAlert = document.createElement('div');
    divAlert.classList.add('alert-iframe-cookie')
    divAlert.innerHTML = '<p>Door te klikken op "Ik geef toestemming" worden de trackers verwijderd en kun je de video bekijken. Je behoudt de mogelijkheid om je toestemming op elk moment in te trekken. Als u op "Ik weiger" klikt, krijgt u geen toegang tot de video. : </p><div class="button-container"><button type="button" onclick="SetConsent(\'youtube', true)" href="#" class="btn btn-success" >Accepteer de cookies</button></div><p>Toestemming verleend door <a href="https://www.dastra.eu">Dastra</a></p>";
    iframe.after(divAlert);
  });

  // Bij toestemming van cookie, 
  window.addEventListener('dastra:consent:youtube', function() {
    // Iframe laden wanneer geaccepteerd
    document.querySelectorAll('iframe[data-blocked-src*="youtube.com"]').forEach(function(iframe){
      iframe.setAttribute('src', iframe.getAttribute('data-blocked-src'));
      iframe.removeAttribute('data-blocked-src');
    });
    
    // Bericht verwijderen wanneer geaccepteerd
    document.querySelectorAll('.alert-iframe-cookie').forEach(function(alert){
      alert.style.display = "none";
    });
  });

  functie Instemming instellen(service, toestemming){
    dastra.cookieConsent.consent.setServiceConsent(service, true);
    dastra.cookieConsent.consent.save();
  };

</script>
<style>
  .alert-iframe-cookie{
    achtergrondkleur:#CCC;
    opvulling: 20px 20px;
    kleur:#fff;
    tekst-uitlijning:centreren;
  }
  
  .knop-container{
    marge: 10px auto; 
  }
  
</style>
```

Hier ben je