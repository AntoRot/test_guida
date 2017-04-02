
**INDICE**

[*PREMESSA*](#premessa)

[*Note di lettura del documento*](#note-di-lettura-del-documento)

[*1* *COMPOSIZIONE DEI file XML*](#composizione-dei-file-xml)

[*1.1* *Indicazioni generali*](#indicazioni-generali)

[*1.2* *Repository schemi XSD*](#repository-schemi-xsd)

[*1.3* *Conformità*](#conformità)

[*1.4* *Implementazione della struttura gerarchica e relazioni tra
livelli*](#implementazione-della-struttura-gerarchica-e-relazioni-tra-livelli)

[*2* *compilazione dei metadati*](#compilazione-dei-metadati)

[*2.1* *Istruzioni*](#istruzioni)

[*2.2* *Mapping requisiti e raccomandazioni RNDT / INSPIRE*
59](#mapping-requisiti-e-raccomandazioni-rndt-inspire)

[*2.3* *Focus - Punti di attenzione* 62](#focus---punti-di-attenzione)

[*3* *metadati per l'interoperabilità*
63](#metadati-per-linteroperabilità)

[*3.1* *Metadati necessari per l’interoperabilità*
63](#metadati-necessari-per-linteroperabilità)

[*ALLEGATO A – Temi INSPIRE* 65](#allegato-a-temi-inspire)

[*ALLEGATO B – Esempi di file XML* 67](#allegato-b-esempi-di-file-xml)

[*B.1 Esempio di file XML per il dataset*
67](#b.1-esempio-di-file-xml-per-il-dataset)

[*B.2 Esempio di file XML per la serie*
73](#b.2-esempio-di-file-xml-per-la-serie)


## <a name=premessa>PREMESSA</a>


L’allegato 2 del [Decreto 10 novembre 2011](http://www.rndt.gov.it/RNDT/home/images/struttura/documenti/DM_RNDT.pdf) recante le _regole tecniche del
Repertorio Nazionale dei Dati Territoriali_ delinea, al § 3.1.1, la
struttura, mutuata dallo Standard ISO 19115, in cui possono essere
organizzati i metadati.

La struttura gerarchica dei metadati così individuata permette di
generalizzare a livello di serie tutte le informazioni condivise da più
dataset, di mantenere a livello di dataset quelle informazioni che
effettivamente distinguono un dataset da un altro e di dettagliare
ulteriormente le informazioni a livello di sezione.

Non esiste, in effetti, una definizione univoca di cosa si intenda per
dataset e di conseguenza anche di serie di dataset o di subset di
dataset: l'esatta definizione di dataset può essere funzione del tipo di
dato da descrivere, dell'ambiente istituzionale in cui lo stesso viene
prodotto, dal modo in cui viene gestito e fornito. Per questo, il
modello di metadati proposto è definito in modo da contenere il set
minimo di elementi di metadati ed allo stesso tempo risulta
sufficientemente “generico” al fine di poter essere adattato alle
diverse tipologie di dati che dovranno essere documentati nel
Repertorio.

Nell’implementazione della struttura gerarchica delineata, potrebbe
essere impossibile documentare ognuno dei livelli previsti: per esempio,
potrebbe essere difficile individuare più dataset e quindi, in questo
caso, la documentazione avverrà come un dataset “flat” (*piatto*)
oppure, ancora, potrebbe essere difficile suddividere uno strato
informativo in unità elementari per cui si avrà la documentazione dello
strato informativo a livello di dataset ma non ci sarà quella a livello
di sezione.

In ogni caso, come precisato nel citato allegato 2, la scelta della
strutturazione dei metadati nei livelli gerarchici indicati è comunque
lasciata alla singola Amministrazione: il principio che deve guidare
nella documentazione è quello di scendere all’elemento minimo che si può
fornire o a cui si può accedere ovvero di attenersi all’elemento minimo
che ha senso descrivere, che può anche non coincidere con l’elemento
minimo di fornitura, se esiste.

Il [Regolamento (CE) n. 1205/2008](http://eur-lex.europa.eu/LexUriServ/LexUriServ.do?uri=OJ:L:2008:326:0012:0030:IT:PDF), recante attuazione della [direttiva
INSPIRE (Direttiva 2007/2/CE)](http://eur-lex.europa.eu/LexUriServ/LexUriServ.do?uri=OJ:L:2007:108:0001:0014:IT:PDF) per quanto riguarda i metadati, ha
individuato come campi di applicazione dei metadati i dataset, le serie
e i servizi. Si evince, quindi, che, rispetto alle norme europee citate,
il RNDT contempla un livello informativo in più, la sezione (tile).

Risulta evidente, quindi, l’esigenza di fornire delle indicazioni più
dettagliate per l’implementazione del modello concettuale dei metadati,
delineato nell’allegato 2, al fine di garantire la conformità al
Regolamento INSPIRE di cui sopra e alle relative [Linee Guida Tecniche][linee-guida-inspire] edite dal Joint
Research Centre della Commissione Europea.

Il presente documento rappresenta la parte generale di tale
implementazione, valida, pertanto, per tutte le tipologie di dati,
poiché delinea le indicazioni comuni. Ad integrazione di esso, per i
dati raster, un ulteriore documento riporterà le relative indicazioni
specifiche.

Inoltre, sarà predisposto un documento specifico per la documentazione,
nel RNDT, dei servizi relativi ai dati territoriali.

Per quanto non specificato nel presente documento si rimanda alle linee
guida INSPIRE di cui sopra.

[linee-guida-inspire]:http://inspire.jrc.ec.europa.eu/documents/Metadata/MD_IR_and_ISO_20131029.pdf

## <a name=note-di-lettura-del-documento>Note di lettura del documento</a>

Nella definizione dei requisiti, delle raccomandazioni e delle
istruzioni nel presente documento sono utilizzate le forme verbali
analoghe alle [linee guida INSPIRE][linee-guida-inspire].

Anche le notazioni di requisiti e raccomandazioni, così come gli esempi
XML, seguono i formati redazionali delle linee guida di cui sopra.

I requisiti sono rappresentati nel modo seguente:

```
** Requisito n \# ** testo del requisito

```

le raccomandazioni nel modo seguente:

**Raccomandazione n \#**testo della raccomandazione

mentre gli esempi XML sono indicati con il font Courier New su sfondo
grigio con una parte in giallo per evidenziare il pezzo specifico
relativo all'elemento in questione, nel modo seguente:

&lt;rndt:esempio\_XML&gt;

&lt;rndt:parte\_specifica\_elemento&gt;

Testo evidenziato relativo alla parte specifica del metadato

&lt;/rndt:parte\_specifica\_elemento&gt;

&lt;/rndt:esempio\_XML&gt;

Quando un requisito, una raccomandazione o una parte del testo deriva da
indicazioni tratte dalle linee guida INSPIRE e ne rappresenta la
traduzione o un adattamento, allora tale evenienza viene indicata con
uno sfondo grigio come nel modo seguente:

**Requisito n \#**testo del requisito

COMPOSIZIONE DEI file XML
=========================

Indicazioni generali
--------------------

Come stabilito nell’allegato 2 al citato DM, l’alimentazione e
l’aggiornamento del RNDT avviene attraverso la trasmissione di file XML.

Gli schemi XSD di riferimento indicati sono quelli ‘*adattati’* a
partire dagli schemi di cui allo Standard ISO TS 19139 e pubblicati sul
portale del Repertorio stesso. Nel seguito tali schemi verranno indicati
come schemi XSD RNDT per distinguergli da quelli di cui allo Standard
predetto che verranno indicati come schemi XSD ISO.

Gli schemi XSD RNDT seguono le regole di codifica (a meno di alcune
modifiche) stabilite nello Standard citato che fornisce gli strumenti
per l’implementazione del 19115 dal modello concettuale al linguaggio
XML, al fine di aumentare l’interoperabilità fornendo specifiche comuni
per descrivere, validare e scambiare i metadati relativi ai dati
territoriali.

Gli adattamenti di cui sopra sono stati resi necessari per tenere conto
della struttura gerarchica[^4] definita nell’allegato 2 nonché dei
diversi (rispetto allo Standard) livelli di obbligatorietà ivi
contemplati. A tale scopo, è stato introdotto un nuovo namespace,
*ITgmd*, che si aggiunge ai namespaces mutuati da ISO e comunque
mantenuti nel “pacchetto” dell’implementazione RNDT. Gli schemi di
questo namespace includono solo gli elementi e le classi di metadati che
differiscono da quelli ISO; per tutti gli elementi e le classi non
incluse nel namespace *ITgmd*, si fa riferimento agli analoghi elementi
e classi del namespace ISO *gmd* (per questo motivo tra i due
namespaces, *ITgmd* e *gmd*, c’è una dipendenza di tipo “*import*”).

È evidente che gli schemi adattati del Repertorio sono da utilizzare
qualora la scelta della gerarchia implementata sia quella completa,
serie-dataset-sezione. In questo caso, il portale del RNDT, in virtù di
quanto sancito al comma 1 dell’art. 4 del DM, fornisce un adeguato
servizio di conversione verso i formati standard.

Il DM, sempre nell’allegato 2, contempla anche, per l’alimentazione del
Repertorio, la possibilità di utilizzare gli schemi ISO di cui al citato
Standard ISO TS 19139.

Sulla base di ciò, pertanto, qualora i set di metadati vengano
documentati utilizzando i livelli serie-dataset o semplicemente il
dataset e/o la serie in livelli flat indipendenti (come indicato nelle
linee guida INSPIRE), allora si possono comunque utilizzare gli schemi
XSD ISO, tenendo presente che, in questo caso, è necessario rispettare i
requisiti di obbligatorietà dei metadati stabiliti nel citato allegato
2. Ciò garantirà la piena conformità, oltre all’interoperabilità, con
gli Standard ISO di riferimento e le regole tecniche INSPIRE (v. anche
il successivo § 1.2).

Considerato, quindi, l’obiettivo indicato in premessa, nel presente
documento si farà riferimento esclusivamente agli schemi XSD ISO.

Repository schemi XSD
---------------------

### Schemi XSD ISO

Ai fini della validazione dei file XML nel RNDT, gli schemi XSD
ufficiali relativi agli Standard ISO a cui fare riferimento sono
disponibili in due repository:

1)  repository ISO per gli standard pubblici all’indirizzo

> [*http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/*](http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO_19139_Schemas/);

1)  repository OGC all’indirizzo
    [*http://schemas.opengis.net/iso/19139/20070417/*](http://schemas.opengis.net/iso/19139/20070417/).

In entrambi i repository indicati, la versione del GML di riferimento è
la 3.2.1 il cui namespace è
[*http://www.opengis.net/gml/3.2*](http://www.opengis.net/gml/3.2) . Il
RNDT non valida file XML con versioni GML diverse da quella indicata.

Pertanto, per validare i file XML nel RNDT utilizzare lo schema
[*http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/gmd/gmd.xsd*](http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO_19139_Schemas/gmd/gmd.xsd)
oppure
[*http://schemas.opengis.net/iso/19139/20070417/gmd/gmd.xsd*](http://schemas.opengis.net/iso/19139/20070417/gmd/gmd.xsd).

### Schemi XSD RNDT

Gli schemi *adattati* del RNDT sono disponibili sul portale del
Repertorio stesso nella sezione “*Documenti*”; essi includono tutti i
namespace degli schemi XSD ISO di cui al paragrafo precedente. Gli
adattamenti rispetto a tali ultimi schemi sono inseriti nel namespace
*ITgmd*.

Conformità
----------

### RNDT vs ISO

Nella tabella 1 è riportata la corrispondenza tra i metadati previsti
dal profilo del RNDT e quelli previsti dal *core set* dello Standard ISO
19115:2003 (tabella 3, § 6.5)[^5]. Accanto ad ogni elemento è indicato,
tra parentesi, il livello di obbligatorietà (***O*** per obbligatorio,
***Op*** per opzionale, ***C*** per condizionato).

I diversi livelli di obbligatorietà degli elementi del profilo del RNDT
rispetto ai corrispondenti ISO sono stati imposti rispettando le regole
di cui all’allegato C dello Standard ISO.

Si può, quindi, affermare che i metadati previsti nel set “*core*” di
ISO 19115 rappresentano un sottoinsieme di quelli previsti dal RNDT;
pertanto, la conformità di un set di metadati al core di ISO non
garantisce la conformità al RNDT in quanto devono essere considerati
anche quei metadati obbligatori nel Repertorio ma non previsti nel
“*core*” ISO.

Viceversa, la conformità di un set di metadati al profilo del RNDT
garantisce la conformità al “*core*” di ISO 19115.

  ---------------------------------------------------------------------------------------
  **Metadati RNDT**
  --------------------------------------- -----------------------------------------------
  **Informazioni sui metadati**

  Identificatore del file (O)

  Lingua dei metadati (O)

  Set dei caratteri dei metadati (C)

  Id file precedente (O)

  Livello gerarchico (O)

  Responsabile dei metadati (O)

  Data dei metadati (O)

  Nome dello Standard (O)

  Versione dello Standard (O)

  **Identificazione dei dati**

  Titolo (O)

  Data (O)
  
  Tipo data (O)

  Formato di presentazione (O)

  Responsabile (O)

  Identificatore (O)

  Id livello superiore (O)

  Altri dettagli (Op)

  Descrizione (O)

  Parola chiave (O)
  
  Thesaurus (Op)

  Punto di contatto (O)

  Tipo di rappresentazione spaziale (O)

  Risoluzione spaziale (O)

  Lingua (O)

  Set di caratteri (C)

  Categoria tematica (O)

  Informazioni supplementari (Op)

  **Vincoli sui dati**

  Limitazione d’uso (O)

  Vincoli di accesso (O)

  Vincoli di fruibilità (O)

  Altri vincoli (C)

  Vincoli di sicurezza (O)

  **Estensione dei dati**

  Localizzazione geografica (O)

  Estensione verticale (Op)

  Estensione temporale (Op)

  **Qualità dei dati**

  Livello di qualità (O)

  Accuratezza posizionale (O)

  Genealogia (O)

  Conformità: specifiche (C)

  Conformità: grado (C)

  **Sistema di riferimento**

  Sistema di riferimento spaziale (O)

  Formato di distribuzione (O)

  Distributore (O)

  Risorsa on line (Op)

  **Gestione dei dati**

  Frequenza di aggiornamento (Op)
  ---------------------------------------------------------------------------------------

### Tab. 1 – Mapping metadati RNDT – metadati core ISO 19115 {#tab.-1-mapping-metadati-rndt-metadati-core-iso-19115 .ListParagraph}

### RNDT vs INSPIRE

La corrispondenza tra i metadati previsti dal Repertorio e i metadati di
cui al Regolamento (CE) 1205/2008 è riportata al § 3.4.8.1 dell’allegato
2 al DM.

Inoltre, per ogni elemento riportato nel successivo capitolo 2, viene
anche indicato, se esistente, il corrispondente elemento INSPIRE.

Anche in questo caso, i metadati INSPIRE risultano essere un
sottoinsieme dei metadati del Repertorio; pertanto, la conformità ad
INSPIRE non garantisce la conformità al RNDT, mentre è vero il
contrario.

In più, nel caso di incongruenza tra INSPIRE e ISO, è stata recepita
l’indicazione dello Standard ISO, che, comunque, non è in contrasto con
quella indicata da INSPIRE, essendo, quest’ultima, meno vincolante.

Implementazione della struttura gerarchica e relazioni tra livelli
------------------------------------------------------------------

### Gerarchia e relazioni serie/dataset/sezione

Come indicato nella premessa, il Regolamento (CE) relativo ai metadati
contempla, per quanto riguarda i dati territoriali, solo i livelli di
serie e dataset.

Dal Regolamento e dalle già citate Linee Guida Tecniche si evince che
non esiste nessuna relazione tra i due livelli tale da consentire di
creare una gerarchizzazione dell’informazione contenuta nei metadati,
come previsto dal diagramma UML riportato nella figura 3 del paragrafo
6.2 dello Standard ISO 19115 e come indicato, a livello informativo,
negli allegati G e H del medesimo Standard. Negli esempi riportati
nell’allegato A delle Linee Guida Tecniche INSPIRE, infatti, i due
livelli di serie e dataset vengono rappresentati in modo indipendente e
quindi senza nessuna relazione tra di loro.

Il RNDT, di converso, prevede la possibilità di implementare, attraverso
gli identificatori presenti, la gerarchia tra i livelli previsti.

Per quanto riguarda la struttura XML, gli schemi XSD ISO consentono di
documentare serie e dataset appartenenti alla serie in un unico file o,
in alternativa, in file distinti. Questa seconda opzione è quella
seguita negli esempi delle Linee Guida INSPIRE.

Nel RNDT si possono caricare file compilati nelle due modalità; in più,
se serie e dataset documentati sono documentati in file distinti, il
RNDT ricostruisce, attraverso gli identificatori, le relazioni, se
esistenti, tra i diversi livelli.

Come prescritto al § 4.3.2.1 dell'allegato 2 al DM, infatti, sono
previste due coppie di identificatori utili a gestire, rispettivamente,
le trasmissioni dei file XML al RNDT e le relazioni tra i livelli
gerarchici individuati.

Per le trasmissioni, i metadati in questione sono “*Identificatore del
file*” (*fileIdentifier*) e “*Id file precedente*” (*parentIdentifier*);
le istruzioni di compilazione di tali metadati sono riportate ai
successivi paragrafi 2.1.1.1 e 2.1.1.4.

In riferimento a ciò, nel caso di una prima trasmissione i due
identificatori assumeranno lo stesso valore; nel caso, invece, di un
aggiornamento, l’identificatore “*Id file precedente*” del file XML
corrente dovrà assumere il valore dell’elemento “*Identificatore del
file*” presente nel file XML della trasmissione temporalmente precedente
a cui è relazionato.

Per la gestione delle relazioni tra livelli gerarchici, sono previsti i
metadati “*Identificatore*” (*identifier*) e “*Id livello superiore*”
(*series*); le relative istruzioni di compilazione sono riportate ai
successivi paragrafi 2.1.2.5 e 2.1.2.6.

I casi possibili di implementazione dei file XML, pertanto, sono i
seguenti:

1)  file XML distinti per serie e dataset indipendenti tra loro. I
    metadati “*Identificatore*” e “*Id livello superiore*” assumeranno
    lo stesso valore in riferimento al livello gerarchico corrente;

2)  file XML distinti per serie e dataset tra loro collegati. I metadati
    “*Identificatore*” e “*Id livello superiore*” della serie
    assumeranno lo stesso valore, mentre il metadato “*Id livello
    superiore*” del dataset assumerà il valore del metadato
    “*Identificatore*” della serie;

3)  unico file per serie e dataset collegati tra loro. Gli
    identificatori assumeranno i valori indicati al punto 2);

4)  unico file per serie, dataset e sezioni collegati tra loro. Gli
    identificatori assumeranno i valori indicati al punto 2). Per le
    sezioni, il metadato “*Id livello superiore*” assumerà il valore del
    metadato “*Identificatore*” del dataset a cui appartengono.

I casi 1) e 2) sono coerenti con le Linee Guida INSPIRE come innanzi
riportato; i file XML compilati come indicato nei casi 3) e 4), invece,
non vengono validati da INSPIRE ma, secondo quanto disposto dal comma 1
art. 4 del DM, il RNDT provvede, con una specifica funzione, a fornire,
per ogni livello (limitatamente a quelli previsti da INSPIRE), il
relativo file XML conforme alle indicazioni INSPIRE riconducendosi così
al caso 2).

Quanto allo schema XSD di riferimento, per il caso 4) devono essere
utilizzati gli schemi RNDT.

**Raccomandazione 1** Considerate le indicazioni fornite nelle linee
guida INSPIRE, si raccomanda di documentare i metadati utilizzando un
file per ogni livello gerarchico (serie e/o dataset), secondo quanto
riportato nei casi 1) e 2) di cui sopra.

### Relazioni dati/servizi

Per quanto riguarda le relazioni tra dati e servizi, nel set di metadati
individuato dal RNDT sono presenti alcuni elementi che consentono di
documentare tali relazioni.

In particolare, a livello di metadati dei servizi, l’elemento “*Risorsa
accoppiata*” (*operatesOn*) consente di indicare i dataset agganciati
dal servizio indicando il link dei relativi metadati.

A livello di metadati dei dati, invece, l’elemento “*Risorsa on-line*”
può essere utilizzato per indicare l’URL degli eventuali servizi
disponibili sui dati (v., a tale proposito le indicazioni al § 2.1.7.3).

### Nella figura 1 sono rappresentate le relazioni tra i vari livelli in cui è possibile descrivere i metadati dei dati territoriali e relativi servizi. {#nella-figura-1-sono-rappresentate-le-relazioni-tra-i-vari-livelli-in-cui-è-possibile-descrivere-i-metadati-dei-dati-territoriali-e-relativi-servizi. .ListParagraph}

![](media/image6.png){width="2.4520833333333334in"
height="2.2916666666666665in"}

  ###  {#section-3 .ListParagraph}        ### RNDT {#rndt .ListParagraph}
  --------------------------------------- -----------------------------------------------------------
  ### md dati {#md-dati .ListParagraph}   ### metadati serie {#metadati-serie .ListParagraph}
  ###  {#section .ListParagraph}          ### metadati dataset {#metadati-dataset .ListParagraph}
  ###  {#section-1 .ListParagraph}        ### metadati sezione {#metadati-sezione .ListParagraph}
  ###  {#section-2 .ListParagraph}        ### metadati servizio {#metadati-servizio .ListParagraph}

### \
 {#section-4 .ListParagraph}

###  {#section-5 .ListParagraph}

###  {#section-6 .ListParagraph}

### Fig. 1 – Relazioni tra i vari livelli del RNDT {#fig.-1-relazioni-tra-i-vari-livelli-del-rndt .ListParagraph}

compilazione dei metadati
=========================

Nel presente capitolo vengono definite le istruzioni utili per la
compilazione dei metadati previsti dall’allegato 2 del DM, in coerenza
con quanto disposto dal Regolamento CE n. 1205/2008 e dalle relative
Linee Guida Tecniche.

Istruzioni
----------

L’indicazione generale, valida per tutti i metadati definiti, è che,
all’interno del file XML, il tag corrispondente a ciascun elemento deve
essere obbligatoriamente valorizzato. Ciò significa che la presenza del
tag nel file XML, senza che questo sia opportunamente valorizzato, non
garantisce la validità del file stesso, sebbene non sia comunque
inficiata la validazione rispetto agli schemi XSD.

Per questo, risulta valido, ai fini del caricamento nel RNDT, il
seguente tracciato XML:
```xml

<gmd:organisationName>  
  <gco:CharacterString>Regione Piemonte – Settore cartografia   
  e sistema informativo territoriale</gco:CharacterString>  
</gmd:organisationName>

```
mentre non è valido il tracciato seguente:
```xml

<gmd:organisationName>  
  <gco:CharacterString></gco:CharacterString>  
</gmd:organisationName>

```
L’indicazione di cui sopra è valida anche per i metadati che hanno come
dominio le liste di valori di cui al § 3.4.3 dell’allegato 2 al DM,
sebbene esista, all’interno del tag, un attributo (*codeListValue*), il
cui valore corrisponde al valore da assegnare al tag stesso.

Nel caso di tali metadati, inoltre, il valore del tag può essere
espresso sia in italiano che in inglese facendo riferimento alle colonne
“*Nome*” o “*Elemento corrispondente ISO19115:2003*” delle liste di
valori citate (l’attributo *codeListValue*, invece, deve essere sempre
valorizzato con il valore espresso nella lingua inglese di cui allo
Standard ISO). A tale proposito, si rimanda agli esempi di file XML
presenti in corrispondenza di ciascun elemento.

Pertanto, si ritiene valido il tracciato XML seguente:

**…**

&lt;gmd:role&gt;

&lt;gmd:CI\_RoleCode codeListValue="pointOfContact"
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_RoleCode"&gt;punto
di contatto&lt;/gmd:CI\_RoleCode&gt;

&lt;/gmd:role&gt;

**…**

oppure

**…**

&lt;gmd:role&gt;

&lt;gmd:CI\_RoleCode codeListValue="pointOfContact"
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_RoleCode"&gt;pointOfContact&lt;/gmd:CI\_RoleCode&gt;

&lt;/gmd:role&gt;

**…** .

**Raccomandazione 2 Da preferire la modalità rappresentata nel primo
esempio di tracciato XML che esprime il valore del tag nella lingua
dichiarata per i metadati (italiano). Nel caso delle enumerazioni il
valore va espresso, invece, in linguaggio neutrale.**

Non è valido, invece, il tracciato seguente:

**…**

&lt;gmd:role&gt;

&lt;gmd:CI\_RoleCode codeListValue="pointOfContact"
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_RoleCode"/&gt;

&lt;/gmd:role&gt;

**…**

Ciò premesso, di seguito, per ogni elemento, vengono forniti l’elemento
INSPIRE corrispondente, le istruzioni di implementazione e un esempio di
tracciato XML, basato sugli schemi XSD di cui allo Standard ISO TS 19139
e sulle Linee Guida Tecniche INSPIRE.

### Informazioni sui metadati

####  Identificatore del file

  **Nome elemento**                   **Identificatore del file**
  ----------------------------------- -----------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-1
  **Molteplicità**                    \[1\]
  **Elemento INSPIRE**                Nessun elemento corrispondente
  **Definizione**                     Identificatore univoco del file dei metadati.
  **Istruzioni di implementazione**   > Testo libero.

**Requisito 1** L'elemento è opzionale per ISO 19115, ma è obbligatorio
per il RNDT in base al DM 10/11/2011.

**Requisito 2** L'elemento deve contenere, come prefisso, il **codice
iPA** assegnato all’Amministrazione nel momento dell’accreditamento
all'Indice delle Pubbliche Amministrazioni come da comma 1 dell’art. 19
dell’allegato A del DPCM 1 aprile 2008. La condizione imprescindibile è
che l’identificativo debba essere univoco. Il separatore tra il codice
iPA e la restante parte dell’identificatore è “**:**” (due punti).

**Raccomandazione 3** Il formato consigliato è il seguente:
***iPA**:cod-Ente:aaaammgg:hhmmss* dove: *iPA* è il codice IPA;
*cod-Ente* è un codice interno a discrezione dell’Amministrazione che
può essere anche un progressivo; *aaaammgg* è la data corrente
(anno-mese-giorno); *hhmmss* è l’orario corrente (ore-minuti-secondi).

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

&lt;gmd:fileIdentifier&gt;

&lt;gco:CharacterString&gt;r\_campan:000002:20090220:111239&lt;/gco:CharacterString&gt;

&lt;/gmd:fileIdentifier&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Lingua dei metadati

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Nome elemento**                   **Lingua dei metadati**
  ----------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-2

  **Molteplicità**                    \[1\]

  **Elemento INSPIRE**                Lingua dei metadati

  **Definizione**                     Linguaggio nel quale sono espressi i metadati.

  **Istruzioni di implementazione**   L’elenco di codici per le 24 lingue ufficiali della UE, da utilizzare per valorizzare l’elemento, è il seguente (codelist basata sui codici a tre lettere di ISO 639-2/B come definita all’indirizzo [*http://www.loc.gov/standards/iso639-2/*](http://www.loc.gov/standards/iso639-2/)):
                                      
                                      Bulgaro – **bul**
                                      
                                      Ceco – **cze**
                                      
                                      Croato - **hrv**
                                      
                                      Danese – **dan**
                                      
                                      Estone – **est**
                                      
                                      Finlandese – **fin**
                                      
                                      Francese – **fre**
                                      
                                      Greco – **gre**
                                      
                                      Inglese – **eng**
                                      
                                      Irlandese – **gle**
                                      
                                      Italiano – **ita**
                                      
                                      Lettone – **lav**
                                      
                                      Lituano – **lit**
                                      
                                      Maltese – **mlt**
                                      
                                      Olandese – **dut**
                                      
                                      Polacco – **pol**
                                      
                                      Portoghese – **por**
                                      
                                      Rumeno – **rum**
                                      
                                      Slovacco – **slo**
                                      
                                      Sloveno – **slv**
                                      
                                      Spagnolo – **spa**
                                      
                                      Svedese - **swe**
                                      
                                      Tedesco – **ger**
                                      
                                      Ungherese – **hun**
                                      
                                      La lingua di default per i metadati del RNDT è, ovviamente, l’**italiano** (**ita**).
                                      
                                      La lista di tutti i codici (compresi quelli delle lingue regionali) è disponibile all’indirizzo [*http://www.loc.gov/standards/iso639-2/*](http://www.loc.gov/standards/iso639-2/).
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Requisito 3** L'elemento è opzionale per ISO 19115, ma è obbligatorio
per il RNDT in base al DM 10/11/2011 e al Regolamento 1205/2008/CE.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:language&gt;

&lt;gmd:LanguageCode codeList="http://www.loc.gov/standards/iso639-2/"
codeListValue="ita"&gt;ita&lt;/gmd:LanguageCode&gt;

&lt;/gmd:language&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Set dei caratteri dei metadati

  **Nome elemento**                   **Set dei caratteri dei metadati**
  ----------------------------------- -------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-3
  **Molteplicità**                    \[0..1\]
  **Elemento INSPIRE**                Nessun elemento corrispondente.
  **Definizione**                     Nome dello standard del set di caratteri utilizzato per i metadati.
  **Istruzioni di implementazione**   L’elemento deve assumere uno dei valori della lista “*MD\_CharacterSetCode*” (§ 3.4.3.5 – all. 2 DM).

**Requisito 4** L’elemento è condizionato: esso deve essere documentato
se ISO/IEC 10646-1 non è utilizzato e non è definito dall’ecoding (rif.
ISO 19115).

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:characterSet&gt;

&lt;gmd:MD\_CharacterSetCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#
MD\_CharacterSetCode"
codeListValue="utf8"&gt;utf8&lt;/gmd:MD\_CharacterSetCode&gt;

&lt;/gmd:characterSet&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Id file precedente

  **Nome elemento**                   **Id file precedente**
  ----------------------------------- ---------------------------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-4
  **Molteplicità**                    \[1\]
  **Elemento INSPIRE**                Nessun elemento corrispondente.
  **Definizione**                     Identificatore univoco del file di metadati dell’ eventuale trasmissione precedente a cui il file corrente è relazionato.
  **Istruzioni di implementazione**   Testo libero. Per quanto riguarda il formato e i relativi requisiti, vale anche quanto indicato al § 2.1.1.1.

**Requisito 5** L’elemento serve a tracciare la “storia” delle
trasmissioni dei file XML e quindi degli aggiornamenti dei metadati.
Esso deve assumere il valore dell’elemento “*Identificatore del file*”
del file trasmesso temporalmente in precedenza e a cui il file corrente
è in relazione. Nel caso di primo impianto (quindi non esiste nessun
file precedente) l’elemento assume lo stesso valore dell’elemento
“*Identificatore del file*” del file corrente.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:parentIdentifier&gt;

&lt;gco:CharacterString&gt;r\_campan:000001:20090124:093213&lt;/gco:CharacterString&gt;

&lt;/gmd:parentIdentifier&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Livello gerarchico

  **Nome elemento**                   **Livello gerarchico**
  ----------------------------------- -------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-5
  **Molteplicità**                    \[1\]
  **Elemento INSPIRE**                Tipo di risorsa
  **Definizione**                     Categoria di informazione cui vengono applicati i metadati.
  **Istruzioni di implementazione**   L’elemento deve assumere uno dei valori della lista “*MD\_ScopeCode*” (§ 3.4.3.13 - all. 2 DM).

**Requisito 6** L'elemento è opzionale per ISO 19115, ma è obbligatorio
per il RNDT in base al DM 10/11/2011 e al Regolamento 1205/2008/CE.

**Requisito 7** I valori della lista *MD\_ScopeCode* ammissibili per
INSPIRE sono: **dataset** o **serie**.

**Raccomandazione 4** La scelta del valore più appropriato per il tipo
di risorsa dovrebbe essere fatta tenendo conto delle definizioni
presenti al § 2 all. 2 del DM 10/11/2011 e alle seguenti indicazioni:

- **dataset**: collezione identificabile di dati che può essere parte di
una serie oppure una risorsa a sè stante;

- **serie**: collezione di risorse o di dataset in relazione tra di loro
che condividono le stesse specifiche di prodotto.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:hierarchyLevel&gt;

&lt;gmd:MD\_ScopeCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_ScopeCode"
codeListValue="dataset"&gt;dataset&lt;/gmd:MD\_ScopeCode&gt;

&lt;/gmd:hierarchyLevel&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Responsabile dei metadati

  ----------------------------------------------------------------------------------------------------------------------------------------------
  **Nome elemento**                   **Responsabile dei metadati**
  ----------------------------------- ----------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-6 (I-6.1, I-6.2, I-6.3, I-6.4 )

  **Molteplicità**                    \[1..\*\]

  **Elemento INSPIRE**                Punto di contatto dei metadati

  **Definizione**                     Organizzazione responsabile della creazione e della manutenzione dei metadati.

  **Istruzioni di implementazione**   -   **Nome dell’Ente** \[1\] - Testo libero
                                      
                                      -   **Ruolo** \[1\] – Fare riferimento alla lista *CI\_RoleCode* di cui al § 3.4.3.3 - all. 2 DM.
                                      
                                      -   **Sito web** \[0..1\] - formato URL. Specificare obbligatoriamente anche il protocollo (es. *http*).
                                      
                                      -   **Telefono** \[0..1\] - Testo libero.
                                      
                                      -   **E-mail** \[1..\*\] - Testo libero.
                                      
  ----------------------------------------------------------------------------------------------------------------------------------------------

**Requisito 8** Devono essere forniti i seguenti elementi: **nome
dell'Ente**, **ruolo**, **indirizzo e-mail**, **sito web** e/o
**riferimento telefonico**.

**Requisito 9** Il valore della codelist CI\_RoleCode per il ruolo deve
essere "**punto di contatto**" (**pointOfContact**).

**Requisito 10** Come indicato all'allegato 2 del DM, deve essere
documentato **almeno uno dei due** metadati tra "Sito web" e "Telefono".

**Raccomandazione 5** Il nome dell'Ente dovrebbe essere riportato per
intero, senza abbreviazioni. Indicare il nome completo dell’ufficio
responsabile della comunicazione dei metadati come indicato all’atto
dell’accreditamento IPA. Si consiglia di indicare indirizzi e-mail
istituzionali e non personali.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:contact&gt;

&lt;gmd:CI\_ResponsibleParty&gt;

&lt;gmd:organisationName&gt;

&lt;gco:CharacterString&gt;Regione Piemonte – Settore cartografia e
sistema informativo territoriale&lt;/gco:CharacterString&gt;

&lt;/gmd:organisationName&gt;

&lt;gmd:contactInfo&gt;

&lt;gmd:CI\_Contact&gt;

&lt;gmd:address&gt;

&lt;gmd:CI\_Address&gt;

&lt;gmd:electronicMailAddress&gt;

&lt;gco:CharacterString&gt;sitad@csi.it&lt;/gco:CharacterString&gt;

&lt;/gmd:electronicMailAddress&gt;

&lt;/gmd:CI\_Address&gt;

&lt;/gmd:address&gt;

&lt;gmd:onlineResource&gt;

&lt;gmd:CI\_OnlineResource&gt;

&lt;gmd:linkage&gt;

&lt;gmd:URL&gt;http://www.sistemapiemonte.it/serviziositad/&lt;/gmd:URL&gt;

&lt;/gmd:linkage&gt;

&lt;/gmd:CI\_OnlineResource&gt;

&lt;/gmd:onlineResource&gt;

&lt;/gmd:CI\_Contact&gt;

&lt;/gmd:contactInfo&gt;

&lt;gmd:role&gt;

&lt;gmd:CI\_RoleCode codeListValue="pointOfContact"
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_RoleCode"&gt;punto
di contatto&lt;/gmd:CI\_RoleCode&gt;

&lt;/gmd:role&gt;

&lt;/gmd:CI\_ResponsibleParty&gt;

&lt;/gmd:contact&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

oppure

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:contact&gt;

&lt;gmd:CI\_ResponsibleParty&gt;

&lt;gmd:organisationName&gt;

&lt;gco:CharacterString&gt;Regione Piemonte – Settore cartografia e
sistema informativo territoriale&lt;/gco:CharacterString&gt;

&lt;/gmd:organisationName&gt;

&lt;gmd:contactInfo&gt;

&lt;gmd:CI\_Contact&gt;

&lt;gmd:phone&gt;

&lt;gmd:CI\_Telephone&gt;

&lt;gmd:voice&gt;

&lt;gco:CharacterString&gt;0114321428&lt;/gco:CharacterString&gt;

&lt;/gmd:voice&gt;

&lt;/gmd:CI\_Telephone&gt;

&lt;/gmd:phone&gt;

&lt;gmd:onlineResource&gt;

&lt;gmd:CI\_OnlineResource&gt;

&lt;gmd:linkage&gt;

&lt;gmd:URL&gt;http://www.sistemapiemonte.it/serviziositad/&lt;/gmd:URL&gt;

&lt;/gmd:linkage&gt;

&lt;/gmd:CI\_OnlineResource&gt;

&lt;/gmd:onlineResource&gt;

&lt;/gmd:CI\_Contact&gt;

&lt;/gmd:contactInfo&gt;

&lt;gmd:role&gt;

&lt;gmd:CI\_RoleCode codeListValue="pointOfContact"
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_RoleCode"&gt;punto
di contatto&lt;/gmd:CI\_RoleCode&gt;

&lt;/gmd:role&gt;

&lt;/gmd:CI\_ResponsibleParty&gt;

&lt;/gmd:contact&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Data dei metadati

  **Nome elemento**                   **Data dei metadati**
  ----------------------------------- ------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-7
  **Molteplicità**                    \[1\]
  **Elemento INSPIRE**                Data dei metadati
  **Definizione**                     Data di creazione o di ultima modifica dei metadati.
  **Istruzioni di implementazione**   Formato ISO 8601.

**Requisito 11** La data deve essere espressa conformemente allo
Standard ISO 8601: *aaaa-mm-gg* oppure *aaaammgg*, dove *aaaa* è l'anno,
*mm* il mese, gg il giorno.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:dateStamp&gt;

&lt;gco:Date&gt;2009-02-23&lt;/gco:Date&gt;

&lt;/gmd:dateStamp&gt;

**…**

&lt;gmd:MD\_Metadata&gt;

#### Nome dello Standard

  **Nome elemento**                   **Nome dello Standard**
  ----------------------------------- -------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-8
  **Molteplicità**                    \[1\]
  **Elemento INSPIRE**                Nessun elemento corrispondente
  **Definizione**                     Nome dello standard e/o del profilo di metadati utilizzato.
  **Istruzioni di implementazione**   Testo libero.

**Requisito 12** Fare riferimento al DM e relativi allegati che
regolamentano il funzionamento del RNDT. Il valore che deve essere
inserito è “*DM - Regole tecniche RNDT*”.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:metadataStandardName&gt;

&lt;gco:CharacterString&gt;DM - Regole tecniche
RNDT&lt;/gco:CharacterString&gt;

&lt;/gmd:metadataStandardName&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Versione dello Standard

  **Nome elemento**                   **Versione dello Standard**
  ----------------------------------- ---------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-9
  **Molteplicità**                    \[1\]
  **Elemento INSPIRE**                Nessun elemento corrispondente
  **Definizione**                     Versione dello standard/profilo di metadati utilizzato.
  **Istruzioni di implementazione**   Testo libero.

**Requisito 13** Fare riferimento al DM e relativi allegati che
regolamentano il funzionamento del RNDT. Il valore che deve essere
inserito è “*10 novembre 2011*”.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:metadataStandardVersion&gt;

&lt;gco:CharacterString&gt;10 novembre 2011&lt;/gco:CharacterString&gt;

&lt;/gmd:metadataStandardVersion&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

### Identificazione dei dati

#### Titolo

  **Nome elemento**                   **Titolo**
  ----------------------------------- --------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-10
  **Molteplicità**                    \[1\]
  **Elemento INSPIRE**                Titolo della risorsa
  **Definizione**                     Nome caratteristico e spesso unico con il quale la risorsa è conosciuta.
  **Istruzioni di implementazione**   Testo libero.

**Raccomandazione 6** Il titolo deve essere conciso e puntuale. Esso non
dovrebbe contenere acronimi o abbreviazioni incomprensibili. Si
consiglia una lunghezza massima di 250 caratteri, riportando il "nome
ufficiale" della risorsa.

**Raccomandazione 7** Se i dati documentati sono parte di un progetto
più ampio, si consiglia di indicare, tra parentesi, il progetto alla
fine del titolo. Nel caso dei nomi dei progetti, sono consentite anche
le abbreviazioni, purchè il resto del titolo segua la raccomandazione di
cui sopra e l'abbreviazione sia spiegata nella descrizione della
risorsa.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

&lt;gmd:citation&gt;

&lt;gmd:CI\_Citation&gt;

&lt;gmd:title&gt;

&lt;gco:CharacterString&gt;Database Topografico della Regione
Puglia&lt;/gco:CharacterString&gt;

&lt;/gmd:title&gt;

&lt;/gmd:CI\_Citation&gt;

&lt;/gmd:citation&gt;

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Data

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Nome elemento**                   **Data**
  ----------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-11 (I-11.1 – I-11.2)

  **Molteplicità**                    \[1..\*\]

  **Elemento INSPIRE**                A seconda del tipo di data specificato, può corrispondere a “Data di pubblicazione”, “Data dell’ultima revisione” o “Data di creazione”.

  **Definizione**                     Data di riferimento dei dati.

  **Istruzioni di implementazione**   -   **Data** \[1\] - formato ISO 8601
                                      
                                      -   **Tipo data** \[1\] – L’elemento deve assumere uno dei valori della lista “*CI\_DateTypeCode*” (§ 3.4.3.1 - all. 2 DM).
                                      
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Requisito 14** Il Regolamento 1205/2008/CE richiede l'indicazione di
un riferimento temporale scelto tra *estensione temporale* e *data* (che
può essere quella di *creazione* o di *pubblicazione* o di *revisione*).
Il DM (conformemente a ISO 19115) prescrive l'obbligo di indicare almeno
una tra i tre tipi di data di cui sopra, mentre l'estensione temporale è
opzionale.

**Raccomandazione 8** Riportare almeno la data dell'ultima revisione dei
dati documentati.

**Requisito 15** Il sistema di riferimento temporale di default deve
essere il calendario Gregoriano con la data espressa conformemente allo
Standard ISO 8601: *aaaa-mm-gg* oppure *aaaammgg*, dove *aaaa* è l'anno,
*mm* il mese, gg il giorno.

**Requisito 16** Nel caso venga indicata la data di creazione dei dati,
questa deve essere una sola.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

&lt;gmd:citation&gt;

&lt;gmd:CI\_Citation&gt;

**…**

&lt;gmd:date&gt;

&lt;gmd:CI\_Date&gt;

&lt;gmd:date&gt;

&lt;gco:Date&gt;1998-10-01&lt;/gco:Date&gt;

&lt;/gmd:date&gt;

&lt;gmd:dateType&gt; &lt;gmd:CI\_DateTypeCode codeListValue="creation"
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_DateTypeCode"&gt;creazione&lt;/gmd:CI\_DateTypeCode&gt;

&lt;/gmd:dateType&gt;

&lt;/gmd:CI\_Date&gt;

&lt;/gmd:date&gt;

**…**

&lt;/gmd:CI\_Citation&gt;

&lt;/gmd:citation&gt;

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Formato di presentazione

  **Nome elemento**                   **Formato di presentazione**
  ----------------------------------- -----------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-12
  **Molteplicità**                    \[1..\*\]
  **Elemento INSPIRE**                Nessun elemento corrispondente
  **Definizione**                     Modalità in cui la risorsa è rappresentata.
  **Istruzioni di implementazione**   L’elemento deve assumere uno dei valori della lista “*CI\_PresentationFormCode*” (§ 3.4.3.2 - all. 2 DM).

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

&lt;gmd:citation&gt;

&lt;gmd:CI\_Citation&gt;

**…**

&lt;gmd:presentationForm&gt;

&lt;gmd:CI\_PresentationFromCode codeListValue="mapDigital"
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_PresentationFormCode"&gt;mappa
digitale&lt;/gmd:CI\_PresentationFormCode&gt;

&lt;/gmd:presentationForm&gt;

**…**

&lt;/gmd:CI\_Citation&gt;

&lt;/gmd:citation&gt;

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Responsabile

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Nome elemento**                   **Responsabile**
  ----------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-13 (I-13.1, I-13.2, I-13.3, I-13.4)

  **Molteplicità**                    \[1..\*\]

  **Elemento INSPIRE**                Nessun elemento corrispondente

  **Definizione**                     Organizzazione titolare dei dati.

  **Istruzioni di implementazione**   -   **Nome dell’Ente** \[1\] – Testo libero.
                                      
                                      -   **Ruolo** \[1\] – L’elemento deve assumere uno dei valori della lista “*CI\_RoleCode*” (§3.4.3.3 - all. 2 DM), tranne “*punto di contatto*” (*pointOfContact*) e “*distributore*” (*distributor*).
                                      
                                      -   **Sito web** \[0..1\] - formato URL. Specificare obbligatoriamente anche il protocollo (es. *http*).
                                      
                                      -   **Telefono** \[0..1\] - Testo libero.
                                      
                                      -   **E-mail** \[1..\*\] - Testo libero.
                                      
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Requisito 17** Devono essere forniti i seguenti elementi: **nome
dell'Ente**, **ruolo**, **indirizzo e-mail**, **sito web** o
**riferimento telefonico**.

**Requisito 18** Come indicato all'allegato 2 del DM, deve essere
documentato almeno uno dei due metadati tra "Sito web" e "Telefono".

**Raccomandazione 9** Il nome dell'Ente dovrebbe essere riportato per
intero, senza abbreviazioni. Indicare il nome completo dell’ufficio
responsabile dei dati. Si consiglia di indicare indirizzi e-mail
istituzionali e non personali.

**Raccomandazione 10** Scegliere i ruoli che meglio rappresentano la
funzione svolta dall'organizzazione responsabile.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

&lt;gmd:citation&gt;

&lt;gmd:CI\_Citation&gt;

**…**

&lt;gmd:citedResponsibleParty&gt;

&lt;gmd:CI\_ResponsibleParty&gt;

&lt;gmd:organisationName&gt;

&lt;gco:CharacterString&gt;Regione Piemonte – Settore cartografia e
sistema informativo territoriale&lt;/gco:CharacterString&gt;

&lt;/gmd:organisationName&gt;

&lt;gmd:contactInfo&gt;

&lt;gmd:CI\_Contact&gt;

&lt;gmd:address&gt;

&lt;gmd:CI\_Address&gt;

&lt;gmd:electronicMailAddress&gt;

&lt;gco:CharacterString&gt;sitad@csi.it&lt;/gco:CharacterString&gt;

&lt;/gmd:electronicMailAddress&gt;

&lt;/gmd:CI\_Address&gt;

&lt;/gmd:address&gt;

&lt;gmd:onlineResource&gt;

&lt;gmd:CI\_OnlineResource&gt;

&lt;gmd:linkage&gt;

&lt;gmd:URL&gt;http://www.sistemapiemonte.it/serviziositad/&lt;/gmd:URL&gt;

&lt;/gmd:linkage&gt;

&lt;/gmd:CI\_OnlineResource&gt;

&lt;/gmd:onlineResource&gt;

&lt;/gmd:CI\_Contact&gt;

&lt;/gmd:contactInfo&gt;

&lt;gmd:role&gt;

&lt;gmd:CI\_RoleCode codeListValue="owner"
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_RoleCode"&gt;proprietario&lt;/gmd:CI\_RoleCode&gt;

&lt;/gmd:role&gt;

&lt;/gmd:CI\_ResponsibleParty&gt;

&lt;/gmd:citedResponsibleParty&gt;

**…**

&lt;/gmd:CI\_Citation&gt;

&lt;/gmd:citation&gt;

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Identificatore

  **Nome elemento**                   **Identificatore**
  ----------------------------------- -----------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-14
  **Molteplicità**                    \[1\]
  **Elemento INSPIRE**                Identificatore univoco della risorsa
  **Definizione**                     Riferimento univoco che identifica la risorsa nel livello gerarchico specificato.
  **Istruzioni di implementazione**   Testo libero.

**Requisito 19** L'elemento deve contenere, come prefisso, il **codice
iPA** assegnato all’Amministrazione nel momento dell’accreditamento
all'Indice delle Pubbliche Amministrazioni come da comma 1 dell’art. 19
dell’allegato A del DPCM 1 aprile 2008. La condizione imprescindibile è
che l’identificativo debba essere univoco. Il separatore tra il codice
iPA e la restante parte dell’identificatore è “**:**” (due punti).

**Requisito 20** La proprietà obbligatoria per l'identificatore è
"*code*" (v. B.2.7.3 di ISO 19115).

**Requisito 21** Se viene fornito anche un valore per l'elemento
"*codeSpace*" (non richiesto da RNDT), allora il tipo di dato per
l'identificatore deve essere *RS\_Identifier* anzichè *MD\_Identifier*.

**Raccomandazione 11** Il formato consigliato è il seguente:
***iPA**:cod-Ente* dove: *iPA* è il codice IPA e *cod-Ente* è un codice
interno a discrezione dell’Amministrazione che può essere anche un UUID.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

&lt;gmd:citation&gt;

&lt;gmd:CI\_Citation&gt;

**…**

&lt;gmd:identifier&gt;

&lt;gmd: MD\_Identifier&gt;

&lt;gmd:code&gt;

&lt;gco:CharacterString&gt;r\_piemon:00000001&lt;/gco:CharacterString&gt;

&lt;/gmd:code&gt;

&lt;/gmd:MD\_Identifier&gt;

&lt;/gmd:identifier&gt;

**…**

&lt;/gmd:CI\_Citation&gt;

&lt;/gmd:citation&gt;

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### ID livello superiore

  **Nome elemento**                   **ID livello superiore**
  ----------------------------------- ----------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-15
  **Molteplicità**                    \[1\]
  **Elemento INSPIRE**                Nessun elemento corrispondente
  **Definizione**                     Riferimento univoco relativo alla serie di cui il dataset è parte.
  **Istruzioni di implementazione**   Testo libero. Per quanto riguarda il formato, vale quanto indicato al § 2.1.2.5.

**Requisito 22** L’elemento è utile per gestire le relazioni tra i
livelli gerarchici. Esso deve assumere il valore dell'elemento
“*Identificatore*” (§ 2.1.2.5) del livello padre a cui è relazionato.
Nel caso non esista un livello gerarchico di rango superiore (per es.
serie o dataset “flat”, cioè che non appartiene a nessuna serie),
l’elemento deve assumere comunque il valore dell’elemento
“*Identificatore*” del livello corrente.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

&lt;gmd:citation&gt;

&lt;gmd:CI\_Citation&gt;

**…**

&lt;gmd:series&gt;

&lt;gmd:CI\_Series&gt;

&lt;gmd:issueIdentification&gt;

&lt;gco:CharacterString&gt;r\_piemon:00000001&lt;/gco:CharacterString&gt;

&lt;/gmd:issueIdentification&gt;

&lt;/gmd:CI\_Series&gt;

&lt;/gmd:series&gt;

**…**

&lt;/gmd:CI\_Citation&gt;

&lt;/gmd:citation&gt;

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Altri dettagli

  **Nome elemento**                   **Altri dettagli**
  ----------------------------------- --------------------------------------
  **Riferimento**                     All.2 DM – tab. I-16
  **Molteplicità**                    \[0..1\]
  **Elemento INSPIRE**                Nessun elemento corrispondente
  **Definizione**                     Ulteriori informazioni di citazione.
  **Istruzioni di implementazione**   Testo libero.

**Raccomandazione 12** Si consiglia di utilizzare questo elemento per
indicare, se disponibile, il riferimento, attraverso un URL, alle norme
(legge nazionale o regionale, delibera, atto amministrativo, …) relative
alla produzione e/o trattamento dei dati. L’elemento può essere
correlato con il metadato “*Informazioni supplementari*” da utilizzare
per specificare il riferimento a documenti specifici, diversi dalle
norme, da cui si possono ottenere ulteriori informazioni sulle
caratteristiche tecniche del dato.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

&lt;gmd:citation&gt;

&lt;gmd:CI\_Citation&gt;

**…**

&lt;gmd:otherCitationDetails&gt;
&lt;gco:CharacterString&gt;[*http://www.regione.emilia-romagna.it/temi/territorio/cartografia-regionale/vedi-anche/database-topografico-regionale/le-norme-e-gli-atti-in-vigore/atto-di-indirizzo-e-coordinamento-tecnico-per/at\_download/file*](http://www.regione.emilia-romagna.it/temi/territorio/cartografia-regionale/vedi-anche/database-topografico-regionale/le-norme-e-gli-atti-in-vigore/atto-di-indirizzo-e-coordinamento-tecnico-per/at_download/file)&lt;/gco:CharacterString&gt;

&lt;/gmd:otherCitationDetails&gt;

**…**

&lt;/gmd:CI\_Citation&gt;

&lt;/gmd:citation&gt;

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Descrizione

  **Nome elemento**                   **Descrizione**
  ----------------------------------- ---------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-17
  **Molteplicità**                    \[1\]
  **Elemento INSPIRE**                Breve descrizione della risorsa
  **Definizione**                     Breve testo di descrizione del contenuto della risorsa.
  **Istruzioni di implementazione**   Testo libero.

**Raccomandazione 13** La descrizione può includere:

- un breve riassunto con i dettagli più importanti sui dati documentati;

- la copertura dei dati, ovvero la trascrizione linguistica
dell'estensione o localizzazione geografica in aggiunta al riquadro di
delimitazione (bounding box);

- i principali attributi dei dati;

- le fonti dei dati;

- i riferimenti normativi (che possono essere meglio dettagliati
attraverso l'elemento "*Altri dettagli*" - v. § 2.1.2.7);

- l'importanza della risorsa.

**Raccomandazione 14** Non utilizzare acronimi di cui non si fornisce
una spiegazione.

**Raccomandazione 15** Riassumere i dettagli più importanti nei primi
periodi o nei primi 100 caratteri.

**Esempio di XML:**

**…**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

**…**

&lt;gmd:abstract&gt;

&lt;gco:CharacterString&gt;Dataset dei siti italiani iscritti nella
Lista del Patrimonio Mondiale UNESCO identificati dalle relative
perimetrazioni (area iscritta e zona tampone), approvate dal Comitato
del Patrimonio Mondiale UNESCO. I siti, in alcuni casi, sono di tipo
seriale, cioè composti da più elementi identificati, denominati e
individuati sul territorio. Le perimetrazioni sono state identificate su
cartografie differenti secondo i casi e l'estensione geografica. Le
perimetrazioni di origine fanno parte dei documenti ufficiali di ciascun
sito.Attributi e loro significato:ID: Identificativo interno;
COD\_UNESCO: Codice internazionale associato al sito; SITO:
Denominazione ufficiale del sito; SERIALE: 0 sito non seriale, 1 sito
seriale; COD\_COMPON: Codice della componente (è popolato solo per le
componenti dei siti seriali); COMPONENTE: Denominazione ufficiale della
componente; TIPO\_AREA: sito per area che identifica un sito, buffer per
area che identifica zona tampone di un sito; SCALA\_NOMI: Fattore di
scala della cartografia utilizzata per la perimetrazione del sito o area
di rispetto; TIPOLOGIA: sito culturale, monumento, complesso
monumentale, sito, sito naturale, formazione fisica e biologica,
formazione geologica, habitat minacciato, sito di eccezionale bellezza,
interesse scientifico, sito misto&lt;/gco:CharacterString&gt;

&lt;/gmd:abstract&gt;

**…**

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Parole chiave

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Nome elemento**                   **Parole chiave**
  ----------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-18 (I-18.1, I-18.2)

  **Molteplicità**                    \[1..\*\]

  **Elemento INSPIRE**                Parola chiave (Valore della parola chiave – Vocabolario controllato di origine)

  **Definizione**                     Parola formalizzata o utilizzata comunemente per descrivere la risorsa.

  **Istruzioni di implementazione**   -   **Parola chiave** \[1..\*\] - Testo libero
                                      
                                      -   **Thesaurus** \[0..1\] :
                                      
                                          -   **Titolo** \[1\]– Testo libero;
                                      
                                          -   **Data** \[1..\*\] – utilizzare il formato previsto dallo Standard ISO 8601: *aaaa-mm-gg* oppure *aaaammgg*;
                                      
                                          -   **Tipo data** \[1..\*\] **-** L’elemento deve assumere uno dei valori della lista “*CI\_DateTypeCode*” (§ 3.4.3.1 - all. 2 DM).
                                      
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Requisito 23** Il DM 10/11/2011 e il Regolamento 1205/2008/CE
prescrivono la presenza di **almeno una parola chiave**.

**Requisito 24 Se viene utilizzata una sola parola chiave**, allora
essa:

- deve descrivere la categoria tematica INSPIRE corrispondente, come
definita negli allegati I, II e III della Direttiva;

- deve essere espressa in italiano per i 34 temi INSPIRE.

**Requisito 25** Nel caso delle parole chiave relative ai temi INSPIRE,
è obbligatorio citare le informazioni relative al thesaurus *GEMET –
INSPIRE Themes* che sono le seguenti:

**Titolo** = “*GEMET - INSPIRE themes, version 1.0*”

**Data** = “*2010-01-13*”

**Tipo data** = “*pubblicazione*”.

I nomi e le definizioni delle 34 categorie tematiche di INSPIRE sono
stati integrati in una sezione dedicata del thesaurus GEMET (General
Environmental Multilingual Thesaurus) nelle 24 lingue ufficiali della
Comunità Europea (la versione italiana è disponibile all'indirizzo
http://www.eionet.europa.eu/gemet/inspire\_themes?langcode=it). Tale
sezione è nota come "**GEMET - INSPIRE themes**".

L'elenco delle parole chiave corrispondenti ai temi INSPIRE è riportato
anche nell'allegato A del presente documento. Perché possa essere
validata con il validatore disponibile nel geoportale INSPIRE (v. §
1.3.2.2), essendo *case sensitive*, è necessario fornire la parola
chiave come riportata nel thesaurus indicato.

In aggiunta al thesaurus citato, possono essere inserite altre parole
chiave, che possono essere descritte sia tramite un testo libero che
essere derivate da un Vocabolario Controllato.

**Requisito 26 Se vengono utilizzate più parole chiave** e queste sono
tratte da Vocabolari controllati (thesauri, ontologie), per esempio
**GEMET - Concepts**, **EUROVOC** o **AGROVOC**, allora deve essere
fornita anche la citazione del Vocabolario controllato di origine.

**Requisito 27** Nel caso le parole chiave siano tratte dal thesaurus
GEMET[^6], allora le informazioni da citare devono essere le seguenti:

**Titolo** = “*GEMET – Concepts, version 2.4*”

**Data** = “*2008-06-01*”

**Tipo data** = “*pubblicazione*”.

Nel tracciato XML che segue sono riportati alcuni esempi su come
riportare parole chiave tratte dai thesauri GEMET - Concepts e AGROVOC.

**Requisito 28** La citazione del thesaurus deve includere almeno il
**titolo**, la **data** e il **tipo di data** (tra creazione,
pubblicazione o revisione) del vocabolario controllato da cui sono
tratte le parole chiave.

**Requisito 29** Per poter essere coerenti con lo Standard ISO 19115,
tutte le parole chiave tratte dalla stessa versione dello stesso
vocabolario controllato devono essere raggruppate nella stessa istanza
della proprietà "*descriptiveKeywords*" di ISO 19115.

**Raccomandazione 16** è preferibile scegliere parole chiave da
collezioni di termini collegati e predefiniti (vocabolari controllati).

**Raccomandazione 17** Si consiglia di inserire almeno due parole chiave
in aggiunta a quella (obbligatoria) tratta da *GEMET - INSPIRE themes*.

**Raccomandazione 18** Sarebbe auspicabile includere sia un codice (un
valore in linguaggio neutrale) che un'etichetta "human-readable" (in
italiano).

**Raccomandazione 19** è importante specificare la versione del
thesaurus usato per le parole chiave.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

**…**

&lt;gmd:descriptiveKeywords&gt;

&lt;gmd:MD\_Keywords&gt;

&lt;gmd:keyword&gt;

&lt;gco:CharacterString&gt;Orto immagini&lt;/gco:CharacterString&gt;

&lt;/gmd:keyword&gt;

&lt;gmd:thesaurusName&gt;

&lt;gmd:CI\_Citation&gt;

&lt;gmd:title&gt;

&lt;gco:CharacterString&gt;GEMET - INSPIRE themes, version
1.0&lt;/gco:CharacterString&gt;

&lt;/gmd:title&gt;

&lt;gmd:date&gt;

&lt;gmd:CI\_Date&gt;

&lt;gmd:date&gt;

&lt;gco:Date&gt;2008-06-01&lt;/gco:Date&gt;

&lt;/gmd:date&gt;

&lt;gmd:dateType&gt;

&lt;gmd:CI\_DateTypeCode codeListValue="publication"
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_DateTypeCode"&gt;pubblicazione&lt;/gmd:CI\_DateTypeCode&gt;

&lt;/gmd:dateType&gt;

&lt;/gmd:CI\_Date&gt;

&lt;/gmd:date&gt;

&lt;/gmd:CI\_Citation&gt;

&lt;/gmd:thesaurusName&gt;

&lt;/gmd:MD\_Keywords&gt;

&lt;/gmd:descriptiveKeywords&gt;

&lt;gmd:descriptiveKeywords&gt;

&lt;gmd:MD\_Keywords&gt;

&lt;gmd:keyword&gt;

&lt;gco:CharacterString&gt;ambiente naturale&lt;/gco:CharacterString&gt;

&lt;/gmd:keyword&gt;

&lt;gmd:thesaurusName&gt;

&lt;gmd:CI\_Citation&gt;

&lt;gmd:title&gt;

&lt;gco:CharacterString&gt;GEMET – Concepts, version
2.4&lt;/gco:CharacterString&gt;

&lt;/gmd:title&gt;

&lt;gmd:date&gt;

&lt;gmd:CI\_Date&gt;

&lt;gmd:date&gt;

&lt;gco:Date&gt;2010-01-13&lt;/gco:Date&gt;

&lt;/gmd:date&gt;

&lt;gmd:dateType&gt;

&lt;gmd:CI\_DateTypeCode codeListValue="publication"
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_DateTypeCode"&gt;pubblicazione&lt;/gmd:CI\_DateTypeCode&gt;

&lt;/gmd:dateType&gt;

&lt;/gmd:CI\_Date&gt;

&lt;/gmd:date&gt;

&lt;/gmd:CI\_Citation&gt;

&lt;/gmd:thesaurusName&gt;

&lt;/gmd:MD\_Keywords&gt;

&lt;/gmd:descriptiveKeywords&gt;

&lt;gmd:descriptiveKeywords&gt;

&lt;gmd:MD\_Keywords&gt;

&lt;gmd:keyword&gt;

&lt;gco:CharacterString&gt;risorse naturali&lt;/gco:CharacterString&gt;

&lt;/gmd:keyword&gt;

&lt;gmd:thesaurusName&gt;

&lt;gmd:CI\_Citation&gt;

&lt;gmd:title&gt;

&lt;gco:CharacterString&gt;AGROVOC&lt;/gco:CharacterString&gt;

&lt;/gmd:title&gt;

&lt;gmd:date&gt;

&lt;gmd:CI\_Date&gt;

&lt;gmd:date&gt;

&lt;gco:Date&gt;2008-04-14&lt;/gco:Date&gt;

&lt;/gmd:date&gt;

&lt;gmd:dateType&gt;

&lt;gmd:CI\_DateTypeCode codeListValue="publication"
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_DateTypeCode"&gt;pubblicazione&lt;/gmd:CI\_DateTypeCode&gt;

&lt;/gmd:dateType&gt;

&lt;/gmd:CI\_Date&gt;

&lt;/gmd:date&gt;

&lt;/gmd:CI\_Citation&gt;

&lt;/gmd:thesaurusName&gt;

&lt;/gmd:MD\_Keywords&gt;

&lt;/gmd:descriptiveKeywords&gt;

&lt;gmd:descriptiveKeywords&gt;

&lt;gmd:MD\_Keywords&gt;

&lt;gmd:keyword&gt;

&lt;gco:CharacterString&gt;raster&lt;/gco:CharacterString&gt;

&lt;/gmd:keyword&gt;

&lt;/gmd:MD\_Keywords&gt;

&lt;/gmd:descriptiveKeywords&gt;

**…**

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Punto di contatto

  --------------------------------------------------------------------------------------------------------------------------------------------------------
  **Nome elemento**                   **Punto di contatto**
  ----------------------------------- --------------------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-19 (I-19.1, I-19.2, I-19.3, I-19.4)

  **Molteplicità**                    \[1..\*\]

  **Elemento INSPIRE**                Parte responsabile – Ruolo della parte responsabile

  **Definizione**                     Organizzazione che è possibile contattare per avere informazioni sulla risorsa.

  **Istruzioni di implementazione**   -   **Nome dell’Ente** \[1\] - Testo libero
                                      
                                      -   **Ruolo** \[1\] – L’elemento deve assumere uno dei valori della lista “*CI\_RoleCode*” (§3.4.3.3 - all. 2 DM).
                                      
                                      -   **Sito web** \[0..1\] - formato URL. Specificare obbligatoriamente anche il protocollo (es. *http*).
                                      
                                      -   **Telefono** \[0..1\] - Testo libero.
                                      
                                      -   **E-mail** \[1..\*\] - Testo libero.
                                      
  --------------------------------------------------------------------------------------------------------------------------------------------------------

**Requisito 30** Devono essere forniti i seguenti elementi: **nome
dell'Ente**, **ruolo**, **indirizzo e-mail**, **sito web** e/o
**riferimento telefonico**.

**Requisito 31** Come indicato all'allegato 2 del DM, deve essere
documentato almeno uno dei due metadati tra "Sito web" e "Telefono".

**Raccomandazione 20** Il nome dell'Ente dovrebbe essere riportato per
intero, senza abbreviazioni. Si consiglia di indicare indirizzi e-mail
istituzionali e non personali.

**Raccomandazione 21** Scegliere il ruolo che meglio rappresenta la
funzione espletata dall'Ente.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

**…**

&lt;gmd:pointOfContact&gt;

&lt;gmd:CI\_ResponsibleParty&gt;

&lt;gmd:organisationName&gt;

&lt;gco:CharacterString&gt;Regione Piemonte – Settore cartografia e
sistema informativo territoriale&lt;/gco:CharacterString&gt;

&lt;/gmd:organisationName&gt;

&lt;gmd:contactInfo&gt;

&lt;gmd:CI\_Contact&gt;

&lt;gmd:address&gt;

&lt;gmd:CI\_Address&gt;

&lt;gmd:electronicMailAddress&gt;

&lt;gco:CharacterString&gt;sitad@csi.it&lt;/gco:CharacterString&gt;

&lt;/gmd:electronicMailAddress&gt;

&lt;/gmd:CI\_Address&gt;

&lt;/gmd:address&gt;

&lt;gmd:onlineResource&gt;

&lt;gmd:CI\_OnlineResource&gt;

&lt;gmd:linkage&gt;

&lt;gmd:URL&gt;http://www.sistemapiemonte.it/serviziositad/&lt;/gmd:URL&gt;

&lt;/gmd:linkage&gt;

&lt;/gmd:CI\_OnlineResource&gt;

&lt;/gmd:onlineResource&gt;

&lt;/gmd:CI\_Contact&gt;

&lt;/gmd:contactInfo&gt;

&lt;gmd:role&gt;

&lt;gmd:CI\_RoleCode codeListValue="pointOfContact"
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_RoleCode"&gt;punto
di contatto&lt;/gmd:CI\_RoleCode&gt;

&lt;/gmd:role&gt;

&lt;/gmd:CI\_ResponsibleParty&gt;

&lt;/gmd:pointOfContact&gt;

**…**

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Set di caratteri

  **Nome elemento**                   **Set di caratteri**
  ----------------------------------- -------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-23
  **Molteplicità**                    \[0..\*\]
  **Elemento INSPIRE**                Nessun elemento corrispondente
  **Definizione**                     Nome dello standard del set di caratteri utilizzato per i dati.
  **Istruzioni di implementazione**   L’elemento deve assumere uno dei valori della lista “*MD\_CharacterSetCode*” (§ 3.4.3.5 – all. 2 DM).

**Requisito 32** L’elemento è condizionato: esso deve essere documentato
se ISO/IEC 10646-1 non è utilizzato e non è definito dall’ecoding (rif.
ISO 19115).

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

**…**

&lt;gmd:characterSet&gt;

&lt;gmd:MD\_CharacterSetCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_CharacterSetCode"
codeListValue="utf8"&gt;utf8&lt;/gmd:MD\_CharacterSetCode&gt;

&lt;/gmd:characterSet&gt;

**…**

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Tipo di rappresentazione spaziale

  **Nome elemento**                   **Tipo di rappresentazione spaziale**
  ----------------------------------- ---------------------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-20
  **Molteplicità**                    \[1..\*\]
  **Elemento INSPIRE**                Nessun elemento corrispondente
  **Definizione**                     Metodo di rappresentazione spaziale dei dati.
  **Istruzioni di implementazione**   L’elemento deve assumere uno dei valori della lista “*CI\_SpatialRepresentationTypeCode*” (§ 3.4.3.14 - all. 2 DM).

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

**…**

&lt;gmd:spatialRepresentationType&gt;

&lt;gmd:MD\_SpatialRepresentationTypeCode codeListValue="vector"
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_SpatialRepresentationTypeCode"&gt;dati
vettoriali&lt;/gmd:MD\_SpatialRepresentationTypeCode&gt;

&lt;/gmd:spatialRepresentationType&gt;

**…**

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Risoluzione spaziale

  -----------------------------------------------------------------------------------------------------------------------------------------------------------
  **Nome elemento**                   **Risoluzione spaziale**
  ----------------------------------- -----------------------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-21 (I-21.1, I-21.2)

  **Molteplicità**                    \[1..\*\]

  **Elemento INSPIRE**                Risoluzione spaziale

  **Definizione**                     Fattore che fornisce la comprensione generale della densità dei dati nel dataset.

  **Istruzioni di implementazione**   -   **Scala equivalente** \[1\]– Inserire il denominatore della scala equivalente.
                                      
                                      -   **Distanza** \[1\] – Inserire la risoluzione geometrica al suolo espressa come valore numerico e unità di misura.
                                      
  -----------------------------------------------------------------------------------------------------------------------------------------------------------

**Requisito 33** La risoluzione spaziale può essere espressa o
attraverso la scala equivalente o attraverso la risoluzione geometrica
al suolo (distanza). Deve essere fornito, quindi, **uno solo** tra i due
elementi (**scala equivalente** o **distanza**).

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

**…**

&lt;gmd:spatialResolution&gt;

&lt;gmd:MD\_Resolution&gt;

&lt;gmd:equivalentScale&gt;

&lt;gmd:MD\_RepresentativeFraction&gt;

&lt;gmd:denominator&gt;

&lt;gco:Integer&gt;10000&lt;/gco:Integer&gt;

&lt;/gmd:denominator&gt;

&lt;/gmd:MD\_RepresentativeFraction&gt;

&lt;/gmd:equivalentScale&gt;

&lt;/gmd:MD\_Resolution&gt;

&lt;/gmd:spatialResolution&gt;

**…**

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

oppure

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

**…**

&lt;gmd:spatialResolution&gt;

&lt;gmd:MD\_Resolution&gt;

&lt;gmd:distance&gt;

&lt;gco:Distance
uom="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/uom/ML\_gmxUom.xml\#m"&gt;10.0&lt;/gco:Distance&gt;

&lt;/gmd:distance&gt;

&lt;/gmd:MD\_Resolution&gt;

&lt;/gmd:spatialResolution&gt;

**…**

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Lingua

  **Nome elemento**                   **Lingua**
  ----------------------------------- ------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-22
  **Molteplicità**                    \[1..\*\]
  **Elemento INSPIRE**                Lingua della risorsa
  **Definizione**                     Linguaggio utilizzato per i dati.
  **Istruzioni di implementazione**   Fare riferimento al § 2.1.1.2 (Lingua dei metadati).

**Requisito 34** L'elemento deve essere compilato con un valore tratto
dalla codelist *LanguageCode* di cui a ISO/TS 19139, basata sui codici a
tre lettere di ISO 639-2.

**Raccomandazione 22** Se la risorsa non contiene nessuna informazione
testuale (per esempio, solo codici e cifre), la lingua dovrebbe essere
impostata sul valore della lingua dei metadati (**italiano**).

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

**…**

&lt;gmd:language&gt;

&lt;gmd:LanguageCode codeList="http://www.loc.gov/standards/iso639-2/"
codeListValue="ita"&gt;ita&lt;/gmd:LanguageCode&gt;

&lt;/gmd:language&gt;

**…**

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Categoria tematica

  **Nome elemento**                   **Categoria tematica**
  ----------------------------------- ---------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-24
  **Molteplicità**                    \[1..\*\]
  **Elemento INSPIRE**                Categoria di argomento
  **Definizione**                     Tema principale cui si riferiscono i dati.
  **Istruzioni di implementazione**   L’elemento deve assumere uno dei valori della lista “*MD\_TopicCategoryCode*” (§ 3.4.3.15 – all. 2 DM).

**Requisito 35** Il valore per esprimere la categoria tematica deve
essere un nome in linguaggio neutrale (v. i valori presenti nella
colonna "*Elemento corrispondente ISO 19115:2003*" della tabella al §
3.4.3.15 – all. 2 DM).

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

**…**

&lt;gmd:topicCategory&gt;

&lt;gmd:MD\_TopicCategoryCode&gt;imageryBaseMapsEarthCover&lt;/gmd:MD\_TopicCategoryCode&gt;

&lt;/gmd:topicCategory&gt;

**…**

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Informazioni supplementari

  **Nome elemento**                   **Informazioni supplementari**
  ----------------------------------- --------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-25
  **Molteplicità**                    \[0..1\]
  **Elemento INSPIRE**                Nessun elemento corrispondente
  **Definizione**                     Informazioni descrittive supplementari sui dati.
  **Istruzioni di implementazione**   Testo libero.

**Raccomandazione 23** Si consiglia di utilizzare questo elemento per
inserire l’URL dove è possibile reperire il file di qualsiasi
documentazione tecnica utile a fornire ulteriori informazioni sulla
risorsa (es. capitolato, specifiche tecniche, …). L’elemento può essere
correlato con il metadato “*Altri dettagli*” da utilizzare per
specificare il riferimento alle norme o atti amministrativi su cui si
basa la produzione e/o il trattamento dei dati.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

**…**

&lt;gmd:supplementalInformation&gt;
&lt;gco:CharacterString&gt;[*http://www.regione.emilia-romagna.it/temi/territorio/cartografia-regionale/vedi-anche/database-topografico-regionale/progetti-in-corso/capitolato-tecnico-per-la-progettazione-la6/at\_download/file*](http://www.regione.emilia-romagna.it/temi/territorio/cartografia-regionale/vedi-anche/database-topografico-regionale/progetti-in-corso/capitolato-tecnico-per-la-progettazione-la6/at_download/file)&lt;/gco:CharacterString&gt;

&lt;/gmd:supplementalInformation&gt;

**…**

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

### Vincoli sui dati

#### Limitazione d’uso 

  **Nome elemento**                   **Limitazione d’uso**
  ----------------------------------- ----------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-26
  **Molteplicità**                    \[1\]
  **Elemento INSPIRE**                Condizioni applicabili all’accesso e all’uso
  **Definizione**                     Restrizioni di utilizzo dei dati.
  **Istruzioni di implementazione**   Testo libero.

**Requisito 36** Se all'accesso e all'uso della risorsa non è applicata
nessuna condizione, deve essere indicato il valore "*Nessuna condizione
applicabile*". Se le condizioni applicate, invece, sono sconosciute,
deve essere indicato il valore "*Condizioni sconosciute*".

**Requisito 37** Attraverso questo elemento deve essere fornita la
descrizione dei termini e delle condizioni, inclusi anche, se
applicabili, i costi corrispondenti dei dati. Citare esplicitamente le
licenze d'uso adottate (standard o definite dall'Ente). È possibile
anche inserire il link (URL) dove tali termini,condizioni e/o licenze
sono descritti.

**Raccomandazione 24** Per informazioni più dettagliate, si consiglia di
indicare il link alla licenza utilizzata (per es.
*http://creativecommons.org/licenses/by/4.0*), a un sito web o a un
documento che contiene le informazioni.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

**…**

&lt;gmd:resourceConstraints&gt;

&lt;gmd:MD\_Constraints&gt;

&lt;gmd:useLimitation&gt;

&lt;gco:CharacterString&gt;Nessuna condizione
applicabile&lt;/gco:CharacterString&gt;

&lt;/gmd:useLimitation&gt;

**…**

&lt;/gmd:MD\_Constraints&gt;

&lt;/gmd:resourceConstraints&gt;

**…**

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Vincoli di accesso

  **Nome elemento**                   **Vincoli di accesso**
  ----------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-27
  **Molteplicità**                    \[1..\*\]
  **Elemento INSPIRE**                Corrisponde all’elemento “Vincoli per l’accesso pubblico”
  **Definizione**                     Vincoli di accesso ai dati per assicurare la protezione della privacy o della proprietà intellettuale e ogni altra restrizione o limitazione ad ottenere la risorsa (l’accesso comprende la visualizzazione, la stampa o la riproduzione del dato, non comprende l’elaborazione del dato). Il dato può essere pubblico ovvero conoscibile da chiunque oppure a conoscibilità limitata (cfr. art. 1 Codice A. D.)
  **Istruzioni di implementazione**   L’elemento deve assumere uno dei valori della lista “*MD\_RestrictionCode*” (§ 3.4.3.12 – all. 2 DM).

**Requisito 38** Se l’elemento assume il valore “*altri vincoli*”
(*otherRestrictions*), allora è necessario documentare anche l’elemento
“*Altri vincoli*” (§ 2.1.3.4).

**Requisito 39** Vista l’estensione della lista *MD\_RestrictionCode*
effettuata dal RNDT con l’aggiunta del valore “*dato pubblico*”, se si
vuole utilizzare tale valore, l’elemento deve assumere il valore “*altri
vincoli*” (*otherRestrictions*) e l’elemento “*Altri vincoli*” (che è
testo libero) deve assumere il valore “*dato pubblico*”.

**Requisito 40** Per garantire la conformità ad INSPIRE, se il valore
dell'elemento “*Vincoli di fruibilità*” (§ 2.1.3.3) è pari ad “*Altri
vincoli*” (*otherRestrictions*), allora anche il valore dell’elemento
corrente “*Vincoli di accesso*” deve assumere il valore “*Altri
vincoli*” (*otherRestrictions*), dettagliando nell’elemento “*Altri
vincoli*” (§ 2.1.3.4), che è testo libero, le informazioni relative ai
due tipi di vincolo. A tale proposito, v. anche le istruzioni e gli
esempi XML al § 2.1.3.4.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

**…**

&lt;gmd:resourceConstraints&gt;

**…**

&lt;gmd:MD\_LegalConstraints&gt;

&lt;gmd:accessConstraints&gt;

&lt;gmd:MD\_RestrictionCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_RestrictionCode"
codeListValue="copyright"&gt;copyright&lt;/gmd:MD\_RestrictionCode&gt;

&lt;/gmd:accessConstraints&gt;

**…**

&lt;/gmd:MD\_LegalConstraints&gt;

&lt;/gmd:resourceConstraints&gt;

**…**

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Vincoli di fruibilità

  **Nome elemento**                   **Vincoli di fruibilità**
  ----------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-28
  **Molteplicità**                    \[1..\*\]
  **Elemento INSPIRE**                Nessun elemento corrispondente
  **Definizione**                     Vincoli sulla possibilità di utilizzare il dato, anche trasferendolo nei sistemi informativi automatizzati di un'altra amministrazione, derivanti da regolamenti e norme nazionali ed europee (protezione della privacy, proprietà intellettuale, altre restrizioni) - cfr. art. 1 Codice A.D.
  **Istruzioni di implementazione**   L’elemento deve assumere uno dei valori della lista “*MD\_RestrictionCode*” (§ 3.4.3.12 – all. 2 DM).

**Requisito 41** Se l’elemento assume il valore “*altri vincoli*”
(*otherRestrictions*), allora è necessario documentare anche l’elemento
“*Altri vincoli*” (§ 2.1.3.4).

**Requisito 42** Vista l’estensione della lista *MD\_RestrictionCode*
effettuata dal RNDT con l’aggiunta del valore “*dato pubblico*”, se si
vuole utilizzare tale valore, l’elemento deve assumere il valore “*altri
vincoli*” (*otherRestrictions*) e l’elemento “*Altri vincoli*” (che è
testo libero) deve assumere il valore “*dato pubblico*”.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

**…**

&lt;gmd:resourceConstraints&gt;

&lt;gmd:MD\_LegalConstraints&gt;

**…**

&lt;gmd:useConstraints&gt;

&lt;gmd:MD\_RestrictionCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_RestrictionCode"
codeListValue="copyright"&gt;copyright&lt;/gmd:MD\_RestrictionCode&gt;

&lt;/gmd:useConstraints&gt;

**…**

&lt;/gmd:MD\_LegalConstraints&gt;

&lt;/gmd:resourceConstraints&gt;

**…**

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Altri vincoli

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Nome elemento**                   **Altri vincoli**
  ----------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-29

  **Molteplicità**                    \[0..\*\]

  **Elemento INSPIRE**                Corrisponde all’elemento “Vincoli per l’accesso pubblico”

  **Definizione**                     Altri vincoli e prerequisiti legali per l’accesso e l’utilizzo della risorsa.

  **Istruzioni di implementazione**   Testo libero.
                                      
                                      In riferimento a quanto indicato per gli elementi "*Vincoli di accesso*" (§ 2.1.3.2) e "*Vincoli di fruibilità*" (§ 2.1.3.3), i casi possibili sono rappresentati nella seguente tabella:
                                      
                                                  **Vincoli accesso**   **Vincoli fruibilità**   **Altri vincoli**                                   **note**
                                        --------- --------------------- ------------------------ --------------------------------------------------- --------------------------------------------
                                        1° caso   ≠ ‘altri vincoli’     ≠ ‘altri vincoli’        **Non deve essere documentato.**                    Combinazione esempi § 2.1.3.2 e § 2.1.3.3.
                                        2° caso   = ‘altri vincoli’     ≠ ‘altri vincoli’        Dettagliare i vincoli di accesso.                   v\. esempio 1
                                        3° caso   = ‘altri vincoli’     = ‘altri vincoli’        Dettagliare i vincoli di accesso e di fruibilità.   v\. esempio 2
                                        4° caso   ≠ ‘altri vincoli’     = ‘altri vincoli’        Dettagliare i vincoli di fruibilità.                **Non ammissibile per INSPIRE**
                                      
                                      Per garantire la conformità ad INSPIRE, come indicato anche nelle istruzioni al § 2.1.3.3, il 4° caso rappresentato nella tabella (con sfondo grigio) non è ammissibile.
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Requisito 43** L’elemento deve essere valorizzato solo se l’elemento
“*Vincoli di accesso*” (§ 2.1.3.2) e/o l’elemento “*Vincoli di
fruibilità*” (§ 2.1.3.3) assumono il valore ‘*Altri vincoli*’
(*otherRestrictions*).

**Esempi di XML:**

**esempio 1**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

**…**

&lt;gmd:resourceConstraints&gt;

&lt;gmd:MD\_LegalConstraints&gt;

**…**

&lt;gmd:accessConstraints&gt;

&lt;gmd:MD\_RestrictionCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_RestrictionCode"
codeListValue="otherRestrictions"&gt;altri
vincoli&lt;/gmd:MD\_RestrictionCode&gt;

&lt;/gmd:accessConstraints&gt;

&lt;gmd:useConstraints&gt;

&lt;gmd:MD\_RestrictionCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_RestrictionCode"
codeListValue="copyright"&gt;copyright&lt;/gmd:MD\_RestrictionCode&gt;

&lt;/gmd:useConstraints&gt;

&lt;gmd:otherConstraints&gt;

&lt;gco:CharacterString&gt;L’accesso ai dati è
pubblico&lt;/gco:CharacterString&gt;

&lt;/gmd:otherConstraints&gt;

&lt;/gmd:MD\_LegalConstraints&gt;

&lt;/gmd:resourceConstraints&gt;

**…**

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

**esempio 2**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

**…**

&lt;gmd:resourceConstraints&gt;

&lt;gmd:MD\_LegalConstraints&gt;

**…**

&lt;gmd:accessConstraints&gt;

&lt;gmd:MD\_RestrictionCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_RestrictionCode"
codeListValue="otherRestrictions"&gt;altri
vincoli&lt;/gmd:MD\_RestrictionCode&gt;

&lt;/gmd:accessConstraints&gt;

&lt;gmd:useConstraints&gt;

&lt;gmd:MD\_RestrictionCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_RestrictionCode"
codeListValue="otherRestrictions"&gt;altri vincoli
&lt;/gmd:MD\_RestrictionCode&gt;

&lt;/gmd:useConstraints&gt;

&lt;gmd:otherConstraints&gt;

&lt;gco:CharacterString&gt;L’accesso e la fruibilità del dato sono
pubblici&lt;/gco:CharacterString&gt;

&lt;/gmd:otherConstraints&gt;

&lt;/gmd:MD\_LegalConstraints&gt;

&lt;/gmd:resourceConstraints&gt;

**…**

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Vincoli di sicurezza

  **Nome elemento**                   **Vincoli di sicurezza**
  ----------------------------------- ---------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-30
  **Molteplicità**                    \[1\]
  **Elemento INSPIRE**                Corrisponde all’elemento “Vincoli per l’accesso pubblico”
  **Definizione**                     Restrizioni imposte ai dati per questioni di sicurezza.
  **Istruzioni di implementazione**   L’elemento deve assumere uno dei valori della lista “*MD\_ClassificationCode*” (§ 3.4.3.6 – all. 2 DM).

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

**…**

&lt;gmd:resourceConstraints&gt;

&lt;gmd:MD\_SecurityConstraints&gt;

&lt;gmd:classification&gt;

&lt;gmd:MD\_ClassificationCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_ClassificationCode"
codeListValue="unclassified"&gt;non
classificato&lt;/gmd:MD\_ClassificationCode&gt;

&lt;/gmd:classification&gt;

&lt;/gmd:MD\_SecurityConstraints&gt;

&lt;/gmd:resourceConstraints&gt;

**…**

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

### Estensione dei dati

#### Localizzazione geografica

  -------------------------------------------------------------------------------------------------------------------------------------------
  **Nome elemento**                   **Localizzazione geografica**
  ----------------------------------- -------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-31 (I-31.1, I-31.2, I-31.3, I-31.4)

  **Molteplicità**                    \[1\]

  **Elemento INSPIRE**                Riquadro di delimitazione geografica

  **Definizione**                     Estensione della risorsa nello spazio geografico fornita sotto forma di un riquadro di delimitazione.

  **Istruzioni di implementazione**   -   **Longitudine ovest** \[1\] - Utilizzare il tipo *gco:Decimal*
                                      
                                      -   **Longitudine est** \[1\] - Utilizzare il tipo *gco:Decimal*
                                      
                                      -   **Latitudine sud** \[1\] - Utilizzare il tipo *gco:Decimal*
                                      
                                      -   **Latitudine nord** \[1\] - Utilizzare il tipo *gco:Decimal*
                                      
  -------------------------------------------------------------------------------------------------------------------------------------------

**Requisito 44** Il riquadro di delimitazione geografica (bounding box)
deve essere il più piccolo possibile.

**Requisito 45** Il riquadro di delimitazione geografica (bounding box)
deve essere espresso in gradi decimali con una precisione di almeno due
cifre decimali nel sistema di riferimento WGS84.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

**…**

&lt;gmd:extent&gt;

&lt;gmd:EX\_Extent&gt;

&lt;gmd:geographicElement&gt;

&lt;gmd:EX\_GeographicBoundingBox&gt;

&lt;gmd:westBoundLongitude&gt;

&lt;gco:Decimal&gt;14.34879&lt;/gco:Decimal&gt;

&lt;/gmd:westBoundLongitude&gt;

&lt;gmd:eastBoundLongitude&gt;

&lt;gco:Decimal&gt;15.14967&lt;/gco:Decimal&gt;

&lt;/gmd:eastBoundLongitude&gt;

&lt;gmd:southBoundLatitude&gt;

&lt;gco:Decimal&gt;40.973&lt;/gco:Decimal&gt;

&lt;/gmd:southBoundLatitude&gt;

&lt;gmd:northBoundLatitude&gt;

&lt;gco:Decimal&gt;41.48564&lt;/gco:Decimal&gt;

&lt;/gmd:northBoundLatitude&gt;

&lt;/gmd:EX\_GeographicBoundingBox&gt;

&lt;/gmd:geographicElement&gt;

&lt;/gmd:EX\_Extent&gt;

&lt;/gmd:extent&gt;

**…**

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Estensione verticale

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Nome elemento**                   **Estensione verticale**
  ----------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-32 (I-32.1, I-32.2, I-32.3, I-32.4)

  **Molteplicità**                    \[0..1\]

  **Elemento INSPIRE**                Nessun elemento corrispondente

  **Definizione**                     Dominio verticale dei dati.

  **Istruzioni di implementazione**   -   **Quota minima** \[1\] - utilizzare il tipo *gco:Real*.
                                      
                                      -   **Quota massima** \[1\] - utilizzare il tipo *gco:Real*.
                                      
                                      -   **CRS verticale** \[1\] **-** Per la documentazione di questo elemento, utilizzare, facendo comunque riferimento alla lista di valori “*MD\_ReferenceSystemCode*” di cui al § 3.4.3.11 dell’allegato 2 al DM, il tag relativo con la compilazione del solo attributo “href” attraverso il quale indicare l’URI al quale reperire le informazioni del sistema di riferimento considerato. Nel caso in cui si tratta di un sistema di riferimento inserito nel database di EPSG, allora l’URI da considerare è “[*http://www.epsg-registry.org/export.htm?gml=urn:ogc:def:crs:EPSG::xxxx*](http://www.epsg-registry.org/export.htm?gml=urn:ogc:def:crs:EPSG::xxxx)” dove ‘*xxxx*’ è il codice EPSG del sistema considerato (v., a questo proposito, la tabella delle corrispondenze al § 3.4.8.3 dell’allegato 2 al DM). Nel caso in cui il sistema di riferimento non sia inserito nel database di EPSG, allora l’URI da considerare è il seguente: “[*http://www.rndt.gov.it/ReferenceSystemCode\#codice\_dominio*](http://www.rndt.gov.it/ReferenceSystemCode#codice_dominio)” dove ‘*codice\_dominio*’ è il valore della omonima colonna della lista di valori citata, corrispondente al sistema considerato.
                                      
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Requisito 46** L'estensione verticale è opzionale. Se si vuole
documentare, devono essere forniti i seguenti elementi: **quota
minima**, **quota massima**, **CRS verticale**.

**Requisito 47** Per l'elemento "*CRS verticale*", deve essere
utilizzato, facendo comunque riferimento alla lista di valori
“*MD\_ReferenceSystemCode*” di cui al § 3.4.3.11 dell’allegato 2 al DM,
il tag ISO relativo con la compilazione del solo attributo “*href*”
attraverso il quale indicare l’URI al quale reperire le informazioni del
sistema di riferimento considerato. Nel caso di un sistema di
riferimento presente nel database di EPSG, allora deve essere inserito
l’URI

[*http://www.epsg-registry.org/export.htm?gml=urn:ogc:def:crs:EPSG::xxxx*](http://www.epsg-registry.org/export.htm?gml=urn:ogc:def:crs:EPSG::xxxx)

dove ‘*xxxx*’ è il codice EPSG del sistema considerato (v., a questo
proposito, la tabella delle corrispondenze al § 3.4.8.3 dell’allegato 2
al DM). Nel caso di un sistema di riferimento non presente in EPSG,
allora deve essere inserito l’URI

[*http://www.rndt.gov.it/ReferenceSystemCode\#codice\_dominio*](http://www.rndt.gov.it/ReferenceSystemCode#codice_dominio)

dove ‘*codice\_dominio*’ è il valore della omonima colonna della lista
di valori citata, corrispondente al sistema considerato.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

**…**

&lt;gmd:extent&gt;

&lt;gmd:EX\_Extent&gt;

**…**

&lt;gmd:verticalElement&gt;

&lt;gmd:EX\_VerticalExtent&gt;

&lt;gmd:minimumValue&gt;

&lt;gco:Real&gt;15.56&lt;/gco:Real&gt;

&lt;/ gmd:minimumValue&gt;

&lt; gmd:maximumValue&gt;

&lt;gco:Real&gt;345.15&lt;/gco:Real&gt;

&lt;/ gmd:maximumValue&gt;

&lt;gmd:verticalCRS
xlink:href="[*http://www.epsg-registry.org/export.htm?gml=urn:ogc:def:crs:EPSG::4979*](http://www.epsg-registry.org/export.htm?gml=urn:ogc:def:crs:EPSG::4979)"/&gt;

&lt;/gmd:EX\_VerticalExtent&gt;

&lt;/gmd:verticalElement&gt;

&lt;/gmd:EX\_Extent&gt;

&lt;/gmd:extent&gt;

**…**

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Estensione temporale

  -------------------------------------------------------------------------------------------
  **Nome elemento**                   **Estensione temporale**
  ----------------------------------- -------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-33 (I-33.1, I-33.2)

  **Molteplicità**                    \[0..\*\]

  **Elemento INSPIRE**                Estensione temporale

  **Definizione**                     Periodo di tempo coperto dal contenuto della risorsa.

  **Istruzioni di implementazione**   -   **Data inizio** \[1\] - formato ISO 8601
                                      
                                      -   **Data fine** \[1\] - formato ISO 8601
                                      
  -------------------------------------------------------------------------------------------

**Requisito 48** Il Regolamento 1205/2008/CE richiede l'indicazione di
un riferimento temporale scelto tra *estensione temporale* e *data* (che
può essere quella di *creazione* o di *pubblicazione* o di *revisione*).
In base a quanto previsto dal DM, per il RNDT l'estensione temporale è
opzionale. La prescrizione di INSPIRE è comunque rispettata in quanto il
medesimo DM prescrive l'obbligo di indicare almeno una tra i tre tipi di
data di cui sopra (v. § 2.1.2.2).

**Requisito 49** Nel tag XML ‘*gml:TimePeriod*’ è presente l’attributo
‘*gml:id*’ che è obbligatorio e che deve essere univoco all’interno
dello stesso file XML. Per garantire ciò, tale id può avere il formato
di un UUID.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

**…**

&lt;gmd:extent&gt;

&lt;gmd:EX\_Extent&gt;

**…**

&lt;gmd:temporalElement&gt;

&lt;gmd:EX\_TemporalExtent&gt;

&lt;gmd:extent&gt; &lt;gml:TimePeriod gml:id="TP1"&gt;

&lt;gml:beginPosition&gt;20051204&lt;/gml:beginPosition&gt;

&lt;gml:endPosition&gt;20070130&lt;/gml:endPosition&gt;

&lt;/gml:TimePeriod&gt;

&lt;/gmd:extent&gt;

&lt;/gmd:EX\_TemporalExtent&gt;

&lt;/gmd:temporalElement&gt;

**…**

&lt;/gmd:EX\_Extent&gt;

&lt;/gmd:extent&gt;

**…**

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

### Qualità dei dati

**Requisito 50 Deve** essere presente uno ed un solo set di informazioni
sulla qualità riferito all'intera risorsa (elemento *dataQualityInfo*).

#### Livello di qualità

  **Nome elemento**                   **Livello di qualità**
  ----------------------------------- -------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-34
  **Molteplicità**                    \[1\]
  **Elemento INSPIRE**                Nessun elemento corrispondente
  **Definizione**                     Livello cui sono applicate le informazioni di qualità.
  **Istruzioni di implementazione**   L'elemento deve assumere uno dei valori della lista “*MD\_ScopeCode*” (§ 3.4.3.13 - all. 2 DM).

**Requisito 51** Le informazioni sulla qualità devono essere riferite
all'intera risorsa (serie o dataset).

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:dtataQualityInfo&gt;

&lt;gmd:DQ\_DataQuality&gt;

&lt;gmd:scope&gt;

&lt;gmd:DQ\_Scope&gt;

&lt;gmd:level&gt;

&lt;gmd:MD\_ScopeCode codeListValue="dataset"
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_ScopeCode"&gt;dataset&lt;/gmd:MD\_ScopeCode&gt;

&lt;/gmd:level&gt;

&lt;/gmd:DQ\_Scope&gt;

&lt;/gmd:scope&gt;

**…**

&lt;/gmd:DQ\_DataQuality&gt;

&lt;/gmd:dataQualityInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Accuratezza posizionale

  ------------------------------------------------------------------------------------------------------------
  **Nome elemento**                   **Accuratezza posizionale**
  ----------------------------------- ------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-35 (I-35.1, I-35.2)

  **Molteplicità**                    \[1\]

  **Elemento INSPIRE**                Nessun elemento corrispondente

  **Definizione**                     Informazioni per la descrizione dell’accuratezza posizionale dei dati.

  **Istruzioni di implementazione**   -   **Unità di misura** \[1\] - utilizzare il metro (m).
                                      
                                      -   **Valore** \[1\] - utilizzare il tipo *gco:Real*.
                                      
  ------------------------------------------------------------------------------------------------------------

**Requisito 52** Devono essere forniti i seguenti elementi: **unità di
misura**, **valore**.

**Requisito 53** L'unità di misura da utilizzare deve essere il metro
(m). Per documentare questo elemento, è necessario valorizzare gli
attributi (presenti nei relativi tag) ‘*gml:id*’, ‘*codeSpace*’ e
‘*xlink:href*’ attraverso i quali vengono forniti i riferimenti del
sistema e l’unità utilizzati.

**Requisito 54** Per l'elemento "*Valore*" deve essere utilizzato il
tipo *gco:Real*.

Nel tracciato XML che segue è riportato un esempio su come documentare
gli elementi "Unità di misura" e "Valore".

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:dtataQualityInfo&gt;

&lt;gmd:DQ\_DataQuality&gt;

**…**

&lt;gmd:report&gt;

&lt;gmd:DQ\_AbsoluteExternalPositionalAccuracy&gt;

&lt;gmd:result&gt;

&lt;gmd:DQ\_QuantitativeResult&gt;

&lt;gmd:valueUnit&gt;

&lt;gml:BaseUnit gml:id="m"&gt;

&lt;gml:identifier codeSpace="http://www.bipm.org/en/si/base\_units
"&gt;m&lt;/gml:identifier&gt;

&lt;gml:unitsSystem xlink:href="http://www.bipm.org/en/si"/&gt;

&lt;/gml:BaseUnit&gt;

&lt;/gmd:valueUnit&gt;

&lt;gmd:value&gt;

&lt;gco:Record&gt;

&lt;gco:Real&gt;0.30&lt;/gco:Real&gt;

&lt;/gco:Record&gt;

&lt;/gmd:value&gt;

&lt;/gmd:DQ\_QuantitativeResult&gt;

&lt;/gmd:result&gt;

&lt;/gmd:DQ\_AbsoluteExternalPositionalAccuracy&gt;

&lt;/gmd:report&gt;

**…**

&lt;/gmd:DQ\_DataQuality&gt;

&lt;/gmd:dataQualityInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Genealogia

  **Nome elemento**                   **Genealogia**
  ----------------------------------- --------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-36
  **Molteplicità**                    \[1\]
  **Elemento INSPIRE**                Genealogia
  **Definizione**                     Testo descrittivo sulla storia del processo e/o la qualità generale del set di dati.
  **Istruzioni di implementazione**   Testo libero.

**Raccomandazione 25** Si consiglia di utilizzare l'elemento per
descrivere la provenienza e il processo di produzione dei dati, fornendo
informazioni sulla storia e il ciclo di vita, dalla rilevazione e
l’acquisizione fino alla forma attuale. Come richiesto dal Regolamento e
dalle linee guida INSPIRE, l’elemento può includere qualsiasi
informazione sulla qualità richiesta per garantire l’interoperabilità e
la valutazione dei dati e, dove necessario, una dichiarazione che indica
se l'insieme di dati è stato convalidato o sottoposto a un controllo di
qualità, se si tratta della versione ufficiale (qualora esistano più
versioni) e se ha una validità legale.

**Raccomandazione 26** Se il fornitore dei dati ha una propria procedura
per la gestione della qualità dei dati, allora dovrebbero essere
utilizzati gli appositi elementi previsti da ISO per valutare e
riferire, nei metadati, i risultati sulla qualità dei dati. In caso
contrario, dovrebbe essere utilizzato l'elemento "Genealogia" previsto
dal RNDT per descrivere in modo generale la qualità dei dati.

**Raccomandazione 27** L'uso di acronimi dovrebbe essere evitato. Se
utilizzati, dovrebbe essere illustrato il loro significato.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:dtataQualityInfo&gt;

&lt;gmd:DQ\_DataQuality&gt;

**…**

&lt;gmd:lineage&gt;

&lt;gmd:LI\_Lineage&gt;

&lt;gmd:statement&gt;

&lt;gco:CharacterString&gt;La produzione di ortofoto digitali alla scala
1:10.000, si compone delle seguenti fasi operative: scansione dei
fotogrammi; rete di inquadramento e di appoggio; triangolazione aerea;
allestimento del DTM; ortorettifica. Le ortofoto vengono riprodotte
almeno ogni tre anni.&lt;/gco:CharacterString&gt;

&lt;/gmd:statement&gt;

&lt;/gmd:LI\_Lineage&gt;

&lt;/gmd:lineage&gt;

&lt;/gmd:DQ\_DataQuality&gt;

&lt;/gmd:dataQualityInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Conformità: specifiche

**Requisito 55** In ottemperanza alla Direttiva INSPIRE 2007/2/CE, i
metadati devono includere informazioni sul grado di conformità alle
disposizioni di esecuzione (implementing rules)[^7].

**NOTA 1** - Tutte le linee guida tecniche di specifica dei dati (Data
Specifications Technical Guidelines) includono, all'allegato A, un
"Abstract Test Suite" (ATS) che descrivono come, attraverso un certo
numero di test, può essere valutata la conformità con le disposizioni di
esecuzione (implementing rules) sull'interoperabilità di dati e servizi.

**NOTA 2** - L'ATS consiste in diverse classi di conformità che possono
essere testate separatamente. Ciò consente di riportare nel dettaglio la
conformità ai differenti aspetti delle disposizioni di esecuzione
(implementing rules). A tale proposito, si può fare riferimento alla
sezione 8 delle linee guida tecniche[^8].

**Requisito 56** La conformità dei dati valutata rispetto ad una certa
specifica tecnica deve essere riportata attraverso un'istanza
dell'elemento *DQ\_DomainConsistency* fornito da ISO 19115.

**NOTA 1** - Il requisito di cui sopra si applica a qualsiasi specifica
tecnica (non solo INSPIRE) rispetto alla quale i dati sono testati.
Cioè, se un dataset è prodotto o armonizzato secondo una data specifica
che include procedure di valutazione della qualità, allora la conformità
a detta specifica dovrebbe essere documentata utilizzando i metadati
"Conformità" previsti dal RNDT.

**NOTA 2** - Considerato che, a differenza di INSPIRE, nell'attuale
versione del RNDT la molteplicità dell'elemento è pari a 1, se sono
documentate più specifiche, il file viene comunque validato e caricato
correttamente sebbene nell'area di consultazione venga visualizzato solo
l'elemento richiesto relativo al Regolamento (UE).

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Nome elemento**                   **Conformità: specifiche**
  ----------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-37 (I-37.1, I-37.2, I-37.3)

  **Molteplicità**                    \[1\]

  **Elemento INSPIRE**                Conformità - specifica

  **Definizione**                     Citazione delle specifiche INSPIRE (adottate a norma dell’art. 7 par. 1 della direttiva 2007/2/CE) cui la risorsa si conforma.

  **Istruzioni di implementazione**   -   **Titolo** \[1\] – Testo libero.
                                      
                                      -   **Data** \[1\] – utilizzare il formato previsto dallo Standard ISO 8601: *aaaa-mm-gg* oppure *aaaammgg*.
                                      
                                      -   **Tipo data** \[1\] **–** Il valore da inserire, tratto dalla lista “*CI\_DateTypeCode*” (§ 3.4.3.1 - all. 2 DM), è “*pubblicazione*” (*publication*).
                                      
                                      Nel tracciato XML è presente anche un ulteriore elemento (che è obbligatorio per gli schemi XSD ma che non è richiesto nè da INSPIRE nè dal RNDT): “*explanation*”. Valorizzare tale elemento come da esempio XML.
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Requisito 57** Per indicare le specifiche alle quali è riferita la
conformità dei dati, devono essere forniti gli elementi: **titolo**,
**data** e **tipo data**.

**Requisito 58** Deve essere indicata almeno la citazione del
Regolamento (UE) n. 1089/2010, in riferimento al quale le informazioni
da inserire sono le seguenti:

**Titolo**: *REGOLAMENTO (UE) N. 1089/2010 DELLA COMMISSIONE del 23
novembre 2010 recante attuazione della direttiva 2007/2/CE del
Parlamento europeo e del Consiglio per quanto riguarda
l'interoperabilità dei set di dati territoriali e dei servizi di dati
territoriali*

**Data**: *2010-12-08*

**Tipo data**: *pubblicazione*.

**Raccomandazione 28** Nel caso si intendano citare anche le linee guida
tecniche INSPIRE di riferimento rispetto alle quali è stata verificata
la conformità, esse potranno essere indicate o attraverso l'URI o
attraverso le seguenti informazioni:

**Titolo**: "*INSPIRE Data Specification on &lt;Theme Name&gt; –
Technical Guidelines*", dove “*Theme Name*” è il nome della categoria
tematica (es. *Addresses*) come riportata negli allegati della
Direttiva;

**Data**: *aaaa-mm-gg* (disponibile sul sito di INSPIRE - v. nota 8);

**Tipo data**: "*pubblicazione*".

**NOTA -** Considerato che attualmente le Specifiche sono disponibili
solo in lingua inglese, il titolo è riportato in quella lingua.

**Raccomandazione 29** Nel caso in cui un dataset non sia ancora
conforme a tutti i requisiti previste nella relativa specifica INSPIRE,
si raccomanda di riportare le informazioni sulla conformità con le
singole classi indicate nell'Abstract Test Suite all'allegato A delle
specifiche medesime (Data Specifications).

**Raccomandazione 30** Nel caso si intendano citare le singole classi di
conformità indicate nell'Abstract Test Suite (ATS) all'allegato A delle
linee guida tecniche INSPIRE di riferimento, esse potranno essere
indicate o attraverso l'URI o attraverso le seguenti informazioni:

**Titolo**: "*INSPIRE Data Specification on &lt;Theme Name&gt; –
Technical Guidelines - &lt;name of the conformance class&gt;*", dove
“*Theme Name*” è il nome della categoria tematica (es. *Addresses*) come
riportata negli allegati della Direttiva e "*name of the conformance
class*" è il nome della classe dell'ATS rispetto alla quale è verificata
la conformità;

**Data**: *aaaa-mm-gg* (disponibile sul sito di INSPIRE - v. nota 8);

**Tipo data**: "*pubblicazione*".

**Esempio di XML:**

**esempio 1**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:dtataQualityInfo&gt;

&lt;gmd:DQ\_DataQuality&gt;

**…**

&lt;gmd:report&gt;

&lt;gmd:DQ\_DomainConsistency&gt;

&lt;gmd:result&gt;

&lt;gmd:DQ\_ConformanceResult&gt;

&lt;gmd:specification&gt;

&lt;gmd:CI\_Citation&gt;

&lt;gmd:title&gt;

&lt;gco:CharacterString&gt;REGOLAMENTO (UE) N. 1089/2010 DELLA
COMMISSIONE del 23 novembre 2010 recante attuazione della direttiva
2007/2/CE del Parlamento europeo e del Consiglio per quanto riguarda
l'interoperabilità dei set di dati territoriali e dei servizi di dati
territoriali&lt;/gco:CharacterString&gt;

&lt;/gmd:title&gt;

&lt;gmd:date&gt;

&lt;gmd:CI\_Date&gt;

&lt;gmd:date&gt;

&lt;gco:Date&gt;2010-12-08&lt;/gco:Date&gt;

&lt;/gmd:date&gt;

&lt;gmd:dateType&gt;

&lt;gmd:CI\_DateTypeCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_DateTypeCode"
codeListValue="publication"&gt;pubblicazione&lt;/gmd:CI\_DateTypeCode&gt;

&lt;/gmd:dateType&gt;

&lt;/gmd:CI\_Date&gt;

&lt;/gmd:date&gt;

&lt;/gmd:CI\_Citation&gt;

&lt;/gmd:specification&gt;

&lt;gmd:explanation&gt;

&lt;gco:CharacterString&gt;Fare riferimento alle specifiche
indicate&lt;/gco:CharacterString&gt;

&lt;/gmd:explanation&gt;

**…**

&lt;/gmd:DQ\_ConformanceResult&gt;

&lt;/gmd:result&gt;

&lt;/gmd:DQ\_DomainConsistency&gt;

&lt;/gmd:report&gt;

**…**

&lt;/gmd:DQ\_DataQuality&gt;

&lt;/gmd:dataQualityInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

**esempio 2**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:dtataQualityInfo&gt;

&lt;gmd:DQ\_DataQuality&gt;

**…**

&lt;gmd:report&gt;

&lt;gmd:DQ\_DomainConsistency&gt;

&lt;gmd:result&gt;

&lt;gmd:DQ\_ConformanceResult&gt;

&lt;gmd:specification&gt;

&lt;gmd:CI\_Citation&gt;

&lt;gmd:title&gt;

&lt;gco:CharacterString&gt; INSPIRE Data Specification on Addresses –
Technical Guidelines&lt;/gco:CharacterString&gt;

&lt;/gmd:title&gt;

&lt;gmd:date&gt;

&lt;gmd:CI\_Date&gt;

&lt;gmd:date&gt;

&lt;gco:Date&gt;2014-04-17&lt;/gco:Date&gt;

&lt;/gmd:date&gt;

&lt;gmd:dateType&gt;

&lt;gmd:CI\_DateTypeCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_DateTypeCode"
codeListValue="publication"&gt;pubblicazione&lt;/gmd:CI\_DateTypeCode&gt;

&lt;/gmd:dateType&gt;

&lt;/gmd:CI\_Date&gt;

&lt;/gmd:date&gt;

&lt;/gmd:CI\_Citation&gt;

&lt;/gmd:specification&gt;

&lt;gmd:explanation&gt;

&lt;gco:CharacterString&gt;Fare riferimento alle specifiche
indicate&lt;/gco:CharacterString&gt;

&lt;/gmd:explanation&gt;

**…**

&lt;/gmd:DQ\_ConformanceResult&gt;

&lt;/gmd:result&gt;

&lt;/gmd:DQ\_DomainConsistency&gt;

&lt;/gmd:report&gt;

**…**

&lt;/gmd:DQ\_DataQuality&gt;

&lt;/gmd:dataQualityInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

**esempio 3**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:dtataQualityInfo&gt;

&lt;gmd:DQ\_DataQuality&gt;

**…**

&lt;gmd:report&gt;

&lt;gmd:DQ\_DomainConsistency&gt;

&lt;gmd:result&gt;

&lt;gmd:DQ\_ConformanceResult&gt;

&lt;gmd:specification xlink:href="
http://inspire.ec.europa.eu/conformanceClass/ad/3.0.1/tg"/&gt;

&lt;gmd:explanation&gt;

&lt;gco:CharacterString&gt;Fare riferimento alle specifiche
indicate&lt;/gco:CharacterString&gt;

&lt;/gmd:explanation&gt;

**…**

&lt;/gmd:DQ\_ConformanceResult&gt;

&lt;/gmd:result&gt;

&lt;/gmd:DQ\_DomainConsistency&gt;

&lt;/gmd:report&gt;

**…**

&lt;/gmd:DQ\_DataQuality&gt;

&lt;/gmd:dataQualityInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

**esempio 4**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:dtataQualityInfo&gt;

&lt;gmd:DQ\_DataQuality&gt;

**…**

&lt;gmd:report&gt;

&lt;gmd:DQ\_DomainConsistency&gt;

&lt;gmd:result&gt;

&lt;gmd:DQ\_ConformanceResult&gt;

&lt;gmd:specification&gt;

&lt;gmd:CI\_Citation&gt;

&lt;gmd:title&gt;

&lt;gco:CharacterString&gt; INSPIRE Data Specification on Addresses –
Technical Guidelines – CRS&lt;/gco:CharacterString&gt;

&lt;/gmd:title&gt;

&lt;gmd:date&gt;

&lt;gmd:CI\_Date&gt;

&lt;gmd:date&gt;

&lt;gco:Date&gt;2014-04-17&lt;/gco:Date&gt;

&lt;/gmd:date&gt;

&lt;gmd:dateType&gt;

&lt;gmd:CI\_DateTypeCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_DateTypeCode"
codeListValue="publication"&gt;pubblicazione&lt;/gmd:CI\_DateTypeCode&gt;

&lt;/gmd:dateType&gt;

&lt;/gmd:CI\_Date&gt;

&lt;/gmd:date&gt;

&lt;/gmd:CI\_Citation&gt;

&lt;/gmd:specification&gt;

&lt;gmd:explanation&gt;

&lt;gco:CharacterString&gt;Fare riferimento alle specifiche
indicate&lt;/gco:CharacterString&gt;

&lt;/gmd:explanation&gt;

**…**

&lt;/gmd:DQ\_ConformanceResult&gt;

&lt;/gmd:result&gt;

&lt;/gmd:DQ\_DomainConsistency&gt;

&lt;/gmd:report&gt;

**…**

&lt;/gmd:DQ\_DataQuality&gt;

&lt;/gmd:dataQualityInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Conformità: grado

  **Nome elemento**                   **Conformità: grado**
  ----------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-38
  **Molteplicità**                    \[1\]
  **Elemento INSPIRE**                Conformità - grado
  **Definizione**                     Indicazione del grado di conformità alle specifiche INSPIRE (adottate a norma dell’art. 7 par. 1 della direttiva 2007/2/CE).
  **Istruzioni di implementazione**   Tipo booleano. Indicare "true" se i dati sono conformi alle specifiche indicate, "false" altrimenti. Se la conformità non è stata ancora valutata, si rimanda alla raccomandazione 32.

In base al Regolamento 1205/2008/CE, il grado di conformità può assumere
uno dei seguenti tre valori: *conforme*, *non conforme* o *non
valutata*. L'ultimo valore è stato introdotto come una misura di
transizione in quanto al tempo dell'adozione del suddetto Regolamento
non erano ancora disponibili le specifiche INSPIRE rispetto alle quali
valutare la conformità.

**Raccomandazione 31** Siccome le disposizioni di esecuzione
(implementing rules) sull'interoperabilità di dati e servizi sono state
emanate, **si raccomanda** di valutare e dichiarare la conformità dei
servizi documentati ("*conforme*" o "*non conforme*").

**NOTA** - In riferimento alla raccomandazione precedente, è ancora
possibile dichiarare nei metadati che la conformità con le disposizioni
di esecuzione (implementing rules) è "*non valutata*". Ciò, come
indicato da INSPIRE, risulta difficile implementarlo utilizzando ISO
19115 che prevede (essendo l'elemento di tipo booleano) due soli valori:
*conforme* (*true*) o *non conforme* (*false*). ISO 19139, però, prevede
un meccanismo per fornire un valore nullo utilizzando l'attributo
*nilReason*.

**Raccomandazione 32** Per dichiarare che la conformità con le
disposizioni di esecuzione (implementing rules) non è stata ancora
valutata, dovrebbe essere fornito un valore nullo del tag con
l'attributo *nilReason* impostato a "*unknown*".

**Esempi di XML**

**esempio 1**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:dataQualityInfo&gt;

&lt;gmd:DQ\_DataQuality&gt;

**…**

&lt;gmd:report&gt;

&lt;gmd:DQ\_DomainConsistency&gt;

&lt;gmd:result&gt;

&lt;gmd:DQ\_ConformanceResult&gt;

**…**

&lt;gmd:pass&gt;

&lt;!-- Se i dati non sono conformi il valore deve essere "false" --&gt;

&lt;gco:Boolean&gt;true&lt;/gco:Boolean&gt;

&lt;/gmd:pass&gt;

**…**

&lt;/gmd:DQ\_ConformanceResult&gt;

&lt;/gmd:result&gt;

&lt;/gmd:DQ\_DomainConsistency&gt;

&lt;/gmd:report&gt;

**…**

&lt;/gmd:DQ\_DataQuality&gt;

&lt;/gmd:dataQualityInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

**esempio 2**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:dataQualityInfo&gt;

&lt;gmd:DQ\_DataQuality&gt;

**…**

&lt;gmd:report&gt;

&lt;gmd:DQ\_DomainConsistency&gt;

&lt;gmd:result&gt;

&lt;gmd:DQ\_ConformanceResult&gt;

**…**

&lt;gmd:pass gco:nilReason="unknown"/&gt;

**…**

&lt;/gmd:DQ\_ConformanceResult&gt;

&lt;/gmd:result&gt;

&lt;/gmd:DQ\_DomainConsistency&gt;

&lt;/gmd:report&gt;

**…**

&lt;/gmd:DQ\_DataQuality&gt;

&lt;/gmd:dataQualityInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

### Sistema di riferimento

#### Sistema di riferimento spaziale

  **Nome elemento**                   **Sistema di riferimento spaziale**
  ----------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-39
  **Molteplicità**                    \[1\]
  **Elemento INSPIRE**                Nessun elemento corrispondente
  **Definizione**                     Sistema di riferimento dei dati.
  **Istruzioni di implementazione**   Testo libero. Fare riferimento alla lista di valori *MD\_ReferenceSystemCode*’ (§ 3.4.3.11 - all. 2 DM) o al codice EPSG di cui alla tabella delle corrispondenze (§ 3.4.8.3 - all. 2 DM).

**Requisito 59** Per la documentazione dell' elemento, deve essere
valorizzato il tag ‘*gmd:code*’ con il nome del sistema di riferimento
presente nella colonna ‘*Nome*’ della lista ‘*MD\_ReferenceSystemCode*’
di cui al § 3.4.3.11 dell’allegato 2 al DM. Alternativamente, il tag
“*gmd:code*” può essere valorizzato con il relativo codice EPSG (v., a
questo proposito, la tabella delle corrispondenze al § 3.4.8.3
dell’allegato 2 al DM) introducendo, in questo caso, anche il tag
“*gmd:codeSpace*” attraverso il quale indicare l’URL del registro EPSG
“[*http://www.epsg-registry.org*](http://www.epsg-registry.org)”.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:referenceSystemInfo&gt;

&lt;gmd:MD\_ReferenceSystem&gt;

&lt;gmd:referenceSystemIdentifier&gt;

&lt;gmd:RS\_Identifier&gt;

&lt;gmd:code&gt;

&lt;gco:CharacterString&gt;ROMA40/EST&lt;/gco:CharacterString&gt;

&lt;/gmd:code&gt;

&lt;/gmd:RS\_Identifier&gt;

&lt;/gmd:referenceSystemIdentifier&gt;

&lt;/gmd:MD\_ReferenceSystem&gt;

&lt;/gmd:referenceSystemInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

oppure

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:referenceSystemInfo&gt;

&lt;gmd:MD\_ReferenceSystem&gt;

&lt;gmd:referenceSystemIdentifier&gt;

&lt;gmd:RS\_Identifier&gt;

&lt;gmd:code&gt;

&lt;gco:CharacterString&gt;3004&lt;/gco:CharacterString&gt;

&lt;/gmd:code&gt;

&lt;gmd:codeSpace&gt;

&lt;gco:CharacterString&gt;http://www.epsg-registry.org/&lt;/gco:CharacterString&gt;

&lt;/gmd:codeSpace&gt;

&lt;/gmd:RS\_Identifier&gt;

&lt;/gmd:referenceSystemIdentifier&gt;

&lt;/gmd:MD\_ReferenceSystem&gt;

&lt;/gmd:referenceSystemInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

### Distribuzione dei dati

#### Formato di distribuzione

  ----------------------------------------------------------------------------------------------
  **Nome elemento**                   **Formato di distribuzione**
  ----------------------------------- ----------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-40 (I-40.1, I-40.2)

  **Molteplicità**                    \[1..\*\]

  **Elemento INSPIRE**                Nessun elemento corrispondente

  **Definizione**                     Descrizione del formato con cui i dati sono distribuiti.

  **Istruzioni di implementazione**   -   **Nome formato** \[1\] - Testo libero
                                      
                                      -   **Versione formato** \[1\] - Testo libero
                                      
  ----------------------------------------------------------------------------------------------

**Requisito 60** Devono essere forniti gli elementi: **nome formato**,
**versione formato**.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:distributionInfo&gt;

&lt;gmd:MD\_Distribution&gt;

&lt;gmd:distributionFormat&gt;

&lt;gmd:MD\_Format&gt;

&lt;gmd:name&gt;

&lt;gco:CharacterString&gt;shp&lt;/gco:CharacterString&gt;

&lt;/gmd:name&gt;

&lt;gmd:version&gt;

&lt;gco:CharacterString&gt;9.3&lt;/gco:CharacterString&gt;

&lt;/gmd:version&gt;

&lt;/gmd:MD\_Format&gt;

&lt;/gmd:distributionFormat&gt;

**…**

&lt;/gmd:MD\_Distribution&gt;

&lt;/gmd:distributionInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Distributore

  ----------------------------------------------------------------------------------------------------------------------------------------------
  **Nome elemento**                   **Distributore**
  ----------------------------------- ----------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-41 (I-41.1, I-41.2, I-41.3, I-41.4)

  **Molteplicità**                    \[1..\*\]

  **Elemento INSPIRE**                Nessun elemento corrispondente

  **Definizione**                     Informazioni sull’organizzazione che distribuisce i dati.

  **Istruzioni di implementazione**   -   **Nome dell’Ente** \[1\] – Testo libero.
                                      
                                      -   **Ruolo** \[1\] – Fare riferimento alla lista “*CI\_RoleCode*” (§ 3.4.3.3 - all. 2 DM).
                                      
                                      -   **Sito web** \[0..1\] - formato URL. Specificare obbligatoriamente anche il protocollo (es. *http*).
                                      
                                      -   **Telefono** \[0..1\] - Testo libero.
                                      
                                      -   **E-mail** \[1..\*\] - Testo libero.
                                      
  ----------------------------------------------------------------------------------------------------------------------------------------------

**Requisito 61** Devono essere forniti i seguenti elementi: **nome
dell'Ente**, **ruolo**, **indirizzo e-mail**, **sito web** e/o
**riferimento telefonico**.

**Requisito 62** Come indicato all'allegato 2 del DM, deve essere
documentato almeno uno dei due metadati tra "Sito web" e "Telefono".

**Raccomandazione 33** Il nome dell'Ente dovrebbe essere riportato per
intero, senza abbreviazioni. Indicare il nome completo dell’ufficio
responsabile presso cui chiedere informazioni per ottenere i dati. Si
consiglia di indicare indirizzi e-mail istituzionali e non personali.

**Raccomandazione 34** Scegliere il ruolo che meglio rappresenta la
funzione espletata dall'Ente.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:distributionInfo&gt;

&lt;gmd:MD\_Distribution&gt;

**…**

&lt;gmd:distributor&gt;

&lt;gmd:MD\_Distributor&gt;

&lt;gmd:distributorContact&gt;

&lt;gmd:CI\_ResponsibleParty&gt;

&lt;gmd:organisationName&gt;

&lt;gco:CharacterString&gt;Agenzia per le Erogazioni in
Agricoltura&lt;/gco:CharacterString&gt;

&lt;/gmd:organisationName&gt;

&lt;gmd:contactInfo&gt;

&lt;gmd:CI\_Contact&gt;

&lt;gmd:address&gt;

&lt;gmd:CI\_Address&gt;

&lt;gmd:electronicMailAddress&gt;

&lt;gco:CharacterString&gt;info@agea.gov.it&lt;/gco:CharacterString&gt;

&lt;/gmd:electronicMailAddress&gt;

&lt;/gmd:CI\_Address&gt;

&lt;/gmd:address&gt;

&lt;gmd:onlineResource&gt;

&lt;gmd:CI\_OnlineResource&gt;

&lt;gmd:linkage&gt;

&lt;gmd:URL&gt;http://www.agea.gov.it&lt;/gmd:URL&gt;

&lt;/gmd:linkage&gt;

&lt;/gmd:CI\_OnlineResource&gt;

&lt;/gmd:onlineResource&gt;

&lt;/gmd:CI\_Contact&gt;

&lt;/gmd:contactInfo&gt;

&lt;gmd:role&gt;

&lt;gmd:CI\_RoleCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_RoleCode"
codeListValue="distributor"&gt;distributore&lt;/gmd:CI\_RoleCode&gt;

&lt;/gmd:role&gt;

&lt;/gmd:CI\_ResponsibleParty&gt;

&lt;/gmd:distributorContact&gt;

&lt;/gmd:MD\_Distributor&gt;

&lt;/gmd:distributor&gt;

**…**

&lt;/gmd:MD\_Distribution&gt;

&lt;/gmd:distributionInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

#### Risorsa on-line

  **Nome elemento**                   **Risorsa on-line**
  ----------------------------------- -------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-42
  **Molteplicità**                    \[0..\*\]
  **Elemento INSPIRE**                Localizzatore della risorsa
  **Definizione**                     Informazioni sulle fonti online attraverso le quali la risorsa può essere ottenuta.
  **Istruzioni di implementazione**   Formato URL. Specificare obbligatoriamente il protocollo (es. *http*).

**Requisito 63** Se è disponibile un collegamento al servizio,
l'elemento deve essere utilizzato per indicare un **URL valido** che
fornisca:

• un link ad un documento di “capabilities” di un servizio;

• un link ad un documento WSDL di un servizio (SOAP binding);

• un link ad una pagina web dove reperire ulteriori informazioni;

• un link ad un’applicazione client con cui si accede direttamente ad un
servizio.

**Raccomandazione 35** Se non è disponibile nessun collegamento diretto
alla risorsa, fornire il link a un punto di contatto dove è possibile
reperire maggiori informazioni.

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:distributionInfo&gt;

&lt;gmd:MD\_Distribution&gt;

**…**

&lt;gmd:transferOptions&gt;

&lt;gmd:MD\_DigitalTransferOptions&gt;

&lt;gmd:onLine&gt;

&lt;gmd:CI\_OnlineResource&gt;

&lt;gmd:linkage&gt;

&lt;gmd:URL&gt;http://www.sian.it&lt;/gmd:URL&gt;

&lt;/gmd:linkage&gt;

&lt;/gmd:CI\_OnlineResource&gt;

&lt;/gmd:onLine&gt;

&lt;/gmd:MD\_DigitalTransferOptions&gt;

&lt;/gmd:transferOptions&gt;

&lt;/gmd:MD\_Distribution&gt;

&lt;/gmd:distributionInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

### Gestione dei dati

#### Frequenza di aggiornamento

  **Nome elemento**                   **Frequenza di aggiornamento**
  ----------------------------------- ---------------------------------------------------------------------------------------------------------------
  **Riferimento**                     All.2 DM – tab. I-43
  **Molteplicità**                    \[0..\*\]
  **Elemento INSPIRE**                Nessun elemento corrispondente
  **Definizione**                     Frequenza con la quale sono registrati gli aggiornamenti dei dati.
  **Istruzioni di implementazione**   L'elemento deve assumere uno dei valori della lista “*MD\_MaintenanceFrequencyCode*” (§ 3.4.3.9 - all. 2 DM).

**Esempio di XML:**

&lt;gmd:MD\_Metadata&gt;

**…**

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

**…**

&lt;gmd:resourceMaintenance&gt;

&lt;gmd:MD\_MaintenanceInformation&gt;

&lt;gmd:maintenanceAndUpdateFrequency&gt;

&lt;gmd:MD\_MaintenanceFrequencyCode codeListValue="asNeeded"
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_MaintenanceFrequencyCode"&gt;quando
necessario&lt;/gmd:MD\_MaintenanceFrequencyCode&gt;

&lt;/gmd:maintenanceAndUpdateFrequency&gt;

&lt;/gmd:MD\_MaintenanceInformation&gt;

&lt;/gmd:resourceMaintenance&gt;

**…**

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

**…**

&lt;/gmd:MD\_Metadata&gt;

Mapping requisiti e raccomandazioni RNDT / INSPIRE
--------------------------------------------------

Nella tabella 2 si riporta la corrispondenza tra i requisiti e le
raccomandazioni definite nel presente documento e quelle definite da
INSPIRE. Per ogni requisito/raccomandazione si riporta il numero e il
paragrafo di riferimento (numero e titolo); ove non diversamente
specificato, relativamente ai requisiti e alle raccomandazioni INSPIRE,
si fa riferimento alle linee guida INSPIRE sui metadati[^9].

  **Requisito / raccomandazione RNDT**
  --------------------------------------------------------------------------- -------------------------------------------------------------------------------------------
  **Requisiti**
  Requisito 1 - § 2.1.1.1 - Identificatore del file
  Requisito 2 - § 2.1.1.1 - Identificatore del file
  Requisito 3 - § 2.1.1.2 - Lingua dei metadati
  Requisito 4 - § 2.1.1.3 - Set dei caratteri dei metadati
  Requisito 5 - § 2.1.1.4 - Id file precedente
  Requisito 6 - § 2.1.1.5 - Livello gerarchico
  Requisito 7 - § 2.1.1.5 - Livello gerarchico
  Requisito 8 - § 2.1.1.6 - Responsabile dei metadati
  Requisito 9 - § 2.1.1.6 - Responsabile dei metadati
  Requisito 10 - § 2.1.1.6 - Responsabile dei metadati
  Requisito 11 - § 2.1.1.7 - Data dei metadati
  Requisito 12 - § 2.1.1.8 - Nome dello Standard
  Requisito 13 - § 2.1.1.9 - Versione dello Standard
  Requisito 14 - § 2.1.2.2 - Data
  Requisito 15 - § 2.1.2.2 - Data
  Requisito 16 - § 2.1.2.2 - Data
  Requisito 17 - § 2.1.2.4 - Responsabile
  Requisito 18 - § 2.1.2.4 - Responsabile
  Requisito 19 - § 2.1.2.5 - Identificatore
  Requisito 20 - § 2.1.2.5 - Identificatore
  Requisito 21 - § 2.1.2.5 - Identificatore
  Requisito 22 - § 2.1.2.6 - ID livello superiore
  Requisito 23 - § 2.1.2.9 - Parole chiave
  Requisito 24 - § 2.1.2.9 - Parole chiave
  Requisito 25 - § 2.1.2.9 - Parole chiave
  Requisito 26 - § 2.1.2.9 - Parole chiave
  Requisito 27 - § 2.1.2.9 - Parole chiave
  Requisito 28 - § 2.1.2.9 - Parole chiave
  Requisito 29 - § 2.1.2.9 - Parole chiave
  Requisito 30 - § 2.1.2.10 - Punto di contatto
  Requisito 31 - § 2.1.2.10 - Punto di contatto
  Requisito 32 - § 2.1.2.11 - Set di caratteri
  Requisito 33 - § 2.1.2.13 - Risoluzione spaziale
  Requisito 34 - § 2.1.2.14 - Lingua
  Requisito 35 - § 2.1.2.15 - Categoria tematica
  Requisito 36 - § 2.1.3.1 - Limitazione d'uso
  Requisito 37 - § 2.1.3.1 - Limitazione d'uso
  Requisito 38 - § 2.1.3.2 - Vincoli di accesso
  Requisito 39 - § 2.1.3.2 - Vincoli di accesso
  Requisito 40 - § 2.1.3.2 - Vincoli di accesso
  Requisito 41 - § 2.1.3.3 - Vincoli di fruibilità
  Requisito 42 - § 2.1.3.3 - Vincoli di fruibilità
  Requisito 43 - § 2.1.3.4 - Altri vincoli
  Requisito 44 - § 2.1.4.1 - Localizzazione geografica
  Requisito 45 - § 2.1.4.1 - Localizzazione geografica
  Requisito 46 - § 2.1.4.2 - Estensione verticale
  Requisito 47 - § 2.1.4.2 - Estensione verticale
  Requisito 48 - § 2.1.4.3 - Estensione temporale
  Requisito 49 - § 2.1.4.3 - Estensione temporale
  Requisito 50 - § 2.1.5 - Qualità dei dati
  Requisito 51 - § 2.1.5.1 - Livello di qualità
  Requisito 52 - § 2.1.5.2 - Accuratezza posizionale
  Requisito 53 - § 2.1.5.2 - Accuratezza posizionale
  Requisito 54 - § 2.1.5.2 - Accuratezza posizionale
  Requisito 55 - § 2.1.5.4 - Conformità: specifiche
  Requisito 56 - § 2.1.5.4 - Conformità: specifiche
  Requisito 57 - § 2.1.5.4 - Conformità: specifiche
  Requisito 58 - § 2.1.5.4 - Conformità: specifiche
  Requisito 59 - § 2.1.6.1 - Sistema di riferimento spaziale
  Requisito 60 - § 2.1.7.1 - Formato di distribuzione
  Requisito 61 - § 2.1.7.2 - Distributore
  Requisito 62 - § 2.1.7.2 - Distributore
  Requisito 63 - § 2.1.7.3 - Risorsa on-line
  **Raccomandazioni**
  Raccomandazione 1 - § 1.4.1 - Gerarchia e relazioni serie/dataset/sezione
  Raccomandazione 2 - § 2.1 - Istruzioni
  Raccomandazione 3 - § 2.1.1.1 - Identificatore del file
  Raccomandazione 4 - § 2.1.1.5 - Livello gerarchico
  Raccomandazione 5 - § 2.1.1.6 - Responsabile dei metadati
  Raccomandazione 6 - § 2.1.2.1 - Titolo
  Raccomandazione 7 - § 2.1.2.1 - Titolo
  Raccomandazione 8 - § 2.1.2.2 - Data
  Raccomandazione 9 - § 2.1.2.4 - Responsabile
  Raccomandazione 10 - § 2.1.2.4 - Responsabile
  Raccomandazione 11 - § 2.1.2.5 - Identificatore
  Raccomandazione 12 - § 2.1.2.7 - Altri dettagli
  Raccomandazione 13 - § 2.1.2.8 - Descrizione
  Raccomandazione 14 - § 2.1.2.8 - Descrizione
  Raccomandazione 15 - § 2.1.2.8 - Descrizione
  Raccomandazione 16 - § 2.1.2.9 - Parole chiave
  Raccomandazione 17 - § 2.1.2.9 - Parole chiave
  Raccomandazione 18 - § 2.1.2.9 - Parole chiave
  Raccomandazione 19 - § 2.1.2.9 - Parole chiave
  Raccomandazione 20 - § 2.1.2.10 - Punto di contatto
  Raccomandazione 21 - § 2.1.2.10 - Punto di contatto
  Raccomandazione 22 - § 2.1.2.14 - Lingua
  Raccomandazione 23 - § 2.1.2.16 - Informazioni supplementari
  Raccomandazione 24 - § 2.1.3.1 - Limitazione d'uso
  Raccomandazione 25 - § 2.1.5.3 - Genealogia
  Raccomandazione 26 - § 2.1.5.3 - Genealogia
  Raccomandazione 27 - § 2.1.5.3 - Genealogia
  Raccomandazione 28 - § 2.1.5.4 - Conformità: specifiche
  Raccomandazione 29 - § 2.1.5.4 - Conformità: specifiche
  Raccomandazione 30 - § 2.1.5.4 - Conformità: specifiche
  Raccomandazione 31 - § 2.1.5.4 - Conformità: grado
  Raccomandazione 32 - § 2.1.5.4 - Conformità: grado
  Raccomandazione 33 - § 2.1.7.2 - Distributore
  Raccomandazione 34 - § 2.1.7.2 - Distributore
  Raccomandazione 35 - § 2.1.7.3 - Risorsa on-line

### Tab. 2 – Mapping requisiti e raccomandazioni RNDT / INSPIRE  {#tab.-2-mapping-requisiti-e-raccomandazioni-rndt-inspire .ListParagraph}

### Altri requisiti e raccomandazioni

Alcuni requisiti e raccomandazioni INSPIRE non trovano corrispondenza in
quelli indicati nel presente documento. Nella tabella 3 vengono indicati
quali sono e come vengono soddisfatti comunque nel RNDT.

  **Requisito / raccomandazione INSPIRE**
  ------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Requisiti**
  TG Requirement 8 - § 2.2.7 - Resource language
  TG Requirement 30 - § 2.9 - Constraints related to access and use
  TG Requirement 31 - § 2.9 - Constraints related to access and use
  TG Requirement 32 - § 2.9.1 - Limitations on public access
  TG Requirement 36 - § 2.10.1 - Responsible party
  **Raccomandazioni**
  TG Recommendation 9 - § 2.2.5 - Unique resource identifier
  TG Recommendation 18 - § 2.7.2 - Spatial resolution

### Tab. 3 – Altri requisiti INSPIRE soddisfatti nel RNDT  {#tab.-3-altri-requisiti-inspire-soddisfatti-nel-rndt .ListParagraph}

Focus - Punti di attenzione
---------------------------

Sulla base dell'esperienza condotta negli oltre due anni di esercizio
del RNDT da diverse amministrazioni nella documentazione e nel
caricamento dei metadati e sulla base anche delle risultanze dei test di
interoperabilità condotti da JRC sul servizio di ricerca, si ritiene
utile richiamare l'attenzione nella compilazione dei metadati medesimi
in riferimento ai seguenti punti:

-   **Grado di conformità**

> **Raccomandazione 36** Con riferimento al Regolamento (UE) n.
> 1089/2010, alle disposizioni INSPIRE di esecuzione (Data
> Specifications) e alle classi di conformità ivi previste, si
> raccomanda di attenersi scrupolosamente alle indicazioni fornite nel §
> 2.1.5.5. Se la conformità dei dati rispetto alle specifiche di cui
> sopra, pertanto, non è stata ancora valutata, seguire quanto indicato
> nella **raccomandazione 32** evitando di indicare valori ("conforme" o
> "non conforme") non corrispondenti alla reale valutazione dei dati
> medesimi. L'importanza di tale indicazione risiede nel fatto che il
> grado di conformità dei dati è una delle informazioni richieste da
> INSPIRE in fase di monitoraggio e, come tale, viene anche
> rappresentata attraverso i canali ufficiali alla Commissione Europea.

-   **Bounding box**

> **Raccomandazione 37** Relativamente alle unità amministrative
> italiane (Comuni, Province e Regioni), il RNDT utilizza i bounding box
> derivati dagli strati informativi resi disponibili da ISTAT. Stante i
> criteri di ricerca geografici implementati nella versione attuale
> dell'applicazione RNDT, al fine, pertanto, di ottimizzare la ricerca
> dei metadati da parte degli utenti, si raccomanda di fare riferimento
> alle coordinate dei bounding box di cui sopra.

-   **Risorsa on line**

> **Raccomandazione 38** Considerate le modalità di validazione del
> validatore INSPIRE, si raccomanda di attenersi scrupolosamente a
> quanto indicato al § 2.1.7.3 in particolar modo relativamente alla
> **validità dell'URL** indicato come riferimento per la risorsa.

metadati per l'interoperabilità
===============================

Metadati necessari per l’interoperabilità
-----------------------------------------

Oltre al set di metadati definito nel Regolamento (CE) n. 1205/2008,
applicabile a tutte le categorie di dati di cui agli allegati I, II e
III della Direttiva INSPIRE, il Regolamento (CE) n. 1089/2010[^13],
relativo all’interoperabilità dei set di dati territoriali e dei servizi
di dati territoriali, ha individuato, all’art. 13, alcuni metadati
supplementari.

In più, nelle Specifiche sui dati[^14], sono stati individuati ulteriori
metadati opzionali, specifici per i vari temi.

Sebbene INSPIRE preveda scadenze diverse per la disponibilità dei
metadati per l'interoperabilità rispetto a quelli per la ricerca di cui
al Regolamento (CE) n. 1205/2008, è da sottolineare che il nucleo di
metadati definito dal profilo RNDT include tutti i metadati obbligatori
e alcuni tra quelli condizionati o opzionali di cui sopra, che, quindi,
sono già resi disponibili nel Catalogo.

Nella tabella 2 è riportata la corrispondenza tra i metadati previsti
dal profilo del RNDT, quelli definiti nel Regolamento (CE) n. 1089/2010
e quelli opzionali definiti nelle varie Specifiche sui dati. Per quanto
riguarda questi ultimi, vengono riportati solo quelli che hanno una
corrispondenza con i metadati del RNDT.

Nella tabella, accanto ad ogni elemento è indicato, tra parentesi, il
livello di obbligatorietà (***O*** per obbligatorio, ***Op*** per
opzionale, ***C*** per condizionato).

  **Metadati INSPIRE**
  ---------------------------------------------------- -----------------------------------------------
  **Metadati art. 13 Regolamento (CE) n. 1089/2010**
  Sistema di riferimento coordinate (O)
  Sistema di riferimento temporale (C)
  Codifica (O)
  Coerenza topologica (C)
  Codifica dei caratteri (C)
  Tipo di rappresentazione territoriale (O)
  **Metadati opzionali Specifiche sui Dati**
  Maintenance information (Op)
  Positional accuracy (Op)
  Spatial representation informazion (Op)
  Supplemental information (Op)
  Content information (Op)

### Tab. 4 – Mapping metadati RNDT – metadati Reg. (CE) 1089/2010 e specifiche INSPIRE sui dati {#tab.-4-mapping-metadati-rndt-metadati-reg.-ce-10892010-e-specifiche-inspire-sui-dati .ListParagraph}

Da evidenziare, inoltre, che i suddetti metadati RNDT soddisfano i
requisiti e le raccomandazioni indicate nelle specifiche sui dati[^15];
infatti:

-   i documenti XML compilati secondo le indicazioni della presente
    > guida, comprensivi dei metadati per l'interoperabilità, sono
    > validati senza errori rispetto agli schemi XML di cui a ISO 19139
    > (cfr. *TG Requirement 3*);

-   i documenti XML compilati secondo le indicazioni della presente
    guida, comprensivi dei metadati per l'interoperabilità, contengono
    gli elementi richiesti e rispettano la molteplicità specificata per
    detti elementi (cfr. *TG Requirement 4*);

-   gli elementi relativi ai metadati per l'interoperabilità sono
    disponibili secondo il *path* specificato nello Standard ISO TS
    19139 (cfr. *TG Requirement 5*);

-   i metadati per l'interoperabilità, una volta che vengono caricati
    dalle pubbliche amministrazioni nel RNDT, sono resi disponibili,
    insieme ai metadati definiti nel Regolamento (CE) n. 1205/2008,
    attraverso il servizio di ricerca del RNDT medesimo (cfr.
    *Recommendation 29*).

ALLEGATO A – Temi INSPIRE {#allegato-a-temi-inspire .ListParagraph}
=========================

Di seguito è riportato, in ordine alfabetico, l'elenco dei temi INSPIRE,
di cui agli allegati I, II e III della Direttiva, da utilizzare come
parole chiave (cfr. § 2.1.2.9); tale elenco è tratto dal thesaurus
GEMET[^16]. In corsivo il corrispondente tema in inglese[^17] e in
parentesi l'allegato di riferimento.

-   Condizioni atmosferiche - *Atmospheric conditions* (III)

-   Copertura del suolo - *Land cover* (II)

-   Distribuzione della popolazione - demografia - *Population
    distribution — demography* (III)

-   Distribuzione delle specie - *Species distribution* (III)

-   Edifici - *Buildings* (III)

-   Elementi geografici meteorologici - *Meteorological geographical
    features* (III)

-   Elementi geografici oceanografici - *Oceanographic geographical
    features* (III)

-   Elevazione - *Elevation* (II)

-   Geologia - *Geology* (II)

-   Habitat e biotopi - *Habitats and biotopes* (III)

-   Idrografia - *Hydrography* (I)

-   Impianti agricoli e di acquacoltura - *Agricultural and aquaculture
    facilities* (III)

-   Impianti di monitoraggio ambientale - *Environmental monitoring
    facilities* (III)

-   Indirizzi - *Addresses* (I)

-   Nomi geografici *Geographical names* (I)

-   Orto immagini - *Orthoimagery* (II)

-   Parcelle catastali[^18] - *Cadastral parcels* (I)

-   Produzione e impianti industriali - *Production and industrial
    facilities* (III)

-   Regioni biogeografiche - *Bio-geographical regions* (III)

-   Regioni marine - *Sea regions* (III)

-   Reti di trasporto - *Transport networks* (I)

-   Risorse energetiche - *Energy resources* (III)

-   Risorse minerarie - *Mineral resources* (III)

-   Salute umana e sicurezza - *Human health and safety* (III)

-   Servizi di pubblica utilità  e servizi amministrativi - *Utility and
    governmental services* (III)

-   Sistemi di coordinate - *Coordinate reference systems* (I)

-   Sistemi di griglie geografiche - *Geographical grid systems* (I)

-   Siti protetti - *Protected sites* (I)

-   Suolo - *Soil* (III)

-   Unità  amministrative - *Administrative units* (I)

-   Unità  statistiche - *Statistical units* (III)

-   Utilizzo del territorio - *Land use* (III)

-   Zone a rischio naturale - *Natural risk zones* (III)

-   Zone sottoposte a gestione/limitazioni/regolamentazione e unità  con
    obbligo di comunicare dati - *Area management/restriction/regulation
    zones and reporting units* (III)

ALLEGATO B – Esempi di file XML {#allegato-b-esempi-di-file-xml .ListParagraph}
===============================

B.1 Esempio di file XML per il dataset {#b.1-esempio-di-file-xml-per-il-dataset .ListParagraph}
--------------------------------------

L’esempio riportato riguarda un dataset “flat” non appartenente a
nessuna serie. Ciò si evince dal fatto che i due metadati
“*Identificatore*” (relativo al livello corrente, quindi dataset,
corrispondente al tag XML *identifier*) e “*Id livello superiore*”
(corrispondente al tag XML *series*) assumono lo stesso valore.

L’esempio, però, è valido anche se si vuole documentare nel RNDT un
dataset appartenente ad una serie precedentemente inserita. In questo
caso, è necessario documentare opportunamente il metadato “*Id livello
superiore*” valorizzandolo con l’id della serie a cui il dataset
appartiene.

&lt;?xml version="1.0" encoding="UTF-8"?&gt;

&lt;gmd:MD\_Metadata xsi:schemaLocation="
http://www.isotc211.org/2005/gmd
http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/gmd/gmd.xsd"
xmlns:gsr="http://www.isotc211.org/2005/gsr "
xmlns:xlink="http://www.w3.org/1999/xlink"
xmlns:gts="http://www.isotc211.org/2005/gts"
xmlns:gmd="http://www.isotc211.org/2005/gmd"
xmlns:gco="http://www.isotc211.org/2005/gco"
xmlns:gml="http://www.opengis.net/gml/3.2"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xmlns:gss="http://www.isotc211.org/2005/gss"&gt;

&lt;gmd:fileIdentifier&gt;

&lt;gco:CharacterString&gt;r\_molise:000002:20111219:172006&lt;/gco:CharacterString&gt;

&lt;/gmd:fileIdentifier&gt;

&lt;gmd:language&gt;

&lt;gmd:LanguageCode codeList="http://www.loc.gov/standards/iso639-2"
codeListValue="ita"&gt;ita&lt;/gmd:LanguageCode&gt;

&lt;/gmd:language&gt;

&lt;gmd:characterSet&gt;

&lt;gmd:MD\_CharacterSetCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_CharacterSetCode"
codeListValue="utf8"&gt;utf8&lt;/gmd:MD\_CharacterSetCode&gt;

&lt;/gmd:characterSet&gt;

&lt;gmd:parentIdentifier&gt;

&lt;gco:CharacterString&gt;r\_molise:000002:20111219:172006&lt;/gco:CharacterString&gt;

&lt;/gmd:parentIdentifier&gt;

&lt;gmd:hierarchyLevel&gt;

&lt;gmd:MD\_ScopeCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_ScopeCode"
codeListValue="dataset"&gt;dataset&lt;/gmd:MD\_ScopeCode&gt;

&lt;/gmd:hierarchyLevel&gt;

&lt;gmd:contact&gt;

&lt;gmd:CI\_ResponsibleParty&gt;

&lt;gmd:organisationName&gt;

&lt;gco:CharacterString&gt;E-Geos&lt;/gco:CharacterString&gt;

&lt;/gmd:organisationName&gt;

&lt;gmd:contactInfo&gt;

&lt;gmd:CI\_Contact&gt;

&lt;gmd:address&gt;

&lt;gmd:CI\_Address&gt;

&lt;gmd:electronicMailAddress&gt;

&lt;gco:CharacterString&gt;info@e-geos.it&lt;/gco:CharacterString&gt;

&lt;/gmd:electronicMailAddress&gt;

&lt;/gmd:CI\_Address&gt;

&lt;/gmd:address&gt;

&lt;gmd:onlineResource&gt;

&lt;gmd:CI\_OnlineResource&gt;

&lt;gmd:linkage&gt;

&lt;gmd:URL&gt;http://www.e-geos.it/&lt;/gmd:URL&gt;

&lt;/gmd:linkage&gt;

&lt;/gmd:CI\_OnlineResource&gt;

&lt;/gmd:onlineResource&gt;

&lt;/gmd:CI\_Contact&gt;

&lt;/gmd:contactInfo&gt;

&lt;gmd:role&gt;

&lt;gmd:CI\_RoleCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_RoleCode"
codeListValue="pointOfContact"&gt;punto di
contatto&lt;/gmd:CI\_RoleCode&gt;

&lt;/gmd:role&gt;

&lt;/gmd:CI\_ResponsibleParty&gt;

&lt;/gmd:contact&gt;

&lt;gmd:dateStamp&gt;

&lt;gco:Date&gt;2011-12-19&lt;/gco:Date&gt;

&lt;/gmd:dateStamp&gt;

&lt;gmd:metadataStandardName&gt;

&lt;gco:CharacterString&gt;DM – Regole tecniche
RNDT&lt;/gco:CharacterString&gt;

&lt;/gmd:metadataStandardName&gt;

&lt;gmd:metadataStandardVersion&gt;

&lt;gco:CharacterString&gt;10 novembre 2011&lt;/gco:CharacterString&gt;

&lt;/gmd:metadataStandardVersion&gt;

&lt;gmd:referenceSystemInfo&gt;

&lt;gmd:MD\_ReferenceSystem&gt;

&lt;gmd:referenceSystemIdentifier&gt;

&lt;gmd:RS\_Identifier&gt;

&lt;gmd:code&gt;

&lt;gco:CharacterString&gt;WGS84&lt;/gco:CharacterString&gt;

&lt;/gmd:code&gt;

&lt;/gmd:RS\_Identifier&gt;

&lt;/gmd:referenceSystemIdentifier&gt;

&lt;/gmd:MD\_ReferenceSystem&gt;

&lt;/gmd:referenceSystemInfo&gt;

&lt;gmd:identificationInfo&gt;

&lt;gmd:MD\_DataIdentification&gt;

&lt;gmd:citation&gt;

&lt;gmd:CI\_Citation&gt;

&lt;gmd:title&gt;

&lt;gco:CharacterString&gt;MOLISEDB.GIS.incendi&lt;/gco:CharacterString&gt;

&lt;/gmd:title&gt;

&lt;gmd:date&gt;

&lt;gmd:CI\_Date&gt;

&lt;gmd:date&gt;

&lt;gco:Date&gt;20080415&lt;/gco:Date&gt;

&lt;/gmd:date&gt;

&lt;gmd:dateType&gt;

&lt;gmd:CI\_DateTypeCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_DateTypeCode"
codeListValue="creation"&gt;creation&lt;/gmd:CI\_DateTypeCode&gt;

&lt;/gmd:dateType&gt;

&lt;/gmd:CI\_Date&gt;

&lt;/gmd:date&gt;

&lt;gmd:identifier&gt;

&lt;gmd:RS\_Identifier&gt;

&lt;gmd:code&gt;

&lt;gco:CharacterString&gt;r\_molise:0000000002&lt;/gco:CharacterString&gt;

&lt;/gmd:code&gt;

&lt;/gmd:RS\_Identifier&gt;

&lt;/gmd:identifier&gt;

&lt;gmd:citedResponsibleParty&gt;

&lt;gmd:CI\_ResponsibleParty&gt;

&lt;gmd:organisationName&gt;

&lt;gco:CharacterString&gt;E-Geos&lt;/gco:CharacterString&gt;

&lt;/gmd:organisationName&gt;

&lt;gmd:contactInfo&gt;

&lt;gmd:CI\_Contact&gt;

&lt;gmd:address&gt;

&lt;gmd:CI\_Address&gt;

&lt;gmd:electronicMailAddress&gt;

&lt;gco:CharacterString&gt;info@e-geos.it&lt;/gco:CharacterString&gt;

&lt;/gmd:electronicMailAddress&gt;

&lt;/gmd:CI\_Address&gt;

&lt;/gmd:address&gt;

&lt;gmd:onlineResource&gt;

&lt;gmd:CI\_OnlineResource&gt;

&lt;gmd:linkage&gt;

&lt;gmd:URL&gt;http://www.e-geos.it/&lt;/gmd:URL&gt;

&lt;/gmd:linkage&gt;

&lt;/gmd:CI\_OnlineResource&gt;

&lt;/gmd:onlineResource&gt;

&lt;/gmd:CI\_Contact&gt;

&lt;/gmd:contactInfo&gt;

&lt;gmd:role&gt;

&lt;gmd:CI\_RoleCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_RoleCode"
codeListValue="author"&gt;autore&lt;/gmd:CI\_RoleCode&gt;

&lt;/gmd:role&gt;

&lt;/gmd:CI\_ResponsibleParty&gt;

&lt;/gmd:citedResponsibleParty&gt;

&lt;gmd:citedResponsibleParty&gt;

&lt;gmd:CI\_ResponsibleParty&gt;

&lt;gmd:organisationName&gt;

&lt;gco:CharacterString&gt;Molise Dati S.p.a&lt;/gco:CharacterString&gt;

&lt;/gmd:organisationName&gt;

&lt;gmd:contactInfo&gt;

&lt;gmd:CI\_Contact&gt;

&lt;gmd:phone&gt;

&lt;gmd:CI\_Telephone&gt;

&lt;gmd:voice&gt;
&lt;gco:CharacterString&gt;08746191&lt;/gco:CharacterString&gt;

&lt;/gmd:voice&gt;

&lt;/gmd:CI\_Telephone&gt;

&lt;/gmd:phone&gt;

&lt;gmd:address&gt;

&lt;gmd:CI\_Address&gt;

&lt;gmd:electronicMailAddress&gt;
&lt;gco:CharacterString&gt;info@molisedati.it&lt;/gco:CharacterString&gt;

&lt;/gmd:electronicMailAddress&gt;

&lt;/gmd:CI\_Address&gt;

&lt;/gmd:address&gt;

&lt;gmd:onlineResource&gt;

&lt;gmd:CI\_OnlineResource&gt;

&lt;gmd:linkage&gt;

&lt;gmd:URL&gt;http://www.molisedati.it/&lt;/gmd:URL&gt;

&lt;/gmd:linkage&gt;

&lt;/gmd:CI\_OnlineResource&gt;

&lt;/gmd:onlineResource&gt;

&lt;/gmd:CI\_Contact&gt;

&lt;/gmd:contactInfo&gt;

&lt;gmd:role&gt;

&lt;gmd:CI\_RoleCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_RoleCode"
codeListValue=" owner"&gt;proprietario&lt;/gmd:CI\_RoleCode&gt;

&lt;/gmd:role&gt;

&lt;/gmd:CI\_ResponsibleParty&gt;

&lt;/gmd:citedResponsibleParty&gt;

&lt;gmd:presentationForm&gt;

&lt;gmd:CI\_PresentationFormCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_PresentationFormCode"
codeListValue="mapDigital"&gt;mapDigital&lt;/gmd:CI\_PresentationFormCode&gt;

&lt;/gmd:presentationForm&gt;

&lt;gmd:series&gt;

&lt;gmd:CI\_Series&gt;

&lt;gmd:issueIdentification&gt;

&lt;gco:CharacterString&gt;r\_molise:0000000002&lt;/gco:CharacterString&gt;

&lt;/gmd:issueIdentification&gt;

&lt;/gmd:CI\_Series&gt;

&lt;/gmd:series&gt;

&lt;/gmd:CI\_Citation&gt;

&lt;/gmd:citation&gt;

&lt;gmd:abstract&gt;

&lt;gco:CharacterString&gt;Livello informativo in cui sono state
acquisite le aree colpite da incendio&lt;/gco:CharacterString&gt;

&lt;/gmd:abstract&gt;

&lt;gmd:pointOfContact&gt;

&lt;gmd:CI\_ResponsibleParty&gt;

&lt;gmd:organisationName&gt;

&lt;gco:CharacterString&gt;Molise Dati S.p.a&lt;/gco:CharacterString&gt;

&lt;/gmd:organisationName&gt;

&lt;gmd:contactInfo&gt;

&lt;gmd:CI\_Contact&gt;

&lt;gmd:phone&gt;

&lt;gmd:CI\_Telephone&gt;

&lt;gmd:voice&gt;

&lt;gco:CharacterString&gt;08746191&lt;/gco:CharacterString&gt;

&lt;/gmd:voice&gt;

&lt;/gmd:CI\_Telephone&gt;

&lt;/gmd:phone&gt;

&lt;gmd:address&gt;

&lt;gmd:CI\_Address&gt;

&lt;gmd:electronicMailAddress&gt;

&lt;gco:CharacterString&gt;info@molisedati.it&lt;/gco:CharacterString&gt;

&lt;/gmd:electronicMailAddress&gt;

&lt;/gmd:CI\_Address&gt;

&lt;/gmd:address&gt;

&lt;gmd:onlineResource&gt;

&lt;gmd:CI\_OnlineResource&gt;

&lt;gmd:linkage&gt;

&lt;gmd:URL&gt;http://www.molisedati.it/&lt;/gmd:URL&gt;

&lt;/gmd:linkage&gt;

&lt;/gmd:CI\_OnlineResource&gt;

&lt;/gmd:onlineResource&gt;

&lt;/gmd:CI\_Contact&gt;

&lt;/gmd:contactInfo&gt;

&lt;gmd:role&gt;

&lt;gmd:CI\_RoleCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_RoleCode"
codeListValue="pointOfContact"&gt;punto di
contatto&lt;/gmd:CI\_RoleCode&gt;

&lt;/gmd:role&gt;

&lt;/gmd:CI\_ResponsibleParty&gt;

&lt;/gmd:pointOfContact&gt;

&lt;gmd:descriptiveKeywords&gt;

&lt;gmd:MD\_Keywords&gt;

&lt;gmd:keyword&gt;

&lt;gco:CharacterString&gt;Zone a rischio
naturale&lt;/gco:CharacterString&gt;

&lt;/gmd:keyword&gt;

&lt;gmd:thesaurusName&gt;

&lt;gmd:CI\_Citation&gt;

&lt;gmd:title&gt;

&lt;gco:CharacterString&gt;GEMET - INSPIRE themes, version
1.0&lt;/gco:CharacterString&gt;

&lt;/gmd:title&gt;

&lt;gmd:date&gt;

&lt;gmd:CI\_Date&gt;

&lt;gmd:date&gt;

&lt;gco:Date&gt;2008-06-01&lt;/gco:Date&gt;

&lt;/gmd:date&gt;

&lt;gmd:dateType&gt;

&lt;gmd:CI\_DateTypeCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_DateTypeCode"
codeListValue="publication"&gt;pubblicazione&lt;/gmd:CI\_DateTypeCode&gt;

&lt;/gmd:dateType&gt;

&lt;/gmd:CI\_Date&gt;

&lt;/gmd:date&gt;

&lt;/gmd:CI\_Citation&gt;

&lt;/gmd:thesaurusName&gt;

&lt;/gmd:MD\_Keywords&gt;

&lt;/gmd:descriptiveKeywords&gt;

&lt;gmd:resourceConstraints&gt;

&lt;gmd:MD\_Constraints&gt;

&lt;gmd:useLimitation&gt;

&lt;gco:CharacterString&gt;Nessuna limitazione
d'uso&lt;/gco:CharacterString&gt;

&lt;/gmd:useLimitation&gt;

> &lt;/gmd:MD\_Constraints&gt;

&lt;/gmd:resourceConstraints&gt;

&lt;gmd:resourceConstraints&gt;

&lt;gmd:MD\_LegalConstraints&gt;

&lt;gmd:accessConstraints&gt;

&lt;gmd:MD\_RestrictionCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_RestrictionCode"
codeListValue="otherRestrictions"&gt;altri
vincoli&lt;/gmd:MD\_RestrictionCode&gt;

&lt;/gmd:accessConstraints&gt;

&lt;gmd:useConstraints&gt;

&lt;gmd:MD\_RestrictionCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_RestrictionCode"
codeListValue="otherRestrictions"&gt;altri
vincoli&lt;/gmd:MD\_RestrictionCode&gt;

&lt;/gmd:useConstraints&gt;

&lt;gmd:otherConstraints&gt;

&lt;gco:CharacterString&gt;Dato pubblico (cfr. art. 1 Codice
Amministrazione Digitale)&lt;/gco:CharacterString&gt;

&lt;/gmd:otherConstraints&gt;

&lt;/gmd:MD\_LegalConstraints&gt;

&lt;/gmd:resourceConstraints&gt;

&lt;gmd:resourceConstraints&gt;

&lt;gmd:MD\_SecurityConstraints&gt;

&lt;gmd:classification&gt;

&lt;gmd:MD\_ClassificationCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_ClassificationCode"
codeListValue="unclassified"&gt;Non
classificato&lt;/gmd:MD\_ClassificationCode&gt;

&lt;/gmd:classification&gt;

&lt;/gmd:MD\_SecurityConstraints&gt;

&lt;/gmd:resourceConstraints&gt;

&lt;gmd:spatialRepresentationType&gt;

&lt;gmd:MD\_SpatialRepresentationTypeCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_SpatialRepresentationTypeCode"
codeListValue="vector"&gt;dati
vettoriali&lt;/gmd:MD\_SpatialRepresentationTypeCode&gt;

&lt;/gmd:spatialRepresentationType&gt;

&lt;gmd:spatialResolution&gt;

&lt;gmd:MD\_Resolution&gt;

&lt;gmd:equivalentScale&gt;

&lt;gmd:MD\_RepresentativeFraction&gt;

&lt;gmd:denominator&gt;

&lt;gco:Integer&gt;10000&lt;/gco:Integer&gt;

&lt;/gmd:denominator&gt;

&lt;/gmd:MD\_RepresentativeFraction&gt;

&lt;/gmd:equivalentScale&gt;

&lt;/gmd:MD\_Resolution&gt;

&lt;/gmd:spatialResolution&gt;

&lt;gmd:language&gt;

&lt;gmd:LanguageCode codeList=" http://www.loc.gov/standards/iso639-2"
codeListValue="ita"&gt;ita&lt;/gmd:LanguageCode&gt;

&lt;/gmd:language&gt;

&lt;gmd:characterSet&gt;

&lt;gmd:MD\_CharacterSetCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#MD\_CharacterSetCode"
codeListValue="utf8"&gt;utf8&lt;/gmd:MD\_CharacterSetCode&gt;

&lt;/gmd:characterSet&gt;

&lt;gmd:topicCategory&gt;

&lt;gmd:MD\_TopicCategoryCode&gt;health&lt;/gmd:MD\_TopicCategoryCode&gt;

&lt;/gmd:topicCategory&gt;

&lt;gmd:extent&gt;

&lt;gmd:EX\_Extent&gt;

&lt;gmd:geographicElement&gt;

&lt;gmd:EX\_GeographicBoundingBox&gt;

&lt;gmd:westBoundLongitude&gt;

&lt;gco:Decimal&gt;14.018032&lt;/gco:Decimal&gt;

&lt;/gmd:westBoundLongitude&gt;

&lt;gmd:eastBoundLongitude&gt;

&lt;gco:Decimal&gt;14.933199&lt;/gco:Decimal&gt;

&lt;/gmd:eastBoundLongitude&gt;

&lt;gmd:southBoundLatitude&gt;

&lt;gco:Decimal&gt;41.398734&lt;/gco:Decimal&gt;

&lt;/gmd:southBoundLatitude&gt;

&lt;gmd:northBoundLatitude&gt;

&lt;gco:Decimal&gt;41.941072&lt;/gco:Decimal&gt;

&lt;/gmd:northBoundLatitude&gt;

&lt;/gmd:EX\_GeographicBoundingBox&gt;

&lt;/gmd:geographicElement&gt;

> &lt;gmd:temporalElement&gt;
>
> &lt;gmd:EX\_TemporalExtent&gt;
>
> &lt;gmd:extent&gt;
>
> &lt;gml:TimePeriod gml:id="TP1"&gt;
>
> &lt;gml:beginPosition&gt;2009-01-01&lt;/gml:beginPosition&gt;
>
> &lt;gml:endPosition&gt;2013-12-31&lt;/gml:endPosition&gt;
>
> &lt;/gml:TimePeriod&gt;
>
> &lt;/gmd:extent&gt;
>
> &lt;/gmd:EX\_TemporalExtent&gt;
>
> &lt;/gmd:temporalElement&gt;
>
> &lt;gmd:verticalElement&gt;
>
> &lt;gmd:EX\_VerticalExtent&gt;
>
> &lt;gmd:minimumValue&gt;

&lt;gco:Real&gt;15.56&lt;/gco:Real&gt;

> &lt;/gmd:minimumValue&gt;
>
> &lt;gmd:maximumValue&gt;
>
> &lt;gco:Real&gt;345.15&lt;/gco:Real&gt;
>
> &lt;/gmd:maximumValue&gt;
>
> &lt;gmd:verticalCRS
> xlink:href="http://www.epsg-registry.org/export.htm?gml=urn:ogc:def:crs:EPSG::4979"/&gt;
>
> &lt;/gmd:EX\_VerticalExtent&gt;
>
> &lt;/gmd:verticalElement&gt;

&lt;/gmd:EX\_Extent&gt;

&lt;/gmd:extent&gt;

&lt;/gmd:MD\_DataIdentification&gt;

&lt;/gmd:identificationInfo&gt;

&lt;gmd:distributionInfo&gt;

&lt;gmd:MD\_Distribution&gt;

&lt;gmd:distributionFormat&gt;

&lt;gmd:MD\_Format&gt;

&lt;gmd:name&gt;

&lt;gco:CharacterString&gt;shp&lt;/gco:CharacterString&gt;

&lt;/gmd:name&gt;

&lt;gmd:version&gt;

&lt;gco:CharacterString&gt;9.3&lt;/gco:CharacterString&gt;

&lt;/gmd:version&gt;

&lt;/gmd:MD\_Format&gt;

&lt;/gmd:distributionFormat&gt;

&lt;gmd:distributor&gt;

&lt;gmd:MD\_Distributor&gt;

&lt;gmd:distributorContact&gt;

&lt;gmd:CI\_ResponsibleParty&gt;

&lt;gmd:organisationName&gt;

&lt;gco:CharacterString&gt;Regione Molise&lt;/gco:CharacterString&gt;

&lt;/gmd:organisationName&gt;

&lt;gmd:contactInfo&gt;

&lt;gmd:CI\_Contact&gt;

&lt;gmd:address&gt;

&lt;gmd:CI\_Address&gt;

&lt;gmd:electronicMailAddress&gt;
&lt;gco:CharacterString&gt;info@regione.molise.it&lt;/gco:CharacterString&gt;
&lt;/gmd:electronicMailAddress&gt;

&lt;/gmd:CI\_Address&gt;

&lt;/gmd:address&gt;

&lt;gmd:onlineResource&gt;

&lt;gmd:CI\_OnlineResource&gt;

&lt;gmd:linkage&gt;

&lt;gmd:URL&gt;http://www.regione.molise.it/&lt;/gmd:URL&gt;

&lt;/gmd:linkage&gt;

&lt;/gmd:CI\_OnlineResource&gt;

&lt;/gmd:onlineResource&gt;

&lt;/gmd:CI\_Contact&gt;

&lt;/gmd:contactInfo&gt;

&lt;gmd:role&gt;

&lt;gmd:CI\_RoleCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_RoleCode"
codeListValue="distributor"&gt;distributore&lt;/gmd:CI\_RoleCode&gt;

&lt;/gmd:role&gt;

&lt;/gmd:CI\_ResponsibleParty&gt;

&lt;/gmd:distributorContact&gt;

&lt;/gmd:MD\_Distributor&gt;

&lt;/gmd:distributor&gt;

&lt;/gmd:MD\_Distribution&gt;

&lt;/gmd:distributionInfo&gt;

&lt;gmd:dataQualityInfo&gt;

&lt;gmd:DQ\_DataQuality&gt;

&lt;gmd:scope&gt;

&lt;gmd:DQ\_Scope&gt;

&lt;gmd:level&gt;

&lt;gmd:MD\_ScopeCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_ScopeCode"
codeListValue="dataset"&gt;dataset&lt;/gmd:MD\_ScopeCode&gt;

&lt;/gmd:level&gt;

&lt;/gmd:DQ\_Scope&gt;

&lt;/gmd:scope&gt;

&lt;gmd:report&gt;

&lt;gmd:DQ\_AbsoluteExternalPositionalAccuracy&gt;

&lt;gmd:result&gt;

&lt;gmd:DQ\_QuantitativeResult&gt;

&lt;gmd:valueUnit&gt;

&lt;gml:BaseUnit gml:id="UD1"&gt;

&lt;gml:identifier
codeSpace="http://www.bipm.fr/en/si/base\_units"&gt;m&lt;/gml:identifier&gt;

&lt;gml:unitsSystem xlink:href="http://www.bipm.fr/en/si"/&gt;

&lt;/gml:BaseUnit&gt;

&lt;/gmd:valueUnit&gt;

&lt;gmd:value&gt;

&lt;gco:Record&gt;

&lt;gco:Real&gt;5.0&lt;/gco:Real&gt;

&lt;/gco:Record&gt;

&lt;/gmd:value&gt;

&lt;/gmd:DQ\_QuantitativeResult&gt;

&lt;/gmd:result&gt;

&lt;/gmd:DQ\_AbsoluteExternalPositionalAccuracy&gt;

&lt;/gmd:report&gt;

&lt;gmd:report&gt;

&lt;gmd:DQ\_DomainConsistency&gt;

&lt;gmd:result&gt;

&lt;gmd:DQ\_ConformanceResult&gt;

&lt;gmd:specification&gt;

&lt;gmd:CI\_Citation&gt;

&lt;gmd:title&gt;

&lt;gco:CharacterString&gt;REGOLAMENTO (UE) N. 1089/2010 DELLA
COMMISSIONE del 23 novembre 2010 recante attuazione della direttiva
2007/2/CE del Parlamento europeo e del Consiglio per quanto riguarda
l'interoperabilità dei set di dati territoriali e dei servizi di dati
territoriali&lt;/gco:CharacterString&gt;

&lt;/gmd:title&gt;

&lt;gmd:date&gt;

&lt;gmd:CI\_Date&gt;

&lt;gmd:date&gt;

&lt;gco:Date&gt;2010-12-08&lt;/gco:Date&gt;

&lt;/gmd:date&gt;

&lt;gmd:dateType&gt; &lt;gmd:CI\_DateTypeCode
codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO\_19139\_Schemas/resources/codelist/gmxCodelists.xml\#CI\_DateTypeCode"
codeListValue="publication"&gt;Pubblicazione&lt;/gmd:CI\_DateTypeCode&gt;

&lt;/gmd:dateType&gt;

&lt;/gmd:CI\_Date&gt;

&lt;/gmd:date&gt;

&lt;/gmd:CI\_Citation&gt;

&lt;/gmd:specification&gt;

&lt;gmd:explanation&gt;

&lt;gco:CharacterString&gt;Non richiesto&lt;/gco:CharacterString&gt;

&lt;/gmd:explanation&gt;

&lt;gmd:pass&gt;

&lt;gco:Boolean&gt;false&lt;/gco:Boolean&gt;

&lt;/gmd:pass&gt;

&lt;/gmd:DQ\_ConformanceResult&gt;

&lt;/gmd:result&gt;

&lt;/gmd:DQ\_DomainConsistency&gt;

&lt;/gmd:report&gt;

&lt;gmd:lineage&gt;

&lt;gmd:LI\_Lineage&gt;

&lt;gmd:statement&gt;

&lt;gco:CharacterString&gt;I dati di origine sono Gauss-Boaga fuso Est e
sono stati riproiettati in WGS 84 geografico con il software Verto 2000
IGM, che utilizza il girigliato IGM. Il caricamento dati è stato
realizzato, mantenendo la struttura informativa originale, tramite le
funzioni di base di ArcGIS nella banca dati SVA, su RDBMS
DB2&lt;/gco:CharacterString&gt;

&lt;/gmd:statement&gt;

&lt;/gmd:LI\_Lineage&gt;

&lt;/gmd:lineage&gt;

&lt;/gmd:DQ\_DataQuality&gt;

&lt;/gmd:dataQualityInfo&gt;

&lt;/gmd:MD\_Metadata&gt;

B.2 Esempio di file XML per la serie {#b.2-esempio-di-file-xml-per-la-serie .ListParagraph}
------------------------------------

Fermo restando quanto indicato al § 1.4, le linee guida INSPIRE denotano
che non ci sono differenze significative tra i metadati del dataset e i
metadati della serie. Pertanto, per la serie si può fare riferimento
all’esempio per il dataset riportato al paragrafo precedente.

Nel caso della serie, non esistendo nessun livello gerarchico superiore,
i due metadati “*Identificatore*” e “*Id livello superiore*” assumeranno
sempre lo stesso valore.

[^1]: https://creativecommons.org/licenses/by-sa/3.0/it/

[^2]: Decreto 10 novembre 2011 del Ministro per la Pubblica
    Amministrazione e l’Innovazione di concerto con il Ministro
    dell’Ambiente e della Tutela del Territorio e del Mare recante
    “*Regole tecniche per la definizione del contenuto del Repertorio
    nazionale dei dati territoriali, nonché delle modalità di prima
    costituzione e di aggiornamento dello stesso*”, pubblicato sulla
    G.U. n. 48 del 27 febbraio 2012 - supplemento ordinario n. 37.

[^3]: “*INSPIRE Metadata Implementing Rules: Technical Guidelines based
    on EN ISO 19115 and EN ISO 19119*” v. 1.3, disponibili al link
    http://inspire.jrc.ec.europa.eu/documents/Metadata/MD\_IR\_and\_ISO\_20131029.pdf

[^4]: Nel diagramma UML riportato in fig. 3, par. 6.2 dello Standard ISO
    19115 sono rappresentate le classi a cui si applicano i metadati. In
    riferimento a ciò, lo Standard specifica che i metadati possono
    essere applicati anche a tutte le altre classi della codeList
    *MD\_ScopeCode* non riportate nel diagramma. Tra queste classi c’è
    anche “*tile*” (*sezione*) scelto come ulteriore livello di
    dettaglio dei metadati nel RNDT.

[^5]: Nella nuova versione dello Standard (*ISO 19115-1:2014 Geographic
    Information - Metadata - Part 1: Fundamentals*) il concetto di
    *core* *metadata* è stato rimosso. Come indicato, nel presente
    documento si fa riferimento all'edizione 2003 dello Standard ISO.

[^6]: Disponibile al link
    [*http://www.eionet.europa.eu/gemet/index\_html?langcode=it*](http://www.eionet.europa.eu/gemet/index_html?langcode=it)

[^7]: *Regolamento (UE) n. 1089/2010 della Commissione, del 23 novembre
    2010, recante attuazione della direttiva 2007/2/CE del Parlamento
    europeo e del Consiglio per quanto riguarda l'interoperabilità dei
    set di dati territoriali e dei servizi di dati territoriali*,
    Gazzetta Ufficiale dell'Unione Europea L323 dell'8/10/2010

[^8]: Disponibili alla pagina
    http://inspire.jrc.ec.europa.eu/index.cfm/pageid/2.

[^9]: v\. nota 3.

[^10]: La raccomandazione, sebbene mutuata dalle linee guida tecniche
    indicate, è valida per tutte le categorie di dati territoriali.

[^11]: v\. nota 10.

[^12]: v\. nota 10.

[^13]: Modificato dai Regolamenti (UE) della Commissione n. 102/2011 e
    n. 1253/2013.

[^14]: v\. nota 8.

[^15]: I requisiti e la raccomandazione citati sono indicati con i
    relativi numeri della specifica *INSPIRE Data Specification on
    Addresses – Technical Guidelines*, ma sono validi per tutte le
    categorie di dati territoriali.

[^16]: v\. nota 7

[^17]: http://www.eionet.europa.eu/gemet/inspire\_themes?langcode=en

[^18]: Corrisponde a "*particelle catastali*"; viene così riportato in
    conformità alla traduzione italiana della Direttiva INSPIRE, come
    pubblicata nella GU dell'Unione Europea L 108/1 del 25/04/2007
    disponibile al link
    http://eurlex.europa.eu/LexUriServ/LexUriServ.do?uri=OJ:L:2007:108:0001:0014:IT:PDF.
