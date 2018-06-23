---
title: L'esecuzione di operazioni di copia Bulk | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk copy [SQL Server Native Client]
- data access [SQL Server Native Client], bulk copy operations
- SQL Server Native Client, bulk copy operations
- SQLNCLI, bulk copy operations
ms.assetid: 50d8456b-e6a1-4b25-bc7e-56946ed654a7
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1912c8f7f2c419ff27ed18207a1b910cfb9a209a
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35702872"
---
# <a name="performing-bulk-copy-operations"></a>Esecuzione di operazioni di copia bulk
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  La funzionalità di copia bulk di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporta il trasferimento di grandi quantità di dati in o da una tabella o una vista di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il trasferimento dei dati può essere eseguito anche specificando un'istruzione SELECT. È possibile spostare i dati tra [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e un file di dati del sistema operativo, ad esempio un file ASCII. Il file di dati può avere formati diversi. Per eseguire una copia bulk in un file di formato, è necessario definire il formato. I dati possono essere caricati in variabili di programma e trasferiti a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mediante metodi e funzioni di copia bulk.  
  
 Per un'applicazione di esempio che illustri questa caratteristica, vedere [Bulk copia i dati mediante IRowsetFastLoad &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md).  
  
 In un'applicazione la copia bulk viene generalmente utilizzata in una delle modalità seguenti:  
  
-   Copia bulk da una tabella, da una vista o dal set di risultati di un'istruzione Transact-SQL in un file di dati in cui i dati vengono archiviati nello stesso formato della tabella o della vista.  
  
     Tale file viene definito file di dati in modalità nativa.  
  
-   Copia bulk da una tabella, da una vista o dal set di risultati di un'istruzione Transact-SQL in un file di dati in cui i dati vengono archiviati in un formato diverso da quello della tabella o della vista.  
  
     In questo caso viene creato un file di formato separato che definisce le caratteristiche (tipo di dati, posizione, lunghezza, carattere di terminazione e così via) di ogni colonna che viene archiviata nel file di dati. Se tutte le colonne vengono convertite in formato carattere, il file risultante viene definito file di dati in modalità carattere.  
  
-   Copia bulk da un file di dati in una tabella o una vista.  
  
     Se necessario, viene utilizzato un file di formato per determinare il layout del file di dati.  
  
-   Caricare i dati in variabili di programma, quindi importarli in una tabella o in una vista utilizzando le funzioni di copia bulk per eseguire una copia bulk in una riga per volta.  
  
 Non è necessario che i file di dati utilizzati dalle funzioni di copia bulk vengano creati da un altro programma per la copia bulk. È possibile generare un file di dati e il file di formato in base alle definizioni della copia bulk in qualsiasi altro modo. Tali file possono essere quindi utilizzati con un programma per la copia bulk di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per importare i dati in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. È ad esempio possibile esportare dati da un foglio di calcolo in un file delimitato da tabulazione, compilare un file di formato che descrive il file delimitato da tabulazione, quindi utilizzare un programma per la copia bulk per importare rapidamente i dati in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. I file di dati generati dalla copia bulk possono essere importati anche in altre applicazioni. È ad esempio possibile utilizzare le funzioni di copia bulk per esportare i dati da una tabella o da una vista in un file con valori delimitati da tabulazioni, che è quindi possibile caricare in un foglio di calcolo.  
  
 I programmatori che eseguono la codifica di applicazioni per l'utilizzo delle funzioni di copia bulk devono seguire le regole generali per garantire un buon livello di prestazioni per la copia bulk. Per ulteriori informazioni sul supporto per le operazioni di copia bulk in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vedere [Bulk importazione ed esportazione di dati &#40;SQL Server&#41;](../../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 Un tipo CLR definito dall'utente deve essere associato come dati binari. Anche se un file di formato specifica SQLCHAR come tipo di dati per una colonna con tipo definito dall'utente (UDT) di destinazione, l'utilità BCP tratterà i dati come binari.  
  
 Non utilizzare SET FMTONLY OFF con le operazioni di copia bulk. SET FMTONLY OFF può compromettere la riuscita dell'operazione di copia bulk o determinare risultati imprevisti.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>Provider OLE DB di SQL Server Native Client  
 Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client implementa due metodi per l'esecuzione di operazioni di copia bulk con un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database. Il primo metodo consiste nell'usare il [IRowsetFastLoad](../../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md) comporta l'utilizzo dell'interfaccia per operazioni di copia bulk basate sulla memoria; e il secondo il [IBCPSession](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md) interfaccia per le operazioni di copia bulk basate su file.  
  
### <a name="using-memory-based-bulk-copy-operations"></a>Utilizzo di operazioni di copia bulk basate sulla memoria  
 Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider implementa il **IRowsetFastLoad** interfaccia per esporre il supporto per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] operazioni di copia bulk basate sulla memoria. Il **IRowsetFastLoad** interfaccia implementa il [IRowsetFastLoad:: commit](../../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-commit-ole-db.md) e [IRowsetFastLoad:: InsertRow](../../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-insertrow-ole-db.md) metodi.  
  
#### <a name="enabling-a-session-for-irowsetfastload"></a>Abilitazione di una sessione per IRowsetFastLoad  
 Il consumer notifica al provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client la necessità di eseguire la copia bulk impostando su VARIANT_TRUE la proprietà dell'origine dati SSPROP_ENABLEFASTLOAD specifica del provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Con la proprietà impostata sull'origine dati, il consumer crea una sessione del provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. La nuova sessione consente al consumer di accedere per il **IRowsetFastLoad** interfaccia.  
  
> [!NOTE]  
>  Se il **IDataInitialize** interfaccia viene utilizzata per l'inizializzazione dell'origine dati, quindi è necessario impostare la proprietà SSPROP_IRowsetFastLoad nel *rgPropertySets* parametro del  **IOpenRowset:: OPENROWSET** metodo; in caso contrario, la chiamata per il **OpenRowset** metodo restituirà E_NOINTERFACE.  
  
 L'abilitazione di una sessione per la copia bulk vincola il supporto del provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client per le interfacce nella sessione. Una sessione abilitata per la copia bulk espone solo le interfacce seguenti:  
  
-   **IDBSchemaRowset**  
  
-   **IGetDataSource**  
  
-   **IOpenRowset**  
  
-   **ISupportErrorInfo**  
  
-   **ITransactionJoin**  
  
 Per disabilitare la creazione di set di righe abilitati per la copia bulk e fare in modo che la sessione del provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ripristini l'elaborazione standard, reimpostare SSPROP_ENABLEFASTLOAD su VARIANT_FALSE.  
  
#### <a name="irowsetfastload-rowsets"></a>Set di righe IRowsetFastLoad  
 I set di righe della copia bulk del provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client sono di sola scrittura ma espongono interfacce che consentono al consumer di determinare la struttura di una tabella [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le interfacce seguenti sono esposte su un set di righe del provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client abilitato per la copia bulk:  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
-   **IColumnsRowset**  
  
-   **IConvertType**  
  
-   **IRowsetFastLoad**  
  
-   **IRowsetInfo**  
  
-   **ISupportErrorInfo**  
  
 Le proprietà SSPROP_FASTLOADOPTIONS, SSPROP_FASTLOADKEEPNULLS e SSPROP_FASTLOADKEEPIDENTITY specifiche del provider controllano i comportamenti di un set di righe della copia bulk del provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Le proprietà sono specificate nel *rgProperties* membro di un * rgPropertySets ***IOpenRowset**membro del parametro.  
  
|ID proprietà|Description|  
|-----------------|-----------------|  
|SSPROP_FASTLOADKEEPIDENTITY|Colonna: nessuna<br /><br /> L/S: Lettura/Scrittura<br /><br /> Tipo: VT_BOOL<br /><br /> Impostazione predefinita: VARIANT_FALSE<br /><br /> Descrizione: gestisce i valori Identity forniti dal consumer.<br /><br /> VARIANT_FALSE: i valori per una colonna Identity nella tabella [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vengono generati da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Qualsiasi valore associato per la colonna viene ignorata per la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client.<br /><br /> VARIANT_TRUE: il consumer associa una funzione di accesso che fornisce un valore per una colonna Identity [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La proprietà identity non è disponibile in colonne che NULL, pertanto il consumer fornisce un valore univoco in ogni **IRowsetFastLoad:: Insert** chiamare.|  
|SSPROP_FASTLOADKEEPNULLS|Colonna: nessuna<br /><br /> L/S: Lettura/Scrittura<br /><br /> Tipo: VT_BOOL<br /><br /> Impostazione predefinita: VARIANT_FALSE<br /><br /> Descrizione: gestisce valori NULL per le colonne con un vincolo DEFAULT. Ha effetto solo su colonne di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che supportano valori NULL e alle quali è applicato un vincolo DEFAULT.<br /><br /> VARIANT_FALSE: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] inserisce il valore predefinito per la colonna quando il consumer del provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client inserisce una riga che contiene NULL per la colonna.<br /><br /> VARIANT_TRUE: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] inserisce NULL per il valore di colonna quando il consumer del provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client inserisce una riga contenente NULL per la colonna.|  
|SSPROP_FASTLOADOPTIONS|Colonna: nessuna<br /><br /> L/S: Lettura/Scrittura<br /><br /> Tipo: VT_BSTR<br /><br /> Impostazione predefinita: nessuna<br /><br /> Descrizione: Questa proprietà è lo stesso come il **-h** "*hint*[,... *n*] "opzione del **bcp** utilità. Di seguito sono indicate le stringhe che è possibile utilizzare come opzioni per l'esecuzione della copia bulk di dati in una tabella.<br /><br /> **ORDINE**(*colonna*[**ASC** &#124; **DESC**] [,... *n*]): ordinamento dei dati nel file di dati. Le prestazioni della copia bulk vengono migliorate se il file di dati da caricare viene ordinato in base all'indice cluster della tabella.<br /><br /> **ROWS_PER_BATCH** = *bb*: numero di righe di dati per batch (come *bb*). Il server ottimizza il caricamento bulk in base al valore *bb*. Per impostazione predefinita **ROWS_PER_BATCH** è sconosciuto.<br /><br /> **KILOBYTES_PER_BATCH** = *cc*: numero di kilobyte (KB) di dati per batch (come cc). Per impostazione predefinita **KILOBYTES_PER_BATCH** è sconosciuto.<br /><br /> **TABLOCK**: viene acquisito un blocco a livello di tabella per la durata dell'operazione di copia bulk. Questa opzione migliora in modo significativo le prestazioni, in quanto mantenere attivo un blocco solo per la durata dell'operazione di copia bulk riduce la contesa dei blocchi per la tabella. Una tabella può essere caricata da più client contemporaneamente se la tabella non include indici e **TABLOCK** è specificato. Per impostazione predefinita, il comportamento di blocco è determinato dall'opzione di tabella **tabella di blocco per il caricamento bulk**.<br /><br /> **Check_constraints**: eventuali vincoli *table_name* vengono controllati durante l'operazione di copia bulk. Per impostazione predefinita, i vincoli vengono ignorati.<br /><br /> **FIRE_TRIGGER**: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizza delle versioni delle righe per i trigger e memorizza le versioni di riga nell'archivio delle versioni in **tempdb**. Le ottimizzazioni della registrazione bulk sono, pertanto, disponibili anche quando i trigger sono abilitati. Prima l'importazione bulk di un batch con un numero elevato di righe con i trigger abilitati, potrebbe essere necessario aumentare le dimensioni di **tempdb**.|  
  
### <a name="using-file-based-bulk-copy-operations"></a>Utilizzo di operazioni di copia bulk basate su file  
 Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider implementa il **IBCPSession** interfaccia per esporre il supporto per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] le operazioni di copia bulk basate su file. Il **IBCPSession** interfaccia implementa il [ibcpsession:: BCPColFmt](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md), [ibcpsession:: BCPColumns](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md), [ibcpsession:: Bcpcontrol](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md), [IBCPSession::BCPDone](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpdone-ole-db.md), [ibcpsession:: BCPExec](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpexec-ole-db.md), [ibcpsession:: BCPInit](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md), [ibcpsession::Bcpreadfmt](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md), e [ibcpsession:: Bcpwritefmt](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)metodi.  
  
## <a name="sql-server-native-client-odbc-driver"></a>Driver ODBC di SQL Server Native Client  
 Il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client offre lo stesso supporto per le operazioni di copia bulk disponibili nelle versioni precedenti del driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per informazioni sulle operazioni di copia bulk utilizzando il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client, vedere [l'esecuzione di operazioni di copia Bulk &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità di SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [Proprietà dell'origine dati &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-data-source-objects/data-source-properties-ole-db.md)   
 [Informazioni sull'importazione ed esportazione in blocco di dati &#40;SQL Server&#41;](../../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)   
 [IRowsetFastLoad &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md)   
 [IBCPSession &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Ottimizzazione delle prestazioni dell'importazione Bulk](http://msdn.microsoft.com/library/ms190421\(SQL.105\).aspx)  
  
  
