---
title: Log delle modifiche per SQL Server Data Tools (SSDT) | Microsoft Docs
ms.custom: 
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssdt
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b071f8b8-c8e5-44e0-bbb6-04804dd1863a
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 5bd0e1d3955d898824d285d28979089e2de6f322
ms.openlocfilehash: 243d2e6187a58554cee80066912de7dfcc0c52fc
ms.contentlocale: it-it
ms.lasthandoff: 05/20/2017

---
# <a name="changelog-for-sql-server-data-tools-ssdt"></a>Log delle modifiche per SQL Server Data Tools (SSDT)
È il registro delle modifiche per [SQL Server Data Tools (SSDT) per Visual Studio 2015](https://msdn.microsoft.com/library/mt204009.aspx).  
  
I messaggi dettagliati sulle caratteristiche nuove e modificate, visitare [blog del Team di SSDT](https://blogs.msdn.microsoft.com/ssdt/)

## <a name="ssdt-171"></a>SSDT 17,1
Numero di build: 14.0.61705.170

### <a name="whats-new"></a>Novità
**Progetti AS:**
- Gli utenti possono impostare la codifica di hint per le colonne nell'interfaccia utente nei modelli 1400
- IntelliSense non correlati al modello è ora disponibile in modalità offline
- Esplora modelli tabulari ora contiene un nodo per rappresentare denominate espressioni M disponibili nel modello (modelli tabulari a livello di compatibilità di 1400)
- Azure Active Directory selezione utenti simile a una pagina IAM del portale di Microsoft Azure disponibili quando si imposta i membri del ruolo nei modelli tabulari

**Progetti di database:**
- Aggiornamento di DacFx 17,1

### <a name="bug-fixes"></a>Correzioni di bug
- Risolto un problema in cui il nome del gruppo di finestre di progettazione di Business Intelligence è stato visualizzato in modo non corretto in Opzioni di Visual Studio in VS2017
- Risolto un problema in cui può verificarsi un arresto anomalo la generazione di una mappa del codice per una soluzione con un progetto di Report o come progetto
- Un numero fisso di problemi con l'integrazione di PowerQuery per i modelli tabulari di Analysis Services 1400 a livello di compatibilità
- Risolto un problema nel nuovo editor DAX finestra degli strumenti in cui l'operatore di assegnazione non è stato in una riga distinta quando si definisce una misura
- Risolto un problema che impedisce la visualizzazione tabulare misura dall'aggiornamento durante la ridenominazione delle misure nella prospettiva
- Aggiornato motore integrato dell'area di lavoro di Analysis Services e modello a oggetti tabulare che corregge un test di regressione che ha causato contenente traduzioni avrà esito negativo nei progetti tabulari 1200 distribuire nel server SQL Server 2016 Analysis Services
- Correzione di un problema di prestazioni che ha effettuato creation\deletion di nuove origini di dati tabulare 1400 molto lente
- Risolto un problema in cui il diagramma vista origine dati nei modelli multidimensionali Impossibile arresta rendering se la modifica di visualizzazione rapidamente tra diverse viste origine dati

## <a name="dacfx-171"></a>17.1 DacFx
- Risolto un problema durante la crittografia di una colonna con le tabelle con ottimizzazione per la memoria con altre colonne di identità
- Supporto per l'opzione CATALOG_COLLATION per creare DATABASE SQLDOM

## <a name="dacfx-1701"></a>DacFx 17.0.1 
- Risolvere per problema con i database con una chiave asimmetrica da un modulo HSM, con un provider EKM [voce Connect](https://connect.microsoft.com/SQLServer/feedback/details/3132749/sqlpackage-exe-fails-when-extracting-a-database-which-contains-an-asymmetric-key-using-an-ekm-provider)

## <a name="ssdt-170-supports-up-to-sql-server-2017"></a>SSDT 17,0 (supporta fino a 2017 di SQL Server)
Numero di build: 14.0.61704.140

### <a name="whats-new"></a>Novità
**Progetti di database:**
- Che modifica un indice cluster in una vista non è più bloccherà la distribuzione
- Le stringhe di confronto dello schema correlate alla crittografia delle colonne useranno il nome appropriato invece del nome dell'istanza.   
- È stata aggiunta una nuova opzione della riga di comando a SqlPackage: ModelFilePath.  Ciò consente agli utenti esperti specificare un file esterno model.xml per l'importazione, la pubblicazione e operazioni di scripting   
- L'API DacFx è stato esteso per supportare l'autenticazione di Azure AD universale e multi-factor authentication (MFA)

**Progetti IS:**
- L'origine OData SSIS e Gestione connessione OData supportano ora la connessione ai feed OData di Microsoft Dynamics AX Online e Microsoft Dynamics CRM Online.
- Progetto SSIS supporta ora la versione di server di destinazione di "SQL Server 2017" 
- Supporto per le attività di controllo CDC, barra di divisione CDC e l'origine CDC quando la destinazione SQL Server 2017. 

**Progetti AS:**
- Integrazione di Analysis Services PowerQuery (modelli tabulari a livello di compatibilità di 1400):
    - DirectQuery è disponibile per SQL Oracle, Teradata e se l'utente ha installato il driver di terze parti 3rd
    - Aggiungere colonne dall'esempio in PowerQuery
    - Dati di accedere alle opzioni nei modelli 1400 (proprietà a livello di modello utilizzato dal motore M)
        - Abilitare la combinazione rapida (valore predefinito è false, se impostata su true, il mashup ignorerà livelli di privacy di origine dati quando si combinano dati)
        - Abilitare Legacy reindirizza (valore predefinito è false, quando è impostato su true, il motore mashup seguirà reindirizzamenti HTTP potenzialmente non sicuri.  Ad esempio, un reindirizzamento da HTTPS a un URI HTTP)  
        - Restituire i valori di errore come Null (valore predefinito è false, quando è impostata su true, errore a livello di cella verrà restituito come null. Se è false, verrà generata un'eccezione è una cella contiene un errore)  
    - Origini dati aggiuntive (origini dati di file) utilizzando PowerQuery
        - Excel 
        - Testo/CSV 
        - Xml 
        - JSON 
        - Cartella 
        - Database di Access 
        - Archiviazione BLOB Azure 
    - Interfaccia utente localizzata PowerQuery
- Finestra degli strumenti Editor di DAX
    - DAX una migliore esperienza per le misure, colonne calcolate e le espressioni di righe di dettaglio, disponibile tramite la vista, dal menu di altre finestre SSDT di modifica
    - Miglioramenti per parser\Intellisense DAX


**Progetti RS:**
- È ora disponibile il controllo RVC incorporabile con supporto di SSRS 2016.

### <a name="bug-fixes"></a>Correzioni di bug
**Progetti AS:**
- È stato risolto il problema della priorità dei modelli per i progetti BI in modo che non vengano visualizzati nella parte più alta delle categorie dei nuovi progetti in Visual Studio
- È stato risolto il problema di arresto anomalo di Visual Studio che si verifica in rare circostanze all'apertura di una soluzione SSIS, SSAS o SSRS
- Progetti tabulari: vari miglioramenti e correzioni delle prestazioni per l'analisi DAX e la barra della formula.
- Progetti tabulari: Esplora modelli tabulari non sarà più visibile se non ci sono progetti tabulari di SSAS aperti.
- Progetti multidimensionali: risolto un problema a causa del quale la finestra di dialogo di elaborazione era inutilizzabile in computer con valori DPI alti.
- Progetti tabulari: risolto un problema a causa del quale si verifica un errore in SSDT all'apertura di qualsiasi progetto BI quando SSMS è già aperto. [Argomento Connect](http://connect.microsoft.com/SQLServer/feedback/details/3100900/ssdt-faults-when-opening-any-bi-project-when-ssms-is-already-open)
- Progetti tabulari: risolto un problema a causa del quale le gerarchie non venivano salvate correttamente nel file bim in un modello 1103. [Argomento Connect](http://connect.microsoft.com/SQLServer/feedback/details/3105222/vs-2015-ssdt)
- Progetti tabulari: risolto un problema a causa del quale la modalità area di lavoro integrata era consentita nei computer a 32 bit anche se non è supportata.
- Progetti tabulari: risolto un problema a causa del quale il clic su qualsiasi elemento in modalità di semiselezione (ad esempio, digitazione di un'espressione DAX ma clic su una misura) potrebbe causare arresti anomali del sistema.
- Progetti tabulari: risolto un problema a causa del quale la distribuzione guidata reimposta la proprietà .Name del modello su "Model". [Argomento Connect](http://connect.microsoft.com/SQLServer/feedback/details/3107018/ssas-deployment-wizard-resets-modelname-to-model)
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
- Alcuni problemi sono stati risolti con le stringhe dell'interfaccia utente incomplete visualizzate in alcune versioni localizzate
- Un numero fisso di problemi con l'integrazione di PowerQuery a livello di compatibilità 1400 come modelli tabulari
- Risolto un problema con i modelli di stile Creazione guidata Report non venga visualizzato correttamente
- Risolto un problema con la creazione guidata Report che possono portare a impostazioni origine dati non corretti quando si passa da SQL a AS
- Risolto un problema che causa un errore di compilazione progetto di Analysis Services (tabulare) dalla riga di comando (devenv.com\exe)
- Risolto un problema con il parser misura DAX per visualizzare il colore del testo evidenziato e corretto quando si avvia con lettere prima: =
- Risolto un problema di attivazione di un ObjectRefException se i percorsi sono troppo lunghi il tentativo di visualizzare tutti i file di progetto tabulare in modalità integrata dell'area di lavoro
- Risolto un problema con la finestra di progettazione origine dati per Provider di dati a Client Compact 4.0 in cui sono state visualizzate non disponibile
- Risolto un problema che ha causato un errore durante il tentativo di esplorare il modello di data mining in VS2017
- Risolto un problema in un modello multidimensionale in VS2017 in cui si arresta il rendering dopo la modifica di viste diagramma vista origine dati e quindi raggiunge un'eccezione
- Risolto un problema di visualizzazione in anteprima i report con una connessione AS non è riuscita a VS2017
 

**Progetti RS:**
- È stato risolto un problema per cui, durante la progettazione di report in SSDT, la visualizzazione ad albero di parametri, origini dati e set di dati si comprimeva quando veniva apportata la maggior parte delle modifiche 
- Risolto un problema a causa del quale con Salva viene salvata la versione di RDL e non la versione più recente.
- Risolto un problema a causa del quale SSDT RS esegue il backup dei file quando il backup è disattivato e vari altri problemi.
- Risolto un problema in Generatore Report a causa del quale viene visualizzato un errore quando si fa clic "Dividi celle". [Argomento Connect](http://connect.microsoft.com/SQLServer/feedback/details/3101818/ssdt-2015-ssrs-designer-error-by-matrix-cell-split)
- Risolto un problema a causa del quale la memorizzazione nella cache potrebbe causare dati errati in un report. [Argomento Connect](http://connect.microsoft.com/SQLServer/feedback/details/3102158/ssdtbi-14-0-60812-report-preview-data-is-frequently-wrong-due-to-bad-caching)

**Progetti IS:**
- Risolto un problema a causa del quale l'impostazione run64bitruntime non viene mantenuta.
- Risolto un problema a causa del quale DataViewer non salva le colonne visualizzate.
- Risolto un problema a causa del quale Parti del pacchetto nasconde le annotazioni. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3106624/package-parts-hide-annotations)
- Risolto un problema a causa del quale Parti del pacchetto ignora layout e annotazioni in flussi di dati. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3109241/package-parts-discard-data-flow-layouts-and-annotations)
- Risolto un problema a causa del quale si verifica un arresto anomalo di SSDT quando si importa un progetto da SQL Server.
- Risolto un problema con TimeoutInMinutes di attività Hadoop File System predefinito su 10, dopo aver salvato il pacchetto SSIS di apertura e in fase di esecuzione.

**Progetti di database:**
- È stata ripristinata l'impostazione per IgnoreColumnOrder nella distribuzione DACPAC di SSDT [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/1221587/ssdt-dacpac-deploy-add-setting-back-in-for-ignorecolumnorder)
- Non è possibile compilare SSDT se viene usato STRING_SPLIT [Argomento Connect](http://connect.microsoft.com/SQLServer/feedback/details/2906200/ssdt-failing-to-compile-if-string-split-is-used)
- È stato risolto un problema per cui DeploymentContributors hanno accesso al modello pubblico ma lo schema sottostante non è stato inizializzato [Problema Github](https://github.com/Microsoft/DACExtensions/issues/8)
- È stata introdotta una correzione temporanea di DacFx per il posizionamento di FILEGROUP
- È stato risolto l'errore "Riferimento non risolto" per sinonimi esterni 
- Always Encrypted: la crittografia online non disabilita il rilevamento di modifiche al momento dell'annullamento e non funziona correttamente se il rilevamento di modifiche non è stato azzerato prima dell'avvio della crittografia


## <a name="ssdt-165-supports-up-to-sql-server-2016"></a>SSDT 16,5 (supporta fino a SQL Server 2016)
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
DacServices service = new DacServices(connectionString);
using(DacPackage package = DacPackage.Load(@"C:\My\db.dacpac")) {
var options = new PublishOptions() {
    GenerateDeploymentScript = true, // Should a deployment script be created?
    GenerateDeploymentReport = true, // Should an xml deploy report be created?
    DatabaseScriptPath = @"C:\My\OutputScript.sql", // optional path to save script to
    MasterDbScriptPath = @"C:\My\OutputScript_Master.sql", // optional path to save master script to
    DeployOptions = new DacDeployOptions()
};

// Call publish and receive deployment script & report in the results
PublishResult result = service.Publish(package, "TargetDb", options);
Console.WriteLine(result.DatabaseScript);
Console.WriteLine(result.MasterDbScript);
Console.WriteLine(result.DeploymentReport);

// Call script and receive deployment script & report in results
result = service.Script(package, "TargetDb", options);
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

* È stato corretto il bug Connect [1608896](https://connect.microsoft.com/SQLServer/feedback/details/1608896/move-multiple-integration-service-package-tasks) relativo allo spostamento di più attività pacchetto del servizio di integrazione





## <a name="ssdt-164-for-sql-server-2016"></a>SSDT 16.4 (per SQL Server 2016)
Data di rilascio: 20 settembre 2016

Numero di build: 14.0.60918

**Novità**

L'opzione Confronto schema è ora supportata in SqlPackage.exe e nell'API DacFx. Per informazioni dettagliate, vedere [Schema Compare in SqlPackage and the Data-Tier Application Framework](https://blogs.msdn.microsoft.com/ssdt/2016/09/20/schema-compare-in-sqlpackage-and-the-data-tier-application-framework-dacfx/) (Confronto schema in SqlPackage e in DacFx).

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



## <a name="ssdt-163-for-sql-server-2016"></a>SSDT 16.3 (per SQL Server 2016)
Data di rilascio: 15 agosto 2016

Numero di build: 14.0.60812.0  

**Novità**

- **Controllo e numerazione delle versioni:** le versioni sono ora contrassegnate numericamente invece che in base al mese. Questo comportamento è allineato ai nuovi criteri di SSMS e semplifica i casi in cui sono disponibili più versioni o hotfix in un mese. Questa versione è la 16.3, che significa il terzo aggiornamento dopo la versione RTM. Qualsiasi hotfix avrà il numero di versione 16.3.1 e così via, con il prossimo aggiornamento (previsto per il mese prossimo) specificato come 16.4.
- **Analysis Services - Esplora modelli tabulari:** Esplora modelli tabulari permette di spostarsi in modo pratico tra i diversi oggetti di metadati in un modello, tra cui origini, tabelle, misure e relazioni. Questa funzionalità viene implementata come finestra di strumenti separata, che può essere visualizzata aprendo il menu Visualizza in Visual Studio, scegliendo Altre finestre e quindi facendo clic su Esplora modelli tabulari. La finestra Esplora modelli tabulari viene visualizzata per impostazione predefinita nell'area di Esplora soluzioni in una scheda separata. Esplora modelli tabulari organizza gli oggetti di metadati in una struttura ad albero molto somigliante allo schema per un modello tabulare 1200 e include molte più funzionalità.
- **Strumenti di database - Always Encrypted**: questa versione include nuove finestre di dialogo di [gestione di chiavi Always Encrypted](https://msdn.microsoft.com/library/mt708953.aspx) per aggiungere facilmente chiavi master della colonna o chiavi di crittografia della colonna al progetto del database o a un database attivo in Esplora oggetti di SQL Server. Questa versione supporta i certificati inclusi nell'archivio certificati di Windows. Nelle prossime versioni saranno supportati anche Azure Key Vault e provider CNG.
    - Durante la creazione della chiave master della colonna o della chiave di crittografia della colonna, è possibile che le modifiche non vengano visualizzate in Esplora oggetti di SQL Server immediatamente dopo aver fatto clic su Aggiorna database. Per risolvere questo problema, aggiornare il nodo del database in Esplora oggetti di SQL Server.
    - Se si prova a crittografare una colonna in una tabella con dati da Esplora oggetti di SQL Server, potrebbe verificarsi un errore. Questa funzionalità è attualmente supportata solo in progetti di database di SSDT e in SSMS. Il supporto per Esplora oggetti di SQL Server verrà abilitato in una versione successiva.


**Aggiornamenti e correzioni**
* **Strumenti di database:**
    - **SSDT:**
        - Bug Connect 1898001[: correzione di un problema di descrizione delle colonne con limite di 128 caratteri](https://connect.microsoft.com/SQLServer/feedback/details/1898001/column-description-limited-to-128-characters).
        - Correzione di un problema per cui la pubblicazione di un database da Visual Studio non viene applicata alla proprietà DatabaseServiceObjective nel codice XML del profilo di pubblicazione.
        - Bug Connect 2900167 [Correzione di un problema relativo agli unit test che lascia erroneamente i file temporanei](http://connect.microsoft.com/SQLServer/feedback/details/2900167/running-ssdt-unit-tests-leaves-temp-files-behind).
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
        

 
  
## <a name="ssdt-july-for-sql-server-2016"></a>Versione di luglio di SSDT (per SQL Server 2016)  
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
    * Se il filegroup predefinito non è PRIMARIO, l'importazione e/o la pubblicazione in Azure V12 non riesce. Questa impostazione viene ora ignorata durante la pubblicazione.
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
    * Correzione di un problema nell'interfaccia utente delle tabelle calcolate dei modelli di livello di compatibilità 1200 durante l'uso della formattazione predefinita per il tipo di colonna per permettere la modifica del tipo di formattazione dall'interfaccia utente. 
    

## <a name="ssdt-june-for-sql-server-2016"></a>Versione di giugno di SSDT (per SQL Server 2016)  
Data di rilascio: 1 giugno 2016  
  
Numero di build: 14.0.60525.0 

È ora disponibile la versione di SSDT con disponibilità generale. L'aggiornamento alla versione con disponibilità generale di SSDT per giugno 2016 aggiunge il supporto per gli aggiornamenti più recenti di SQL Server 2016 RTM e diverse correzioni di bug. Per informazioni dettagliate, vedere [SQL Server Data Tools GA update for June 2016](https://blogs.msdn.microsoft.com/ssdt/2016/06/01/sql-server-data-tools-ga-update-for-june-2016/) (Aggiornamento della versione disponibile a livello generale di SQL Server Data Tools per giugno 2016).

      

## <a name="ssdt-april-for-sql-server-2016-rc3"></a>Versione di aprile di SSDT (per SQL Server 2016 RC3)  
Data di rilascio: 15 aprile 2016  
  
Numero di build: 14.0.60413.0  
  
**Database SQL Server**  
* **Supporto per Always Encrypted:** per i database che contengono colonne Always Encrypted, SSDT e DacFx permettono la visualizzazione e la modifica dei database e la pubblicazione da un progetto del database a questi database. Si noti che il supporto per la modifica di colonne con crittografia di colonna presente verrà reso disponibile in una versione successiva.  
* **Finestra di dialogo Connessione ed Esplora oggetti di SQL Server**: più correzioni e miglioramenti.  
    * La pagina Dettagli che elenca le proprietà di connessione avanzate era stata modificata per mostrare la stringa di connessione completa in una casella a più righe e per migliorare il supporto nei computer con valori DPI alti.  
    * È stata ripristinata la finestra di dialogo di errore tradizionale, con gli errori di connessione dettagliati. Questa finestra è utile per la diagnosi di problemi di accesso grazie a messaggi di errore più chiari e a un'analisi dello stack, in modo che i DBA o CSS possano ottenere le informazioni necessarie per diagnosticare i problemi.  
    * Per gli utenti con autorizzazioni minime, sono stati corretti diversi errori relativi agli elenchi di database nella finestra di dialogo Connessione e in Esplora oggetti di SQL Server, alla visualizzazione della cartella Sicurezza e ad altri problemi.  
    * Sono state migliorate le prestazioni del database SQL di Azure durante l'espansione del nodo dei database per elencare tutti i database.  
* **Programma di installazione di SSDT:**  
    * Correzione di un problema per cui viene scaricato .NET alla disinstallazione.  
    * Le dimensioni del programma di installazione sono ora impostate correttamente in computer con valori DPI alti.  
    * È stato rimosso il controllo delle versioni che blocca l'installazione di SSDT se è presente una nuova versione di SQL Server.  
    * Confronto schema: è stato corretto un problema di prestazioni per cui la selezione/deselezione di più elementi richiede molto tempo in Visual Studio.  
    * Supporto per l'uso di LocalDB 2014 su computer x86, poiché non esiste una versione x86 di SQL Server 2016.  
* **Compilazione e distribuzione:**  
    * Correzione di un problema per cui le colonne calcolate non sono supportate nelle tabella temporali.  
    * L'opzione "Esegui script di distribuzione in modalità utente singolo" viene ignorata durante la distribuzione in Azure V12, perché non è supportata in scenari cloud.  
  
  
## <a name="ssdt-hotfix-for-sql-server-2016-rc2"></a>Hotfix per SSDT (per SQL Server 2016 RC2)  
Data di rilascio: 5 aprile 2016  
  
Numero di build: 14.0.60329.0  
  
Questa build contiene un hotfix per la versione di SSDT che include funzionalità per SQL Server Integration Services. La build 14.0.60316.0 può anche essere usata con Analysis Services e Reporting Services in SQL Server 2016.   
  
Per ottenere questo hotfix, usare i [collegamenti per il download in questo post di blog](https://blogs.msdn.microsoft.com/ssdt/2016/04/05/ssdt-preview-update-rc2/).  
  
Per gli sviluppatori di report: se si compilano nuovi report usando questa build di SSDT, [leggere il problema noto e la soluzione alternativa](https://blogs.msdn.microsoft.com/ssdt/2016/04/05/ssdt-preview-update-rc2/) per un problema temporaneo nei report di SSRS, la cui soluzione è disponibile solo in questo hotfix.  
  
## <a name="ssdt-hotfix-for-sql-server-2016-rc0"></a>Hotfix per SSDT (per SQL Server 2016 RC0)  
Data di rilascio: 18 marzo 2016  
  
Numero di build: 14.0.60316.0  
  
Questa build contiene un hotfix per la versione di SSDT che include funzionalità per SQL Server 2016 RC0. Attualmente non esiste la versione RC1 di SSDT. La build 14.0.60316.0 può essere usata con la versione RC0 o RC1 di SQL Server 2016.  
      
## <a name="ssdt-february-2016-preview-for-sql-server-2016-rc0"></a>Anteprima di febbraio 2016 di SSDT (per SQL Server 2016 RC0)  
Data di rilascio: 7 marzo 2016  
  
Numero di build: 14.0.60305.0  
  
-   **Modelli di progetto di SQL Server**  
  
    Nessun annuncio per questa versione di anteprima di SSDT. Per informazioni su altre funzionalità di questa versione, vedere [Novità del motore di database](https://msdn.microsoft.com/library/bb510411.aspx).  
  
-   **Modelli di progetto dei pacchetti SSIS**  
  
    Progettazione SSIS crea e gestisce pacchetti per SQL Server 2016, 2014 o 2012. Nuovi modelli rinominati come parti. Il connettore Hadoop di SSIS supporta il formato ORC. Per informazioni dettagliate, vedere [Novità di Integration Services](https://msdn.microsoft.com/library/bb522534.aspx).  
  
-   **Modelli di progetto SSAS (progetti di modello tabulare)**  
  
    L'aggiornamento di questo mese per Analysis Services offre il supporto per la visualizzazione di tabelle per i modelli tabulari e tutti i modelli creati con il nuovo livello di compatibilità di SQL Server 2016 sono ora supportati nei pacchetti SSIS. Per altre informazioni. Per informazioni dettagliate, vedere il post di blog sulle [novità di Analysis Services](http://blogs.msdn.com/b/analysisservices/archive/2016/01/28/what-s-new-for-sql-server-2016-analysis-services-in-ctp3-3.aspx) .  
  
-   **Modelli di progetto report di SSRS**  
  
    Nessun annuncio per questa versione di anteprima di SSDT. Per informazioni su altre funzionalità di questa versione, vedere [Novità di SQL Server Reporting Services](https://msdn.microsoft.com/library/ms170438.aspx).  
  
## <a name="ssdt-january-2016-preview"></a>Anteprima di SSMS di gennaio 2016  
Data di rilascio: 4 febbraio 2016  
  
Numero di build: 14.0.60203.0  
  
-   **Modelli di progetto di SQL Server**  
  
    Nessun annuncio per questa versione di anteprima di SSDT. Per informazioni su altre funzionalità di questa versione TCP, vedere [Novità del motore di database](https://msdn.microsoft.com/library/bb510411.aspx)  
  
-   **Modelli di progetto dei pacchetti SSIS**  
  
    Sono stati aggiunti il supporto per componenti di origine e destinazione ODBC, un'attività di controllo CDC,  
      un componente di origine e splitter CDC, Microsoft Connector per SAP BW e Integration Services Feature Pack per Azure. Per informazioni dettagliate, vedere [Novità di Integration Services](https://msdn.microsoft.com/library/bb522534.aspx).  
  
-   **Modelli di progetto di SSAS**  
  
    Include miglioramenti per i modelli tabulari a livello di compatibilità 1200, colonne calcolate e sicurezza a livello di riga per i modelli in modalità DirectQuery, traduzioni dei metadati del modello, esecuzione di script TMSL nell'attività Esegui DDL Analysis Services di SSIS e numerose correzioni di bug.  
    Per informazioni dettagliate, vedere [Novità di Analysis Services (MSDN)](https://msdn.microsoft.com/library/bb522628.aspx) o il [post di blog sulle novità di Analysis Services](http://blogs.msdn.com/b/analysisservices/archive/2016/01/28/what-s-new-for-sql-server-2016-analysis-services-in-ctp3-3.aspx).  
  
-   **Modelli di progetto report di SSRS**  
  
    Nessun annuncio per questa versione di anteprima di SSDT. Per informazioni su altre funzionalità di questa versione TCP, vedere [Novità di Reporting Services](https://msdn.microsoft.com/library/ms170438.aspx).  
  
## <a name="ssdt-december-2015-preview"></a>Anteprima di dicembre 2015 di SSDT  
  
-   I **modelli di progetto di SQL Server** includono correzioni di bug per la finestra di dialogo Connessione, elenchi della cronologia recente e uso corretto del contesto di autenticazione impostato nella proprietà di connessione durante il caricamento di un elenco di database.  
  
    -   Valore di timeout del test di connessione modificato in 15 secondi.  
  
    -   Se l'indirizzo IP del client non viene registrato durante il caricamento di un elenco di database, creare una regola firewall del server del database SQL di Azure.  
  
    -   Supporto di programmabilità delle funzionalità di SQL Server 2016 CTP3.2.  
  
-   I **modelli di progetto di SSAS** aggiungono il supporto per la creazione di tabelle calcolate in base alle espressioni DAX e ad altri oggetti già definiti nel modello.  
  
-   I **modelli di progetto dei pacchetti SSIS** aggiungono il supporto del connettore Hadoop di SSIS per il formato di file Avro e l'autenticazione Kerberos.   
    Si noti che la finestra di progettazione SSIS per SSIS 2012 e 2014 non è ancora inclusa in questo aggiornamento.  
  
## <a name="ssdt-november-2015-preview"></a>Anteprima di novembre 2015 di SSDT  
  
-   **Modelli di progetto di SQL Server**. Anteprima dell'esperienza di connessione migliorata per SQL Server e il database SQL di Azure.  
  
-   **Modelli di progetto dei pacchetti SSIS**. Miglioramento delle prestazioni del catalogo SSIS: le prestazioni della maggior parte delle visualizzazioni del catalogo SSIS per l'utente non amministratore di ssis sono state migliorate.  
  
-   I **modelli di progetto di SSAS** includono miglioramenti per i progetti di modello tabulare in Analysis Services. È possibile usare il comando **Visualizza codice** per visualizzare la definizione del modello in JSON. Se non si usa una versione completa di Visual Studio 2015, è necessario installarla per disporre dell'editor JSON. È possibile scaricare [Studio Community Edition](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) gratuitamente.  
  
## <a name="ssdt-october-2015-preview"></a>Anteprima di ottobre 2015 di SSDT  
  
-   Nuovi modelli di progetto per BI (modelli di Analysis Services, report di Reporting Services e pacchetti di Integration Services). Tutti i modelli di progetto di SQL Server sono ora inclusi in un unico SSDT.  
  
-   Nuove funzionalità SSIS, inclusi il connettore Hadoop, il modello di flusso di controllo e dimensione massima del buffer ampliata dell'attività flusso di dati.  
  
-   Supporto delle funzionalità di SQL Server 2016 CTP 3.0 per i progetti di database relazionale.  
  
-   Varie correzioni di bug in SSIS e supporto per il sistema operativo Windows 7.  
  
## <a name="ssdt-september-2015-preview"></a>Anteprima di settembre 2015 di SSDT  
  
-   Nuovo supporto multilingue in questa versione di anteprima.  
  
## <a name="ssdt-august-2015-preview"></a>Anteprima di agosto 2015 di SSDT  
  
-   Nuovo programma Setup.exe autonomo per l'installazione di SSDT.  Non è più necessario usare una versione modificata del programma di installazione di SQL Server. Questa versione di SSDT include un modello di progetto per la creazione di database relazionali distribuiti al database SQL di Azure o a SQL Server.  
  
## <a name="see-also"></a>Vedere anche  
[Scaricare SQL Server Data Tools &#40;SSDT&#41;](../ssdt/download-sql-server-data-tools-ssdt.md)  
[Versioni precedenti di SQL Server Data Tools &#40;SSDT e SSDT-BI&#41;](../ssdt/previous-releases-of-sql-server-data-tools-ssdt-and-ssdt-bi.md)  
[Novità del motore di database](https://msdn.microsoft.com/library/bb510411.aspx)  
[Novità di Analysis Services](https://msdn.microsoft.com/library/bb522628.aspx)  
[Novità di Integration Services](https://msdn.microsoft.com/library/bb522534.aspx)  
  

