# transcriptomics
casus

goede titel concluderende titel 
goed repruceerbaarheid, verwijzingen, ref genoom allemaal erbij zetten ook die gft, welke pathway, krijgen van de data ook vertellen verwijzen waar de artikel vandaan is lijst met accasion nummers 




INTRODUCTIE
RNA-sequencing (RNA-seq) is een techniek waarmee genexpressie op grote schaal kan worden geanalyseerd. Met deze methode kan worden bepaald welke genen actief zijn in een cel en hoe deze activiteit verandert onder verschillende omstandigheden, zoals ziekte of behandeling (Ozsolak & Milos, 2011). In deze casus wordt RNA-seq toegepast om verschillen in genexpressie te onderzoeken tussen patiënten met reumatoïde artritis (RA) en gezonde controlemonsters.
Reumatoïde artritis is een chronische auto-immuunziekte die gekenmerkt wordt door ontsteking van gewrichten en weefselschade. Hoewel de exacte oorzaken nog niet volledig bekend zijn, is aangetoond dat veranderingen in genexpressie een belangrijke rol spelen in het ziekteproces (Smolen et al., 2016). Door deze veranderingen in kaart te brengen, kan meer inzicht worden verkregen in de moleculaire mechanismen die betrokken zijn bij RA.
Het doel van dit onderzoek is om genen te identificeren die differentieel tot expressie komen tussen RA-patiënten en controles. Daarnaast wordt onderzocht welke biologische processen mogelijk betrokken zijn door middel van pathway-analyse en Gene Ontology (GO)-analyse. Deze aanpak draagt bij aan een beter begrip van de biologische processen die ten grondslag liggen aan reumatoïde artritis.
Om dit doel te bereiken zijn de volgende deelvragen opgesteld:
  Welke genen zijn significant differentieel tot expressie tussen RA-patiënten en controles?
  Welke biologische pathways (KEGG) zijn mogelijk betrokken bij deze verschillen?
  Welke Gene Ontology (GO)-categorieën zijn verrijkt in de set differentieel geëxpresseerde genen?


Ozsolak, F., & Milos, P. M. (2011).
RNA sequencing: advances, challenges and opportunities. Trends in Biotechnology, 29(10), 473–483.
https://www.sciencedirect.com/science/article/pii/S1367593112001585 

Smolen, J. S., Aletaha, D., & McInnes, I. B. (2016).
Rheumatoid arthritis. The Lancet, 388(10055), 2023–2038.
https://www.sciencedirect.com/science/article/abs/pii/S0140673616301738


METHODE
De RNA-seq analyse werd uitgevoerd met behulp van bio-informatica tools in R. De dataset bestond uit RNA-seq reads van patiënten met reumatoïde artritis (RA) en gezonde controles. De sequencingdata bestond uit short-read sequenties (FASTQ-format), verkregen via high-throughput sequencing.
In de eerste stap werden de reads gemapt op het humane referentiegenoom (GRCh38) met behulp van het Rsubread package. Hierbij werd bepaald waar de reads zich bevinden op het genoom. De resulterende BAM-bestanden werden gesorteerd en geïndexeerd met Rsamtools om efficiënte downstream analyses mogelijk te maken.
Vervolgens werd met de functie featureCounts het aantal reads per gen bepaald op basis van een GTF-annotatiebestand. Dit resulteerde in een count matrix waarin per gen en per sample het aantal reads werd weergegeven.
De differentiële genexpressie-analyse werd uitgevoerd met het DESeq2 package. Hiermee werden genen geïdentificeerd die significant verschillen in expressie tussen RA- en controlemonsters. De resultaten werden gevisualiseerd met een volcano plot.
Daarnaast werd een KEGG pathway-analyse uitgevoerd met het pathview package en een Gene Ontology (GO)-analyse met het goseq package. Deze analyses werden gebruikt om biologische processen en pathways te identificeren die mogelijk betrokken zijn bij de waargenomen verschillen. Het volledige script en de gebruikte data zijn beschikbaar in de bijbehorende GitHub-repository.

FLOWSCHEMA

RESULTATEN
De differentiële genexpressie analyse werd uitgevoerd om verschillen tussen RA-patiënten en controlemonsters te identificeren. Op basis van een drempelwaarde van een adjusted p-value (padj) < 0.05 en een log2FoldChange groter dan 1 of kleiner dan -1 werden significante genen geselecteerd. In totaal werd één gen significant opgereguleerd in RA-patiënten, terwijl drie genen significant neer-gereguleerd waren. Dit wijst op een relatief beperkt aantal differentieel geëxpresseerde genen binnen deze dataset.
De meest significante genen werden geïdentificeerd door de resultaten te sorteren op padj. Het gen ND1 vertoonde een sterke toename in expressie in RA-patiënten (log2FoldChange = 3.25; padj = 0.008), terwijl genen zoals TRNN en TRNC een sterke afname in expressie lieten zien (log2FoldChange < -8; padj < 0.015). Daarnaast vertoonden ook LOC101928344 en andere genen een lagere expressie in RA-patiënten.
De resultaten werden gevisualiseerd met een volcano plot (Figuur 1), waarin de relatie tussen log2FoldChange en significantie wordt weergegeven. Hieruit blijkt dat slechts een klein aantal genen voldoet aan de gekozen significantiedrempels, wat consistent is met het lage aantal gevonden differentieel geëxpresseerde genen.
De Gene Ontology (GO)-analyse identificeerde geen significant verrijkte categorieën (padj < 0.05). Ook werd geen overlap gevonden tussen de geselecteerde genen en GO-termen, wat mogelijk verklaard kan worden door het geringe aantal differentieel geëxpresseerde genen (n = 9).

CONCLUSIE
In dit onderzoek is RNA-seq data geanalyseerd om verschillen in genexpressie tussen RA-patiënten en controlemonsters te identificeren. De differentiële expressie analyse liet zien dat slechts een beperkt aantal genen significant verschilde tussen beide groepen. In totaal werd één gen significant opgereguleerd in RA-patiënten en drie genen significant neer-gereguleerd. Dit wijst op relatief kleine veranderingen in genexpressie binnen deze dataset.
De meest opvallende genen waren onder andere ND1, dat sterk verhoogd tot expressie kwam in RA-patiënten, en TRNN en TRNC, die juist sterk verlaagd waren. Deze resultaten suggereren mogelijke veranderingen in mitochondriale activiteit en RNA-gerelateerde processen, wat relevant kan zijn voor de pathofysiologie van reumatoïde artritis.
De aanvullende GO-analyse identificeerde geen significant verrijkte biologische processen. Dit kan verklaard worden door het geringe aantal differentieel geëxpresseerde genen en de beperkte overlap met beschikbare GO-annotaties. Hierdoor was de statistische power van de analyse laag.
Hoewel de resultaten beperkt zijn, tonen ze aan dat RNA-seq analyse geschikt is om verschillen in genexpressie te detecteren. Voor toekomstig onderzoek wordt aanbevolen om grotere datasets te analyseren en meer replicaten te gebruiken, zodat betrouwbare conclusies over betrokken biologische processen en pathways kunnen worden getrokken. Hiermee kan het onderzoek verder bijdragen aan inzicht in de moleculaire mechanismen achter reumatoïde artritis.







## Introductie
Reumatoïde artritis (RA) is een chronische auto-immuunziekte waarbij het immuunsysteem het eigen lichaam aanvalt, vooral de gewrichten. Dit leidt tot ontsteking van het gewrichtsslijmvlies, wat pijn en uiteindelijk schade aan de gewrichten veroorzaakt. De precieze oorzaak van RA is nog niet volledig bekend, maar het lijkt een combinatie te zijn van genetische aanleg en omgevingsfactoren (Gabriel, 2001). Ook is bekend dat afweerstoffen en ontstekingsprocessen een grote rol spelen in de ziekte (Radu & Bungau, 2021).

Met behulp van transcriptomics kan onderzocht worden welke genen anders tot expressie komen bij mensen met RA in vergelijking met gezonde personen. Dit geeft inzicht in de onderliggende biologische processen en kan helpen om beter te begrijpen hoe de ziekte ontstaat en zich ontwikkelt.

In dit onderzoek wordt gekeken naar genexpressie in synoviumweefsel van RA-patiënten en controles. De doelstelling is om te bepalen welke genen en pathways verschillend tot expressie komen tussen deze groepen. Hierbij horen de volgende deelvragen: Welke genen zijn significant verschillend tot expressie? En welke biologische processen zijn hierbij betrokken?

Op basis van bestaande kennis wordt verwacht dat genen die betrokken zijn bij het immuunsysteem en ontstekingsreacties verhoogd tot expressie zullen zijn bij RA-patiënten.


## Methode 
[script](script/)


## Resultaten
De differentiële genexpressie-analyse werd uitgevoerd op synoviumweefsel van RA-patiënten en controles met behulp van DESeq2. In totaal werden 3178 genen geïdentificeerd als significant differentieel tot expressie (padj < 0.01). Hiervan waren 1786 genen opgereguleerd in RA en 1297 genen neer-gereguleerd. In de volcano plot (Figuur 1) is te zien dat een groot aantal genen zowel een hoge log₂ fold change als een lage p-waarde heeft, wat wijst op sterke verschillen tussen de groepen. Enkele van de meest significante genen zijn ANKRD30BL, MT-ND6 en RAB3IL1, die sterk verhoogde expressie vertonen in RA.
Functionele analyse met Gene Ontology (GO) laat zien dat vooral immuun-gerelateerde processen verrijkt zijn (Figuur 2). De meest significante GO-termen zijn onder andere immunoglobulin complex, adaptive immune response, antigen binding en immune system process. Deze resultaten geven aan dat genen die betrokken zijn bij het immuunsysteem en antistofproductie een belangrijke rol spelen in RA. Daarnaast werden ook termen gevonden die wijzen op betrokkenheid van B-cellen en T-cellen, zoals B cell receptor signaling pathway en T cell receptor complex.
Samen tonen deze resultaten aan dat er bij RA sprake is van een sterke activatie en ontregeling van het immuunsysteem, wat consistent is met het bekende ziektebeeld.

bijschift hoe je moet aflezen en resultaten straight to the point


## Conclusie

In dit onderzoek is gekeken naar verschillen in genexpressie tussen RA-patiënten en gezonde controles met behulp van RNA-seq analyse. De resultaten laten zien dat er duidelijke verschillen zijn in genexpressie, waarbij een groot aantal genen significant op- of neer-gereguleerd is. De differentiële expressie-analyse en de volcano plot tonen dat veel genen sterk veranderd zijn bij RA.

De GO-analyse en KEGG pathway-analyse bevestigen dat vooral genen die betrokken zijn bij het immuunsysteem en ontstekingsprocessen een belangrijke rol spelen. Met name processen zoals *adaptive immune response*, *immunoglobulin complex* en *B cell receptor signaling* zijn sterk verrijkt. Dit laat zien dat het immuunsysteem overactief is bij RA en dat antistoffen en immuuncellen een grote rol spelen in de ziekte. Deze resultaten passen goed bij wat al bekend is over RA als auto-immuunziekte.

Een beperking van dit onderzoek is het gebruik van een relatief kleine dataset en subset sequencing data, wat invloed kan hebben op de nauwkeurigheid van de resultaten. Toekomstig onderzoek zou gebruik kunnen maken van grotere datasets en aanvullende analysemethoden.

Samenvattend laat dit onderzoek zien dat transcriptomics een waardevolle methode is om inzicht te krijgen in de onderliggende mechanismen van RA, en kan bijdragen aan het ontwikkelen van betere behandelingen.

versie nummers en beetje packages noemen welke je hebt gebruikt niet de codes en vertellen hoe en wat je ermee hebt gedaan verwijzen naar script feature counts tabel met patieten




