---
title: Versioni precedenti di SQL Server Management Studio | Microsoft Docs
ms.custom: 
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87f593c3-8b76-4c12-963a-31d35f2fb294
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 0773be32343e4707503b4acb616e5a1c807fe32f
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="previous-sql-server-management-studio-releases"></a>Versioni precedenti di SQL Server Management Studio
  
Sono disponibili le seguenti versioni precedenti di SQL Server Management Studio.


   
### <a name="downloadssdtmediadownloadpng-sql-server-management-studio-165-releasehttpgomicrosoftcomfwlinklinkid832812"></a>![Scaricare](../ssdt/media/download.png) [la versione di SQL Server Management Studio 16.5](http://go.microsoft.com/fwlink/?LinkID=832812)

**Informazioni sulla versione**  
  
*Questa versione di SSMS usa Visual Studio 2015 Isolated Shell.*  
Numero di versione: 16.5  
Numero di build per questa versione: 13.0.16000.28

**Problemi noti relativi a questo build**  

1. Invoke-Sqlcmd inserisce erroneamente più righe quando si verifica il vincolo CHECK. [Argomento Microsoft Connect: 811560](https://connect.microsoft.com/SQLServer/feedback/details/811560)

2. Le versioni localizzate non ITA non funzionano completamente durante la creazione di gruppi di disponibilità.

3. Facendo clic sull'XML del piano di query non viene aperta l'interfaccia utente SSMS corretta.

**Log delle modifiche**

* È stato risolto il problema per cui potrebbe verificarsi un arresto anomalo quando è stato fatto clic su un database con nome della tabella contenente ";:".
* È stato risolto il problema per cui le modifiche apportate alla pagina Modello nella finestra delle proprietà del database tabulare AS devono creare uno script della definizione originale. 
[Argomento Microsoft Connect: 3080744](https://connect.microsoft.com/SQLServer/feedback/details/3080744) 
* È stato risolto il problema per cui i file temporanei vengono aggiunti all'elenco "File recenti".  
[Argomento Microsoft Connect: 2558789](https://connect.microsoft.com/SQLServer/feedback/details/2558789)
* È stato risolto il problema per cui la voce del menu di gestione della compressione è disabilitata per i nodi della tabella utente nell'albero Esplora oggetti.  
[Argomento Microsoft Connect: 3104616](https://connect.microsoft.com/SQLServer/feedback/details/3104616)

* È stato risolto il problema per cui l'utente non è in grado di impostare le dimensioni del carattere per Esplora oggetti, Esplora server registrati, Esplora modelli, nonché per i dettagli di Esplora oggetto. Il carattere per le finestre di esplorazione usato sarà il tipo di carattere Ambiente.  
[Argomento Microsoft Connect: 691432](https://connect.microsoft.com/SQLServer/feedback/details/691432)

* È stato risolto il problema per cui SSMS si riconnette sempre al database predefinito quando la connessione viene interrotta.  
[Argomento Microsoft Connect: 3102337](https://connect.microsoft.com/SQLServer/feedback/details/3102337)

* Sono stati risolti numerosi problemi relativi ai valori DPI alti nella gestione dei criteri e nella finestra di modifica delle query, tra cui le icone del piano di esecuzione.

* È stato risolto il problema della mancanza dell'opzione per la configurazione del carattere e dei colori degli eventi estesi.

* È stato risolto il problema degli arresti anomali di SSMS che si verificano durante la chiusura dell'applicazione o quando si tenta di visualizzare la finestra di dialogo degli errori.


   
### <a name="downloadssdtmediadownloadpng-sql-server-management-studio-1641-september-2016-releasehttpgomicrosoftcomfwlinklinkid828615"></a>![Scaricare](../ssdt/media/download.png) [la versione di SQL Server Management Studio 16.4.1 (settembre 2016)](http://go.microsoft.com/fwlink/?LinkID=828615)

**Informazioni sulla versione**  
  
*Questa versione di SSMS usa Visual Studio 2015 Isolated Shell.*  
Numero di versione: 16.4.1  
Numero di build per questa versione: 13.0.15900.1
  
**Problemi noti relativi a questo build**  

1. **Per un'istanza SSMS è possibile accedere a un solo account di Azure Active Directory con l'Autenticazione universale di Active Directory.**  
    Questa restrizione è limitata all'Autenticazione universale di Active Directory. È invece possibile accedere a server diversi usando l'Autenticazione della password di Active Directory, l'Autenticazione integrata di Active Directory o l'Autenticazione di SQL Server.
    
    In alternativa, è possibile usare un'altra istanza di SSMS per accedere come un altro dell'account di Azure Active Directory. 
    
2. **I comandi Data-Tier Application Framework (DacFx) e Progettazione schema in SSM non supportano l'Autenticazione universale di Active Directory.**  
    I comandi che usano DacFx, ad esempio importazione ed esportazione, e Progettazione schema in SSMS non supportano attualmente l'Autenticazione universale di Active Directory.
    
    In alternativa, è possibile usare altre forme di autenticazione disponibili in SSMS, come l'Autenticazione della password di Active Directory, l'Autenticazione integrata di Active Directory o l'Autenticazione di SQL Server.

3. **SSMS può connettersi solo a istanze di SQL Server 2016 Integrated Services (SSIS 2016).**  
    Esiste un limite noto di compatibilità con SQL Server Integration Services che impedisce la connessione a versioni precedenti.
    
    Come soluzione alternativa a questo problema, è possibile connettersi all'istanza di SQL Server Integration Service tramite la versione di [SSMS allineata con l'istanza di SSIS.](../ssms/previous-sql-server-management-studio-releases.md) 
  
4. **SSMS non salva i piani di manutenzione per SQL Server 2008 R2 e le versione precedenti di SQL Server.**  
    Si tratta di un limite noto che si prevede di risolvere in futuro. Nel frattempo, è possibile usare la [versione di SSMS 2014](../ssms/previous-sql-server-management-studio-releases.md) per salvare i piani di manutenzione.  
    
5. **Le installazioni di SSMS non in lingua inglese potrebbero richiedere l'installazione di un pacchetto di protezione aggiuntivo.**  
Le versioni di SSMS non localizzate in lingua inglese e installate in Windows 8, Windows 7, Windows Server 2012 e Windows Server 2008 R2 richiedono il [pacchetto di aggiornamento della sicurezza KB 2862966](https://support.microsoft.com/en-us/kb/2862966) .
  
6. **Gestione configurazione SQL Server non si avvia se nessuna versione di SQL Server è installata nel computer client**  
    Se si avvia Gestione configurazione SQL Server senza aver installato una versione di SQL Server nel computer client, si riceverà l'errore seguente:   
     `Cannot connect to WMI provider. You do not have permission or the server is unreachable. Note that you can only manage SQL Server 2005 and later servers with SQL Server Configuration Manager. Invalid namespace \[0x8004100e]`,   
   
     * Se sono state aggiunte istanze di SQL Server all'elenco 'Server registrati' in SSMS:  
        1. Passare alla vista Server registrati' in SSMS.  
        2. Fare clic con il pulsante destro del mouse sull'istanza di SQL Server che si vuole configurare.  
        3. Selezionare Gestione configurazione SQL Server... dal menu di scelta rapida.    
          
      * Se non sono state aggiunte istanze di SQL Server all'elenco 'Server registrati' in SSMS:  
        1. Aprire un prompt dei comandi come amministratore.  
        2. Eseguire lo strumento Mofcomp usando il comando seguente:  
    `mofcomp "%programfiles(x86)%\Microsoft SQL Server\130\Shared\sqlmgmproviderxpsp2up.mof"`  
        3. Dopo aver eseguito lo strumento Mofcomp, eseguire i comandi seguenti per riavviare il servizio WMI e rendere effettive le modifiche:  
        `net stop "Windows Management Instrumentation"`  
        `net start “Windows Management Instrumentation”`  

 
**Log delle modifiche** 

*  È stato corretto un problema per cui veniva generato un errore durante il tentativo di modifica di una stored procedure:  
[Argomento Microsoft Connect N. 3103831](https://connect.microsoft.com/SQLServer/feedback/details/3103831)

* Nuovi cmdlet 'Read-SqlTableData', 'Read-SqlViewData' e 'Write-SqlTableData' per visualizzare e scrivere dati tramite PowerShell.  
[Scheda Read-SqlTableData di Trello](https://trello.com/c/FXVUNJ8x/131-read-sqltabledata)  
[Argomento Microsoft Connect N. 2685363](https://connect.microsoft.com/SQLServer/feedback/details/2685363)
    
* Nuovo cmdlet 'Add-SqlLogin' per abilitare nuovi scenari di gestione degli account di accesso tramite PowerShell.  
[Argomento Microsoft Connect N. 2588952](https://connect.microsoft.com/SQLServer/feedback/details/2588952)
    
*  Supporto migliorato e facilità d'uso per la connessione a vari cloud nazionali da parte degli utenti.
    
*  È stato corretto un problema per cui veniva generata un'eccezione di tipo memoria insufficiente.  
[Argomento Microsoft Connect N. 3062914](https://connect.microsoft.com/SQLServer/feedback/details/3062914)  
[Argomento Microsoft Connect N. 3074856](https://connect.microsoft.com/SQLServer/feedback/details/3074856)
    
*  È stato corretto un problema per cui l'opzione di filtro in base allo schema non era considerata valida.  
[Argomento Microsoft Connect N. 3058105](https://connect.microsoft.com/SQLServer/feedback/details/3058105)  
[Argomento Microsoft Connect N. 3101136](https://connect.microsoft.com/SQLServer/feedback/details/3101136)
    
*  È stato corretto un problema per cui la finestra Monitoraggio per un database con estensione non risultava accessibile.
    
*  È stato corretto un problema per cui la Guida apriva sempre contenuto online. Gli utenti possono ora decidere se preferiscono la guida online oppure offline tramite "Imposta preferenza Guida" nel menu della guida.   
[Argomento Microsoft Connect N. 2826366](https://connect.microsoft.com/SQLServer/feedback/details/2826366)
    
*  È stato corretto un problema per cui l'inserimento nello script di un modello tabulare di Analysis Services di livello 1200 non rimuoveva la password per gli script, anche se la versione del server aveva [l'oggetto modello client sincronizzato prima dell'esecuzione dello script].
    
*  È stato corretto un problema per cui l'opzione 'SELEZIONA LE PRIME N RIGHE' generava sintassi deprecata per l'operatore TOP.  
[Argomento Microsoft Connect N. 3065435](https://connect.microsoft.com/SQLServer/feedback/details/3065435)
    
*  Sono stati corretti vari problemi di layout tramite SSMS, tra cui la pagina Proprietà account di accesso e le opzioni avanzate di esecuzione query.   
[Argomento Microsoft Connect N. 3058199](https://connect.microsoft.com/SQLServer/feedback/details/3058199)  
[Argomento Microsoft Connect N. 3079122](https://connect.microsoft.com/SQLServer/feedback/details/3058199)  
[Argomento Microsoft Connect N. 3071384](https://connect.microsoft.com/SQLServer/feedback/details/3071384)
    
*  È stato corretto un problema per cui una soluzione veniva creata automaticamente ogni volta che un utente apriva una nuova finestra di query.   
[Argomento Microsoft Connect N. 2924667](https://connect.microsoft.com/SQLServer/feedback/details/2924667)    
[Argomento Microsoft Connect N. 2917742](https://connect.microsoft.com/SQLServer/feedback/details/2917742)   
[Argomento Microsoft Connect N. 2612635](https://connect.microsoft.com/SQLServer/feedback/details/2612635)
    
*  È stato corretto un problema per cui le tabelle temporali non potevano essere espanse in Esplora oggetti nei database di sistema.  
[Argomento Microsoft Connect N. 2551649](https://connect.microsoft.com/SQLServer/feedback/details/2551649)
    
*  Correzione di un problema per cui SSMS esegue una query per SELECT @@trancount dopo l'esecuzione di un batch.    
[Argomento Microsoft Connect N. 3042364](https://connect.microsoft.com/SQLServer/feedback/details/3042364)
    
*  È stato corretto un problema in Analysis Services per cui la creazione di uno script dalla pagina delle proprietà di un server generava una finestra di dialogo di connessione nascosta.
    
*  È stato corretto un problema per cui CTRL+Q non selezionava la barra degli strumenti Avvio veloce.
    
*  È stato corretto un problema per cui la modifica del valore MaxSize di un database tramite la finestra di dialogo Proprietà server è stata interrotta per i database > 2 TB.  
[Argomento Microsoft Connect n. 1231091](https://connect.microsoft.com/SQLServer/feedback/details/1231091)
    
*  È stato corretto un problema per cui la procedura guidata Ripristina database non accettava nomi di file con spazio vuoto iniziale:   
[Argomento Microsoft Connect N. 2395147](https://connect.microsoft.com/SQLServer/feedback/details/2395147)

*  È stato corretto un problema per cui la procedura guidata Ripristina database non accettava nomi di file con spazio vuoto iniziale:   
[Argomento Microsoft Connect N. 2395147](https://connect.microsoft.com/SQLServer/feedback/details/2395147)



### <a name="downloadssdtmediadownloadpng-sql-server-management-studio-163-august-2016-releasehttpgomicrosoftcomfwlinklinkid824938"></a>![Scaricare](../ssdt/media/download.png) [la versione di SQL Server Management Studio 16.3 (agosto 2016)](http://go.microsoft.com/fwlink/?LinkID=824938)
 15 agosto 2016 | Numero di versione: 13.0.15700.28

**Funzionalità**  
1. Nuova opzione di autenticazione 'Autenticazione universale di Active Directory'
2. Nuovi cmdlet per il modulo di PowerShell per SQL Server
3. Miglioramenti a Ottimizzazione guidata motore di database e ai modelli di eventi estesi
4. Supporto beta iniziale per [Display ad alta risoluzione in SSMS](https://blogs.msdn.microsoft.com/sqlreleaseservices/ssms-highdpi-support/)

[Altre informazioni e funzionalità disponibili nel log delle modifiche di SSMS.](../ssms/sql-server-management-studio-changelog-ssms.md)

**Problemi noti**

Di seguito è possibile trovare un elenco di problemi e limitazioni relativi a questa versione di SQL Server Management Studio:  

1. **Per un'istanza SSMS è possibile accedere a un solo account di Azure Active Directory con l'Autenticazione universale di Active Directory.**  
    Questa restrizione è limitata all'Autenticazione universale di Active Directory. È invece possibile accedere a server diversi usando l'Autenticazione della password di Active Directory, l'Autenticazione integrata di Active Directory o l'Autenticazione di SQL Server.
    
    In alternativa, è possibile usare un'altra istanza di SSMS per accedere come un altro dell'account di Azure Active Directory. 
    
2. **I comandi Data-Tier Application Framework (DacFx) e Progettazione schema in SSM non supportano l'Autenticazione universale di Active Directory.**  
    I comandi che usano DacFx, ad esempio importazione ed esportazione, e Progettazione schema in SSMS non supportano attualmente l'Autenticazione universale di Active Directory.
    
    In alternativa, è possibile usare altre forme di autenticazione disponibili in SSMS, come l'Autenticazione della password di Active Directory, l'Autenticazione integrata di Active Directory o l'Autenticazione di SQL Server.

3. **SSMS può connettersi solo a istanze di SQL Server 2016 Integrated Services (SSIS 2016).**  
    Esiste un limite noto di compatibilità con SQL Server Integration Services che impedisce la connessione a versioni precedenti.
    
    Come soluzione alternativa a questo problema, è possibile connettersi all'istanza di SQL Server Integration Service tramite la versione di [SSMS allineata con l'istanza di SSIS.](../ssms/previous-sql-server-management-studio-releases.md) 
  
4. **SSMS non salva i piani di manutenzione per SQL Server 2008 R2 e le versione precedenti di SQL Server.**  
    Si tratta di un limite noto che si prevede di risolvere in futuro. Nel frattempo, è possibile usare la [versione di SSMS 2014](../ssms/previous-sql-server-management-studio-releases.md) per salvare i piani di manutenzione.  
    
5. **Le installazioni di SSMS non in lingua inglese potrebbero richiedere l'installazione di un pacchetto di protezione aggiuntivo.**  
Le versioni di SSMS non localizzate in lingua inglese e installate in Windows 8, Windows 7, Windows Server 2012 e Windows Server 2008 R2 richiedono il [pacchetto di aggiornamento della sicurezza KB 2862966](https://support.microsoft.com/en-us/kb/2862966) .
  
6. **Gestione configurazione SQL Server non si avvia se nessuna versione di SQL Server è installata nel computer client**  
    Se si avvia Gestione configurazione SQL Server senza aver installato una versione di SQL Server nel computer client, si riceverà l'errore seguente:   
     `Cannot connect to WMI provider. You do not have permission or the server is unreachable. Note that you can only manage SQL Server 2005 and later servers with SQL Server Configuration Manager. Invalid namespace \[0x8004100e]`,   
   
     * Se sono state aggiunte istanze di SQL Server all'elenco 'Server registrati' in SSMS:  
        1. Passare alla vista Server registrati' in SSMS.  
        2. Fare clic con il pulsante destro del mouse sull'istanza di SQL Server che si vuole configurare.  
        3. Selezionare Gestione configurazione SQL Server... dal menu di scelta rapida.    
          
      * Se non sono state aggiunte istanze di SQL Server all'elenco 'Server registrati' in SSMS:  
        1. Aprire un prompt dei comandi come amministratore.  
        2. Eseguire lo strumento Mofcomp usando il comando seguente:  
    `mofcomp "%programfiles(x86)%\Microsoft SQL Server\130\Shared\sqlmgmproviderxpsp2up.mof"`  
        3. Dopo aver eseguito lo strumento Mofcomp, eseguire i comandi seguenti per riavviare il servizio WMI e rendere effettive le modifiche:  
        `net stop "Windows Management Instrumentation"`  
        `net start “Windows Management Instrumentation”`  


**Correzioni**
1. Correzione di bug per visualizzare testo non crittografato di colonne LOB (large object) di AlwaysEncrypted decrittografate in SSMS (Argomento Microsoft Connect N. 2413024).
2. Correzione di bug nella finestra di dialogo 	Crittografia sempre attiva per correggere l'arresto anomalo quando gli stili visivi di Windows non sono abilitati (ad esempio, abilitazione della visualizzazione con contrasto elevato).
3. Correzione di bug per l'errore "Impossibile trovare il metodo" che impedisce la connessione alle istanze di SQL Server.
4. Correzione di bug per l'arresto anomalo di SSMS durante la creazione di una funzione di partizione con offset di datetime.
5. Correzione di bug per rimuovere il requisito di Microsoft .NET 3.5 per l'avvio dello strumento di amministrazione Riesecuzione distribuita (DReplay.exe).
6. Correzione di bug in Creazione guidata di distribuzione di Analysis Services per supportare i nomi dei server completi.
7. Correzione di bug in SSMS per visualizzare le partizioni nei modelli tabulari di Analysis Services con un modello di compatibilità 2016 (Argomento Microsoft Connect N. 2845053).

[Altre informazioni sulle correzioni disponibili nel log delle modifiche di SSMS.](../ssms/sql-server-management-studio-changelog-ssms.md)
 
---
### <a name="downloadssdtmediadownloadpng-sql-server-management-studio-july-2016-hotfix-update-releasehttpgomicrosoftcomfwlinklinkid822301"></a>![Scaricare](../ssdt/media/download.png) [la versione di SQL Server Management Studio - Aggiornamento hotfix luglio 2016](http://go.microsoft.com/fwlink/?LinkID=822301)

13 luglio 2016 | Numero di versione: 13.0.15600.2

**Funzionalità**  
1. Supporto per Azure SQL Data Warehouse in SSMS.   
2. Aggiornamenti significativi al modulo SQL Server PowerShell.   
3. Tempi di connessione ai database SQL di Azure significativamente migliorati.  
4. Supporto migliorato per i database tabulari SQL Server 2016 (livello di compatibilità 1200) nella finestra di dialogo di elaborazione Analysis Services e molto altro.   

[Altre informazioni e funzionalità disponibili nel log delle modifiche di SSMS.](../ssms/sql-server-management-studio-changelog-ssms.md)

**Problemi noti** 
1. **Il programma di installazione per la versione dell'hotfix di SSMS di luglio viene visualizzato come versione di agosto di SSMS.**
Nella pagina di installazione per l'hotfix di aggiornamento di luglio è indicato agosto a causa di un'impostazione di compilazione interna. Il pacchetto è in realtà un hotfix per la versione di SSMS di luglio. 
2. **SSMS non si connette a istanze di SQL Server dopo aver installato la versione dell'hotfix di luglio 2016.**
È noto un problema che riguarda l'ultimo aggiornamento di SSMS. Il tentativo di connettersi a un server causa il messaggio di errore seguente: 
   ```
    "Method not found: 'Void Microsoft.SqlServer.Management.Common.SqlConnectionInfo.set_ApplicationIntent(System.String)'"
    ```
  
    La correzione di questo problema sarà disponibile nella prossima versione di SSMS. Come soluzione alternativa per questo problema, è possibile disinstallare e reinstallare SSMS. Per altri dettagli, [visitare questo thread di Microsoft Connect sul problema](https://connect.microsoft.com/SQLServer/feedback/details/2925257/not-able-to-connect-to-sql-server-instances-after-installing-ssms-2016-july-update).
    
3. **SSMS si arresta in modo anomalo quando si tenta di selezionare un account di archiviazione di Azure.**
La versione di SSMS di luglio e il relativo hotfix si arrestano in modo anomalo quando si tenta di selezionare un account di archiviazione di Azure e il "classico" account di archiviazione non è disponibile.
La correzione di questo problema sarà disponibile in una prossima versione di SSMS. Come soluzione alternativa a questo problema, è possibile eseguire il backup/ripristinare i database in un account di archiviazione di Azure creando un account di archiviazione classico oppure [usando T-SQL per eseguire il backup o il ripristino](https://msdn.microsoft.com/library/jj720552(v=sql.120).aspx).

4. **SSMS visualizzerà solo gli account di archiviazione di Azure"classici" nel backup/ripristino guidato.**
La versione di SSMS di luglio e il relativo hotfix visualizzano solo gli account di archiviazione di Azure "classici" per la creazione di nuove credenziali se si tenta di eseguire il backup o il ripristino tramite le procedure guidate.
La correzione di questo problema sarà disponibile in una prossima versione di SSMS. Come soluzione alternativa a questo problema, è possibile eseguire il backup/ripristinare i database nell'account di archiviazione di Azure "classico" oppure eseguire il backup negli account di storage di "tipo ARM" [usando T-SQL per eseguire il backup o il ripristino](https://msdn.microsoft.com/library/jj720552(v=sql.120).aspx). 

5. **Le installazioni di SSMS non in lingua inglese potrebbero richiedere l'installazione di un pacchetto di protezione aggiuntivo.**
Le versioni di SSMS localizzate in lingue diverse dall'inglese e installate in Windows 8, Windows 7, Windows Server 2012 e Windows Server 2008 R2 richiedono il [pacchetto di aggiornamento della sicurezza KB 2862966](https://support.microsoft.com/en-us/kb/2862966) .
6. **SSMS può connettersi solo a istanze di SQL Server 2016 Integrated Services (SSIS 2016).** Esiste un limite noto di compatibilità con SQL Server Integration Services che impedisce la connessione a versioni precedenti.
Come soluzione alternativa di questo problema, è possibile connettersi all'istanza di SQL Server Integration Service tramite la versione di SSMS allineata con l'istanza di SSIS.
7. **SSMS non salva i piani di manutenzione per SQL Server 2008 R2 e le versione precedenti di SQL Server.** Una correzione di questo problema è in fase di sviluppo. Nel frattempo, è possibile usare la versione di SSMS 2014 seguente per salvare i piani di manutenzione.
8. **Gestione configurazione SQL Server non si avvia se nessuna versione di SQL Server è installata nel computer client.** Se si avvia Gestione configurazione SQL Server senza aver installato una versione di SQL Server nel computer client, si riceverà l'errore "Impossibile connettersi al provider WMI". Soluzione alternativa:
    * Aprire un prompt dei comandi come amministratore.
    * Eseguire lo strumento Mofcomp usando il comando seguente:  
      mofcomp "%programfiles(x86)%\Microsoft SQL Server\130\Shared\sqlmgmproviderxpsp2up.mof"
    * Dopo aver eseguito lo strumento Mofcomp, eseguire i comandi seguenti per riavviare il servizio WMI e rendere effettive le modifiche:  
       net stop "Windows Management Instrumentation"  
       net start "Windows Management Instrumentation"

**Correzioni**  
1. Correzione del bug nella progettazione query di SSMS per consentire l'aggiunta di tabelle alla progettazione nel caso in cui un utente non disponga delle autorizzazioni SELECT necessarie.
2. Correzione di bug per l'aggiunta del supporto IntelliSense per le funzioni 'TRY_CAST()' e 'TRY_CONVERT()' [(argomento Microsoft Connect N. 2453461)](https://connect.microsoft.com/SQLServer/feedback/details/2453461/sql-server-2012-issue-with-try-cast).
3. Correzione di bug nella finestra dell'editor SSMS per consentire l'apertura dei file SQL mediante trascinamento della selezione [(argomento Microsoft Connect N. 2690658)](https://connect.microsoft.com/SQLServer/feedback/details/2690658/cannot-drag-sql-files-into-management-studios).
4. Correzione di bug in Analysis Services per visualizzare correttamente il provider di feed di dati per modelli Analysis Services multidimensionali.
5. Correzione di bug in SSMS per evitare l'arresto anomalo del sistema quando si modifica un collegamento di join in Progettazione tabelle di SSMS [argomento Microsoft Connect N. 2721052)](https://connect.microsoft.com/SQLServer/feedback/details/2721052/ssms-view-design-mode-right-click-on-join-crashes-ssms).  

[Altre informazioni e correzioni di bug disponibili nel log delle modifiche di SSMS.](../ssms/sql-server-management-studio-changelog-ssms.md)

---
### <a name="downloadssdtmediadownloadpng-sql-server-management-studio-june-2016-releasehttpgomicrosoftcomfwlinklinkid799832"></a>![Scaricare](../ssdt/media/download.png) [la versione di SQL Server Management Studio di giugno 2016](http://go.microsoft.com/fwlink/?LinkID=799832)

01 giugno 2016 |Numero di versione: 13.0.15000.23

**Funzionalità**  
Nuovo programma di installazione di SSMS semplificato. Versioni autonome di SSMS. Verifica automatica degli aggiornamenti disponibili. Nuova finestra di dialogo Ricerca veloce. SSMS sulla base di Visual Studio 2015 Shell, e molto altro.   
[Altre informazioni disponibili nel log delle modifiche di SSMS.](../ssms/sql-server-management-studio-changelog-ssms.md)

**Problemi noti** 
1. **La generazione di script PowerShell nella procedura guidata Crittografia sempre attiva è attualmente disattivata.**
Una correzione a questo problema sarà disponibile in un aggiornamento mensile successivo di SSMS.
2. **La voce di menu contestuale Crittografa colonne in Esplora oggetti è disattivata per le tabelle e le colonne quando si è connessi al database SQL di Azure.** Una correzione a questo problema sarà disponibile in un aggiornamento mensile successivo di SSMS. In alternativa, fare clic con il pulsante destro del mouse sul database in Esplora Oggetti, selezionare Attività e scegliere Crittografa colonne per crittografare le colonne e le tabelle del database SQL di Azure.
3. **SSMS può connettersi solo a istanze di SQL Server 2016 Integrated Services (SSIS 2016).** Esiste un limite noto di compatibilità con SQL Server Integration Services che impedisce la connessione a versioni precedenti.
Come soluzione alternativa di questo problema, è possibile connettersi all'istanza di SQL Server Integration Service tramite la versione di SSMS allineata con l'istanza di SSIS.
4. **SSMS non salva i piani di manutenzione per SQL Server 2008 R2 e le versione precedenti di SQL Server.** Una correzione di questo problema è in fase di sviluppo. Nel frattempo, è possibile usare la versione di SSMS 2014 seguente per salvare i piani di manutenzione.
5. **Gestione configurazione SQL Server non si avvia se nessuna versione di SQL Server è installata nel computer client.** Se si avvia Gestione configurazione SQL Server senza aver installato una versione di SQL Server nel computer client, si riceverà l'errore "Impossibile connettersi al provider WMI". Soluzione alternativa:
    * Aprire un prompt dei comandi come amministratore.
    * Eseguire lo strumento Mofcomp usando il comando seguente:  
      mofcomp "%programfiles(x86)%\Microsoft SQL Server\130\Shared\sqlmgmproviderxpsp2up.mof"
    * Dopo aver eseguito lo strumento Mofcomp, eseguire i comandi seguenti per riavviare il servizio WMI e rendere effettive le modifiche:  
       net stop "Windows Management Instrumentation"  
       net start "Windows Management Instrumentation"

**Correzioni**  
1. Nuova finestra di dialogo Ricerca veloce in SSMS meglio integrata nel documento corrente che consente la ricerca tramite espressioni regolari ([articolo n. 2735513 di Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/2735513/quick-find-replace-in-ssms-2016-rc3/)).
2. Correzione del bug nella Guida sensibile al contesto di SSMS (F1) per visualizzare correttamente i documenti e gli articoli della Guida.
3. Correzione del bug nella vista Query regredite di Archivio dati query che provocava l'arresto anomalo di SSMS durante lo scorrimento.
4. Correzione del bug nel connettore OLEDB di Analysis Services per Excel per consentire le connessioni da Excel 2016 a SQL Server Analysis Services.
5. Correzione del bug nella finestra di dialogo Connessione di SSMS per visualizzare la finestra di dialogo di connessione sullo stesso monitor come finestra principale di SSMS in sistemi con più monitor ([articolo n.724909 di Microsoft Connect)](https://connect.microsoft.com/SQLServer/feedback/details/724909/connection-dialog-appears-off-screen/).
6. Correzioni di bug in Always Encrypted. Bug corretto dove l'opzione di menu Crittografia sempre attiva non risultava abilitata correttamente per l'estensione database. Bug corretto anche nella procedura guidata Crittografia sempre attiva dove non veniva eseguita correttamente tramite il provider HSM SafeNet (Luna SA).

---
### <a name="downloadssdtmediadownloadpng-sql-server-management-studio-2014-sp1httpdownloadmicrosoftcomdownload156156992e6-f7c7-4e55-833d-249bd2348138enux86sqlmanagementstudiox86enuexe"></a>![Scaricare](../ssdt/media/download.png) [SQL Server Management Studio 2014 SP1](http://download.microsoft.com/download/1/5/6/156992E6-F7C7-4E55-833D-249BD2348138/ENU/x86/SQLManagementStudio_x86_ENU.exe)

14 maggio 2015 | Numero di versione: 12.0.4100.1

**Funzionalità**  
Supporto migliorato di Database SQL di Azure con nuova apertura nel menu del portale di gestione, integrazione di progettazione tabelle e altro ancora.   
[Altre informazioni disponibili nelle note sulla versione](https://support.microsoft.com/en-us/kb/3058865).

**Problemi noti**  
N/D

**Correzioni**
1. SSMS si arresta in modo anomalo durante le attività di spostamento del piano di manutenzione se il nome del piano di manutenzione e il primo nome di SUB_PLAN coincidono.
2. Non è possibile eseguire il debug di una stored procedure che chiama sp_executesql in SQL Server Management Studio (SSMS). Quando si preme F11, viene visualizzato un messaggio di errore "Riferimento oggetto non impostato su un'istanza di un oggetto" ([articolo n.736509 di Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/736509/sql-server-2012-rtm-management-studio-cannot-debug-sp-executesql)).
3. SSMS non gestisce completamente Full-Text in SQL Server Express ([articolo n.740181 di Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/740181/management-studio-does-not-fully-manage-full-text-in-sql-server-express)).
4. SSMS gestisce stored procedure numerate in modo non coerente ( [articolo n.764197 di Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/764197/ssms-2012-inconsistently-handles-numbered-procedures)).
5. In alcuni casi SSM si arresta in modo anomalo, provocando il riavvio automatico ([articolo n.774317 di Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/774317/sql-server-management-studio-2012-2014-crashes-when-closing)).
6. Creare script duplica le istruzioni durante lo scripting di autorizzazioni a livello di colonna in SSMS ([articolo n.797967 di Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/797967/ssms-create-script-duplicates-the-statements-for-grant-or-deny-column-permissions)).
7. È possibile che SSMS si arresti in modo anomalo quando si tenta di aggiornare l'icona della finestra di SSMS sulla barra delle applicazioni ([articolo n.799430 di Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/799430/ssms-2012-sp-1-cu-5-installed-crash-when-enforce-refresh-on-connect)).

---
### <a name="downloadssdtmediadownloadpng-sql-server-management-studio-2012-sp3httpdownloadmicrosoftcomdownloadf67f673709c-d371-4a64-8bf9-c1dd73f60990enux86sqlmanagementstudiox86enuexe"></a>![Scaricare](../ssdt/media/download.png) [SQL Server Management Studio 2012 SP3](http://download.microsoft.com/download/F/6/7/F673709C-D371-4A64-8BF9-C1DD73F60990/ENU/x86/SQLManagementStudio_x86_ENU.exe)  
  
21 novembre 2015 | Numero di versione: 11.0.6020.0

**Funzionalità**  
Edizioni Express di SSMS con funzionalità complete. Frammenti di codice. Indici Columnstore e altro ancora.  
[Altre informazioni disponibili nelle note sulla versione.](https://support.microsoft.com/en-us/kb/3072779)
 
**Problemi noti**  
N/D

**Correzioni**
1. Non è possibile indicare le colonne mancanti nel messaggio di errore quando si importano dati tramite Importazione/Esportazione guidata.
2. Errore "Impossibile creare il piano di ripristino a causa di un'interruzione nella catena LSN" quando si ripristina un backup differenziale in SSMS

---
### <a name="additional-downloads"></a>Download aggiuntivi  
Per un elenco di tutti i download di SQL Server Management Studio, vedere [Area download Microsoft](https://www.microsoft.com/en-us/download/search.aspx?q=sql%20server%20management%20studio&p=0&r=10&t=&s=Relevancy~Descending).  
  
Per la versione più recente di SQL Server Management Studio, vedere [Scaricare SQL Server Management Studio &#40;SSMS&#41;](../ssms/download-sql-server-management-studio-ssms.md).  

---  
## <a name="related-resources"></a>Risorse correlate
[Update center for Microsoft SQL Server (Centro aggiornamenti per Microsoft SQL Server) (Centro aggiornamenti per Microsoft SQL Server)](https://technet.microsoft.com/sqlserver/ff803383.aspx)   
[Esercitazione: SQL Server Management Studio](http://msdn.microsoft.com/en-us/d2bade70-07cf-4d94-b5d2-88aecb538ed1)  
[Forum di SQL Server Management Studio](https://social.msdn.microsoft.com/forums/en-us/home?forum=sqltools)  

  

