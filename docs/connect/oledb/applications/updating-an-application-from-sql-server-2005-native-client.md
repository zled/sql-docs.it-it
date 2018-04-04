---
title: Aggiornamento di un'applicazione da SQL Server 2005 Native Client | Documenti Microsoft
description: Aggiornamento di un'applicazione da SQL Server 2005 Native Client
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, updating applications
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6ddeedf937de12337e8882bfa132461dd2c5f7a8
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2018
---
# <a name="updating-an-application-from-sql-server-2005-native-client"></a>Aggiornamento di un'applicazione da SQL Server 2005 Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Questo argomento illustra le modifiche di rilievo nel Driver OLE DB per SQL Server dal [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  

 Quando si aggiorna da Microsoft Data Access Components (MDAC) a Driver OLE DB per SQL Server, è possibile visualizzare alcune differenze di comportamento. Per altre informazioni, vedere [aggiornamento di un'applicazione al Driver OLE DB per SQL Server da MDAC](../../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  

 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 forniti con [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 forniti con [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.5 fornito con [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 fornito con [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] e [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].  

|Modificato il comportamento nel Driver OLE DB per SQL Server rispetto al [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Native Client|Description|  
|------------------------------------------------------------------------------------|-----------------|  
|In OLE DB viene applicato il riempimento solo in base alla scala definita.|Per le conversioni in cui i dati convertiti vengono inviati al server, il Driver OLE DB per SQL Server inserisce zeri finali nei dati solo fino alla lunghezza massima di **datetime** valori. In SQL Server Native Client 9.0 viene applicato un riempimento fino a un massimo di 9 cifre.|  
|Convalida di DBTYPE_DBTIMESTAMP per ICommandWithParameter::SetParameterInfo.|Il Driver OLE DB per SQL Server implementa il requisito OLE DB per *bScale* in ICommandWithParameter::SetParameterInfo sia impostato su precisione dei secondi frazionari per DBTYPE_DBTIMESTAMP.|  
|Il **sp_columns** stored procedure restituisce ora **"NO"** anziché **"NO"** per la colonna IS_NULLABLE.|Nel Driver OLE DB per SQL Server **sp_columns** stored procedure restituisce ora **"NO"** anziché **"NO"** per una colonna IS_NULLABLE.|  
|SQLBindCol, SQLBindParameter e SQLSetDescRec ora eseguire la verifica della coerenza.|Prima di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, impostazione di SQL_DESC_DATA_PTR non produceva una verifica coerenza per qualsiasi tipo di descrittore in SQLBindCol, SQLBindParameter o SQLSetDescRec.|  
|SQLCopyDesc ora esegue la verifica di coerenza del descrittore.|Prima di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, SQLCopyDesc non un controllo di coerenza quando il campo SQL_DESC_DATA_PTR veniva impostato su un determinato record.|  
|SQLGetDescRec non è più una descrittore verifica coerenza.|Prima di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, SQLGetDescRec eseguita una verifica coerenza descrittore quando è stato impostato il campo SQL_DESC_DATA_PTR. Tale controllo non è richiesto dalla specifica ODBC e in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) e versioni successive non viene più eseguito.|  
|Quando la data non è inclusa nell'intervallo consentito viene restituito un errore differente.|Per il **datetime** tipo, un numero di errore diversi restituirà Driver OLE DB per SQL Server per una data out-of-range rispetto a quello restituito nelle versioni precedenti.<br /><br /> In particolare, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 restituisce il numero 22007 per tutti i compreso nell'intervallo di valori di anno nelle conversioni da stringa a **datetime**, e il Driver OLE DB per SQL Server restituisce il numero 22008 quando la data è compresa nell'intervallo supportato dal **datetime2** ma esterna all'intervallo supportato dal **datetime** o **smalldatetime**.|  
|**Data/ora** valore tronca i secondi frazionari e non arrotondare se arrotondamento cambia il giorno.|Prima di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, il comportamento client per **datetime** valori inviati al server è arrotonda al più vicino 1/300 di secondo. Nel Driver OLE DB per SQL Server, questo scenario causa il troncamento dei secondi frazionari se l'arrotondamento comporta la modifica del giorno.|  
|Possibile troncamento di secondi per **datetime** valore.|Un'applicazione compilata con il Driver OLE DB per SQL Server che si connette a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] server 2005 verranno troncati i secondi e secondi frazionari per la parte relativa all'ora dei dati inviati al server se si associa a una colonna datetime con un identificatore di tipo DBTYPE_DBTIMESTAMP ( OLE DB) o SQL_TIMESTAMP (ODBC) e una scala pari a 0.<br /><br /> Esempio:<br /><br /> Dati di input: 1994-08-21 21:21:36.000<br /><br /> Dati inseriti: 1994-08-21 21:21:00.000|  
|La conversione dei dati OLE DB da DBTYPE_DBTIME a DBTYPE_DATE non può più causare la modifica del giorno.|Nelle versioni precedenti a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, se la parte relativa all'ora di un tipo DBTYPE_DATE è entro mezzo secondo dalla mezzanotte, il codice di conversione OLE DB causa la modifica del giorno. Nel Driver OLE DB per SQL Server, il giorno non viene modificato (i secondi frazionari vengono troncati e non vengono arrotondati).|  
|Modifiche di conversione IBCPSession::BCColFmt.|Nel Driver OLE DB per SQL Server, quando si utilizza IBCPSession::BCOColFmt per convertire SQLDATETIME o SQLDATETIME in un tipo stringa, viene esportato un valore frazionario. Ad esempio, quando si converte il tipo SQLDATETIME nel tipo SQLNVARCHARMAX, le versioni precedenti a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 restituito<br /> 1989-02-01 00:00:00.<br />Restituisce il Driver OLE DB per SQL Server <br />1989-02-01 00:00:00.0000000.|  
|Le applicazioni personalizzate che utilizzano l'API BCP ora possono visualizzare un avviso.|L'API BCP genererà un messaggio di avviso se la lunghezza dei dati di tutti i tipi è superiore a quella specificata per un campo. In precedenza, questo avviso veniva visualizzato solo per i dati di tipo carattere e non per tutti i tipi.|  
|Inserimento di una stringa vuota in un **sql_variant** associato come tipo Data/ora genera un errore.|In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 l'inserimento di una stringa vuota in un **sql_variant** associato come tipo Data/ora non ha generato un errore. Il Driver OLE DB per SQL Server genera correttamente un errore in questa situazione.|  
|Quando è in esecuzione un trigger, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] potrebbe restituire risultati diversi.|Le modifiche introdotte in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] potrebbe causare risultati diversi restituiti da un'istruzione che ha causato un trigger per l'esecuzione quando a un'applicazione **NOCOUNT OFF** attivo. In una situazione di questo tipo l'applicazione potrebbe generare un errore. Per risolvere questo problema, impostare **NOCOUNT ON** nel trigger o chiamare SQLMoreResults per passare al risultato successivo.|  

## <a name="see-also"></a>Vedere anche   
 [Driver OLE DB per la programmazione di SQL Server](../../oledb/oledb-driver-for-sql-server-programming.md)
