---
title: "PowerShell scripting in Analysis Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 60bb9610-7229-42eb-a95f-a377268a8720
caps.latest.revision: 44
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 44
---
# PowerShell scripting in Analysis Services
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] include componenti di PowerShell per esplorare, amministrare ed eseguire query su oggetti server, tabulari e multidimensionali in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]:  
  
-   Il provider **SQLAS**, usato per l'esplorazione della gerarchia di oggetti, è disponibile in presenza di qualsiasi istanza locale di Analysis Services (la modalità server è irrilevante).  
  
-   Il modulo **SQLASCMDLETS** offre cmdlet specifici per determinate attività, come backup, ripristino ed elaborazione, e anche il cmdlet generico [Invoke-ASCmd cmdlet](../../analysis-services/powershell/invoke-ascmd-cmdlet.md) che accetta qualsiasi file di input per query o script ASSL/XMLA o TMSL (Tabular Model Scripting Language).  
  
 Entrambi i componenti implementano un subset dell'interfaccia amministrativa Analysis Services Management Object ([Microsoft.AnalysisServices Namespace](http://msdn.microsoft.com/library/ms146720\(SQL.130\).aspx)), fornendo cmdlet per la gestione e la creazione di oggetti [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  Entrambi sono estensioni per il modulo radice **SQLPS** per SQL Server. Per usare i componenti PowerShell [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], è necessario prima di tutto importare **SQLPS**. Sintassi ed esempi per tutti i cmdlet sono disponibili nel [Analysis Services PowerShell Reference](../../analysis-services/powershell/analysis-services-powershell-reference.md).  Per un esempio di come usare i tipi AMO in PowerShell per creare un database tabulare, vedere [AMO PowerShell Example](../../analysis-services/powershell/amo-powershell-example.md).  
  
##  <a name="bkmk_prereq"></a> Passaggio 1: Installare componenti PowerShell  
 L'approccio consigliato per ottenere componenti PowerShell è l'installazione di SQL Server Management Studio (SSMS). In questo modo si ottengono i moduli PowerShell per SQL Server e il provider di dati Analysis Services Management (AMO). Con SSMS è anche possibile generare facilmente input XMLA e TMSL da usare negli script PowerShell.  
  
 È consigliabile installare un'istanza locale di Analysis Services. Un'istanza locale consente la navigazione nella gerarchia degli oggetti mediante il provider **SQLAS** , anche se non lo si usa mai per ospitare un database.  
  
1.  Passare a  [Scaricare SQL Server Management Studio](https://msdn.microsoft.com/en-us/library/mt238290.aspx) per ottenere la versione più recente di Management Studio. La versione più recente di Management Studio. include un AMO aggiornato che supporta le definizioni di oggetti metadati tabulari per i modelli tabulari creati con livello di compatibilità 1200.  
  
2.  Dopo l'installazione di Management Studio, aprire una finestra di PowerShell. Non deve essere una finestra di amministratore.  
  
3.  Immettere `Get-Module -ListAvailable` per verificare che i moduli **SQLPS** e **SQLASCMDLETS** siano presenti nell'elenco.  
  
     **SQLAS** non sarà visibile se non si installa anche un'istanza locale di Analysis Services (in modalità tabulate o multidimensionale).  
  
4.  Immettere `Get-Command -Module sqlascmdlets` per generare un elenco dei cmdlet impiegati nell'amministrazione di Analysis Services.  
  
     **SQLASCMDLETS** sono disponibili anche quando il provider **SQLAS** non è presente.  
  
    -   [Cmdlet Add-RoleMember](../../analysis-services/powershell/add-rolemember-cmdlet.md)  
  
    -   [Cmdlet Backup-ASDatabase](../../analysis-services/powershell/backup-asdatabase-cmdlet.md)  
  
    -   [Invoke-ASCmd cmdlet](../../analysis-services/powershell/invoke-ascmd-cmdlet.md) **-inputfile**  
  
    -   [Invoke-ProcessASDatabase](../../analysis-services/powershell/invoke-processasdatabase.md)  
  
    -   [Cmdlet Invoke-ProcessCube](../../analysis-services/powershell/invoke-processcube-cmdlet.md)  
  
    -   [Cmdlet Invoke-ProcessDimension](../../analysis-services/powershell/invoke-processdimension-cmdlet.md)  
  
    -   [Cmdlet Invoke-ProcessPartition](../../analysis-services/powershell/invoke-processpartition-cmdlet.md)  
  
    -   [Cmdlet Invoke-ProcessTable](../../analysis-services/powershell/invoke-processtable-cmdlet.md)  
  
    -   [Cmdlet Merge-Partition](../../analysis-services/powershell/merge-partition-cmdlet.md)  
  
    -   [Cmdlet New-RestoreFolder](../../analysis-services/powershell/new-restorefolder-cmdlet.md)  
  
    -   [Cmdlet New-RestoreLocation](../../analysis-services/powershell/new-restorelocation-cmdlet.md)  
  
    -   [Cmdlet Remove-RoleMember](../../analysis-services/powershell/remove-rolemember-cmdlet.md)  
  
    -   [Cmdlet Restore-ASDatabase](../../analysis-services/powershell/restore-asdatabase-cmdlet.md)  
  
> [!NOTE]  
>  Windows PowerShell è installato per impostazione predefinita nelle versioni più recenti dei sistemi operativi Windows. Si consiglia l'uso della versione 4.0 o di una versione successiva.  
  
## Passaggio 2: Caricare componenti per avviare una sessione interattiva  
 Una volta installati i componenti, caricandoli viene avviata una sessione interattiva.  
  
1.  Immettere `Import-Module sqlps -DisableNameChecking`,  
  
     Vengono caricati i componenti PowerShell di SQL Server, compresi quelli per Analysis Services, e viene disattivato l'avviso sui nomi verb non validi.  
  
2.  Immettere `sqlserver:`  
  
     Il prompt  dovrebbe cambiare in **PS SQLSERVER:\\>**.  
  
3.  Se Analysis Services è installato in locale, è possibile esplorare la gerarchia di oggetti. Immettere `cd sqlas` per aprire il provider **SQLAS**.  
  
4.  Digitare `dir` per elencare le istanze di Analysis Services. Il provider non distingue fra le istanze tabulari e multidimensionali.  
  
## Permissions  
 Una sessione PowerShell interattiva viene eseguita con l'identità di sicurezza della persona che la avvia. Molte attività richiederanno che la persona che avvia la sessione sia anche un amministratore del server Analysis Services.  
  
 Le attività PowerShell pianificate devono essere considerate operazioni automatiche. L'account che esegue l'utilità di pianificazione, ad esempio il servizio SQL Server Agent, molto probabilmente deve essere un amministratore di Analysis Services (a seconda dell'attività).  
  
 Le cartelle di dati locali, come le directory di backup e dei dati predefinite, sono già configurate con autorizzazioni per il file system che consentono a un'istanza locale di leggere e scrivere in questi percorsi.  
  
 L'amministrazione remota, specialmente quando viene eseguita da computer client su cui Analysis Services non è installato, richiede che l'istanza remota del server Analysis Services che esegue l'azione possieda autorizzazioni relative al file system per la lettura dei file durante il ripristino o la scrittura dei file durante il backup.  
  
## File script di input: ASSL/XMLA o TMSL  
 Se si usa **invoke-ascmd** per eseguire script, è necessario tenere conto della modalità server, del tipo di database e del livello di compatibilità per la composizione dello script.  
  
-   I database multidimensionali e tabulari con livelli di compatibilità 1050-1103 rispondono agli script composti in XMLA (usando l'estensione ASSL specifica delle definizioni degli oggetti di Analysis Services).  
  
-   I database tabulari di SQL Server 2016 (con livello di compatibilità 1200) rispondono agli script TMSL.  
  
 Se si lavora con versioni miste di modelli tabulari sulla stessa istanza di SQL Server 2016, prestare attenzione a usare lo script giusto.  
  
> [!NOTE]  
>  Gli script possono essere generati in SQL Server Management Studio e poi modificati come necessario. Gli script per i database tabulari con livello di compatibilità 1200 sono composti in TMSL. Tutti gli altri script sono composti in XMLA/ASSL. Un'istanza di SQL Server 2016 in modalità tabulare supporta entrambi i linguaggi di scripting.  
  
## Amministrazione locale e remota  
 L'amministrazione locale di Analysis Services mediante script e comandi PowerShell è più facile per due ragioni:  
  
-   Consente di usare il provider **SQLAS** per navigare nella gerarchia degli oggetti.  
  
-   Le autorizzazioni di file che consentono ad Analysis Services di leggere dalle cartelle dati predefinite, ad esempio per le attività di backup e ripristino, sono già presenti, presupponendo che si usino queste cartelle come percorso del database, e l'istanza locale del server viene usata per l'operazione.  
  
 La gestione di un'istanza remota richiede configurazioni aggiuntive. I passaggi riportati di seguito si basano sul presupposto che siano stati completati i passaggi di installazione per Management Studio ma che l'istanza del servizio si trovi su un computer remoto. È necessario disporre dei diritti di amministratore sul server Analysis Services.  
  
 Poiché Analysis Services è remoto, non è disponibile un provider **SQLAS** per la navigazione locale della gerarchia degli oggetti. Se si ripristinano file da una cartella locale anziché da un'istanza di Analysis Services, sarà necessario creare condivisioni e concedere al server l'accesso in lettura ai file.  
  
1.  Aprire una finestra di amministratore di PowerShell.  
  
2.  Immettere `Set-ExecutionPolicy RemoteUnsigned`  
  
3.  In Esplora file assicurarsi che tutte le cartelle in cui sono archiviati i file di dati siano condivise e che l'istanza di Analysis Services possieda le autorizzazioni di lettura per i contenuti.  
  
##  <a name="bkmk_vers"></a> Versioni e modalità supportate di Analysis Services  
 Nella tabella seguente viene mostrata la disponibilità di PowerShell per Analysis Services in contesti diversi.  
  
|Contesto|Disponibilità della funzionalità PowerShell|  
|-------------|-------------------------------------|  
|Istanze e database multidimensionali|Supportata per l'amministrazione locale e remota.<br /><br /> La partizione di tipo merge richiede una connessione locale.|  
|Istanze e database tabulari|Supportata per l'amministrazione locale e remota a tutti i livelli di compatibilità<br /><br /> Cmdlet SQLAS per modelli tabulari con livello di compatibilità 1200 che usano Tabular Model Scripting Language (TMSL) in JSON anziché XMLA.|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per istanze e database SharePoint|Supporto limitato. È possibile utilizzare connessioni HTTP e il provider per SQLAS per visualizzare informazioni sulle istanze e sui database.<br /><br /> Tuttavia, l'utilizzo che i cmdlet non è supportato. Non è possibile usare PowerShell per Analysis Services per eseguire il backup e il ripristino di un database [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in memoria e non si deve neppure aggiungere o rimuovere ruoli, elaborare dati o eseguire script XMLA arbitrari.<br /><br /> Per scopi di configurazione, [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint è dotato di supporto incorporato per PowerShell che viene fornito separatamente. Per altre informazioni, vedere [Informazioni di riferimento su PowerShell per Power Pivot per SharePoint](../../analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint.md).|  
|Connessioni native a cubi locali<br /><br /> "Data Source=c:\backup\test.cub"|Non supportato.|  
|Connessioni HTTP a file di connessione (con estensione bism) di Business Intelligence Semantic Model in SharePoint<br /><br /> "Data Source=http://server/shared_docs/name.bism"|Non supportato.|  
|Connessioni incorporate a database [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]<br /><br /> "Data Source=$Embedded$"|Non supportato.|  
|Contesto del server locale nelle stored procedure di Analysis Services<br /><br /> "Data Source=*"|Non supportato.|  
  
## Esempi di attività di amministrazione del server con PowerShell  
 **Elencare le proprietà del server**  
  
 Le proprietà del server vengono esposte in vari modi.  Se si ha familiarità con le proprietà esposte in msmdsrv. ini o con le pagine di proprietà di Management Studio, negli esempi seguenti sarà possibile notare che le proprietà sono restituite effettivamente da oggetti diversi.  
  
 Questo script carica un oggetto Server AMO. Se è necessario un nume di proprietà completo, è possibile eseguire questo script per restituire l'elenco.  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as.connect("server-name\instance-name")  
$as.serverproperties  
  
```  
  
 Questo script restituisce le proprietà e i metodi a livello di istanza. In questo elenco è possibile leggere valori come **ServerMode**, **Version**, **ProductName**o **ProductLevel**.  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as | get-member  
  
```  
  
 **Ottenere la modalità del server**  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as.ServerMode  
```  
  
 **Ottenere il livello di compatibilità predefinito**  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as.DefaultCompatibilityLevel  
```  
  
 **Ottenere un elenco di database**  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as.databases  
```  
  
 **Modificare il numero di porta**  
  
 Questo script crea un oggetto per un'istanza denominata, dichiara la porta, imposta la porta, aggiorna l'istanza del server, disconnette l'oggetto e riavvia il servizio. Come passaggio di verifica, è possibile aprire una nuova connessione e restituire la porta.  
  
 È inoltre possibile verificare la porta nel file msmdsrv.ini o nella pagina delle proprietà generali del server in Management Studio.  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as.connect("server-name\instance-name")  
$port = $as.serverproperties['Port']  
$port | select *  
$port.Value = [int]55555  
$as.Update()  
$as.Disconnect()  
restart-service 'MSOLAP$TABULAR'  
$as.connect("server-name\instance-name")  
$port | select *  
  
```  
  
## Vedere anche  
 [Concedere i diritti di amministratore del server a un'istanza di Analysis Services](../../analysis-services/instances/grant-server-admin-rights-to-an-analysis-services-instance.md)   
 [Livello di compatibilità per i modelli tabulari in Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento al linguaggio di scripting per modelli tabulari &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Installare SQL Server PowerShell](../../database-engine/install-windows/install-sql-server-powershell.md)   
 [Post sulla gestione dei modelli tabulari tramite PowerShell](http://go.microsoft.com/fwlink/?linkID=227685)   
 [Configurare l'accesso HTTP ad Analysis Services in Internet Information Services &#40;IIS&#41; 8.0](../../analysis-services/instances/configure http access to analysis services on iis 8.0.md)  
  
  