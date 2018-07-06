---
title: Aggiornamento di un'applicazione OLE DB driver per SQL Server da MDAC | Documenti Microsoft
description: Aggiornamento di un'applicazione al Driver OLE DB per SQL Server da MDAC
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- MSOLEDBSQL, vs. MDAC
- OLE DB Driver for SQL Server, vs. MDAC
- data access [OLE DB Driver for SQL Server], vs. MDAC
- OLE DB Driver for SQL Server, updating applications
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 11597ed3b7cd80cae8604291bd8b662bf6a9ed80
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2018
ms.locfileid: "35612106"
---
# <a name="updating-an-application-to-ole-db-driver-for-sql-server-from-mdac"></a>Aggiornamento di un'applicazione OLE DB driver per SQL Server da MDAC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Esistono alcune differenze tra il Driver OLE DB per SQL Server e Microsoft Data Access Components (MDAC); a partire da Windows Vista, i componenti di accesso dati ora vengono chiamati Windows Data Access Components (o Windows DAC). Sebbene entrambi forniscono l'accesso ai dati nativa [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database, il Driver OLE DB per SQL Server è stato progettato per esporre le nuove caratteristiche di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], mentre nello stesso momento mantenendo la compatibilità con le versioni precedenti.   

 Inoltre, sebbene MDAC contenga componenti per l'utilizzo di OLE DB, ODBC e ActiveX Data Objects (ADO), il Driver OLE DB per SQL Server implementa solo OLE DB (anche se ADO può accedere alla funzionalità del Driver OLE DB per SQL Server).  

 Il Driver OLE DB per SQL Server e MDAC presentano le differenze nelle aree seguenti:  

-   Gli utenti che utilizzano ADO per accedere il Driver OLE DB per SQL Server possono risultare meno funzionalità di filtro quando accedono a provider OLE DB per SQL.  

-   Se un'applicazione ADO utilizza il Driver OLE DB per SQL Server e tenta di aggiornare una colonna calcolata, verrà restituito un errore. Con MDAC, l'aggiornamento è stato accettato ma ignorato.  

-   Il Driver OLE DB per SQL Server è un file di libreria (DLL) singola collegamento dinamico indipendente. Il numero di interfacce esposte pubblicamente è stato ridotto al minimo, per facilitare la distribuzione e limitare al tempo stesso i rischi legati alla sicurezza.  

-   Sono supportate solo le interfacce OLE DB.  

-   Il Driver OLE DB per i nomi di SQL Server sono diversi dai nomi utilizzati con MDAC.  

-   Funzionalità accessibili all'utente fornite dai componenti MDAC è disponibile quando si utilizza il Driver OLE DB per SQL Server. Le più importanti sono le seguenti: pool di connessioni, supporto ADO e supporto del cursore del client. Quando si utilizzano queste funzionalità, il Driver OLE DB per SQL Server fornisce solo la connettività del database. MDAC fornisce funzionalità come la traccia, i controlli di gestione e i contatori delle prestazioni.  

-   Le applicazioni possono utilizzare servizi principali OLE DB con il Driver OLE DB per SQL Server, ma se si utilizza il motore del cursore OLE DB, è necessario utilizzare l'opzione di compatibilità di tipo di dati per evitare potenziali problemi che potrebbero verificarsi perché il motore del cursore non è a conoscenza del nuovo [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] tipi di dati.  

-   Il Driver OLE DB per SQL Server supporta l'accesso a precedente [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.  

-   Il Driver OLE DB per SQL Server non include l'integrazione XML. Il Driver OLE DB per SQL Server supporta la selezione... PER una query di XML, ma non supporta altre funzionalità XML. Tuttavia, il Driver OLE DB per SQL Server supporta il **xml** tipo di dati introdotti in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  

-   Il Driver OLE DB per SQL Server supporta la configurazione delle librerie di rete sul lato client utilizzando solo gli attributi di stringa di connessione. Per una configurazione delle libreria di rete più completa, è necessario utilizzare Gestione configurazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  

-   Le stringhe di connessione MDAC consentono a un valore booleano (**true**) per il **Trusted_Connection** (parola chiave). Un Driver OLE DB per la stringa di connessione SQL Server deve utilizzare **yes** oppure **nessun**.  

-   Gli avvisi e gli errori non hanno subito modifiche particolarmente rilevanti. Avvisi ed errori restituiti dal server ora mantengono il livello di gravità stesso quando viene passato al Driver OLE DB per SQL Server. Se l'intercettazione di determinati avvisi ed errori riveste un'importanza particolare, è necessario assicurarsi che l'applicazione sia stata sottoposta a test approfonditi.  

-   Il Driver OLE DB per SQL Server ha errori più restrittivo rispetto a MDAC, il che significa che alcune applicazioni che non sono completamente conformi alle specifiche OLE DB possono comportarsi in modo diverso. Ad esempio, il provider SQLOLEDB non ha applicato la regola che i nomi di parametro devono iniziare con '\@' per risultato esegue i parametri, ma il Driver OLE DB per SQL Server.  

-   Il Driver OLE DB per SQL Server si comporta in modo diverso da MDAC alle connessioni non riuscite. Ad esempio, MDAC restituisce i valori delle proprietà memorizzati nella cache per una connessione riuscita, mentre il Driver OLE DB per SQL Server segnala un errore all'applicazione chiamante.  

-   Il Driver OLE DB per SQL Server non genera eventi di Visual Studio Analyzer, ma invece genera eventi di traccia di Windows.  

-   Il Driver OLE DB per SQL Server non può essere utilizzato con perfmon. Perfmon è un strumento di Windows disponibile solo con i DSN che utilizzano il driver MDAC SQLODBC incluso in Windows.  

-   Quando il Driver OLE DB per SQL Server è connesso ad [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] e versioni successive, errore server 16947 viene restituito come un SQL_ERROR. Tale errore si verifica quando tramite un'eliminazione o un aggiornamento posizionato non è possibile aggiornare o eliminare una riga. Con MDAC, in caso di connessione a una versione qualsiasi di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l'errore del server 16947 viene restituito come avviso (SQL_SUCCESS_WITH_INFO).  

-   Il Driver OLE DB per SQL Server implementa la **IDBDataSourceAdmin** interfaccia, ovvero un'interfaccia OLE DB facoltativa non implementata in precedenza, ma solo il **CreateDataSource** di questo metodo parametro facoltativo viene implementata. [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  

-   Il Driver OLE DB per SQL Server restituisce sinonimi nel TABLES e TABLE_INFO set di righe dello schema, con TABLE_TYPE impostato su SYNONYM.  

-   I valori del tipo di dati restituiti **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **xml**, **udt**, o altri tipi LOB non possono essere restituiti al client di versioni precedenti a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Se si desidera utilizzare questi tipi come valori restituiti, è necessario utilizzare il Driver OLE DB per SQL Server.  

-   MDAC consente le istruzioni seguenti da eseguire all'inizio di transazioni manuali e implicite, ma non il Driver OLE DB per SQL Server. L'esecuzione deve avvenire in modalità autocommit.  

    -   Tutte le operazioni full-text (DLL indice e catalogo)  

    -   Tutte le operazioni del database (creazione, modifica ed eliminazione del database)  

    -   Riconfigurazione  

    -   Shutdown  

    -   Esecuzione del comando Kill  

    -   Backup  

-   Quando le applicazioni MDAC si connettono a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], i tipi di dati introdotti in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] vengono visualizzati come tipi di dati compatibili con [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)], come mostrato nella tabella seguente.  

    |Tipo di SQL Server 2005|Tipo di SQL Server 2000|  
    |--------------------------|--------------------------|  
    |**ntext**|**text**|  
    |**nvarchar(max)**|**ntext**|  
    |**varbinary(max)**|**image**|  
    |**udt**|**varbinary**|  
    |**xml**|**ntext**|  

     Questo mapping dei tipi influisce sui valori restituiti per i metadati delle colonne. Ad esempio, un **testo** colonna ha una dimensione massima di 2.147.483.647, ma il Driver OLE DB per SQL Server indica la dimensione massima del **varchar (max)** colonne come 2.147.483.647 o -1, a seconda della piattaforma.  

-   Il Driver OLE DB per SQL Server supporta l'ambiguità nelle stringhe di connessione (ad esempio, alcune parole chiave possono essere specificati più di una volta e possono essere consentite parole chiave in conflitto con una risoluzione basata sulla posizione o sulla precedenza) per motivi di compatibilità con le versioni precedenti. Nelle versioni future di Driver OLE DB per SQL Server potrebbero non consentire l'ambiguità nelle stringhe di connessione. È buona norma quando si modifica alle applicazioni di utilizzare il Driver OLE DB per SQL Server per eliminare qualsiasi dipendenza dall'ambiguità delle stringhe di connessione.  

-   Se si utilizza una chiamata OLE DB per avviare le transazioni, sussiste una differenza nel comportamento tra il Driver OLE DB per SQL Server e MDAC; le transazioni avranno inizio immediatamente con il Driver OLE DB per SQL Server, ma le transazioni inizierà dopo il primo accesso al database tramite MDAC. Questo può influenzare il comportamento di stored procedure e batch perché [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] richiede@TRANCOUNT essere lo stesso dopo che un batch o stored procedure termina com'era quando la stored procedure o batch avviato.  

-   Con Driver OLE DB per SQL Server, ITransactionLocal::BeginTransaction provocherà una transazione deve essere avviata immediatamente. Con MDAC l'avvio della transazione è stata ritardata fino a quando non viene eseguita un'istruzione che è necessaria una transazione in modalità transazione implicita. Per altre informazioni, vedere [SET IMPLICIT_TRANSACTIONS &#40;Transact-SQL&#41;](../../../t-sql/statements/set-implicit-transactions-transact-sql.md).  


 Entrambi Driver OLE DB per SQL Server che MDAC supportano l'isolamento transazione sottoposta a commit utilizzando delle versioni delle righe, ma solo Driver OLE DB per SQL Server supporta l'isolamento delle transazioni read. In termini di programmazione, l'isolamento della transazione Read Committed mediante il controllo delle versioni delle righe equivale a una transazione Read Committed.  

## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni con il driver OLE DB per SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
