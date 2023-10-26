---
description: >-
  Deze handleiding laat zien hoe je het uiterlijk van de widget kunt veranderen met behulp van eenvoudige eenvoudige CSS-regels
---

# Geavanceerd ontwerp

## CSS-integratie

Om goede weergaveprestaties te verkrijgen, wordt de Dastra-widget direct weergegeven op de sitepagina, in de container met het id **#dastra-widget**.

Het is mogelijk om het uiterlijk van de widget aan te passen met behulp van eenvoudige CSS-regels.

Basisvoorbeeld:

```CSS
/**Triggerknop**/
.dastra-cw-trigger-knop{
  achtergrondafbeelding:url('data: image/png; base64, iVBORw0KGgoAAAANSUhEUgAAAFYAAABHCAYAAACd3LDJAAAABGdBTUEAALGPC/xhBQAAAAlwSFlzAAAOwQAADsEBuJFr7QAAABl0RVh0U29mdHdhcmUAcGFpbnQubmV0IDQuMC4xMkMEa+wAAArDSURBVHhe7Vx5cFXlFQeULSA7kQhhF6sdO6J0Y+pfxbF0Os60ztiqVVtby0C1qEUdcKsimgJ1QbFGXFAcEEqjuFCoCA5WoRhnIkasCSEJhJCEhLzt7vc7p+f77nnv3by8PB4vC1neb+Y333LPPd85J9+933K/l35ZZJFFFln0TSAWD8TAySsgfOpGsPQbnbrDP64v3TOcL2dxpsDQ8XFghJ4Gxw5hAsB1bLCNDVD75cUsnkU6gED91SBEPcexTQjHtsEI3sq3ZZEKGG6cB8K1OXZxONRxnQBlwCszgOBqoYV8exbJACcO59Jj3sgxI1AQa7ci7p+PuPsi4izET65ErHqBums89vIPYTXXzGY1WSQCzPCrHCsCIJQuRfj3zOT87EYKrsmyJO1Y/6WkP6vKIgoINn6fnmsvSgQ4tgVh+/TUPLScpT1k37cJoJgMQMcs9sJDsAModlyO4p1pqfnuTMTg13yTHMysRqw+OJrVZgGR5ts4Ngqi5CEURVPS495f0h3xni704POstm8jWHNorHCdkxwXhOav0P3HVHS3TE6bUL2N76bACmFbTXWXsvq+C2FGnuWYUFQB3Q+uRXfjpDNgPrpvfZemYhorITWm9h9W3zcBNEVC4XI4qLcdKULn9YkZUXy+grV4gODJX3MzfQvke39hGR97YSDYYXQ2zUb7lQuIeei8LFOPjmKeryzzUsZXt34KQuAwK5MDmX0M4OhQbq7vAPTA9RwDBXf/crRfnNAuOttvYG0ehBZaxc31DWBF8Uia0Nex/winytH6+0S0nj+fmMspc60vn5LefaJyB2slva5jwckjF3GzvR9oaQXsOwHQfvs6tNaMj/OZhLy/nKzel7fX00DmxldkNEd4
}
.dastra-cw-trigger-button svg{
  display:none;
}

/**Modale container**/
.dastra-cw-container{
  grensradius:0;
  box-schaduw: 0 0 50px rgba(0,0,0,.3);
}

/**Knop in de voettekst**/
.dastra-cw-knop {
  font-weight:bold;
}

/**Knop bekijk meer**/
.dastra-cw-viewmore-knop {
  rand:geen;
  color:red;
}

/**Titel van toestemmingscategorie**/
.dastra-cw-verzameling-titel {
  letter-spacing:1px;
  lettergrootte:19px;
  font-weight:200;
}
```

{% hint style="info" %}
&#x20;Houd er rekening mee dat bepaalde aanpassingen aan de widgetcontainer ongewenste effecten kunnen hebben.
{% endhint %}