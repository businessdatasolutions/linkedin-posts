# In 2 maanden tijd 12 educatieve apps gebouwd met AI — dit is wat ik leerde

In januari en februari van dit jaar heb ik met behulp van AI twaalf interactieve webapplicaties gebouwd voor onderwijs en training. Van boekhoudsimulatoren tot strategietools, van toetsgeneratoren tot onderzoeksworkshops. Zonder AI was dit het werk van een heel team geweest. Met AI was het het werk van één docent met een helder beeld van wat studenten nodig hebben.

In dit artikel deel ik wat ik heb gebouwd, hoe ik het heb aangepakt, en wat ik ervan heb geleerd.

---

## Wat ik heb gebouwd

### Simulaties en spelend leren

Studenten leren door te doen, niet door te lezen. Daarom heb ik meerdere simulaties gebouwd waarin studenten actief beslissingen nemen en directe terugkoppeling krijgen.

**FreshBites** (hanbedrijfskunde.github.io/fresh-bites) is een boekhoudsimulatie waarin studenten een volledige werkdag meelopen als boekhouder van een foodtruck. Ze verwerken zes transacties onder tijdsdruk, stellen journaalposten samen, en kunnen aanwijzingen inzetten die hun score beïnvloeden. De transacties worden at random gegenereerd, zodat elke student een unieke combinatie krijgt.

Met de **AEX Monte Carlo Simulator** (hanbedrijfskunde.github.io/aex-mc-simulator) oefenen studenten beleggingsbeslissingen op basis van echte AEX-marktdata. De simulator genereert duizenden scenario's en laat studenten de relatie tussen risico en rendement ervaren — inclusief de theorie achter het CAPM-model.

**PredictivePulse AI** (hanbedrijfskunde.github.io/predictive-maintenance-demo) simuleert een digitale tweeling van industriële machines. Studenten volgen live gezondheidsscores, detecteren anomalieën, en zien de zakelijke impact van voorspellend onderhoud op stilstand en OEE.

### Strategie-onderwijs

Strategische concepten zijn abstract. Deze hulpmiddelen maken ze tastbaar.

De **Strategische Analogie Builder** (businessdatasolutions.github.io/analogy-strategyzing) dwingt studenten en adviseurs om hun strategische analogie ("wij zijn de Uber van X") te onderbouwen met causale mechanismen. Waarom werkte die strategie bij het bronbedrijf, en gelden dezelfde condities bij jouw organisatie?

De **Emergent Strategy Tutorial** (businessdatasolutions.github.io/emergent-strategy-tutorial) neemt studenten mee van klassieke strategie (Porter, Ansoff) naar organische strategie (Mintzberg, complexe adaptieve systemen). Een interactieve, stapsgewijze tutorial met visuele vergelijkingen en praktijkvoorbeelden.

Met de **Innovatieradar** (businessdatasolutions.github.io/innovatieradar) beoordelen studenten het innovatievermogen van een organisatie op twaalf dimensies, gebaseerd op het wetenschappelijke raamwerk van Sawhney, Wolcott en Arroniz (MIT Sloan, 2006). De resultaten worden gevisualiseerd als radardiagram, inclusief historische vergelijking en concrete aanbevelingen.

De **Strategy Map** (hanbedrijfskunde.github.io/strategy-map-example) visualiseert oorzaak-gevolgrelaties over vier perspectieven op basis van het Six Capitals model. Studenten zien hoe investeringen in leren en groei uiteindelijk leiden tot financiële en maatschappelijke impact.

### Toetskwaliteit en toetsing

AI als co-piloot voor docenten bij het bewaken van toetskwaliteit.

De **MC Toetsgenerator** (businessdatasolutions.github.io/mc-toetsgenerator) is een platform met twee modules: validatie van bestaande meerkeuzevragen (geautomatiseerde kwaliteitsanalyse op validiteit, betrouwbaarheid en technische kwaliteit) en generatie van nieuwe vragen op basis van studiemateriaal. Beide modules combineren deterministische regels met LLM-analyse en toetsen tegen Bloom's taxonomie.

### Onderzoek en vaardigheden

Gerichte mini-toepassingen voor specifieke leeruitkomsten.

De **Survey Bias Quiz** (hanbedrijfskunde.github.io/survey-bias) leert studenten vertekening in enquêtevragen herkennen en vermijden. Studenten vergelijken een bevooroordeelde en een neutrale versie van dezelfde vraag, krijgen directe terugkoppeling, en ontvangen na afloop een uitgebreide referentiegids.

De **Workshop Onderzoekend Vermogen** (hanbedrijfskunde.github.io/straor-ond-workshop) is een interactieve webapp voor een 90-minuten workshop, toegankelijk via QR-code op mobiel. Studenten leren een onderbouwde onderzoeksvraag formuleren — van nieuwsgierigheid naar vraagstelling.

De **Ontologie Briefing** (hanbedrijfskunde.github.io/ontology-ivan-baran) bereidt studenten voor op een praktijkproject bij een tech-bedrijf. Een scrollbare webbriefing die uitlegt waarom ruwe machinedata betekenis nodig heeft, hoe ontologieën die bieden, en hoe AI-systemen daar slimme beslissingen mee nemen.

### Docent- en procestools

De **Supervisory Dashboard** (hanbedrijfskunde.github.io/supervisory-dashboard) helpt begeleiders van afstudeerstages het begeleidingsproces per student bij te houden: groepsbeheer, statusoverzicht, en een activiteitendashboard per week.

Het **Masterclass AI Werkboek** (businessdatasolutions.github.io/masterclass-ai/book) is een interactief digitaal werkboek voor de Masterclass AI. Een Quarto-gebaseerd online boek met theorie, interactieve oefeningen en strategische matrices voor AI-implementatie in organisaties.

---

## Wat ik heb geleerd

### Docent als regisseur, AI als uitvoerder

Mijn rol was puur inhoudelijk en onderwijskundig: welke concepten moeten studenten begrijpen, welke misvattingen moeten ze overwinnen, hoe ziet een effectieve leerervaring eruit? Het startpunt was interessant bronmateriaal — een wetenschappelijk artikel, een boek, of een transcriptie van een YouTube-video. Van daaruit deed ik suggesties voor toepassingsvormen: een synthese-tool, een interactieve oefening, een simulatie. AI werkte die vervolgens technisch uit.

Bij de Emergent Strategy Tutorial bijvoorbeeld was de context een module over Verandermanagement. Ik wilde studenten een ander perspectief bieden dan het klassieke paradigma van verandering als programma of project. Mijn startpunt was de talk van Simon Sinek over Infinite Games — gebaseerd op Game Theory — en het artikel van Werner & Le-Brun (2025), "Become an Octopus Organization" uit Harvard Business Review. Van daaruit suggereerde ik een interactieve tutorial die klassieke en organische strategie naast elkaar zet. Bij de Innovatieradar definieerde ik de twaalf dimensies van het wetenschappelijke raamwerk en de didactische opbouw. AI vertaalde dat telkens naar werkende webapplicaties.

Het knelpunt verschuift zo van techniek naar didactisch ontwerp. En dat is precies waar hij hoort.

### Van PRD naar LRD: software best practices voor onderwijs

Bij grotere projecten paste ik een bewezen werkwijze uit de softwarepraktijk toe: beginnen met een requirements document. Maar in plaats van een Product Requirement Document schreef ik een Learner Requirement Document — met de student centraal.

Mijn vaste werkproces voor workshops en modules werd een drietraps-proces:

1. **LRD** — leerdoelen, acceptatiecriteria, functionele eisen. Het *wat* en *waarom*.
2. **Draaiboek** — de workshopflow met tijdsblokken en fasering. Het *wanneer*.
3. **Activiteiten** — de concrete interactieve oefeningen, tools en simulaties. Het *hoe*.

Elke stap bouwde voort op de vorige — en bij elke stap werkte AI de uitwerking uit op basis van mijn inhoudelijke kaders. Het LRD fungeerde als contract tussen docent en AI. Ik definieerde het wat en waarom, AI realiseerde het hoe.

### AI versnelt ontwerp, niet alleen bouw

AI versnelt niet alleen het bouwen, maar ook het ontwerpen van leerervaring. Doordat de technische drempel wegvalt, kun je sneller experimenteren met verschillende didactische vormen — een simulatie, een quiz, een interactieve tutorial — en direct zien wat werkt.

Maar dat betekent niet dat alles digitaal moet. Bij de onderzoeksposter liet ik sommige groepen de poster online invullen en andere groepen op een flipover met post-its en stiften. Het verschil was opvallend: bij de analoge versie gingen studenten rondlopen en met elkaar in gesprek, terwijl bij de digitale versie studenten bleven zitten en soms werden afgeleid door andere zaken op hun apparaat.

De les: de kracht zit in de mix. AI maakt het makkelijk om digitale tools te bouwen, maar als docent moet je per activiteit bewust kiezen wat het leren het beste dient.

---

## Jouw beurt

Alle genoemde tools zijn open source en live te proberen. Maar ik wil verder dan alleen delen.

**Stuur me jouw lastigste onderwijsprobleem in één zin.** Eén concept dat studenten niet snappen, één vaardigheid die ze niet oefenen, één proces dat vastloopt. Ik bouw er binnen een week een werkend prototype voor.

### Verder bouwen?

Wil je van prototype naar volwaardig product? Dat kan ook:

**Doorontwikkeling op maat** — Het prototype aanpassen aan jouw huisstijl, LMS-integratie, studenttracking of organisatie-specifieke scenario's.

**Live deconstructie voor je team** — Een sessie van 90 minuten waarin ik met jouw opleidingsteam live een tool bouw rondom jullie eigen materiaal. Jullie gaan naar huis met een werkend prototype én inzicht in het proces.

**Train-de-trainer** — Leer zelf met AI interactieve leertools bouwen via het LRD-werkproces. Van bronmateriaal naar werkende applicatie — zonder technische achtergrond.

Stuur me een bericht.
