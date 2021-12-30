# Een Datagedreven Queeste naar de Ideale Whisky

Daar ik in den vreemden gesitueerd ben, heb ik een verminderde mogelijkheid om met u mee te genieten van levenswater aller soorten en maten. Toch is reeds een zorgwekkend feit opgevallen: op de borrels die ik bijwonen mocht, leek zowel het aanbod aan whisky als de hunkering van ons ledenebestand naar whisky beneden peil.

Hierop besloot ik direct op te ageren. In het geheim smeedde ik een plan om u te enthousiasmeren voor een nieuwe whisky. Natuurlijk had ik u eenvoudigerwijs kunnen vertellen van een whisky waarvan ik louter verhalen heb gehoord, maar ook ik zag in dat dit een zwakke vorm van evidentialiteit zou vormen. Daarop besloot ik mijn rede en zoektocht te onderbouwen met knoertharde empirische feiten. Volgt mij door de wereld van het machinaal en statistisch leren op een queeste om u, den lezer, tot het begrijpen te dwingen.

Op het wereld-wijde-web vond ik een dataset van 86 Schotse whiskies (https://outreach.mathstat.strath.ac.uk/outreach/nessie/nessie_whisky.html), allen door experts beoordeeld op een dozijn criteria: met een schaal van 1 tot 4: Volume, Zoet, Rokerig, Tabak-gelijkenis, Medicinaliteit, Honingachtig, Pittig, Wijnachtig, Noterig, Moutig, Fruitig en Bloemig.

Ik besloot de whisky's te classificeren op basis van dit smaak-profiel. De meeste statistische leeralgoritmen, echter, zijn *begeleid* en vereisen een grote hoeveelheid 'trainingsdata': Data die nodig is om de prestaties van het algoritme te optimaliseren. Daarnaast is een vereiste een vooraf gekozen set van klassen waarin de data waarin men geïnteresseerd is te verdelen valt. In dit geval heb ik geen van beiden. Daarom stel ik een andere vraag: wat is de beste manier om deze 86 whisky's in $k$ klassen in te delen, zonder dat ik vooraf weet wat die klassen precies zijn?

Dit soort vragen kan beantwoordt worden met zogeheten *onbegeleide parametrische classificatie-algoritmen*: Ze vereisen geen trainingsdata, en vullen zelf de klassen in aan de hand van vooraf ingestelde hoeveelheid klassen $k$. Een nadeel van deze algoritmen is dat men een *post-hoc* analyse dient uit te voeren om naderhand te kunnen zien hoe het algoritme de data precies verdeelt heeft. Voor deze dataset kies ik het redelijk simpele algoritme genaamd "k-means" (https://en.wikipedia.org/wiki/K-means_clustering). Het principe is als volgt:

1. Genereer $k$ willekeurige nep-datapunten
2.  Ga alle 86 whiskies langs, kijk welk van de $k$ nep-datapunten het dichtste bij is, en wijs de whisky die klasse toe.
3. Nu zijn alle whiskies ingedeeld in $k$ klassen, neem het gemiddelde van elke klasse en gebruik deze als nieuwe nep-datapunten en begin opnieuw bij stap 2.
4. Stop wanneer de $k$ gemiddelden niet meer of alleen nog minimaal veranderen.

De hamvraag in deze kwestie is uiteraard: hoeveel $k$ klassen heb ik nodig? Een  standaard-routine is om dit algoritme uit te voeren met verschillende waarden van $k$ en te kijken naar de variatie per klasse. Dit wordt natuurlijk kleiner naarmate het aantal klassen groeit: Bij $k = 86$ heeft iedere whisky zijn eigen klasse en is de variatie per klasse gelijk aan $0$. Men kiest dan een waarde voor $k$ ongeveer in het midden. Hieronder valt de variatie per waarde van $k$ te zien. Ik kies voor $k = 4$.

[afbeelding1]

Ik heb deze analyse met succes uitgevoerd op de 86 whisky's. Om deze groeperingen te visualiseren ben ik genoodzaakt een trucje uit te voeren: de whisky's zijn geclassificeerd op basis van 12 dimensies (boven beschreven), het menselijk oog kan helaas niet meer dan 3 van deze waarnemen. Daarom moet ik de data in dimensionaliteit reduceren naar 2 of 3. Ik doe dit middels een Hoofdcomponentenanalyse (https://nl.wikipedia.org/wiki/Hoofdcomponentenanalyse) die ik om wille van ruimte niet verder uitleg. De onderstaande grafiek laat de resultaten van de k-means analyse zien in twee dimensies. Duidelijk is dat cluster 2 (paars) het verst af staat van de andere groepen.

[afbeelding2]

Tweedens kunnen we de berekende gemiddelden van iedere groep bekijken in onderstaande tabel. Klasse 3 (rood) whisky's lijken gekarakteriseerd te worden door een zoete smaak, klasse 2 (paars) whisky's zijn rokerig en sterk van karakter, klasse 1 (groen) whisky's zijn klassiek en gebalanceerd en klasse 0 (blauw) whisky's zijn licht en zwakker van smaak. 

[afbeelding3]

Ik besloot nu concreet op zoek te gaan naar de ideale whisky voor An t-Uisge. Natuurlijk zou de ideale An t-Uisge whisky gekarakteriseerd worden door een hoge mate van rokerigheid, medicinale kracht, pit met hinten van noten en mout. Aan de andere kant moeten wij niets hebben van zoetheid en fruitigheid. Ik besloot dat deze legendarische whisky de volgende score zou krijgen. Niet verwonderlijk deelt de k-means analyse deze whisky in in klasse 2 (paars). 

[afbeelding4]

Deze whisky is legendarisch met een rede: hij is (nog) fictief. Daarom heb ik deze fictieve whisky vergeleken met alle 86 whisky's uit de data en gekeken welke de hoogste cosinusgelijkheid (https://nl.wikipedia.org/wiki/Cosinusgelijkenis) heeft: stel je trekt in een assenstelsel een lijn door het nulpunt en door een datapunt $x$ en doet hetzelfde met datapunt $y$, wat is dan de hoek tussen de lijnen $x$ en $y$? Een hoek van $0$ graden betekent natuurlijk geen verschil tussen de lijnen. Met een cosinusgelijkenis van maar liefst $0.9$ (slechts een hoek van $5$ graden) kwam ik uit op de whisky van destilleerderij **Caol Ila** (de laagste score is overigens Auchentoshan (klasse 3, rood), dus blijf hiervan weg!). Om meer te weten te komen over deze destilleerderij, plotte ik de coördinaten van alle destilleerderijen op een kaart van Schotland. **Caol Ila** is met paars omcirkeld. Noot: Door verschillen in coördinaatsystemen zijn de locaties niet helemaal accuraat (er zijn geen destilleerderijen in zee), maar nog wel ongeveer.

[afbeelding5]

De conclusie van deze queeste is dat het volgende dispuutsuitje moet plaatsvinden op Islay in Schotland, daar waar de illustere **Caol Ila** gedestilleerd wordt. Tot die tijd hoop ik u te hebben ge-enthousiasmeerd voor een nieuwe whisky die perfect bij ons dispuut past en daarnaast hoop ik dat u iets heeft opgestoken van de methodologie van dit betoog. Hij valt te halen bij Dirck III (https://www.dirckiii.nl/caol-ila-single-malt-12-years-70-cl). 