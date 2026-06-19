# transcriptomics
casus

goede titel concluderende titel 
goed repruceerbaarheid, verwijzingen, ref genoom allemaal erbij zetten ook die gft, welke pathway, krijgen van de data ook vertellen verwijzen waar de artikel vandaan is lijst met accasion nummers 

## Introductie
Reumatoïde artritis (RA) is een chronische auto-immuunziekte waarbij het immuunsysteem het eigen lichaam aanvalt, vooral de gewrichten. Dit leidt tot ontsteking van het gewrichtsslijmvlies, wat pijn en uiteindelijk schade aan de gewrichten veroorzaakt. De precieze oorzaak van RA is nog niet volledig bekend, maar het lijkt een combinatie te zijn van genetische aanleg en omgevingsfactoren (Gabriel, 2001). Ook is bekend dat afweerstoffen en ontstekingsprocessen een grote rol spelen in de ziekte (Radu & Bungau, 2021).

Met behulp van transcriptomics kan onderzocht worden welke genen anders tot expressie komen bij mensen met RA in vergelijking met gezonde personen. Dit geeft inzicht in de onderliggende biologische processen en kan helpen om beter te begrijpen hoe de ziekte ontstaat en zich ontwikkelt.

In dit onderzoek wordt gekeken naar genexpressie in synoviumweefsel van RA-patiënten en controles. De doelstelling is om te bepalen welke genen en pathways verschillend tot expressie komen tussen deze groepen. Hierbij horen de volgende deelvragen: Welke genen zijn significant verschillend tot expressie? En welke biologische processen zijn hierbij betrokken?

Op basis van bestaande kennis wordt verwacht dat genen die betrokken zijn bij het immuunsysteem en ontstekingsreacties verhoogd tot expressie zullen zijn bij RA-patiënten.


## Methode 
flowschema en tabel patienten

In dit onderzoek werd de genexpressie van synoviumbiopten van patiënten met reumatoïde artritis (RA) vergeleken met die van gezonde controles. De gebruikte RNA-seq dataset is afkomstig uit eerder gepubliceerd onderzoek (Platzer et al., 2019) en werd verkregen via de NCBI Sequence Read Archive. De dataset bestond uit 8 samples, verdeeld over een controlegroep en een RA-groep (zie Tabel 1). De analyse werd uitgevoerd op single-end raw sequencing reads in FASTQ-formaat.

<p align="center">
  <strong>Tabel 1. Overzicht van de RNA-seq samples gebruikt in de analyse</strong><br><br>
  <img width="655" height="248" alt="Schermafbeelding 2026-06-19 121709" src="https://github.com/user-attachments/assets/78cb6a64-5278-419a-ae07-f40a3baa38ad" />
  
  <em>
Toelichting: De tabel toont de gebruikte RNA-seq samples afkomstig van synoviumweefsel. In totaal zijn 8 samples geanalyseerd, waarvan 4 controles (Normal) en 4 RA-patiënten (Rheumatoid arthritis, established &gt;12 maanden). Alle samples zijn afkomstig van vrouwelijke individuen. Sample ID verwijst naar de accessionnummers uit de oorspronkelijke dataset (Platzer et al., 2019).
  </em>
</p>


De RNA-seq data werden geanalyseerd in de programmeeromgeving R (v4.6.0) met behulp van verschillende Bioconductor-packages, waaronder Rsubread (v2.26.0), Rsamtools (v2.28.0), DESeq2 (v1.52.0), KEGGREST (v1.52.0), EnhancedVolcano (v1.30.0), pathview (v1.52.0), goseq (v1.64.0) en org.Hs.eg.db (v3.23.1). Allereerst werd het humane referentiegenoom GRCh38 (GCF_000001405.40; https://www.ncbi.nlm.nih.gov/datasets/genome/GCF_000001405.40/) voorbereid en gebruikt om de sequencing reads te aligneren. De verkregen alignments werden vervolgens verwerkt tot gesorteerde en geïndexeerde BAM-bestanden, zodat de mappingresultaten geschikt waren voor verdere analyse.

Vervolgens werd op basis van deze alignments een count matrix opgesteld, waarin het aantal reads per gen werd bepaald. Deze matrix vormde de basis voor de differentiële genexpressie-analyse met behulp van het DESeq2 package (v1.52.0), waarbij genen met een adjusted p-waarde kleiner dan 0.01 als significant differentieel tot expressie werden beschouwd. De resultaten van deze analyse werden gevisualiseerd met behulp van het EnhancedVolcano package (v1.30.0).

Voor de biologische interpretatie van de resultaten werd een KEGG pathway-analyse uitgevoerd met het pathview package (v1.52.0), waarbij genidentificatie werd omgezet naar Entrez-ID’s met behulp van het org.Hs.eg.db package (v3.23.1). 

Daarnaast werd een Gene Ontology (GO) analyse uitgevoerd met het goseq package (v1.64.0), waarbij rekening werd gehouden met lengtebias van genen. Het KEGGREST package (v1.52.0) werd gebruikt voor het opvragen van aanvullende pathway-informatie. 

Zie [script](script/) voor de uitwerking van de methode, zie verder ook de count en de genomic.gtf

## Resultaten
De differentiële genexpressie-analyse toonde duidelijke verschillen tussen RA-patiënten en controles. In totaal werden 3178 genen geïdentificeerd als significant differentieel tot expressie (padj < 0.01), waarvan 1786 genen opgereguleerd en 1297 genen neer-gereguleerd waren. De volcano plot (Figuur 1) laat zien dat een groot aantal genen sterke veranderingen in expressie vertoont, waaronder ANKRD30BL, MT-ND6 en RAB3IL1, die tot de meest significante behoren.


<p align="center">
  <img width="959" height="479" alt="Schermafbeelding" src="https://github.com/user-attachments/assets/8252efdc-9a4e-4aad-abef-cc379ba5be59" />
  <em>
    <strong>Figuur 1. Volcano plot van differentiële genexpressie tussen RA en controle.</strong><br>
    De volcano plot toont de log₂ fold change (x-as) tegenover de −log₁₀ p-waarde (y-as) van 19.944 genen. Elk punt vertegenwoordigt één gen. Genen die significant differentieel tot expressie komen (padj &lt; 0.01 en |log₂ fold change| &gt; 1) zijn weergegeven in rood. Groene punten geven genen weer met een hoge fold change maar zonder significante p-waarde, blauwe punten tonen genen met een lage p-waarde maar kleine fold change, en grijze punten zijn niet significant (NS). Verticale stippellijnen geven de grenswaarden voor log₂ fold change aan, en de horizontale lijn geeft de significatiedrempel aan. Enkele van de meest significante genen zijn gelabeld, waaronder ANKRD30BL, MT-ND6 en RAB3IL1. Data zijn afkomstig van RNA-seq analyse van 4 RA- en 4 controlemonsters.
  </em>
</p>


De KEGG pathway-analyse liet zien dat meerdere biologische routes betrokken zijn bij RA. In de cytokine-cytokine receptor interactie pathway (Figuur 2) werden verschillende genen met veranderde expressie waargenomen, het zelfde in de hematopoietische cel lineage (Figuur 3) en de celcyclus pathway (Figuur 4). Deze pathways bevatten genen die betrokken zijn bij immuunsignalering en celprocessen.


<p align="center">
  <img width="1799" height="1161" alt="hsa04060 pathview" src="https://github.com/user-attachments/assets/29ee48e2-9759-4163-b6ef-e94e2912387f" />
  <em>
    <strong>Figuur 2. KEGG pathway ‘cytokine-cytokine receptor interaction’ (hsa04060) voor RA versus controle.</strong><br>
Het figuur toont genexpressieverschillen binnen de cytokine-signaleringsroute gebaseerd op RNA-seq data. Elk vakje is een gen en is ingekleurd op basis van de log₂ fold change. Rood geeft genen weer met hogere expressie in RA, terwijl groen genen met lagere expressie in RA aanduidt. Witte of grijze vakjes geven genen weer zonder significant verschil of zonder data. De kleurenbalk rechtsboven geeft de schaal van log₂ fold change weer (van −2 tot +2). De analyse is uitgevoerd met het pathview-package, waarbij gebruik is gemaakt van KEGG pathway annotatie. De data zijn afkomstig van synoviumweefsel van 4 RA-patiënten en 4 controles.
  </em>
</p>


<p align="center">
  <img width="1300" height="1842" alt="hsa04640 pathview" src="https://github.com/user-attachments/assets/65024747-3b27-43fa-bbc9-922cd04dc880" />
  <em>
    <strong>Figuur 3. KEGG pathway ‘hematopoietic cell lineage’ (hsa04640) voor RA versus controle.</strong><br>
Het figuur toont genexpressie binnen de differentiatie van immuuncellen gebaseerd op RNA-seq data. Elk vakje vertegenwoordigt een gen en is ingekleurd op basis van de log₂ fold change. Rood geeft genen met hogere expressie in RA weer en groen genen met lagere expressie in RA. De schaal van de expressieverandering wordt weergegeven in de kleurenbalk rechtsboven (−1 tot +1). Witte vakjes geven genen weer waarvoor geen significant verschil of geen data beschikbaar is. De figuur is gegenereerd met pathview op basis van KEGG pathway annotatie. De data zijn afkomstig van synoviumweefsel van 4 RA-patiënten en 4 controles.
  </em>
</p>


  <p align="center">
 <img width="1105" height="877" alt="hsa04110 pathview GOED" src="https://github.com/user-attachments/assets/4dfbdbf9-0bda-4c43-9525-8d543c5199f4" />
  <em>
    <strong>Figuur 4. KEGG pathway ‘cell cycle’ (hsa04110) voor RA versus controle.</strong><br>
In dit figuur wordt de expressie van genen binnen de celcyclus weergegeven op basis van RNA-seq data. Elk vakje stelt een gen voor en is gekleurd volgens de log₂ fold change tussen RA en controle. Rode vakjes geven verhoogde expressie in RA weer, terwijl groene vakjes verlaagde expressie in RA aangeven. De kleurenbalk rechtsboven toont de schaal van log₂ fold change (−2 tot +2). Niet-ingekleurde vakjes geven genen weer zonder significant verschil of zonder beschikbare data. De pathwayvisualisatie is gegenereerd met pathview op basis van KEGG annotatie. De data zijn afkomstig van synoviumweefsel van 4 RA-patiënten en 4 controles.
  </em>
</p>


De GO-analyse bevestigde deze bevindingen en toonde 9 significante GO-termen (padj < 0.01). De meest significante termen zijn weergegeven in Figuur 2 en omvatten onder andere immunoglobulin complex, adaptive immune response, antigen binding en immune system process. Daarnaast werden ook termen geïdentificeerd die verband houden met B-cel- en T-celsignalering.
Samen laten deze resultaten zien dat genexpressieverschillen tussen RA en controles voornamelijk voorkomen in processen die gerelateerd zijn aan het immuunsysteem.


<p align="center">
  <img width="959" height="484" alt="Schermafbeelding 2026-06-19 023201" src="https://github.com/user-attachments/assets/499a49e5-97a5-482f-b41a-b59bde190161" />
  <em>
    <strong>Figuur 2. Top significante GO-termen bij RA ten opzichte van controle.</strong><br>
De staafdiagram toont de tien meest significante Gene Ontology (GO)-termen op basis van differentieel tot expressie komende genen (padj < 0.01). De x-as toont de −log₁₀ van de adjusted p-waarde, waarbij hogere waarden betekenen dat de GO-termen statistisch sterker significant zijn. De y-as toont de bijbehorende GO-termen, waaronder immunoglobulin complex, adaptive immune response en antigen binding. De analyse is uitgevoerd met het goseq-package, waarbij gecorrigeerd is voor lengtebias. Alleen genen met een adjusted p-waarde < 0.01 zijn meegenomen in de analyse. Data zijn afkomstig van RNA-seq analyse van synoviumweefsel van 4 RA-patiënten en 4 controles.
  </em>
</p>


## Conclusie

In dit onderzoek is gekeken naar verschillen in genexpressie tussen RA-patiënten en gezonde controles met behulp van RNA-seq analyse. De resultaten laten zien dat er duidelijke verschillen zijn in genexpressie, waarbij een groot aantal genen significant op- of neer-gereguleerd is. De differentiële expressie-analyse en de volcano plot tonen dat veel genen sterk veranderd zijn bij RA.

De GO-analyse en KEGG pathway-analyse bevestigen dat vooral genen die betrokken zijn bij het immuunsysteem en ontstekingsprocessen een belangrijke rol spelen. Met name processen zoals *adaptive immune response*, *immunoglobulin complex* en *B cell receptor signaling* zijn sterk verrijkt. Dit laat zien dat het immuunsysteem overactief is bij RA en dat antistoffen en immuuncellen een grote rol spelen in de ziekte. Deze resultaten passen goed bij wat al bekend is over RA als auto-immuunziekte.

Een beperking van dit onderzoek is het gebruik van een relatief kleine dataset en subset sequencing data, wat invloed kan hebben op de nauwkeurigheid van de resultaten. Toekomstig onderzoek zou gebruik kunnen maken van grotere datasets en aanvullende analysemethoden.

Samenvattend laat dit onderzoek zien dat transcriptomics een waardevolle methode is om inzicht te krijgen in de onderliggende mechanismen van RA, en kan bijdragen aan het ontwikkelen van betere behandelingen.

versie nummers en beetje packages noemen welke je hebt gebruikt niet de codes en vertellen hoe en wat je ermee hebt gedaan verwijzen naar script feature counts tabel met patieten




