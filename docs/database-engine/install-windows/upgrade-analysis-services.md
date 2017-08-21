---
title: Aggiornare Analysis Services | Microsoft Docs
ms.custom: 
ms.date: 07/17/2017
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading databases
- databases [Analysis Services], upgrading
- installing Analysis Services, side-by-side installations
- Analysis Services upgrades
- Analysis Services upgrades, about upgrading Analysis Services
- SSAS, database migration
- upgrading Analysis Services
- installing Analysis Services, upgrading
- SSAS, upgrading
ms.assetid: a131d329-386e-4470-aaa9-ffcde4e5ec0c
caps.latest.revision: 79
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3b3ad4ecf62f3a30882720140f2f362007f8428b
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="upgrade-analysis-services"></a>Aggiornare Analysis Services
  Le istanze di Analysis Services possono essere aggiornate a una versione di SQL Server con la stessa modalità server per sfruttare i vantaggi delle funzionalità introdotte nella versione corrente, come descritto in [What's New in Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md).  
  
 È possibile aggiornare ogni istanza sul posto, indipendentemente dalle altre istanze in esecuzione sullo stesso hardware. Tuttavia, la maggior parte degli amministratori sceglie di installare una nuova istanza della nuova versione per la verifica dell'applicazione prima di trasferire i carichi di lavoro sul nuovo server. Per i server di sviluppo o test, potrebbe essere più opportuno un aggiornamento sul posto.  
  
 Prima di effettuare l'aggiornamento a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vedere gli argomenti seguenti:  

- [Note sulla versione di SQL Server 2017](../../sql-server/sql-server-2017-release-notes.md) descrive problemi noti e soluzioni alternative.  
- [SQL Server 2016 Release Notes (Note sulla versione di SQL Server 2016)](../../sql-server/sql-server-2016-release-notes.md) descrive problemi noti e soluzioni alternative.  
- [Analysis Services Backward Compatibility](../../analysis-services/analysis-services-backward-compatibility.md) riepiloga le funzionalità non più supportate, deprecate e modificate. È opportuno esaminare periodicamente questi elenchi per valutare l'impatto delle modifiche apportate al prodotto su modelli, script o codici personalizzati in uso. In genere, le transizioni delle funzionalità vengono annunciate durante la fase provvisoria della versione successiva principale.  
  
## <a name="server-upgrade"></a>Aggiornamento del server  
 Esistono due approcci di base per l'aggiornamento di server e database:  
  
-   Gli**aggiornamenti sul posto** consentono di sostituire i file di programma esistenti con i file di programma di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . I database rimangono nello stesso percorso. Le cartelle del programma vengono aggiornate in modo da riflettere il nuovo nome.  
  
-   Gli**aggiornamenti affiancati** consentono di creare una nuova installazione di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], in genere nello stesso computer, a meno che non si esegua contemporaneamente l'aggiornamento hardware. Questo approccio richiede il trasferimento del database nella nuova istanza e la disinstallazione, facoltativa, della versione precedente per liberare spazio su disco.  
  
 I livelli di compatibilità dei database collegati a un determinato server rimangono invariati, a meno che non vengano modificati manualmente.  
  
### <a name="in-place-upgrade"></a>Aggiornamento sul posto  
 È possibile aggiornare un'istanza esistente di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and, as part of the upgrade process, auamatically migrate existing databases from the old instance a the new instance. Poiché i metadati e i dati binari sono compatibili tra le due versioni, i dati verranno mantenuti in seguito all'aggiornamento e non sarà necessario eseguirne la migrazione manuale.  
  
 Per aggiornare un'istanza esistente, eseguire il programma di installazione e specificare il nome dell'istanza esistente come nome della nuova istanza.  
  
### <a name="side-by-side-upgrade"></a>Aggiornamento affiancato  
  
-   Eseguire il backup di tutti i database e verificare che ognuno di essi possa essere ripristinato. Vedere [Backup and Restore of Analysis Services Databases](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md).  
  
-   Identificare un subset di report, fogli di calcolo o snapshot del dashboard da usare successivamente come base di verifica delle operazioni del server dopo l'aggiornamento. Se possibile, raccogliere misure delle prestazioni in modo da confrontare i carichi di lavoro sul server aggiornato.  
  
-   Installare una nuova istanza di Analysis Services, scegliendo la stessa modalità del server (Tabulare o Multidimensionale) attiva sul server da sostituire. Vedere [Install Analysis Services](../../analysis-services/instances/install-windows/install-analysis-services.md).  
  
     Attività successive all'installazione per la configurazione di porte e l'aggiunta di amministratori del server. Vedere [Configurazione successiva all'installazione &#40;Analysis Services&#41;](../../analysis-services/instances/post-install-configuration-analysis-services.md).  
  
-   Collegare o ripristinare ogni database.  
  
-   Eseguire DBCC per verificare l'integrità del database. Sui modelli tabulari è possibile eseguire un controllo più accurato, con test per gli oggetti orfani presenti nell'intera gerarchia del modello. Sui modelli multidimensionali, vengono controllati solo gli indici di partizione. Vedere [Database Consistency Checker &#40;DBCC&#41; per i database tabulari e multidimensionali di Analysis Services](../../analysis-services/instances/database-consistency-checker-dbcc-for-analysis-services.md).  
  
-   Report dei test, fogli di calcolo e dashboard per accertarsi che non si sono verificati cambiamenti in negativo nel comportamento o nei calcoli. Si dovrebbero riscontrare prestazioni più veloci sia per i carichi di lavoro multidimensionali che per quelli tabulari.  
  
-   Verificare le operazioni di elaborazione, correggendo eventuali problemi di accesso o autorizzazione. Se si usa l'account predefinito del servizio per le connessioni, il nuovo servizio viene eseguito con un account diverso. Per altre informazioni sugli account di avvio per Analysis Services, vedere [Configurare gli account del servizio &#40;Analysis Services&#41;](../../analysis-services/instances/configure-service-accounts-analysis-services.md).  
  
-   Verificare il backup e ripristinare le operazioni nel server aggiornato, regolando gli script per l'uso con il nuovo nome del server.  
  
## <a name="database-upgrade"></a>Aggiornamento del database  
 I database creati in versioni precedenti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vengono eseguiti nel server aggiornato con un'impostazione del livello di compatibilità di database precedente. In genere, è possibile aggiornare un database o un modello a un livello di compatibilità più elevato per ottenere l'accesso alle nuove funzionalità, ma questa operazione vincola l'utente a una versione specifica del server.  
  
 Per aggiornare un database, in genere si aggiorna il modello in SQL Server Data Tools (SSDT) e quindi si distribuisce la soluzione a un'istanza del server aggiornato. Vedere [Scaricare la versione più recente di SQL Server Data Tools](https://msdn.microsoft.com/library/mt204009.aspx) per ottenere la versione più recente.  
  
 I database tabulari e multidimensionali seguono percorsi di versione diversi. È un caso che sia i modelli multidimensionali e che i modelli tabulari abbiano un livello di compatibilità pari a 1100.  Le modalità avanzeranno a velocità diverse se le modifiche alle funzionalità influiscono solo uno di questi database.  
  
 Per motivi di background, nella tabella seguente sono riepilogati i livelli di compatibilità, ma è necessario esaminare gli argomenti specifici per conoscere le caratteristiche di ogni livello.  
  
||||  
|-|-|-|  
|Tabella|1200|SQL Server 2016|  
|Tabella|1103|SQL Server 2014|  
|Tabella|1100|SQL Server 2012|  
|Multidimensionale|1100|SQL Server 2012 e versioni successive|  
|Multidimensionale|1050|SQL Server 2005, 2008, 2008 R2|  
  
 Per altre informazioni, vedere [Impostare il livello di compatibilità di un database multidimensionale &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md) e [Livello di compatibilità per i modelli tabulari in Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).  
  
## <a name="tabular-model-upgrade-to-1200-compatibility-level"></a>Aggiornamento del modello tabulare al livello di compatibilità 1200  
 I database e i modelli tabulari ricevono maggiori benefici da SQL Server 2016. Questa versione offre una modalità DirectQuery rivista per i modelli tabulari al livello di compatibilità 1200, semplificata dalla rimozione della modalità ibrida, dall'aggiunta di istruzioni di query per il recupero di un subset di dati in fase di progettazione e della sicurezza a livello di riga tramite DAX al posto delle autorizzazioni di riga nel database back-end.  
  
 Un secondo motivo per eseguire l'aggiornamento è la costruzione di nuovi metadati tabulari all'interno del modello. Un modello tabulare al nuovo livello di compatibilità 1200, sia creato o che aggiornato a tale livello, usa la terminologia nativa per le definizioni dell'oggetto, ad esempio modello, tabelle, relazioni e colonne per descrivere gli elementi principali.  
  
 Per aggiornare un modello tabulare, usare una versione di [SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx) compilata per questa versione al fine di impostare la proprietà **Compatibility Level** su **SQL Server 2016 RTM (1200)**.  
  
 Non usare SSMS, codice o script per modificare il **CompatibilityLevel**. La sola modifica della proprietà non comporta alcun cambiamento. La conversione dei metadati si verifica in SSDT in risposta all'aggiornamento della proprietà, seguito dalla riapertura del progetto.  
  
 Come sempre, assicurarsi di salvare una copia di backup del modello prima dell'aggiornamento nel caso in cui fosse necessario ripristinare la versione pre-aggiornamento.  
  
1.  In SSDT > Esplora soluzioni, fare clic con il pulsante destro del mouse su **model.bim**, scegliere **Visualizza codice** e confermare che il modello verrà chiuso e riaperto in una nuova finestra (finestra del codice).  
  
2.  Il modello si apre come documento XMLA. Per eseguire il confronto dopo la conversione, copiare i contenuti in un altro file (è possibile aprire un nuovo file XML in SSDT).  
  
3.  Fare clic con il pulsante destro del mouse su **model.bim** e impostarlo di nuovo su **Progettazione viste**.  
  
4.  Impostare la proprietà **CompatibilityLevel** su  **SQL Server 2016 RTM (1200)**.  
  
5.  Questo passaggio non può essere annullato. Per questo viene richiesta la conferma dell'azione. Fare clic su **Sì** per continuare. Il progetto sarà aggiornato.  
  
6.  Fare clic con il pulsante destro del mouse su **model.bim** e impostarlo di nuovo su **Visualizza codice**.  
  
     Si noti che, usando i metadati tabulari, la definizione del modello è in JSON.  
  
 **Conversione dei metadati**  
  
 Confrontando i metadati pre e post conversione, si noterà che i metadati vengono convertiti in JSON e le definizioni ridondanti vengono tagliate.  
  
 Il modello consente di mantenere tutte le funzionalità: associazioni di dati, sezioni di partizione, espressioni, identificatori di oggetto, nomi di oggetto, descrizioni, didascalie, traduzioni e annotazioni rimangono integri. Tuttavia, se si dispone di codice o script che fa riferimento a oggetti specifici, parte della riscrittura del codice include la rimozione del riferimento a oggetti che non esistono più. Ad esempio, un modello 1050 o 1103 include sezioni per le dimensioni esterne al cubo, mentre un modello 1200 definisce una tabella come oggetto singolo.  
  
> [!NOTE]  
>  I precedenti livelli di compatibilità tabulare 1050 e 1103 sono supportati ma deprecati. In alcune versioni future di SQL Server, i modelli tabulari trasmessi come oggetti multidimensionali non saranno più supportati. Vedere [Deprecated Analysis Services Features in SQL Server 2016](../../analysis-services/deprecated-analysis-services-features-in-sql-server-2016.md) per l'annuncio.  
  
## <a name="post-upgrade-for-tabular-models-at-1200-compatibilitylevel"></a>Post-aggiornamento per i modelli tabulari a livello di compatibilità 1200  
 Dopo aver convertito il modello, si userà [Tabular Model Scripting Language &#40;TMSL&#41; Reference](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) (Riferimento per Tabular Model Scripting Language &#40;TMSL&#41;) anziché XMLA per le operazioni di script del database. Se il modello è 1200, il TMSL viene generato automaticamente in SSMS. Il codice personalizzato che punta ai database tabulari 1200 deve usare l'API definita nello spazio dei nomi Microsoft.AnalysisServces.Tabular. Script e codice devono essere scritti da zero, poiché non esistono meccanismi di conversione incorporata. Per informazioni sulle operazioni iniziali, vedere [Guida per gli sviluppatori (Analysis Services)](../../analysis-services/analysis-services-developer-documentation.md) .  
  
 È anche possibile aggiungere a un modello tabulare le seguenti funzionalità, supportate solo a livello di compatibilità 1200:  
  
-   Un'implementazione di DirectQuery che supporta nel modello la sicurezza a livello di riga tramite DAX, altre origini dati, subset di dati a scopo di modellazione e configurazione più semplice.  
  
-   Colonne calcolate  
  
-   Cartelle di visualizzazione  
  
## <a name="upgrade-tabular-models-in-directquery-mode"></a>Aggiornare i modelli tabulari in modalità DirectQuery  
 Non è possibile eseguire un aggiornamento sul posto dei modelli tabulari precedenti configurati per DirectQuery. La nuova implementazione di DirectQuery dispone di un'impronta di configurazione ridotta e non tutte le impostazioni possono essere trasferite.  
  
1.  In SSDT disattivare la modalità **DirectQuery** in modo che il modello usi l'archiviazione in memoria. Per istruzioni, vedere [Abilitare la modalità DirectQuery (SSAS tabulare)](https://msdn.microsoft.com/library/hh270245.aspx) .  
  
2.  Impostare la proprietà **CompatibilityLevel** su SQL Server 2016 (RTM) 1200.  
  
3.  Salvare e ricompilare o distribuire il modello.  
  
4.  Riattivare **DirectQuery** . Vedere [DirectQuery for Tabular 1200 models](http://msdn.microsoft.com/library/4227977e-7368-4d45-b78f-24076882e7a8) per maggiori informazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Modalità DirectQuery &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Novità di Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md)   
 [Funzionalità supportate dalle edizioni di SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)   
 [Pianificazione di un'installazione di SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Aggiornare Power Pivot per SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)   
 [Installazione di Analysis Services in modalità Multidimensionale e Data Mining](http://msdn.microsoft.com/library/8a1f33e8-2bd6-4fb8-bd46-c86f2a067f60)   
 [Eseguire l'aggiornamento a SQL Server 2016 usando l'Installazione guidata &#40;programma di installazione&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  

