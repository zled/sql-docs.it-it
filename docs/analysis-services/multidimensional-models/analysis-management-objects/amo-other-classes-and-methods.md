---
title: AMO altri metodi e classi | Documenti Microsoft
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- restores [AMO]
- AMO, backup and restore
- capture logs [AMO]
- AmoException class [AMO]
- Analysis Management Objects, backup and restore
- assembly objects [AMO]
- traces [AMO]
- backups [AMO]
ms.assetid: 60ed5cfa-3a03-4161-8271-0a71a3ae363b
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5ae261375e96cf6bfa322262b0b13653b9534331
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="amo-other-classes-and-methods"></a>Altre classi e altri metodi AMO
  In questa sezione contiene le classi comuni che non sono specifiche per OLAP o di data mining e che sono utili per l'amministrazione o gestione di oggetti in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Tali classi riguardano caratteristiche quali stored procedure, traccia, eccezioni e backup e ripristino.  
  
 In questo argomento sono incluse le sezioni seguenti:  
  
-   [Oggetti assembly](#Assembly)  
  
-   [Metodi backup e ripristino](#Backup)  
  
-   [Oggetti di traccia](#Traces)  
  
-   [Classe CaptureLog e Capturexml](#CaptureLog)  
  
-   [Classe eccezione AMOException](#AMO)  
  
 Nella figura seguente viene illustrata la relazione delle classi descritte in questo argomento.  
  
 ![Altre classi AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-otherclasses.gif "altre classi AMO")  
  
##  <a name="Assembly">Oggetti assembly</a>  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.Assembly>, aggiungerlo alla raccolta di assembly del server, quindi aggiornare l'oggetto <xref:Microsoft.AnalysisServices.Assembly> nel server tramite il metodo Update.  
  
 Per rimuovere un oggetto <xref:Microsoft.AnalysisServices.Assembly>, è necessario eliminarlo tramite il metodo Drop dell'oggetto <xref:Microsoft.AnalysisServices.Assembly>. La rimozione di un oggetto <xref:Microsoft.AnalysisServices.Assembly> dalla raccolta di assembly del database non comporta l'eliminazione dell'assembly, ma ne impedisce la visualizzazione nell'applicazione fino alla successiva esecuzione dell'applicazione stessa.  
  
 Per ulteriori informazioni sui metodi e le proprietà disponibili, vedere <xref:Microsoft.AnalysisServices.Assembly> in <xref:Microsoft.AnalysisServices> .  
  
> [!IMPORTANT]  
>  Gli assembly COM potrebbero comportare un rischio per la sicurezza. A causa di tale rischio e di altre considerazioni, gli assembly COM sono stati deprecati in [!INCLUDE[ssASversion10](../../../includes/ssasversion10-md.md)] e potrebbero non essere supportati nelle versioni future.  
  
##  <a name="Backup">Metodi backup e ripristino</a>  
 I metodi Backup e Restore consentono di creare copie di un database di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e di eseguirne il recupero tramite la copia. Il metodo Backup appartiene all'oggetto <xref:Microsoft.AnalysisServices.Database>, mentre il metodo Restore appartiene all'oggetto <xref:Microsoft.AnalysisServices.Server>.  
  
 Il backup di un database può essere eseguito solo dagli amministratori del server e di database. Solo gli amministratori del server possono ripristinare un database in un server diverso da quello da cui è stato eseguito il backup, mentre gli amministratori di database possono ripristinare un database sovrascrivendo il database esistente solo se risultano proprietari del database da sovrascrivere. Dopo un ripristino, l'amministratore di database può perdere l'accesso al database ripristinato se il database è stato ripristinato con le definizioni di sicurezza originali.  
  
 I file di backup di database devono avere estensione abf.  
  
### <a name="backup-method"></a>Metodo Backup  
 Per eseguire il backup di un database, utilizzare il metodo Backup dell'oggetto di database con il nome del file di backup come parametro.  
  
##### <a name="default-values"></a>Valori predefiniti:  
 AllowOverwrite=**false**  
  
 BackupRemotePartitions=**false**  
  
 Sicurezza =**CopyAll**  
  
 ApplyCompression=**true**  
  
### <a name="restore-method"></a>Metodo Restore  
 Per ripristinare un database in un server, utilizzare il metodo Restore del server con il file di backup come parametro.  
  
##### <a name="default-values"></a>Valori predefiniti:  
 AllowOverwrite=**false**  
  
 DataSourceType=**Remote**  
  
 Sicurezza =**CopyAll**  
  
##### <a name="restrictions"></a>Restrizioni  
  
1.  Una partizione locale non può essere ripristinata come partizione remota.  
  
2.  Una partizione remota non può essere ripristinata come partizione locale, ma può essere ripristinata in un server diverso da quello da cui è stato eseguito il backup.  
  
### <a name="common-parameters-and-properties-for-backup-and-restore-methods"></a>Proprietà e parametri comuni per i metodi Backup e Restore  
  
-   **File** è il nome del file di backup (nome UNC) in/da.  
  
-   **Percorso** specifica le informazioni di backup specifico del server, ad esempio **BackupFile**. In questo modo è possibile specificare un file di backup separato per un database remoto.  
  
-   **DatasourceID** specifica l'ID del database subordinato in un server remoto.  
  
-   **ConnectionString** consente di modificare l'origine dati remota nel caso in cui il server remoto è stato modificato. Quando ConnectionString è presente, è necessario specificare sempre DatasourceID.  
  
-   **Cartella** consente di modifica del mapping delle cartelle per le partizioni nel disco rigido locale  
  
-   **Originale** è la cartella originale per le partizioni locali.  
  
-   **Nuovo** è il nuovo percorso per le partizioni locale utilizzato per si trovano nella cartella "Original" precedente corrispondente.  
  
-   **Password**, se non è vuota, specifica che il server consente di crittografare il file di backup.  
  
##  <a name="Traces">Oggetti di traccia</a>  
 Gli oggetti Trace rappresentano un framework utilizzato per il monitoraggio, la riproduzione e la gestione di un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Un'applicazione client, ad esempio [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)], sottoscrive una traccia e il server restituisce eventi di traccia come specificato nella definizione della traccia stessa.  
  
 Ogni evento viene descritto da una classe di evento che illustra il tipo di evento generato. In una classe di evento le sottoclassi di evento descrivono un livello di categorizzazione più dettagliato. Ogni evento viene descritto da un numero di colonne. Le colonne che descrivono un evento di traccia sono coerenti per tutti gli eventi e conformi alla struttura di traccia SQL. Le informazioni registrate in ogni colonna possono differire a seconda della classe di evento. Sebbene per ogni traccia sia specificato un set predefinito di colonne, il significato della colonna può differire a seconda della classe di evento. La colonna TextData ad esempio viene utilizzata per registrare il codice ASSL per tutti gli eventi relativi alle istruzioni.  
  
 Una definizione della traccia può includere una o più classi di evento di cui eseguire contemporaneamente la traccia. Per ogni classe di evento, è possibile aggiungere una o più colonne di dati alla definizione della traccia, sebbene non sia necessario utilizzare tutte le colonne di traccia. L'amministratore di database può decidere le colonne disponibili da includere in una traccia. È inoltre possibile eseguire selettivamente la traccia di classi di evento in base a criteri di filtro applicati a qualsiasi colonna nella traccia.  
  
 Le tracce possono essere avviate ed eliminate. È inoltre possibile eseguire più tracce contemporaneamente. Gli eventi di traccia possono essere acquisiti in tempo reale o indirizzati a un file per un'analisi o una riproduzione successiva. [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] è lo strumento utilizzato per analizzare e riprodurre eventi di traccia [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Gli eventi di una stessa traccia possono essere ricevuti da più connessioni.  
  
 Le tracce possono essere divise in due gruppi, ovvero tracce del server e tracce della sessione. Nelle tracce del server saranno disponibili le informazioni relative a tutti gli eventi del server, mentre nelle tracce della sessione saranno disponibili le informazioni relative solo agli eventi della sessione corrente.  
  
 Per definire le tracce dalla raccolta di tracce del server, effettuare le operazioni seguenti:  
  
1.  Creare un oggetto <xref:Microsoft.AnalysisServices.Trace> e popolare i dati di base relativi, ad esempio l'ID traccia, il nome, il nome del file di log, gli elementi append|overwrite e così via.  
  
2.  Aggiungere gli eventi da monitorare alla raccolta di eventi dell'oggetto traccia. Per ogni evento vengono aggiunte colonne di dati.  
  
3.  Impostare i filtri per escludere le righe non necessarie di dati aggiungendoli alla raccolta di filtri.  
  
4.  Avviare la traccia. La creazione della traccia non avvia la raccolta dei dati.  
  
5.  Arrestare la traccia.  
  
6.  Verificare il file di traccia tramite [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)].  
  
 Per ottenere le tracce dall'oggetto sessione, effettuare le operazioni seguenti:  
  
1.  Definire le funzioni per gestire gli eventi di traccia generati nell'applicazione da SessionTrace. I possibili eventi sono OnEvent e Stopped.  
  
2.  Aggiungere le funzioni definite al gestore dell'evento.  
  
3.  Avviare la traccia della sessione.  
  
4.  Eseguire il processo e consentire ai gestori di funzione di acquisire gli eventi.  
  
5.  Arrestare la traccia della sessione.  
  
6.  Continuare l'applicazione.  
  
##  <a name="CaptureLog">Classe CaptureLog e Capturexml</a>  
 Tutte le azioni che devono essere eseguite da AMO vengono inviate al server come messaggi XMLA. In AMO sono disponibili gli strumenti per acquisire tutti i messaggi di questo tipo senza le intestazioni SOAP. Per ulteriori informazioni, vedere [Introduzione a classi AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md). La classe CaptureLog è il meccanismo disponibile in AMO per inserire nello script oggetti e operazioni. Per gli oggetti e le operazioni gli script verranno generati in XMLA.  
  
 Per iniziare ad acquisire il codice XML, la proprietà dell'oggetto server CaptureXML deve essere impostata su **true**. In questo modo verrà avviata l'acquisizione di tutte le azioni che devono essere inviate al server nella classe CaptureLog, senza che sia necessario inviare le azioni stesse al server. CaptureLog è considerata una classe poiché dispone del metodo Clear che consente di cancellare il log relativo all'acquisizione.  
  
 Per leggere il log, individuare la raccolta di stringhe e avviare l'iterazione sulle stringhe stesse. È possibile inoltre concatenare tutti i log in una stringa tramite il metodo dell'oggetto server ConcatenateCaptureLog cui sono associati tre parametri, due dei quali sono obbligatori. I parametri obbligatori sono *transazionale*, di tipo booleano, e *parallela*, di tipo Boolean. Se *transazionale* è impostato su **true**, indica che il file batch XML verrà creato come una singola transazione anziché ogni comando viene considerato come una transazione separata. Se *parallela* è impostato su **true**, indica che tutti i comandi nel file batch verranno registrati per l'esecuzione simultanea anziché in sequenza come sono stati registrati.  
  
##  <a name="AMO">Classe eccezione AMOException</a>  
 È possibile utilizzare la classe eccezione AMOException per rilevare facilmente nell'applicazione eccezioni generate da AMO.  
  
 In caso di rilevamento di problemi, in AMO verrà generata un'eccezione. Nella tabella seguente vengono elencati i tipi di eccezioni gestite da AMO. Le eccezioni derivano dalla classe <xref:Microsoft.AnalysisServices.AmoException>.  
  
|Eccezione|Origine|Description|  
|---------------|------------|-----------------|  
|<xref:Microsoft.AnalysisServices.AmoException>|Classe di base|L'applicazione riceve questa eccezione quando un oggetto padre obbligatorio è mancante o quando un elemento necessario non è presente in una raccolta.|  
|<xref:Microsoft.AnalysisServices.OutOfSyncException>|Derivata da AMOException|L'applicazione riceve questa eccezione quando AMO non è sincronizzato con il motore e quest'ultimo restituisce un riferimento a un oggetto sconosciuto in AMO.|  
|<xref:Microsoft.AnalysisServices.OperationException>|Derivata da AMOException|Importante eccezione ricevuta di frequente dalle applicazioni che contiene i dettagli relativi a un errore proveniente dal server probabilmente a causa di un'operazione AMO non corretta, ad esempio Update, Process o Drop.|  
|<xref:Microsoft.AnalysisServices.ResponseFormatException>|Derivata da AMOException|Questa eccezione si verifica quando il motore restituisce un messaggio in un formato sconosciuto in AMO.|  
|<xref:Microsoft.AnalysisServices.ConnectionException>|Derivata da AMOException|Questa eccezione si verifica quando non è possibile stabilire una connessione (tramite Server.Connect) o quando la connessione viene persa durante la comunicazione tra AMO e il motore, ad esempio durante un'operazione Update, Process o Drop.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices>   
 [Introduzione a classi AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [Architettura logica &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Gli oggetti di database &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
