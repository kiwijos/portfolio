---
Title: Load analysis optional
Description: This is my optional load analysis
---

Laddningstider och användarupplevelse
=======================

Syftet med den här analysen är att testa hur fort webbplatsen laddar, samt diskutera vad det beror på och hur det påverkar upplevelsen av webbplatsen. I diskussionen ges även förslag på hur laddningstiderna kan snabbas upp.

<picture>
    <source
    srcset="
        %base_url%/image/bewgorp.png?w=1200&save-as=jpg&q=50 2x,
        %base_url%/image/bewgorp.png?w=600&save-as=jpg&q=50
    "
    media="(min-width: 600px)">
    <source
    srcset="
        %base_url%/image/bewgorp.png?w=900&save-as=jpg&q=50 2x,
        %base_url%/image/bewgorp.png?w=450&save-as=jpg&q=50
    "
    media="(min-width: 400px)">
    <img
    srcset="
        %base_url%/image/bewgorp.png?w=700&save-as=jpg&q=50 2x
    "
    src="
        %base_url%/image/bewgorp.png?w=350&save-as=jpg&q=50
    "
    alt="Förstasidan på slutprojektet">
</picture>

Urval
-----------------------

För att ge en så heltäckande bild av webbplatsen som möjligt har tre sidor valts ut för att göra mätningar av. Det är <a target="_blank" href="http://www.student.bth.se/~allq22/dbwebb-kurser/design/me/kmom10/">förstasidan</a>, <a target="_blank" href="http://www.student.bth.se/~allq22/dbwebb-kurser/design/me/kmom10/highlight">highlight-sidan</a> där alla projekt presenteras och en av <a target="_blank" href="http://www.student.bth.se/~allq22/dbwebb-kurser/design/me/kmom10/highlight/02_proj">projektsidorna (Beat Booker)</a>.

Metod
-----------------------

Utvecklarverktygen i Chrome används för att mäta antalet resurser som skickas till sidorna, hur lång tid det tar och sidornas totala storlek. Mätningarna av laddningstid görs tre gånger utifrån vilka medelvärden räknas ut. Resultaten härifrån presenteras i en tabell och kompletteras med betyg och mätvärden från Pagespeed insights. Då olika stora bilder läses in vid olika skärmstorlekar och upplösning kan mätvärdena variera. Själv har jag gjort mätningarna på min laptop med dubbel pixeldensitet.

Resultat
-----------------------

<div class="embed-container">
<iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vReCloCxNJIlWbOCVYc33EVy_gGoo42oAG8U0e2Z4YyHR8qnuZ1vkDGdnktj2JCmlzDiH3sfUtDfJ3k/pubhtml?gid=0&amp;single=true&amp;widget=true&amp;headers=false" title="Tabell med resultat" frameborder="0"></iframe>
</div>

Förstasidan laddar snabbast i mitt eget test. Vilket inte är speciellt förvånande då det är minst resurser som läses in. Det ger ett gott första intryck som bidrar till en god användarupplevelse överlag. Alla sidor får godkänt på både mobil och desktop av Pagespeed insights test av viktiga webbvärden. Saker man gör bra är att väla rätt storlek på bilder bland annat. De främsta förbättringsförslagen är att välja moderna bildformat som WebP och AVIF och att ta bort resurser som blockerar renderingen.

Analys
-----------------------

Vad gäller moderna bildformat som WebP och AVIF så ger de bättre komprimering och därmed högre bildkvalitet sett till filstorlek jämfört med format som JPEG och PNG. Mindre filstorlek innebär att mindre data förbrukas och bilderna laddar snabbare. Vilket är särskilt viktigt för att öka webbplatsens prestanda och göra upplevelsen bättre på mobila enheter. Rent praktiskt kan hade man kunnat göra en WebP-variant av alla bilder och använda srcset-attributet inuti picture-elementet för att ange dessa varianter som förstahandsval. Då WebP inte stöds av alla webbläsare är det viktigt att alltid ha en JPEG- eller PNG-variant som fallback.

När det kommer till blockerande resurser så är det främst filen style.min.css som pekas ut. Enligt förslaget bör de allra viktigaste CSS-reglerna placeras inline så att de kan läsas in så fort som möjligt medan övriga regler bör läsas in parallellt, eller asynkront som det heter. Hur man gör det här på bästa sätt är inget vi gått igenom i kursen. Så det får bli till en annan gång. Man bör också se till att sådant som inte används tas bort. Här handlar det om CSS men samma principer är även tillämpbara på javascriptkod exempelvis.

Jag skrev i den förra analysen av laddningstider att 1–2 sekunder är en bra tid. Vilket jag fortfarande tycker stämmer. Kollar vi på tiden "Läs in" eller "Load time" som det också heter kalarar webbplatsen gränsen med god marginal. Load time känns mest relevant när vi talar om användarupplevelse. Det är ett ungefärligt mått på när vi som användare uppfattar att sidan laddat klart.

av Alex Lindqvist