---
title: Log delle modifiche per SQL Server Data Tools (SSDT) | Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: b071f8b8-c8e5-44e0-bbb6-04804dd1863a
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: 4fafda7376f5c44c795fab85c6659cf5824522e1
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51677900"
---
# <a name="changelog-for-sql-server-data-tools-ssdt"></a>Log delle modifiche per SQL Server Data Tools (SSDT)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Questo log delle modifiche è per [SQL Server Data Tools (SSDT)](download-sql-server-data-tools-ssdt.md).  
  
Per i post dettagliati sulle novità e le modifiche, vedere il [blog del team di SSDT](https://blogs.msdn.microsoft.com/ssdt/).


## <a name="ssdt-for-visual-studio-2017-1582"></a>SSDT per Visual Studio 2017 (15.8.2)
Numero di build: 14.0.16182.0  
Data versione: 5 novembre 2018  

### <a name="whats-new"></a>Novità
**SSIS:**

È stato risolto un problema relativo alla distribuzione di progetti SSIS contenenti pacchetti con Attività script/Destinazione file flat in Azure-SSIS che impedisce l'esecuzione dei pacchetti in Azure-SSIS. 

### <a name="known-issues"></a>Problemi noti:

- L'attività di esecuzione pacchetti SSIS non supporta il debug quando ExecuteOutOfProcess è impostato su True. Questo problema è limitato al debug. Il salvataggio, la distribuzione e l'esecuzione tramite DTExec.exe o il catalogo SSIS funzionano normalmente.
- SSDT per Visual Studio 2017 (15.8.2) non supporta gli strumenti per la progettazione contenenti un'origine/destinazione Oracle/Teradata. Usare SSDT per Visual Studio 2017 (15.8).


## <a name="ssdt-for-visual-studio-2017-1581"></a>SSDT per Visual Studio 2017 (15.8.1)
Numero di build: 14.0.16179.0  
Data di rilascio: 27 settembre 2018  

### <a name="whats-new"></a>Novità

**SSIS:**

1. Aggiunto il supporto per [!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)].
2. Rimosso il supporto per SQL Server 2012.

### <a name="known-issues"></a>Problemi noti:

- L'attività di esecuzione pacchetti SSIS non supporta il debug quando ExecuteOutOfProcess è impostato su True. Questo problema è limitato al debug. Il salvataggio, la distribuzione e l'esecuzione tramite DTExec.exe o il catalogo SSIS funzionano normalmente.
- La distribuzione di progetti SSIS con pacchetti contenenti Attività script/Destinazione file flat in Azure-SSIS impedisce l'esecuzione dei pacchetti in Azure-SSIS.
- SSDT per Visual Studio 2017 (15.8.1) non supporta gli strumenti per la progettazione contenenti un'origine/destinazione Oracle/Teradata. Usare SSDT per Visual Studio 2017 (15.8).


## <a name="ssdt-for-visual-studio-2017-158"></a>SSDT per Visual Studio 2017 (15.8)
Numero di build: 14.0.16174.0  
Data di rilascio: 05 settembre 2018  

### <a name="whats-new"></a>Novità

**SSIS:**

1. Regressione della correzione in Visual Studio 15.8 per l'errore di compilazione in seguito al salvataggio dell'attività/componente di script.
1. Regressione della correzione in Visual Studio 15.8 per il malfunzionamento della distribuzione guidata.
1. Risoluzione di un problema a causa del quale la gestione connessione ADO.NET non supporta il provider ADO.NET di terze parti.

**Programma di installazione:**

- Implementazione del riavvio intermedio durante l'installazione di SSDT in Windows 10.


### <a name="known-issues"></a>Problemi noti:

- L'attività di esecuzione pacchetti SSIS non supporta il debug quando ExecuteOutOfProcess è impostato su True. Questo problema è limitato al debug. Il salvataggio, la distribuzione e l'esecuzione tramite DTExec.exe o il catalogo SSIS funzionano normalmente.




## <a name="ssdt-for-visual-studio-2017-1571"></a>SSDT per Visual Studio 2017 (15.7.1)
Numero di build: 14.0.16167.0  
Data di rilascio: 02 luglio 2018  
  
### <a name="whats-new"></a>Novità

**SSIS:**

- Aggiunta del supporto per la nuova autorità AAD di Azure per enti pubblici (login.microsoftonline.us) per l'uso con le attività Analysis Services.
- Risoluzione di un problema per cui l'interfaccia utente dell'attività Elaborazione Analysis Services attività di elaborazione dell'interfaccia utente visualizza l'errore "Impossibile trovare il metodo" quando la versione del server di destinazione è SQLServer2016.
- Risoluzione del problema per cui non è possibile eseguire alcuni componenti della pipeline quando la versione del server di destinazione è SQLServer2012.

**Programma di installazione:**

- Filtrare l'elenco di istanze di Visual Studio per escludere le istanze che non possono installare SSDT.

### <a name="known-issues"></a>Problemi noti:

- L'attività di esecuzione pacchetti SSIS non supporta il debug quando ExecuteOutOfProcess è impostato su True. Questo problema è limitato al debug. Il salvataggio, la distribuzione e l'esecuzione tramite DTExec.exe o il catalogo SSIS funzionano normalmente.
- Quando si installa SSDT in Windows 10 e si sceglie "Installare la nuova istanza di Microsoft SQL Server Data Tools per Visual Studio 2017", l'installazione ha esito negativo con il messaggio "L'operazione metafile richiesta non è supportata". Riavviare il computer e avviare nuovamente il programma di installazione di SSDT per continuare l'installazione.



## <a name="ssdt-for-visual-studio-2017-1570"></a>SSDT per Visual Studio 2017 (15.7.0)
Numero di build: 14.0.16165.0  
Data di rilascio: 4 giugno 2018  
  
### <a name="whats-new"></a>Novità

**SSIS:**

- Corregge il problema della visualizzazione non corretta della pagina *Finestre di progettazione Integration Services* nella finestra di dialogo Opzioni.  
- Corregge il problema del tasso di luminosità per il testo visualizzato nell'*Editor trasformazione Ordinamento*.  
- Corregge il problema della sparizione della finestra di dialogo *Risolvi riferimenti* quando si prova a modificare una casella combinata.  
- Corregge il problema del mancato funzionamento del collegamento alla Guida di *Gestione connessione Hadoop* tramite F1.  
- Corregge il problema della perdita di codice di attività Script all'interno di un contenitore se il codice è destinato a SQL Server 2016.  


**Programma di installazione:**

- Corregge il problema dell'impossibilità di installare SSAS prima di SSRS e SSIS in Visual Studio 15.7.2.

### <a name="known-issues"></a>Problemi noti:

- L'attività di esecuzione pacchetti SSIS non supporta il debug quando *ExecuteOutOfProcess* è impostato su *True*. Questo problema è limitato al debug. Il salvataggio, la distribuzione e l'esecuzione tramite DTExec.exe o il catalogo SSIS funzionano normalmente.


## <a name="ssdt-for-visual-studio-2017-1560"></a>SSDT per Visual Studio 2017 (15.6.0)
Numero di build: 14.0.16162.0  
Data di rilascio: 10 aprile 2018
  
### <a name="whats-new"></a>Novità

**SSIS:**

- È stato risolto il problema relativo alla mancata registrazione da parte dell'attività di elaborazione AS delle fasi di elaborazione quando la destinazione è SQLServer2016 o SQLServer2017
- È stato risolto il problema della violazione di accesso che si verifica quando si apre dtsx in SSDT con nomi di attività molto lunghi non in inglese
- È stato risolto il problema della scomparsa, talvolta, dell'elenco delle variabili di ScriptTask nell'interfaccia utente delle attività
- È stato risolto il problema dell'impossibilità di aggiungere una copia di un pacchetto esistente se la posizione del pacchetto è SQL Server
- È stato risolto il problema del blocco dello stato attivo durante l'accesso alla casella combinata nella finestra di dialogo di alcuni editor.
- È stato risolto il problema della mancata modifica dello sfondo quando si cambia il tema di Visual Studio.
- È stato risolto il problema dell'invisibilità delle etichette Annotazione e Caricamento con un tema scuro.
- È stato risolto il problema della definizione non corretta della proprietà relativa allo stato per gli elementi disabilitati della casella degli strumenti SSIS.
- È stato risolto il problema dell'impossibilità di eseguire WebServiceTask.
- È stato risolto il problema dell'esito negativo della distribuzione di pacchetti se la stringa di connessione è impostata su una variabile con espressione dipendente da parametri di progetto.

**Programma di installazione:**

- Aggiunta del collegamento "Analisi utilizzo software per SQL Server Data Tools" nell'informativa sulla privacy.
- È stato risolto il problema della comparsa della finestra del programma di installazione di Visual Studio quando si seleziona "Installare la nuova istanza di Microsoft SQL Server Data Tools per Visual Studio 2017"

### <a name="known-issues"></a>Problemi noti:
- L'attività di esecuzione pacchetti SSIS non supporta il debug quando ExecuteOutOfProcess è impostato su True. Questo problema è limitato al debug. Il salvataggio, la distribuzione e l'esecuzione tramite DTExec.exe o il catalogo SSIS funzionano normalmente.



## <a name="ssdt-for-visual-studio-2017-1552"></a>SSDT per Visual Studio 2017 (15.5.2)
Numero di build: 14.0.16156.0
  
### <a name="whats-new"></a>Novità

**SSIS**
- È stato risolto un problema a causa del quale la migrazione dei progetti SSIS 2008 non riesce quando SSAS e SSIS sono entrambi installati nella stessa istanza di VS 2017.
- È stato risolto un problema a causa del quale non è possibile compilare i progetti RDLC quando Progettazione report RDLC e SSIS sono entrambi installati nella stessa istanza di VS 2017.
- È stato risolto un problema a causa del quale non è possibile aggiornare il colore delle annotazioni.
- È stato risolto un problema a causa del quale alcune stringhe nell'Editor gestione connessione Hadoop risultano troncate in altre lingue.
- È stato risolto un problema a causa del quale alcune stringhe vengono troncate nell'Editor gestione connessione OData.
- È stato risolto un problema a causa del quale alcune stringhe vengono troncate nella finestra di Importazione guidata progetto di Integration Services.
- È stato risolto un problema relativo al titolo nella finestra delle informazioni della casella degli strumenti SSIS.
- È stato risolto un problema a causa del quale alcune stringhe vengono troncate nella finestra di Distribuzione guidata Integration Services. 

**Programma di installazione**
- È stato risolto un problema a causa del quale a volte il download del payload non riesce con l'errore "Impossibile trovare il file specificato (0x80070002)".  

### <a name="known-issues"></a>Problemi noti
- L'attività di esecuzione pacchetti SSIS non supporta il debug quando *ExecuteOutOfProcess* è impostato su *True*. Questo problema è limitato al debug. Il salvataggio, la distribuzione e l'esecuzione tramite DTExec.exe o il catalogo SSIS funzionano normalmente.




## <a name="ssdt-for-visual-studio-2017-1551"></a>SSDT per Visual Studio 2017 (15.5.1)
Numero di build: 14.0.16148.0
  
### <a name="whats-new"></a>Novità

Visual Studio 2017 (15.5.1) è uguale alla versione 15.5.0 tranne che per le correzioni di bug seguenti apportate al programma di installazione:

1.  Risolvere il problema per cui il programma di installazione si blocca dopo l'installazione di SQL Server Integration Services.
2.  Risolvere il problema per cui l'installazione non riesce e viene visualizzato il messaggio di errore seguente: "L'operazione metafile richiesta non è supportata (0x800707D3)".

A parte queste due correzioni di bug, i dettagli seguenti per la versione 15.5.0 si applicano anche alla versione 15.5.1

## <a name="ssdt-for-visual-studio-2017-1550"></a>SSDT per Visual Studio 2017 (15.5.0)
Numero di build: 14.0.16146.0
  
### <a name="whats-new"></a>Novità

SSDT per Visual Studio 2017 (15.5.0) passa dalla versione di anteprima alla disponibilità generale.

**Programma di installazione**
1. L'interfaccia utente del programma di installazione è localizzata.
1. L'icona è stata sostituita con una versione di qualità superiore.

**Integration Services (IS)**
1. È stato aggiunto un passaggio di convalida del pacchetto nella distribuzione guidata durante la distribuzione nel runtime di integrazione di Azure SSIS nel file di definizione dell'applicazione (ADF), che consente di individuare potenziali problemi di compatibilità nei pacchetti SSIS per l'esecuzione nel runtime di integrazione di Azure SSIS. Per altre informazioni, vedere [Convalidare pacchetti SSIS distribuiti in Azure](..\integration-services\lift-shift\ssis-azure-validate-packages.md).
1. L'estensione SSIS è localizzata.

### <a name="bug-fixes"></a>Correzioni di bug

**Integration Services (IS)**
1. È stato risolto un problema per cui il layout della gestione connessione OLEDB e ADO.NET risultava danneggiata.
2. È stato risolto un problema per cui veniva generato un errore di assembly non trovato durante il tentativo di modifica di un'attività di elaborazione della dimensione.

### <a name="known-issues"></a>Problemi noti

**Integration Services (SSIS)** L'attività di esecuzione dei pacchetti SSIS non supporta il debug quando l'elemento ExecuteOutOfProcess è impostato su True. Questo problema è limitato al debug. Il salvataggio, la distribuzione e l'esecuzione tramite DTExec.exe o il catalogo SSIS funzionano normalmente.



## <a name="ssdt-174-for-visual-studio-2015"></a>SSDT 17.4 per Visual Studio 2015
Numero di build: 14.0.61712.050

### <a name="whats-new"></a>Novità

**Progetti Analysis Services (SSAS)**
- Sono state aggiunte tre nuove opzioni per progetti tabulari in Opzioni > Analysis Services Tabular > Importazione dati:
  - Abilita origini dati legacy: consente all'utente di creare origini dati precedenti alla "modalità di compatibilità 1200" in modalità di compatibilità più recenti.
  - Automatic type detection (Rilevamento tipo automatico): se abilitato, l'editor di query per le origini dati moderne tenta di rilevare i tipi di dati per le query non strutturate quando vengono caricate. Se il rilevamento ha esito positivo, è possibile aggiungere un nuovo passaggio alla query.
  - Esegui analisi in background nell'editor di query: quando è abilitato, l'editor di query per le origini dati moderne esegue le query sull'origine dati quando le query vengono caricate per analizzare lo schema di output della query.

**Integration Services (IS)**
- È stato aggiunto un passaggio di convalida del pacchetto nella distribuzione guidata durante la distribuzione nel runtime di integrazione di Azure SSIS nel file di definizione dell'applicazione (ADF), che consente di individuare potenziali problemi di compatibilità nei pacchetti SSIS per l'esecuzione nel runtime di integrazione di Azure SSIS. Per altre informazioni, vedere [Convalidare pacchetti SSIS distribuiti in Azure](..\integration-services\lift-shift\ssis-azure-validate-packages.md).


### <a name="bug-fixes"></a>Correzioni di bug

**Progetti Analysis Services (SSAS):**
- È stato risolto un problema che poteva causare un'eccezione non gestita durante l'archiviazione delle modifiche del modello in TFS.
- È stato risolto un problema che poteva causare un'eccezione durante l'aggiunta di una tabella con espressioni M complesse a un modello 1400.
- È stato risolto un problema che poteva causare un arresto anomalo di Visual Studio durante la ricerca di metadati nella vista diagramma del modello.
- È stato risolto un problema con i modelli 1400 che poteva causare la rimozione delle colonne calcolate dalla definizione della tabella durante il salvataggio delle modifiche alle query della partizione M.
- È stato risolto un problema che si verificava durante l'uso di Rinomina query nei modelli 1400 nell'interfaccia utente di recupero dei dati/editor di tabella che si bloccava durante la convalida della compatibilità con il modello di dati corrente.
- È stato risolto un problema che causava un mancato riferimento all'assembly Newtonsoft durante la distribuzione del modello 1400 in Azure Analysis Services.
- È stato risolto un problema che in alcuni casi causava un errore di importazione di dati tramite PQ nel modello 1400.
- È stato risolto un problema di ridimensionamento nelle finestre di dialogo dell'interfaccia utente di PowerQuery che venivano visualizzate quando veniva impostato il ridimensionamento di Windows.
- È stato risolto un problema con la ridenominazione dei ruoli.
- Sono stati risolti problemi con le configurazioni dei progetti che in alcuni casi potevano causare il mancato salvataggio o la sincronizzazione non corretta delle modifiche.
- È stato risolto un problema nell'editor di PowerQuery che aggiungeva automaticamente passaggi di tipo di modifica.
- È stato risolto un problema che causava un errore di apertura del file BIM dopo il cambio di modalità in/da Area di lavoro integrata.
- La proprietà MaxConnections è ora visibile per le origini dati nei modelli tabulari.
- Sono state aumentate le dimensioni iniziali della finestra dell'editor di PowerQuery.
- Le parole chiave di query M, come ad esempio "Origine" nell'editor di PowerQuery sono state localizzate.
- Le credenziali vengono memorizzate nella cache quando si usano i modelli 1400 e le origini dati strutturate per evitare di dover immettere le stesse credenziali per ogni tabella modificata.

**Progetti SSRS:**
- È stato risolto un problema che impediva la distribuzione di un singolo report in un progetto a più report
- È stato risolto un problema con le origini dati condivise che potevano causare un problema nella distribuzione
- È stato risolto un problema che poteva causare l'arresto in modo anomalo della gestione degli annullamenti quando ci si postava tra la visualizzazione Codice, la visualizzazione Progettazione e la finestra dell'editor di query
- È stato risolto un problema che poteva causare la mancata visualizzazione del pannello dei parametri dopo un errore di runtime
- È stato risolto un problema con i progetti report che potevano causare la perdita dei mapping del controllo del codice sorgente

**Integration Services:**
- È stato risolto un problema che poteva verificarsi durante il passaggio di una connessione in un'attività di processo di Analysis Services
- È stato risolto un problema per cui alcune attività e alcuni componenti non venivano localizzati correttamente.
- È stato risolto un problema per cui i componenti CDC si interrompevano dopo l'applicazione di una correzione SQL per CDC che aggiungeva la colonna \__$command\_id.


## <a name="ssdt-for-visual-studio-2017-1540-preview"></a>SSDT per Visual Studio 2017 (anteprima della versione 15.4.0)
Numero di build: 14.0.16134.0
  
### <a name="whats-new"></a>Novità

Questa versione offre un programma di installazione Web autonoma per progetti relativi a database di SQL Server, Analysis Services, Reporting Services e Integration Services in Visual Studio 2017 15.4 o versioni successive.

### <a name="installer"></a>Programma di installazione

- Consente di impostare un nome alternativo quando si installa una nuova istanza di SSDT per Visual Studio 2017.
- Consente di nascondere le caselle di controllo per la selezione delle funzionalità del programma di installazione se non è selezionata alcuna istanza di Visual Studio.
- Consente di perfezionare alcuni messaggi del programma di installazione in base ai suggerimenti dei clienti.
- Corregge il problema del mancato supporto dell'aggiornamento da parte del programma di installazione.


### <a name="ssis"></a>SSIS

- Corregge il problema dell'impossibilità di elencare le origini dati nell'importazione/esportazione guidata se è installato il Feature Pack di Azure.
- Corregge il problema della generazione di un'eccezione durante la modifica di un'attività di processo di SSIS Analysis Services mentre si passa a un'altra connessione.
- Corregge il problema dell'interruzione dei componenti CDC dopo l'applicazione della correzione di SQL che aggiunge la colonna __$command_id.
- Corregge il problema dell'impossibilità di modificare ed eseguire un pacchetto di terze parti se la destinazione è una versione precedente di SQL Server.
- Corregge il problema della visualizzazione non corretta della finestra di dialogo di configurazione Origine file flat se si fa doppio clic su DTSWizard.exe e si seleziona Origine file flat.
- Corregge il problema dell'impossibilità di eseguire un pacchetto contenente un'attività o un componente di Azure Feature Pack se la destinazione è SQL Server 2017.


**Problemi noti**

- Il programma di installazione non è localizzato.
- L'attività di esecuzione pacchetti SSIS non supporta il debug quando *ExecuteOutOfProcess* è impostato su True. Questo problema è limitato al debug. Il salvataggio, la distribuzione e l'esecuzione tramite DTExec.exe o il catalogo SSIS funzionano normalmente.


## <a name="ssdt-173-for-visual-studio-2015"></a>SSDT 17.3 per Visual Studio 2015
Numero di build: 14.0.61709.290

### <a name="whats-new"></a>Novità

**Analysis Services (AS)**

- Nei modelli 1400 sono abilitati Cosmos DB e HDI Spark.
- Proprietà delle origini dati tabulari.
- "Query vuota" è ora un'opzione supportata per la creazione di una nuova query nell'editor di query per i modelli a livello di compatibilità 1400.
- L'editor di query per i modelli in modalità 1400 consente ora di salvare le query senza che le nuove tabelle vengano automaticamente elaborate.

**Reporting Services (RS)**

- I progetti ora all'apertura nel formato aggiornato richiedono il supporto di MSBuild per la compilazione e la distribuzione.

### <a name="known-issues"></a>Problemi noti

**Analysis Services (AS)**

- I modelli con livello di compatibilità 1400 in modalità DirectQuery che includono prospettive non sono in grado di individuare i metadati o di eseguire query sugli stessi.

**Reporting Services (RS)**

- Il nuovo formato di progetto report non mantiene l'associazione del controllo del codice sorgente e genera un errore simile al messaggio seguente:

   *Il file di progetto C:\path non è associato al controllo del codice sorgente, ma la soluzione contiene informazioni sull'associazione del controllo del codice sorgente relative a esso.*
 
   Per risolvere questo problema, fare clic su **Usa associazione della soluzione** ogni volta che la soluzione è aperta.

- Dopo aver aggiornato il progetto al nuovo formato MSBuild, è possibile che il salvataggio abbia esito negativo con un messaggio simile al seguente:

   *"Il parametro "unevaluatedValue" non può essere null".*

   Per risolvere questo problema, aggiornare le *configurazioni di progetto* e popolare la proprietà *Platform*.

### <a name="bug-fixes"></a>Correzioni di bug

**Analysis Services (AS)**

- Notevole miglioramento delle prestazioni quando si carica la visualizzazione Diagramma del modello tabulare.
- Corretti alcuni problemi per migliorare l'integrazione e l'esperienza con Power Query nei modelli con livello di compatibilità 1400.
   - Risolto un problema che impediva la modifica delle autorizzazioni per le origini file.
   - Corretto un problema che impediva di modificare l'origine per le origini file.
   - Risolto un problema che causava la visualizzazione di un'interfaccia utente non corretta per le origini file.
- Risolto un problema che causava la rimozione della proprietà "JoinOnDate" quando si rendeva inattiva una relazione "Join on Date".
- L'opzione Nuova query del Generatore di query ora consente di creare una query vuota.
- Risolto un problema che durante la modifica di una query origine dati esistente impediva l'aggiornamento della definizione del modello della tabella al livello di compatibilità 1400.
- Corretti problemi delle espressioni di contesto che potevano causare eccezioni.
- Quando si importa una nuova tabella con nome duplicato nei modelli tabulari 1400, all'utente ora viene comunicato che si è verificato un conflitto di nome e che il nome viene modificato in modo da essere univoco.
- La modalità di rappresentazione Utente corrente è stata rimossa dai modelli in modalità di importazione, perché non è uno scenario supportato.
- L'integrazione di Power Query ora supporta opzioni per origini dati aggiuntive (OData.Feed, Odbc.DataSource, Access.Database, SapBusinessWarehouse.Cubes).
- Nelle stringhe delle opzioni di Power Query per le origini dati il testo ora viene localizzato correttamente in base alle impostazioni locali del client.
- Nella visualizzazione Diagramma ora appaiono le colonne appena create dall'editor di query M nei modelli con livello di compatibilità 1400.
- L'editor di Power Query offre ora la possibilità di non importare i dati.
- Risolto un problema relativo all'installazione della cartridge di dati usata per importare le tabelle da Oracle nei modelli multidimensionali in VS2017.
- Risolto un problema che in alcuni casi può causare un arresto anomalo del sistema quando il cursore del mouse esce dalla barra della formula della tabella.
- Risolto un problema nella finestra di dialogo Modifica proprietà tabella per cui modificando il nome della tabella veniva modificato in modo non corretto il nome della tabella di origine causando un errore imprevisto.
- Corretto un arresto anomalo del sistema che può verificarsi in VS2017 quando si tenta di richiamare il test sicurezza cubo nella scheda Dati delle celle della finestra di progettazione Ruoli nei progetti multidimensionali.
- SSDT: le proprietà non possono essere modificate per le origini dati in formato tabulare.
- Risolto un problema che in alcuni casi poteva impedire il corretto funzionamento delle compilazioni di MSBuild e DevEnv con i file della soluzione.
- Ottimizzate le prestazioni quando si esegue il commit delle modifiche apportate al modello (modifiche DAX per le misure, colonne calcolate) e il modello tabulare contiene metadati di dimensioni maggiori
- Risolti alcuni problemi relativi all'importazione dei dati con PowerQuery nei modelli con livello di compatibilità 1400
   - L'importazione richiede molto tempo dopo avere fatto clic su Importa e nell'interfaccia utente non è indicato alcuno stato
   - Un lungo elenco di tabelle nella visualizzazione Strumento di navigazione rallenta la selezione delle tabelle da importare
   - Prestazioni ridotte dell'editor di query quando si usa l'elenco di 35 query visualizzato nell'editor (stesso problema nel desktop PBI)
   - L'importazione di più tabelle disabilita la barra degli strumenti e può non terminare in determinate situazioni 
   - La finestra di progettazione del modello appare disabilitata e non indica dati dopo l'importazione di una tabella con Power Query
   - Se si deseleziona la casella "Crea nuova tabella" nell'interfaccia utente di Power Query viene comunque creata una nuova tabella
   - Non vengono richieste le credenziali per l'origine dati della cartella 
   - Se il riferimento all'oggetto non è impostato può essere generata un'eccezione quando si tenta di ottenere credenziali aggiornate per l'origine dati strutturata
   - L'apertura di Gestione partizioni con l'espressione M era molto lenta
   - Selezionando Proprietà nella tabella dell'editor di Power Query non appaiono le proprietà
- Migliorata l'affidabilità dell'integrazione dell'interfaccia utente di Power Query per il rilevamento delle eccezioni di livello superiore e la visualizzazione nella finestra di output
- Risolto un problema con ChangeSource relativo alle modifiche non persistenti dell'origine dati della struttura con espressione del contesto di esecuzione
- Risolto un problema per cui gli errori di espressione M possono causare errori dell'aggiornamento del modello senza che vengano visualizzati messaggi di errore
- Risolto un problema per cui SSDT veniva chiuso con il messaggio di errore "Prima di chiudere la soluzione è necessario terminare la compilazione"
- Risolto un problema per cui Visual Studio può sembrare bloccato se si imposta una modalità di rappresentazione non corretta nel modello con livello di compatibilità 1400 
- La proprietà di righe di dettaglio ora viene serializzata in JSON solo quando non è vuota (modificata rispetto all'impostazione predefinita)
- Il driver OLEDB Oracle ora è disponibile nell'elenco per la modalità DirectQuery tabulare
- L'aggiunta di espressioni M nei modelli tabulari con compatibilità 1400 ora appare e viene aggiornata in Esplora modelli tabulari
- Risolto un problema che impediva la visualizzazione del provider MSOLAP in VS2017 quando si tentava di eseguire l'importazione selezionando "Altro" come origine dati in modelli con livello di compatibilità precedente a 1400
- Risolto un problema che può generare errori quando si aggiunge una traslazione usando Esplora modelli tabulari 
- Corretto un problema dell'interfaccia della sicurezza a livello di oggetto che in alcuni casi impedisce di visualizzare e nascondere la scheda in modo corretto
- Risolto un problema per cui può verificarsi un errore quando si tenta di aprire un modello multidimensionale caricato in precedenza usando la finestra di dialogo Connetti al database
- Risolto un problema che causava un errore durante l'aggiunta di assembly personalizzati a un modello multidimensionale

**Reporting Services (RS)**

- Risolto un problema di compilazione e creazione di RDLC in VS 2017

## <a name="ssdt-for-visual-studio-2017-1530-preview"></a>SSDT per Visual Studio 2017 (anteprima 15.3.0)
Numero di build: 14.0.16121.0
  
### <a name="whats-new"></a>Novità

Questa anteprima è la prima versione di SSDT per Visual Studio 2017. Questa versione introduce un'esperienza di installazione Web autonoma per i progetti SQL Server Database, Analysis Services, Reporting Services e Integration Services in Visual Studio 2017 15.3 o versioni successive.


**Problemi noti**

- Il programma di installazione non è localizzato.
- SSIS non è localizzato.
- L'attività di esecuzione pacchetti SSIS non supporta il debug quando *ExecuteOutofProcess* è impostato su *True*. Questo problema è limitato al debug. Il salvataggio, la distribuzione e l'esecuzione tramite DTExec.exe o il catalogo SSIS funzionano normalmente.
- Per un elenco completo delle modifiche, vedere il [log delle modifiche](changelog-for-sql-server-data-tools-ssdt.md).
- I pacchetti SSIS che contengono estensioni di terze parti non possono essere destinati all'uso con altre versioni di server.


## <a name="ssdt-172-for-visual-studio-2015"></a>SSDT 17.2 per Visual Studio 2015
Numero di build: 14.0.61707.300

### <a name="whats-new"></a>Novità


**Progetti AS:**
- Ora è possibile configurare la sicurezza a livello di oggetto nella finestra di dialogo *Ruoli* per la sicurezza avanzata nei modelli tabulari con livello di compatibilità 1400.
- Nuova selezione di membri del ruolo AAD per gli utenti senza indirizzi di posta elettronica nei modelli di Azure Analysis Services nei progetti SSDT Analysis Services per Visual Studio 2017.
- Nuova proprietà del progetto "Chiedi sempre conferma" di Azure Analysis Services nei progetti tabulari di SSDT Analysis Services per personalizzare il comportamento di memorizzazione nella cache delle credenziali ADAL.


### <a name="bug-fixes"></a>Correzioni di bug

**Generale**
- Aggiornati i riferimenti di personalizzazione per SQL Server 2017.

**Progetti AS**
- Notevole miglioramento delle prestazioni per migliorare l'esperienza durante il commit di modifiche delle misure DAX e altre modifiche al modello.
- Risolti alcuni problemi di integrazione di Power Query nei progetti di Analysis Services che usano i modelli tabulari con livello di compatibilità 1400.
- Risolto un problema relativo ai progetti multidimensionali limitato a Visual Studio 2017 che poteva impedire il caricamento della finestra di progettazione Progetta aggregazioni.
- Risolto un problema per cui il trascinamento di un elemento nel diagramma vista origine dati multidimensionale di Analysis Services poteva causare un arresto anomalo di Visual Studio 2017.
- Risolto un problema nei progetti di Analysis Services per cui la finestra di dialogo di distribuzione non era sempre in primo piano nella parte superiore di Visual Studio.
- Rimossa l'importazione di Analysis Services dal Marketplace dati come origine dati perché il servizio è stato rimosso.
- Risolto un problema che lasciava disabilitata la finestra di progettazione tabelle dopo aver selezionato Importa nuove tabelle dall'origine dati esistente tramite Esplora modelli tabulari.
- Risolto un problema che poteva lasciare nascoste nel contesto errato le voci Importa da origine dati/Aggiungi origine dati del menu Modello.
- Esperienza migliorata durante la creazione di una misura da Esplora modelli tabulari per evitare che lo stato attivo torni alla colonna usata per creare una misura.
- Quando si passa dall'area di lavoro integrata nei progetti tabulari di Analysis Services a un server dell'area di lavoro esplicito, ora è possibile eseguire la pulizia dei file di database precedenti.
- Risolto un problema nei progetti di modelli tabulari 1400 di Analysis Services per cui lo stato dell'interfaccia utente della casella di controllo Sicurezza a livello di riga veniva inizialmente visualizzato come deselezionato, indipendentemente dallo stato effettivo dell'oggetto sottostante.
- Corretto un arresto anomalo che poteva verificarsi durante l'importazione di file di testo o file di Excel in modelli tabulari con livello di compatibilità 1400 che usano Power Query e generano un'eccezione non gestita.
- Risolto un problema che poteva verificarsi con il cursore della barra di scorrimento nel controllo di modifica della formula DAX, nella finestra di progettazione di modelli tabulari di Analysis Services.
- Risolto un problema che impediva la modifica di un'origine dati di mashup di Power Query quando conteneva un'autenticazione di nome utente/password.
- Risolto un problema che poteva impedire la connessione di un'origine dati quando venivano impostate proprietà aggiuntive nella stringa di connessione.
- Risolto un problema che poteva causare l'arresto anomalo di Visual Studio durante il caricamento di più progetti di modelli tabulari di Analysis Services e la chiusura della seconda finestra di progettazione modelli senza prima interagire con il contenuto della finestra di progettazione.
- Risolto un problema per cui in alcuni casi le modifiche apportate alla formattazione degli indicatori KPI non venivano mantenute.
- Risolto un problema con l'interfaccia utente di Power Query che mostrava lo stato selezionato del menu errato per la visualizzazione o meno della barra della formula.
- Risolto un problema con le origini dati di Power Query nei progetti tabulari con livello di compatibilità 1400 di Analysis Services che poteva causare l'arresto anomalo di Visual Studio quando si selezionava il menu Modifica origine dati da Esplora modelli tabulari.
- Risolto un problema saltuario per cui il caricamento di un modello tabulare 1400 poteva restituire il messaggio di errore *Impossibile caricare il file o l'assembly 'Microsoft.ProBI.MashupLibrary'*.

**Progetti RS**
- Le preferenze utente per lo stato di selezione delle impostazioni relative a Righello e Parametro in RS vengono memorizzate correttamente nelle sessioni.

**Progetti IS**
- Risolto un problema per cui il contenitore ADO/ADO.NET ForEachLoop non veniva visualizzato correttamente.
- Risolto un problema con alcune attività, componenti e procedure guidate non localizzati.
- L'oggetto *TargetServerVersion* più recente è stato modificato da "SQL Server vNext" a "SQL Server 2017".


## <a name="ssdt-171-for-visual-studio-2015"></a>SSDT 17.1 per Visual Studio 2015
Numero di build: 14.0.61705.170

### <a name="whats-new"></a>Novità
**Progetti AS:**
- Gli utenti possono impostare gli hint di codifica per le colonne dell'interfaccia utente nei modelli 1400
- La funzionalità IntelliSense non correlata al modello è ora disponibile in modalità offline
- Esplora modelli tabulari ora contiene un nodo per rappresentare le espressioni M denominate disponibili nel modello (modelli tabulari con livello di compatibilità 1400).
- La funzionalità Selezione utenti di Azure Active Directory, simile alla gestione delle identità e degli accessi del portale di Microsoft Azure, è ora disponibile quando si impostano i membri dei ruoli nei modelli tabulari.

**Progetti di database:**
- Aggiornamento a DacFx 17.1

### <a name="bug-fixes"></a>Correzioni di bug
- Risolto un problema che causava la visualizzazione non corretta del nome del gruppo Finestre di progettazione di Business Intelligence nelle opzioni di Visual Studio in VS2017
- Risolto un problema che poteva causare un arresto anomalo del sistema durante la generazione di una mappa del codice per una soluzione con un progetto report o un progetto di Analysis Services
- Risolti alcuni problemi di integrazione di Power Query nei modelli tabulari con livello di compatibilità 1400 di Analysis Services.
- Risolto un problema nella nuova finestra degli strumenti dell'editor DAX per cui l'operatore di assegnazione non poteva essere su una riga separata durante la definizione di una misura
- Risolto un problema che impediva l'aggiornamento della visualizzazione delle misure tabulari quando si assegnavano nuovi nomi alle misure nella prospettiva
- Aggiornati il motore dell'area di lavoro integrata di Analysis Services e il modello a oggetti tabulare con correzione di una regressione che causava l'esito negativo della distribuzione dei progetti tabulari 1200 contenenti traduzioni al server di Analysis Services in SQL Server 2016
- Corretto un problema di prestazioni che rendeva molto lento il processo di creazione o eliminazione delle nuove origini di dati tabulari 1400
- Risolto un problema che poteva causare l'arresto del rendering del diagramma delle viste origine dati nei modelli multidimensionali se la visualizzazione passava rapidamente da una vista all'altra

## <a name="dacfx-171"></a>DacFx 17.1
- Risolto un problema che si verificava durante la crittografia di una colonna con tabelle ottimizzate per la memoria con altre colonne di identità
- Supporto SQLDOM per l'opzione CATALOG_COLLATION per CREATE DATABASE

## <a name="dacfx-1701"></a>DacFx 17.0.1 
- Corretto un problema dei database con una chiave asimmetrica di un modulo HSM con [argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3132749/sqlpackage-exe-fails-when-extracting-a-database-which-contains-an-asymmetric-key-using-an-ekm-provider) di un provider EKM

## <a name="ssdt-170-for-visual-studio-2015-supports-up-to-sql-server-2017"></a>SSDT 17.0 per Visual Studio 2015 (supporta fino a SQL Server 2017)
Numero di build: 14.0.61704.140

### <a name="whats-new"></a>Novità
**Progetti di database:**
- La modifica di un indice cluster in una vista non bloccherà più la distribuzione
- Le stringhe di confronto dello schema correlate alla crittografia delle colonne usano il nome appropriato invece del nome dell'istanza.   
- È stata aggiunta una nuova opzione della riga di comando a SqlPackage: ModelFilePath.  Questa opzione consente agli utenti esperti di specificare un file model.xml esterno per operazioni di importazione, pubblicazione e scripting   
- L'API DacFx è stato esteso per supportare l'autenticazione universale di Azure AD e il servizio Multi-Factor Authentication (MFA)

**Progetti IS:**
- L'origine OData SSIS e Gestione connessione OData supportano ora la connessione ai feed OData di Microsoft Dynamics AX Online e Microsoft Dynamics CRM Online.
- I progetti SSIS supportano ora la versione del server di destinazione "SQL Server 2017" 
- È stato aggiunto il supporto per Attività di controllo CDC, CDC Splitter e Origine CDC quando la destinazione è SQL Server 2017. 

**Progetti AS:**
- Integrazione di Power Query per Analysis Services (modelli tabulari con livello di compatibilità 1400):
    - DirectQuery è disponibile per SQL Oracle e Teradata se l'utente ha installato driver di terze parti
    - Aggiunta di colonne in base all'esempio in PowerQuery
    - Opzioni di accesso ai dati nei modelli 1400 (proprietà a livello di modello usate dal motore M)
        - Abilita combinazione rapida: il valore predefinito è false, se l'opzione è impostata su true, il motore di mashup ignora i livelli di privacy dell'origine dati quando si combinano i dati
        - Abilita reindirizzamenti legacy: il valore predefinito è false, se l'opzione è impostata su true, il motore di mashup segue i reindirizzamenti HTTP potenzialmente non sicuri.  Ad esempio, un reindirizzamento da un HTTPS a un URI HTTP  
        - Restituisci valori di errore come Null: il valore predefinito è false, se l'opzione è impostata su true, gli errori a livello di cella vengono restituiti come Null. Se è false, viene generata un'eccezione se una cella contiene un errore  
    - Origini dati aggiuntive (origini dati di file) che usano PowerQuery
        - Excel 
        - Testo/CSV 
        - Xml 
        - Json 
        - Cartella 
        - Database di Access 
        - Archiviazione BLOB di Azure 
    - Interfaccia utente localizzata di PowerQuery
- Finestra degli strumenti dell'editor DAX
    - Migliorata l'esperienza di editing DAX per misure, colonne calcolate ed espressioni di righe di dettaglio, disponibile dal menu Visualizza, Altre finestre in SSDT
    - Miglioramenti di parser DAX\IntelliSense


**Progetti RS:**
- È ora disponibile il controllo RVC incorporabile con supporto di SSRS 2016.

### <a name="bug-fixes"></a>Correzioni di bug
**Progetti AS:**
- È stato risolto il problema della priorità dei modelli per i progetti BI in modo che non vengano visualizzati nella parte più alta delle categorie dei nuovi progetti in Visual Studio
- È stato risolto il problema di arresto anomalo di Visual Studio che si verifica in rare circostanze all'apertura di una soluzione SSIS, SSAS o SSRS
- Progetti tabulari: vari miglioramenti e correzioni delle prestazioni per l'analisi DAX e la barra della formula.
- Progetti tabulari: Esplora modelli tabulari non sarà più visibile se non ci sono progetti tabulari di SSAS aperti.
- Progetti multidimensionali: risolto un problema a causa del quale la finestra di dialogo di elaborazione era inutilizzabile in computer con valori DPI alti.
- Progetti tabulari: risolto un problema a causa del quale si verifica un errore in SSDT all'apertura di qualsiasi progetto BI quando SSMS è già aperto. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3100900/ssdt-faults-when-opening-any-bi-project-when-ssms-is-already-open)
- Progetti tabulari: risolto un problema a causa del quale le gerarchie non venivano salvate correttamente nel file bim in un modello 1103. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3105222/vs-2015-ssdt)
- Progetti tabulari: risolto un problema a causa del quale la modalità area di lavoro integrata era consentita nei computer a 32 bit anche se non è supportata.
- Progetti tabulari: risolto un problema a causa del quale il clic su qualsiasi elemento in modalità di semiselezione (ad esempio, digitazione di un'espressione DAX ma clic su una misura) potrebbe causare arresti anomali del sistema.
- Progetti tabulari: risolto un problema a causa del quale la distribuzione guidata reimposta la proprietà .Name del modello su "Model". [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3107018/ssas-deployment-wizard-resets-modelname-to-model)
- Progetti tabulari: risolto un problema a causa del quale la selezione di una gerarchia in Esplora modelli tabulari comporta la visualizzazione delle proprietà anche se non è selezionata la Vista diagramma.
- Progetti tabulari: risolto un problema a causa del quale quando si incolla contenuto nella barra della formula DAX vengono incollati immagini o altri contenuti invece del testo, quando si esegue l'operazione Incolla da particolari applicazioni.
- Progetti tabulari: risolto un problema a causa del quale alcuni vecchi modelli nel livello 1103 non potevano essere aperti a causa della presenza di misure con una definizione specifica.
- Progetti tabulari: risolto un problema a causa del quale non era possibile eliminare sessioni XEvent.
- È stato risolto un problema a causa del quale ogni tentativo di compilare file "smproj" di AS con devenv.com aveva esito negativo
- È stato risolto un problema a causa del quale le modifiche di testo venivano finalizzate con una frequenza eccessiva quando si usava l'IME coreano nei titoli delle schede dei fogli nei modelli tabulari AS
- È stato risolto un problema per cui la funzionalità Intellisense per DAX Related() impediva la corretta visualizzazione delle colonne provenienti da altre tabelle
- È stato migliorato il processo di importazione di un progetto tabulare AS dalla finestra di dialogo del database ordinando l'elenco dei database AS
- È stato risolto un problema a causa del quale, durante la creazione di tabelle calcolate in un modello tabulare AS, le tabelle non venivano elencate come oggetti suggeriti nell'espressione
- È stato risolto un problema che si verificava quando si provava ad aprire modelli AS 1400 usando il server dell'area di lavoro integrata dopo la visualizzazione del codice
- È stato risolto un problema che impediva il corretto funzionamento di alcune origini dati (con nessun supporto per il catalogo iniziale) in determinate circostanze 
- La Distribuzione guidata deve applicare le modifiche alle partizioni di tabelle calcolate anche se è stata abilitata l'opzione per mantenere le partizioni
- È stato risolto un problema a causa del quale la finestra di dialogo Proprietà avanzate in una connessione AS esistente non visualizzava l'elenco completo a meno che non venisse riselezionata
- Risolti alcuni problemi che causavano la visualizzazione di stringhe dell'interfaccia utente incomplete in alcune versioni localizzate
- Risolti alcuni problemi di integrazione di Power Query nei modelli tabulari con livello di compatibilità 1400 di Analysis Services.
- Risolto un problema che causava la visualizzazione non corrette dei modelli di stile della Creazione guidata report
- Risolto un problema della Creazione guidata report che poteva provocare impostazioni non corrette dell'origine dati durante il passaggio da SQL ad AS
- Risolto un problema che causava un errore di compilazione dei progetti di Analysis Services (tabulari) dalla riga di comando (devenv.com\exe)
- Risolto un problema con il parser di misure DAX per visualizzare il colore del testo corretto ed evidenziato quando si usano lettere prima di :=
- Risolto un problema di attivazione di ObjectRefException se i percorsi diventano troppo lunghi nel tentativo di visualizzare tutti i file per il progetto tabulare in modalità area di lavoro integrata
- Risolto un problema della finestra di progettazione dell'origine dati per il provider di dati del client Compact 4.0 che risultava non disponibile
- Risolto un problema che causava un errore quando si tentava di esplorare il modello di data mining di AS in VS2017
- Risolto un problema in un modello multidimensionale di AS in VS2017 che arresta il rendering del diagramma delle viste origine dati dopo la modifica della vista e quindi causa un'eccezione
- Risolto un problema che impediva la visualizzazione in anteprima dei report con una connessione AS in VS2017
 

**Progetti RS:**
- È stato risolto un problema per cui, durante la progettazione di report in SSDT, la visualizzazione ad albero di parametri, origini dati e set di dati si comprimeva quando veniva apportata la maggior parte delle modifiche 
- Risolto un problema a causa del quale con Salva viene salvata la versione di RDL e non la versione più recente.
- Risolto un problema a causa del quale SSDT RS esegue il backup dei file quando il backup è disattivato e vari altri problemi.
- Risolto un problema in Generatore Report a causa del quale viene visualizzato un errore quando si fa clic "Dividi celle". [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3101818/ssdt-2015-ssrs-designer-error-by-matrix-cell-split)
- Risolto un problema a causa del quale la memorizzazione nella cache potrebbe causare dati errati in un report. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3102158/ssdtbi-14-0-60812-report-preview-data-is-frequently-wrong-due-to-bad-caching)

**Progetti IS:**
- Risolto un problema a causa del quale l'impostazione run64bitruntime non viene mantenuta.
- Risolto un problema a causa del quale DataViewer non salva le colonne visualizzate.
- Risolto un problema a causa del quale Parti del pacchetto nasconde le annotazioni. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3106624/package-parts-hide-annotations)
- Risolto un problema a causa del quale Parti del pacchetto ignora layout e annotazioni in flussi di dati. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3109241/package-parts-discard-data-flow-layouts-and-annotations)
- Risolto un problema a causa del quale si verifica un arresto anomalo di SSDT quando si importa un progetto da SQL Server.
- Risolto un problema con l'oggetto TimeoutInMinutes dell'attività File system Hadoop che veniva impostato sul valore predefinito 10 dopo l'apertura del pacchetto SSIS salvato e in fase di esecuzione.

**Progetti di database:**
- È stata ripristinata l'impostazione per IgnoreColumnOrder nella distribuzione DACPAC di SSDT [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/1221587/ssdt-dacpac-deploy-add-setting-back-in-for-ignorecolumnorder)
- Non è possibile compilare SSDT se viene usato STRING_SPLIT [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/2906200/ssdt-failing-to-compile-if-string-split-is-used)
- È stato risolto un problema per cui DeploymentContributors hanno accesso al modello pubblico ma lo schema sottostante non è stato inizializzato [Problema Github](https://github.com/Microsoft/DACExtensions/issues/8)
- È stata introdotta una correzione temporanea di DacFx per il posizionamento di FILEGROUP
- È stato risolto l'errore "Riferimento non risolto" per sinonimi esterni 
- Always Encrypted: la crittografia online non disabilita il rilevamento di modifiche al momento dell'annullamento e non funziona correttamente se il rilevamento di modifiche non è stato azzerato prima dell'avvio della crittografia


## <a name="ssdt-165-for-visual-studio-2015-supports-up-to-sql-server-2016"></a>SSDT 16.5 per Visual Studio 2015 (supporta fino a SQL Server 2016)
Data di rilascio: 20 ottobre 2016

Numero di build: 14.0.61021.0

**Novità**


### <a name="connection-improvements"></a>Miglioramenti apportati alle connessioni

* La nuova casella di ricerca nella scheda **Sfoglia** permette di filtrare i server locali, i server di rete e i database SQL di Azure. La casella è utile quando questi elenchi includono un numero elevato di server o di database.
* La scheda **Cronologia** include opzioni di menu di scelta rapida per aggiungere o rimuovere preferiti e una nuova opzione per rimuovere le connessioni dalla cronologia.

### <a name="sqlpackage-and-dacfx-api-improvements"></a>Miglioramenti apportati a SqlPackage e alle API DacFx

Usando SqlPackage.exe e le API DacFx, è ora possibile generare un report di distribuzione e uno script di distribuzione ed eseguire la pubblicazione in un database, il tutto tramite una sola azione. Questa novità offre un notevole risparmio di tempo a chiunque preferisca mantenere un report degli elementi pubblicati durante una distribuzione. Un altro vantaggio consiste nel fatto che per scenari Azure vengono creati script separati per il database master e per il database di destinazione della distribuzione. Nelle versioni precedenti viene creato un singolo script, che non è utile per distribuzioni ripetute.

Per le azioni di pubblicazione e di scripting di SqlPackage, sono stati aggiunti due nuovi argomenti.

* DeployScriptPath (nome breve: dsp). Percorso facoltativo in cui scrivere lo script di distribuzione. Per una distribuzione di Azure, se sono disponibili comandi TSQL per creare o modificare il database, viene scritto uno script master nello stesso percorso, ma con "Filename_Master.sql" come nome del file di output.
* DeployReportPath (nome breve: drp). Percorso facoltativo in cui scrivere il report di distribuzione.

Per l'azione di scripting, è necessario usare gli argomenti del percorso di output esistenti o i nuovi argomenti specifici dello script o del report, ma non entrambi.

Esempio di utilizzo:

**Azione di pubblicazione**

```Sqlpackage.exe /a:Publish /tsn:(localdb)\ProjectsV13 /tdn:MyDatabase /deployscriptpath:”My\DeployScript.sql” /deployreportpath:”My\DeployReport.xml”```

**Azione di scripting**

```Sqlpackage.exe /a:Script /tsn:(localdb)\ProjectsV13 /tdn:MyDatabase /deployscriptpath:”My\DeployScript.sql” /deployreportpath:”My\DeployReport.xml”```

In DacFx sono state aggiunte due nuove API: DacServices.Publish() e DacServices.Script(). Le API supportano anche l'esecuzione di azioni di pubblicazione+scripting+creazione di report in un'unica operazione. Esempio di utilizzo:

```
DacServices service = new DacServices(connectionString);
using(DacPackage package = DacPackage.Load(@"C:\My\db.dacpac")) {
var options = new PublishOptions() {
    GenerateDeploymentScript = true, // Should a deployment script be created?
    GenerateDeploymentReport = true, // Should an xml deploy report be created?
    DatabaseScriptPath = @"C:\My\OutputScript.sql", // optional path to save script to
    MasterDbScriptPath = @"C:\My\OutputScript_Master.sql", // optional path to save master script to
    DeployOptions = new DacDeployOptions()
};

// Call publish and receive deployment script & report in the results
PublishResult result = service.Publish(package, "TargetDb", options);
Console.WriteLine(result.DatabaseScript);
Console.WriteLine(result.MasterDbScript);
Console.WriteLine(result.DeploymentReport);

// Call script and receive deployment script & report in results
result = service.Script(package, "TargetDb", options);
Console.WriteLine(result.DatabaseScript);
Console.WriteLine(result.MasterDbScript);
Console.WriteLine(result.DeploymentReport);
```

**Analysis Services e Reporting Services**

Il parser DAX della finestra di progettazione tabulare di SSAS ha prestazioni migliori quando si usano espressioni DAX di grandi dimensioni.
Per altre informazioni, vedere il [post di blog su Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2016/09/20/introducing-integrated-workspace-mode-for-sql-server-data-tools-for-analysis-services-tabular-projects-ssdt-tabular/).

### <a name="fixed--improved-this-month"></a>Correzioni/miglioramenti di questo mese

**Strumenti di database**

* [Bug Connect 3055711](https://connect.microsoft.com/SQLServer/feedback/details/3055711/columns-cannot-be-selected-from-cross-apply-openjson-with-explicit-schema): le colonne non possono essere selezionate da CROSS APPLY OPENJSON con uno schema esplicito
* Correzione: problema relativo agli indici di tabella della cronologia generata automaticamente, per cui DacFx elimina l'indice alla ridistribuzione
* Correzione: problema relativo al parser batch DacFx che non esamina i caratteri "]" di parentesi preceduti da un carattere di escape, impedendo la riuscita della pubblicazione
* Miglioramento: SqlPackage include ora descrizioni per ogni azione nell'output della Guida
* Correzione: l'opzione "Memorizza password" nella finestra di dialogo di connessione non viene preservata durante la modifica di opzioni avanzate e durante la modifica di una stringa di connessione salvata in Pubblica, Confronto schema e altri file
* Correzione: per le connessioni visualizzate nella scheda Cronologia con IntegratedAuthentication=true, il campo Autenticazione nelle proprietà di connessione viene lasciato vuoto. Il campo indica ora "Autenticazione di Windows" come previsto
* Correzioni: le modifiche apportate alle impostazioni Intellisense di SQL Server Tools in Strumenti -> Opzioni -> Editor di testo non vengono preservate
* Miglioramento: il pulsante Aggiungi/Rimuovi nella scheda Cronologia della finestra di dialogo di connessione è ora più compatto, riducendo la probabilità che venga visualizzata una barra di scorrimento
* Correzione: sono stati corretti diversi problemi di accessibilità nella finestra di connessione.

**Analysis Services e Reporting Services**

* Correzione di un problema nella finestra di progettazione tabulare di SSDT AS per cui facendo clic sul cursore della barra di scorrimento nella griglia dei dati, si verifica un arresto anomalo in determinate situazioni
* Correzione di un problema per cui l'opzione per rappresentare la connessione come utente corrente nella finestra di progettazione tabulare di SSDT AS non è disponibile
* Correzione di un problema nella finestra di progettazione tabulare di SSDT AS per cui l'eccessiva espansione della barra della formula può impedire la riapertura del progetto
* Correzione di un arresto anomalo nella finestra di progettazione tabulare di SSDT AS che si verifica alla pressione di un pulsante con la scheda Tabella selezionata
* Correzione di un problema nei progetti di SSDT AS per cui l'opzione Analizza in Excel non si connette alle versioni server di Analysis Services di livello inferiore

**Servizio di integrazione**

* È stato corretto il bug Connect  [1608896](https://connect.microsoft.com/SQLServer/feedback/details/1608896/move-multiple-integration-service-package-tasks) relativo allo spostamento di più attività pacchetto del servizio di integrazione





## <a name="ssdt-164-for-visual-studio-2015-for-sql-server-2016"></a>SSDT 16.4 per Visual Studio 2015 (per SQL Server 2016)
Data di rilascio: 20 settembre 2016

Numero di build: 14.0.60918

**Novità**

L'opzione Confronto schema è ora supportata in SqlPackage.exe e nell'API DacFx. Per informazioni dettagliate, vedere  [Schema Compare in SqlPackage and the Data-Tier Application Framework](https://blogs.msdn.microsoft.com/ssdt/2016/09/20/schema-compare-in-sqlpackage-and-the-data-tier-application-framework-dacfx/) (Confronto schema in SqlPackage e in DacFx).

**Analysis Services - Modalità area di lavoro integrata per SSDT tabulare (SSAS)**

SSDT tabulare include ora un'istanza SSAS interna che viene avviata automaticamente in background se è abilitata la modalità area di lavoro integrata per poter aggiungere e visualizzare tabelle, colonne e dati nella finestra di progettazione dei modelli, senza dover fornire un'istanza del server dell'area di lavoro esterna. La modalità Area di lavoro integrata non modifica il modo in cui SSDT tabulare gestisce un server e un database dell'area di lavoro. Ciò che cambia è la posizione in cui SSDT tabulare ospita il database dell'area di lavoro. Per abilitare la modalità area di lavoro integrata, selezionare l'opzione Area di lavoro integrata nella finestra di dialogo Progettazione modelli tabulari visualizzata durante la creazione di un nuovo progetto tabulare. Per progetti tabulari esistenti che usano attualmente un server dell'area di lavoro esplicita, è possibile passare alla modalità area di lavoro integrata impostando il parametro Modalità area di lavoro integrata su True nella finestra Proprietà, visualizzata quando si seleziona il file Model.bim in Esplora soluzioni. Per informazioni dettagliate, vedere il [post di blog su Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2016/09/20/introducing-integrated-workspace-mode-for-sql-server-data-tools-for-analysis-services-tabular-projects-ssdt-tabular/).

**Aggiornamenti e correzioni**
**Strumenti di database:**

- [Problema Connect 3087775](https://connect.microsoft.com/SQLServer/feedback/details/3087775): tabelle temporali interrotte nell'aggiornamento di luglio di Visual Studio Data Tools 14.0.60629.0, messaggio "Il valore non può essere Null. Nome parametro: reportedElement"
- [Problema Connect 1026648](https://connect.microsoft.com/SQLServer/feedback/details/1026648): IsPersistedNullable viene visualizzato in modo diverso in un confronto di SSDT
- [Problema Connect 2054735](https://connect.microsoft.com/SQLServer/feedback/details/2054735): l'identità viene reimpostata quando si importa un file BACPAC
- [Problema Connect 2900167](https://connect.microsoft.com/SQLServer/feedback/details/2900167): l'esecuzione di unit test di SSDT tralascia i file temporanei
- [Problema Connect 1807712](https://connect.microsoft.com/SQLServer/feedback/details/1807712): problema di compatibilità con le versioni precedenti - AppLocal e Nugetization

**Analysis Services e Reporting Services**

* Correzione di un problema in SSDT per cui i popup dei suggerimenti per gli errori sono di intralcio durante la modifica di formule DAX per colonne calcolate DirectQuery.
* Correzione di un problema nella griglia tabulare di SSDT AS per cui l'icona dell'indicatore KPI non appare nella griglia delle misure quando il fattore di scala di Windows è impostato su un valore DPI alto maggiore del 200%.
* Correzione di un problema in SSDT AS per cui incollando dati di tabella di grandi dimensioni il progetto tabulare non risponde.
* Correzione di un problema nell'editor di modelli tabulari di SSDT AS per contrassegnare il modello in modo da indicare che è necessario salvare le modifiche quando si rinomina il nome descrittivo della connessione.
* Correzione di un problema nei progetti tabulari di SSDT AS per cui la larghezza delle colonne nella finestra di dialogo Gestisci relazioni non può essere ridimensionata.
* Correzione di un problema nei modelli tabulari di livello 1200 di SSDT AS per cui incollando dati da Excel con impostazioni locali, ad esempio il tedesco, la virgola non viene considerata il separatore decimale nel modo corretto.
* Correzione di un problema in progetti di SSDT AS con alcuni set di icone degli indicatori KPI che possono generare l'errore "Non è stato possibile recuperare i dati per questo oggetto visivo".
* Correzione di un problema per cui la finestra delle proprietà di un progetto di SSDT AS non viene ancorata correttamente se ridimensionata con scala con valori DPI alti.
* Correzione di un problema nei progetti di SSDT AS che può causare un errore durante l'aggiornamento di determinati modelli con tabelle incollate.
* Correzione di un problema in SSDT AS per cui incollando righe del foglio completo da Excel l'operazione è molto lenta e crea molte colonne indesiderate.
* Correzione di un problema in SSDT AS per cui l'analisi e l'evidenziazione di espressioni DataTable statiche di grandi dimensioni sono risultano davvero molto lente o appaiono bloccate.
* Correzione di un problema in SSDT AS relativo all'aggiunta di misure e valori KPI alla prospettiva corrente selezionata nell'editor.
* Correzione di un problema in SSDT per cui l'importazione di dati in un progetto di Analysis Services da SQL Azure non supporta tipi di schema diversi da "dbo".



## <a name="ssdt-163-for-visual-studio-2015-for-sql-server-2016"></a>SSDT 16.3 per Visual Studio 2015 (per SQL Server 2016)
Data di rilascio: 15 agosto 2016

Numero di build: 14.0.60812.0  

**Novità**

- **Controllo e numerazione delle versioni:** le versioni sono ora contrassegnate numericamente invece che in base al mese. Questo comportamento è allineato ai nuovi criteri di SSMS e semplifica i casi in cui sono disponibili più versioni o hotfix in un mese. Questa versione è la 16.3, che significa il terzo aggiornamento dopo la versione RTM. Qualsiasi hotfix avrà il numero di versione 16.3.1 e così via, con il prossimo aggiornamento (previsto per il mese prossimo) specificato come 16.4.
- **Analysis Services - Esplora modelli tabulari:** Esplora modelli tabulari permette di spostarsi in modo pratico tra i diversi oggetti di metadati in un modello, tra cui origini, tabelle, misure e relazioni. Questa funzionalità viene implementata come finestra di strumenti separata, che può essere visualizzata aprendo il menu Visualizza in Visual Studio, scegliendo Altre finestre e quindi facendo clic su Esplora modelli tabulari. La finestra Esplora modelli tabulari viene visualizzata per impostazione predefinita nell'area di Esplora soluzioni in una scheda separata. Esplora modelli tabulari organizza gli oggetti di metadati in una struttura ad albero molto somigliante allo schema per un modello tabulare 1200 e include molte più funzionalità.
- **Strumenti di database - Always Encrypted**: questa versione include nuove finestre di dialogo di [gestione di chiavi Always Encrypted](../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md) per aggiungere facilmente chiavi master della colonna o chiavi di crittografia della colonna al progetto del database o a un database attivo in Esplora oggetti di SQL Server. Questa versione supporta i certificati inclusi nell'archivio certificati di Windows. Nelle prossime versioni saranno supportati anche Azure Key Vault e provider CNG.
    - Durante la creazione della chiave master della colonna o della chiave di crittografia della colonna, è possibile che le modifiche non vengano visualizzate in Esplora oggetti di SQL Server immediatamente dopo aver fatto clic su Aggiorna database. Per risolvere questo problema, aggiornare il nodo del database in Esplora oggetti di SQL Server.
    - Se si prova a crittografare una colonna in una tabella con dati da Esplora oggetti di SQL Server, potrebbe verificarsi un errore. Questa funzionalità è attualmente supportata solo in progetti di database di SSDT e in SSMS. Il supporto per Esplora oggetti di SQL Server verrà abilitato in una versione successiva.


**Aggiornamenti e correzioni**
* **Strumenti di database:**
    - **SSDT:**
        - Bug Connect 1898001[: correzione di un problema di descrizione delle colonne con limite di 128 caratteri](https://connect.microsoft.com/SQLServer/feedback/details/1898001/column-description-limited-to-128-characters).
        - Correzione di un problema per cui la pubblicazione di un database da Visual Studio non viene applicata alla proprietà DatabaseServiceObjective nel codice XML del profilo di pubblicazione.
        - Bug Connect 2900167 [Correzione di un problema relativo agli unit test che lascia erroneamente i file temporanei](https://connect.microsoft.com/SQLServer/feedback/details/2900167/running-ssdt-unit-tests-leaves-temp-files-behind).
        - Correzione di un problema per cui la casella combinata Periodo di conservazione in Impostazioni database è troncata.
        - Correzione di un problema di mancata verifica di una vecchia password vuota nelle proprietà dei progetti SQL CLR durante la modifica della password.
    - **DACFx:**
        - Correzione di un problema per cui il livello di compatibilità di DACFx non viene aggiornato per l'errore SqlAzureV12.
        - Correzione di un problema per cui la proprietà IsAutoGeneratedHistoryTable viene erroneamente esclusa dal confronto tra i modelli.

- **Analysis Services e Reporting Services**
    - **SSDT:**
        - Correzione di un problema per cui un modello tabulare non può essere salvato quando viene persa la connessione al server.
        - Correzione di un problema per cui SSDT inizia a non rispondere a causa di un possibile errore di ciclo infinito in Analysis Services.
        - Correzione di un problema relativo alle espressioni DAX che provoca comportamenti incoerenti in base al modo in cui si esegue il commit dell'espressione.
        - Correzione di un problema di arresto anomalo di Visual Studio durante la creazione di indicatori KPI.
        - Correzione di un problema per cui vengono generati report non validi per SQL Server 2008 R2, 2012 e 2014.
        - Correzione di un problema relativo all'ordine della gerarchia che provoca un errore di ciclo infinito per un progetto DWPRO.
        - Correzione di un problema di RDL di Reporting Services per cui il downgrade di RDL richiede una ricompilazione completa che confonde l'utente.
        - Correzione di un problema relativo agli indicatori KPI per cui la funzionalità Nascondi a strumenti client non ha alcun effetto.
        

 
  
## <a name="ssdt-july-for-visual-studio-2015-for-sql-server-2016"></a>SSDT July per Visual Studio 2015 (per SQL Server 2016)  
Data di rilascio: 30 giugno 2016  
  
Numero di build: 14.0.60629.0  
  
**Novità**  
* **Supporto per Always Encrypted:** per i database che contengono colonne Always Encrypted, questa versione aggiunge supporto completo per Always Encrypted tramite le API di base e l'utilità della riga di comando (SqlPackage.exe). È possibile compilare e pubblicare progetti di database con supporto completo per tutte le funzionalità di Always Encrypted.  
* **Supporto migliorato per tabelle temporali:** l'esperienza è stata semplificata scollegando le tabelle temporali prima delle modifiche e ricollegandole al termine delle modifiche. Questo significa che le tabelle temporali hanno parità con altri tipi di tabelle (standard, in memoria) in termini di operazioni supportate. 
* **Modifiche apportate all'installazione e a SqlPackage.exe:** modifiche apportate per isolare SSDT dagli aggiornamenti del motore di SQL Server e di SSMS. Per informazioni dettagliate, vedere [Changes to SSDT and SqlPackage.exe installation and updates](https://blogs.msdn.microsoft.com/ssdt/2016/06/30/changes-to-ssdt-and-sqlpackage-exe-installation-and-updates/) (Modifiche apportate all'installazione e agli aggiornamenti di SSDT e SqlPackage.exe).

 

**Aggiornamenti e correzioni**
* **Strumenti di database:**
    * Da questa versione in poi SSDT non disabiliterà più Transparent Data Encryption (TDE) in un database. Poiché nelle versioni precedenti l'opzione di crittografia predefinita nelle impostazioni di database di un progetto è disabilitata, comporta la disattivazione della crittografia. Con questa correzione, la crittografia può essere abilitata, ma mai disabilitata durante la pubblicazione. 
    * Sono stati aumentati il numero di tentativi e la resilienza per connessioni del database SQL di Azure durante la connessione iniziale.
    * Se il filegroup predefinito non è PRIMARY, l'importazione e/o la pubblicazione in Azure V12 non riesce. Questa impostazione viene ora ignorata durante la pubblicazione.
    * Correzione di un problema per cui durante l'esportazione di un database con un oggetto con identificatore delimitato attivato la convalida dell'esportazione può non riuscire in alcuni casi.
    * Correzione di un problema per cui viene aggiunta erroneamente l'opzione TEXTIMAGE_ON per la creazione di tabelle hekaton in cui non è consentita.
    * Correzione di un problema per cui l'esportazione impiega molto tempo a esportare grandi quantità di dati a causa del fatto che una scrittura nel file model.xml dopo il completamento della fase dei dati provoca la riscrittura del file BACPAC.
    * Correzione di un problema per cui gli utenti non vengono visualizzati nella cartella Sicurezza per connessioni Azure SQL DW e APS.


 * **Analysis Services e Reporting Services:**
    * Correzione di un problema SxS con il provider MSOLAP OLEDB per cui viene installato solo il provider a 32 bit, con un impatto sulla connessione di Excel 2016 a 64 bit a SQL Server 2014. Il problema non viene riprodotto con installazioni di ClickOnce da Office365, ma solo per l'installazione MSI di Excel.
    * Correzione di un problema per migliorare l'affidabilità in un caso limite durante l'aggiornamento di un modello di Analysis Services con tabelle incollate dal livello di compatibilità 1103 al 1200, che può restituire l'errore "La relazione utilizza un ID colonna non valido".
    * Correzione di un problema SxS per cui quando SSDT-BI 2013 si trova nello stesso computer non è più possibile importare dati in un modello di Analysis Services dopo la disinstallazione di SSDT 2015 (impostazione del Registro di sistema per le cartridge condivise).
    * Affidabilità migliorata per risolvere problemi/arresti anomali in caso di perdita della connessione al motore di Analysis Services, ovvero SSDT lasciato attivo durante la notte e server Analysis Services riciclato o altri casi in cui la connessione viene temporaneamente persa. 
    * Correzione dei problemi relativi all'apertura delle finestre di dialogo su schermate diverse da Visual Studio in scenari a più monitor. 
    * Supporto corretto/abilitato per incollare da tabelle HTML (dati della griglia) in tabelle incollate di un modello di Analysis Services. 
    * Correzione di un problema per cui l'aggiornamento di una tabella incollata vuota nel livello 1200 non riesce (usata solo come tabella contenitore per misure). 
    * Correzione di un problema di aggiornamento del modello tabulare di Analysis Services con tabelle incollate nel livello 1200 per risolvere un problema del motore di Analysis Services con oggetti CalcTable, usati per le tabelle incollate nel livello 1200, in modo da eseguire un'elaborazione completa nelle nuove tabelle calcolate dopo l'aggiornamento. 
    * Correzione di un problema per cui l'annullamento della creazione di una nuova tabella calcolata del modello 1200 di Analysis Services con un'espressione DAX incompleta può arrestarsi in modo anomalo. 
    * Correzione di un problema di importazione di un modello 1200 dal server Analysis Services in un progetto di SSDT AS quando il nome del database e il nome di una tabella sono uguali. 
    * Correzione di un problema relativo alla modifica di una misura KPI in un modello tabulare 1103. 
    * Correzione di un'eccezione relativa a un riferimento a un oggetto non impostato generata quando si incolla una misura KPI nella griglia per un modello 1200 di Analysis Services. 
    * Correzione di un problema per cui una colonna in una tabella calcolata non può essere eliminata dalla vista diagramma nei modelli 1200. 
    * Correzione di un'eccezione relativa a un riferimento a un oggetto non impostato durante la visualizzazione delle proprietà del file di progetto model.bim in visualizzazione codice. 
    * Correzione di un problema per cui quando si incollano dati nella griglia di un modello di Analysis Services per creare una tabella incollata, vengono restituiti valori non corretti nelle impostazioni locali che usano la virgola come separatore decimale. 
    * Correzione di un problema relativo all'apertura di un progetto di SQL 2008 RS in SSDT quando si sceglie di non aggiornarlo. 
    * Correzione di un problema nell'interfaccia utente delle tabelle calcolate dei modelli con livello di compatibilità 1200 durante l'uso della formattazione predefinita per il tipo di colonna, per permettere la modifica del tipo di formattazione dall'interfaccia utente. 
    

## <a name="ssdt-june-for-visual-studio-2015-for-sql-server-2016"></a>SSDT June per Visual Studio 2015 (per SQL Server 2016)  
Data di rilascio: 1 giugno 2016  
  
Numero di build: 14.0.60525.0 

È ora disponibile la versione di SSDT con disponibilità generale. L'aggiornamento alla versione con disponibilità generale di SSDT per giugno 2016 aggiunge il supporto per gli aggiornamenti più recenti di SQL Server 2016 RTM e diverse correzioni di bug. Per informazioni dettagliate, vedere [SQL Server Data Tools GA update for June 2016](https://blogs.msdn.microsoft.com/ssdt/2016/06/01/sql-server-data-tools-ga-update-for-june-2016/) (Aggiornamento della versione disponibile a livello generale di SQL Server Data Tools per giugno 2016).

  
  
## <a name="additional-resources"></a>Risorse aggiuntive
  
[Scaricare SQL Server Data Tools &#40;SSDT&#41;](../ssdt/download-sql-server-data-tools-ssdt.md)  
[Versioni precedenti di SQL Server Data Tools &#40;SSDT e SSDT-BI&#41;](../ssdt/previous-releases-of-sql-server-data-tools-ssdt-and-ssdt-bi.md)  
[Novità del motore di database](https://msdn.microsoft.com/library/bb510411.aspx)  
[Novità di Analysis Services](../analysis-services/what-s-new-in-analysis-services.md)  
[Novità di Integration Services](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)  
  
