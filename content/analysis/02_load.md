---
Title: Load analysis
Description: This is my load analysis
---

Laddningstider och användarupplevelse
=======================

Syftet med den här analysen är att testa tre olika webbplatsers laddningstider och resursanvändning, samt diskutera hur det påverkar användarupplevelsen. I diskussionen ges även förslag på sätt att snabba upp laddningstiderna.

Urval
-----------------------

Jag har valt att analysera samma webbplatser som i föregående analys. De tillhör alla kategorin museer och har ett liknande upplägg när det kommer till innehåll med många bilder på utställningar blanda annat. Sidorna laddar olika snabbt och det ska bli intressant att se vad det kan bero på. Jag har valt att bara analysera webbplatsernas förstasidor. En förstasida är som namnet antyder det första man som besökare ser när man kommer till en webbplats och därmed viktig för att hålla oss kvar där. Vad gäller användarupplevelse är förstasidan alltså särskilt intressant att analysera. Den här gången kommer jag att förkorta namnen på National Museum of Natural History till NMNH och National Air and Space Museum till NASM.

Metod
-----------------------

Utvecklarverktygen i Chrome används för att mäta antalet resurser som skickas till varje sida, hur lång tid det tar och sidornas totala storlek. Mätningarna av laddningstid görs tre gånger för varje sida och medelvärden räknas ut. Vissa sidor laddar resurser efterhand man scrollar, så kallad lat inläsning. För att få enkelt jämförbara resultat görs därför mätningarna av antalet resurser och storlek längst ner på varje sida där alla resurser har skickats och laddats upp. Att skjuta upp laddningen av vissa resurser kan bidra till högre prestanda och det kommer göras en notering av de sidor som använder tekniken. Resultaten härifrån kombineras med betyg och mätvärden från Pagespeed insights.

Resultat
-----------------------

<div class="embed-container">
<iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vR2ofQgiruvR4ALLAj2zrR9-Qvzfsm4zLOFKGbeOGLiaVnNLt9R-Cn4SWAs2Bn7a7AElEaKwRW7L36H/pubhtml?gid=0&amp;single=true&amp;widget=true&amp;headers=false" frameborder="0"></iframe>
</div>

Frans Hals Museum
-----------------------
<picture>
    <source
    srcset="
        %base_url%/image/03_franshalsmuseum.png?w=1200&save-as=jpg&q=50 2x,
        %base_url%/image/03_franshalsmuseum.png?w=600&save-as=jpg&q=50
    "
    media="(min-width: 600px)">
    <source
    srcset="
        %base_url%/image/03_franshalsmuseum.png?w=900&save-as=jpg&q=50 2x,
        %base_url%/image/03_franshalsmuseum.png?w=450&save-as=jpg&q=50
    "
    media="(min-width: 400px)">
    <img
    srcset="
        %base_url%/image/03_franshalsmuseum.png?w=700&save-as=jpg&q=50 2x
    "
    src="
        %base_url%/image/03_franshalsmuseum.png?w=350&save-as=jpg&q=50
    "
    alt="Frans Hals Museum website front page.">
</picture>

Sidan får varken godkänt på mobil eller desktop av Pagespeed insights test av viktiga webbvärden. Det är relativt långa väntetider på innehållet som tar längst tid att rendera (LCP) bland annat. På desktop upptäcker man också element som skiftar layouten på ett oväntat sätt mätt i Cumulative Layout Shift (CLS). Vilket kan vara störande för den som besöker webbplatsen. Det är många resurser som laddas in och framförallt bilder. Vilket jag också ser i mitt eget test. Gissningsvis är det bilder som laddas in sent som får layouten att skifta. Men det här är inget jag själv märker när jag besöker webbplatsen. Ett pluss är att det inte tar lång stund innan sidan är interaktiv på desktop enligt Pagespeed insights.

Webbplatsen använder lat inläsning för att skjuta upp laddningen av resurser som inte behövs direkt. Det snabbar upp den initiala inladdningen och ger ett bättre första intryck. För att förbättra sidan ytterligare kan man försöka optimera resurserna som används. Enligt page speed insights är bilderna den stora boven. Men även JavaScript och CSS-kod som blockerar renderingen av sidan onödigt mycket.  

När jag kollar på sidan i nätvärksfliken ser jag åtminstone sex foton som är sparade i bildformatet PNG och som med fördel kan sparas som JPEG istället för att minska filstorlekarna. Vill man ta det ytterligare ett steg hade man kunnat använda modernare bildformat som WebP exempelvis, som ger bättre komprimering. Då skulle man alltså kunna få ännu mindre filstorlekar utan att behöva tumma på kvaliteten. Vilket man inte gärna vill när man är ett museum där bilderna står i fokus.

Man bygger sidan med ramverket WordPress och bör se över vilka plugin och temamallar som används. För att optimera sidans prestanda och därmed förbättra upplevelsen är det viktigt att i så hög grad som möjligt se till att bara skript och stilregler som faktiskt används på sidan laddas in.

Sidan som använts i testerna: <a target="_blank" href="https://www.franshalsmuseum.nl/en/">Frans Hals Museum</a>

National Museum of Natural History
-----------------------
<picture>
    <source
    srcset="
        %base_url%/image/01_naturalhistory.png?w=1200&save-as=jpg&q=50 2x,
        %base_url%/image/01_naturalhistory.png?w=600&save-as=jpg&q=50
    "
    media="(min-width: 600px)">
    <source
    srcset="
        %base_url%/image/01_naturalhistory.png?w=900&save-as=jpg&q=50 2x,
        %base_url%/image/01_naturalhistory.png?w=450&save-as=jpg&q=50
    "
    media="(min-width: 400px)">
    <img
    srcset="
        %base_url%/image/01_naturalhistory.png?w=700&save-as=jpg&q=50 2x
    "
    src="
        %base_url%/image/01_naturalhistory.png?w=350&save-as=jpg&q=50
    "
    alt="National Museum of Natural History website front page.">
</picture>

Sidan får godkänt på både mobil och desktop av Pagespeed insights test av viktiga webbvärden. Den går också snabbast att ladda i mitt test. Värt att påpeka är att sidan laddar in minst antal resurser och är minst totalt sett. Vilket såklart har en inverkan på andra resultat. Så hur väl hanteras resurserna?

Man använder SVG på en del grafik som ikoner. På övriga bilder är det WebP som används, vilket som vi nämnt tidigare är ett bra alternativ till PNG och JPEG. Bilderna har dubbla filändelser vilket tyder på att de laddats upp som antingen PNG eller JPEG och gjorts om till WebP-formatet automatiskt. Man använder Drupal för att bygga webbplatsen och det finns moduler för sådant. Det är förmodligen det man använder. Jag uppfattar bilderna som mycket skarpa och högkvalitativa. Man hade nog kommit undan med att komprimera dem ännu mer utan att det gått att märka någon uppenbar försämring av kvaliteten.

Kollar vi på Pagespeed insights främsta rekommendation är det att välja bilder i rätt storlek. När jag granskar sidan i utvecklarverktygen ser jag flera exempel på det. Mot slutet på sidan ser vi som exempel en rad med tre bilder. De laddas in som 625 pixlar breda men visas i ungefär halva till bara en tredjedel av storleken beroende på hur brett fönstret är. Det kan vara befogat på enheter med högre upplösning, där pixelförhållandet i CSS är det dubbla eller tredubbla till och med. Ska man bara välja en storlek som kan visas på många olika enheter är det alltså ett rimligt val. Vill man däremot optimera bilderna kan det vara värt att ladda in olika storlekar beroende på den aktuella enhetens bredd och upplösning. Det här gäller i princip alla bilder på sidan.

Den största bilden som skickas verkar inte ens visas upp på mindre skärmar. Det är bilden av två barn som tar på en väggmålning. När bilden väl dyker upp är den inzoomad på mitten. Man får utgå från att inzoomningen är medveten och att det är därför man använder en så stor bild. Ett alternativ hade förstås varit att beskära bilden så att bara den del som faktiskt visas på sidan behöver laddas. Då bilden inte visas på mindre skärmar är dock frågan om den fyller någon funktion och behöver skickas i över huvud taget. Att behöva skicka bilden över ett dåligt nätverk exempelvis tycks orimligt kostsamt. Den översta bilden på sidan av elefanten är lika bred. Här utnyttjas däremot bredden och jag uppfattar bilden som betydligt viktigare för sidan. Men även denna skickas i full bredd på mindre skärmar när det egentligen inte behövs.

Pagespeed insights har även anmärkningar vad gäller JavaScript och CSS-kod som blockerar renderingen av sidan. Kanske finns det kod som kan kortas ner eller till och med tas bort om den inte är nödvändig. Använder man pluginmoduler bör man se över hur de är konfigurerade så att man bara laddar skript som faktiskt används. Man kan också tillämpa lat inläsning och skjuta upp laddning av resurser som inte behövs direkt. Många gånger är förstasidan inte dit man egentligen vill komma, utan man hoppar direkt vidare till en annan sida. Då är lat inläsning ett extra stort pluss  eftersom man som besökare ändå inte kommer se det som ligger below the fold så att säga.

Sidan som använts i testerna: <a target="_blank" href="https://naturalhistory.si.edu/">National Museum of Natural History</a>

National Air and Space Museum
-----------------------
<picture>
    <source
    srcset="
        %base_url%/image/01_airandspace.png?w=1200&save-as=jpg&q=50 2x,
        %base_url%/image/01_airandspace.png?w=600&save-as=jpg&q=50
    "
    media="(min-width: 600px)">
    <source
    srcset="
        %base_url%/image/01_airandspace.png?w=900&save-as=jpg&q=50 2x,
        %base_url%/image/01_airandspace.png?w=450&save-as=jpg&q=50
    "
    media="(min-width: 400px)">
    <img
    srcset="
        %base_url%/image/01_airandspace.png?w=700&save-as=jpg&q=50 2x
    "
    src="
        %base_url%/image/01_airandspace.png?w=350&save-as=jpg&q=50
    "
    alt="National Air and Space Museum website front page.">
</picture>

Sidan får inte godkänt på varken mobil eller desktop av Pagespeed insights test av viktiga webbvärden. Vi ser samma förbättringsförslag som innan. Det är många bilder som kan optimeras. Både vad gäller att välja rätt storlek och bildformat. Likt sidan innan använder man Drupal. Här ser jag dock inte att man utnyttjar något hjälpmedel för att generera optimala varianter av bilderna. Det är i första hand JPEG och PNG som visas. Förslagen handlar också om att reducera kod som inte behövs och att skjuta upp mindre viktiga resurser till huvudinnehållet på sidan har laddats.

Man laddar in tredjepartskod som används för att bädda in video. Videon som visas är nästan längst ner på sidan. Och man skulle med stor fördel kunna vänta med laddningen till man kommer dit om möjligt. Det verkar också vara fel på inbäddningen av något videoklipp som gör att laddningen av sidan aldrig riktigt slutförs. Pagespeed insights rekomenderar att man begränsar användningen av kod från tredjepartsleverantörer generellt. I det här fallet verkar koden för inbäddning som kommer från YouTube orsaka betydande fördröjningar.

Sidan som använts i testerna: <a target="_blank" href="https://airandspace.si.edu/">National Air And Space Museum</a>

Analys
-----------------------

På alla tre sidor är bilderna det man vinner mest på att optimera.  Förmodligen gäller det museumsidor generellt då man gärna använder mycket bilder. Det handlar om att använda rätt storlek och modernare bildformat som ger bättre komprimering. Enklare sagt än gjort kan man tycka. Och visst kan det innebära extra jobb. Nackdelen med många modernare bildformat är att de inte har lika god kompatibilitet som PNG eller JPEG exempelvis. Det blir alltså inte bara en fråga om att byta ut formatet på bilderna, utan det behövs olika format-varianter av samma bild och kod som gör att dessa används optimalt i olika webbläsare. Som vi sett kan man få hjälp att programmatiskt generera varianter av uppladdade bilder i optimala format. Om man inte redan gör det är det något som man åtminstone bör testa och utvärdera resultatet av. Antagligen kan man hitta plugin som fungerar inom det egna ramverket och som dessutom är gratis.

Ett annat sätt att snabba upp laddningstiderna är att reducera mängden JavaScript och CSS. Det kan finnas kod som inte är nödvändig eller som inte används i över huvud taget. Man bör också se till att minifiera kod innan den laddas upp. Pluginmoduler och färdiga teman kan underlätta arbetet med att bygga och designa en sida avsevärt. Men det ställer också krav på att utvärdera hur sidan presterar och att hålla sig uppdaterad med det senaste. Om moduler laddar överflödiga resurser eller gör att sidan slutar fungera som det är tänkt bör man ändra i koden. Man ska också fråga sig vilka resurser som faktiskt behövs. Om man bara har en bild på sin sida kanske det inte är värt kostanden att ladda extra skript för att automatiskt göra om den till ett annat format exempelvis.

Rent allmänt skulle jag säga att 1-2 sekunder är en snabb laddningstid. Sitter jag hemma med min bärbara dator och god nätverksanslutning förväntar jag mig att innehåll åtminstone ska börja dyka upp då. Ofta gör det inget om det tar ett par sekunder till att slutföra laddningen så länge man kan börja interagera med det som finns. Även 3-4 sekunder är inom någon slags rimlig gräns. Men tar det längre tid än så skulle jag tycka att det går långsamt. Och tar det lång stund att ens ladda det första innehållet blir jag misstänksam. Då tänker jag att sidan i bästa fall är gammal eller dåligt designad. Tankarna går också till skadlig kod och att man håller på att bli omdirigerad. Intrycket är i vilket fall som helst oseriöst och jag väljer ofta att gå vidare innan sidan laddat färdigt. Talar vi om användarupplevelse kan långa laddningstider alltså skicka helt fel signaler redan innan man sett sidan. 

Jag uppfattar sidorna i testet som snabba eller mycket rimliga åtminstone. NASM uppfattar jag som långsammast. NMNH är snabbast. Den är också minst storleksmässigt. Att jag tar upp storleken är inget som bör tolkas som minuspoäng. Visserligen gör det att man i teorin kan komma undan med sämre optimering av enskilda resurser och ändå få jämförelsevis bra tider. Men det är ju också goda skäl att hålla nere storleken. Som jag redan varit inne på är förstasidan en viktig del i helhetsupplevelsen. Att åtminstone hålla förstasidan relativt slimmad är något man på riktigt bör överväga. Men det är snarare en fråga om design i grunden än optimering. Att använda lat inläsning är ett alternativ som gör att man i princip kan få båda delarna. Idag ser vi det användas överallt, på sociala medier, nyhetssajter och streamingtjänster bara för att ge ett par exempel.

av Alex Lindqvist
