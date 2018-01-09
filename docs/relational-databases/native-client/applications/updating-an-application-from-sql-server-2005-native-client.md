---
title: Aggiornamento di un'applicazione da SQL Server 2005 Native Client | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|applications
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: SQL Server Native Client, updating applications
ms.assetid: 1e1e570c-7f14-4e16-beab-c328e3fbdaa8
caps.latest.revision: "42"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ea8bd24944008b1301f02024f9aa77910a7dbe37
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="updating-an-application-from-sql-server-2005-native-client"></a>Aggiornamento di un'applicazione da SQL Server 2005 Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  In questo argomento vengono descritte le modifiche di rilievo introdotte in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client rispetto a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 Quando si esegue l'aggiornamento da Microsoft Data Access Components (MDAC) a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, si potrebbero anche notare alcune differenze di comportamento. Per ulteriori informazioni, vedere [aggiornamento di un'applicazione a SQL Server Native Client da MDAC](../../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client 9.0 forniti con [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client 10.0 forniti con [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.5 fornito con [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 fornito con [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] e [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].  
  
|Differenze di comportamento in SQL Server Native Client nelle versione successive a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]|Description|  
|------------------------------------------------------------------------------------|-----------------|  
|In OLE DB viene applicato il riempimento solo in base alla scala definita.|Per le conversioni in cui i dati convertiti vengono inviati al server, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (a partire da [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) vengono inseriti nei dati solo fino alla lunghezza massima di zeri finali **datetime** valori. In SQL Server Native Client 9.0 viene applicato un riempimento fino a un massimo di 9 cifre.|  
|Convalida di DBTYPE_DBTIMESTAMP per ICommandWithParameter::SetParameterInfo.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client (a partire da [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) implementa il requisito OLE DB per *bScale* in ICommandWithParameter::SetParameterInfo sia impostato su precisione dei secondi frazionari per DBTYPE_DBTIMESTAMP.|  
|Il **sp_columns** stored procedure restituisce ora **"NO"** anziché **"NO"** per la colonna IS_NULLABLE.|A partire da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]), **sp_columns** stored procedure restituisce ora **"NO"** anziché **"NO"** per una colonna IS_NULLABLE .|  
|SQLBindCol, SQLBindParameter e SQLSetDescRec ora eseguire la verifica della coerenza.|Prima di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, impostazione di SQL_DESC_DATA_PTR non produceva una verifica coerenza per qualsiasi tipo di descrittore in SQLBindCol, SQLBindParameter o SQLSetDescRec.|  
|SQLCopyDesc ora esegue la verifica di coerenza del descrittore.|Prima di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, SQLCopyDesc non un controllo di coerenza quando il campo SQL_DESC_DATA_PTR veniva impostato su un determinato record.|  
|SQLGetDescRec non è più una descrittore verifica coerenza.|Prima di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, SQLGetDescRec eseguita una verifica coerenza descrittore quando è stato impostato il campo SQL_DESC_DATA_PTR. Tale controllo non è richiesto dalla specifica ODBC e in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) e versioni successive non viene più eseguito.|  
|Quando la data non è inclusa nell'intervallo consentito viene restituito un errore differente.|Per il **datetime** tipo, verrà restituito un numero di errore diverso dalla [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (a partire da [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) per un out-of-range data rispetto a quello restituito nelle versioni precedenti.<br /><br /> In particolare, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 restituisce il numero 22007 per tutti i valori fuori intervallo anno nelle conversioni di stringa per **datetime**, e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client a partire dalla versione 10.0 ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) restituisce 22008 quando la data è compresa nell'intervallo supportato dal **datetime2** ma non compreso nell'intervallo supportato dal **datetime** o **smalldatetime**.|  
|**DateTime** valore tronca i secondi frazionari e non arrotondare se l'arrotondamento verrà modificato il giorno.|Prima di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, il comportamento client per **datetime** valori inviati al server è arrotonda al più vicino 1/300 di secondo. A partire da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, in questo scenario si verifica il troncamento dei secondi frazionari se l'arrotondamento comporta la modifica del giorno.|  
|Possibile troncamento di secondi per **datetime** valore.|In un'applicazione compilata con [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client (o versioni successive) che si connette a un server [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2005 vengono troncati i secondi e i secondi frazionari per la porzione di tempo dei dati inviati al server se si esegue l'associazione a una colonna datetime con un identificatore di tipo DBTYPE_DBTIMESTAMP (OLE DB) o SQL_TIMESTAMP (ODBC) e una scala di 0.<br /><br /> Ad esempio<br /><br /> Dati di input: 1994-08-21 21:21:36.000<br /><br /> Dati inseriti: 1994-08-21 21:21:00.000|  
|La conversione dei dati OLE DB da DBTYPE_DBTIME a DBTYPE_DATE non può più causare la modifica del giorno.|Nelle versioni precedenti a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, se la parte relativa all'ora di un tipo DBTYPE_DATE è entro mezzo secondo dalla mezzanotte, il codice di conversione OLE DB causa la modifica del giorno. A partire da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, il giorno non viene modificato (i secondi frazionari vengono troncati ma non vengono arrotondati).|  
|Modifiche di conversione IBCPSession::BCColFmt.|A partire da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, quando si utilizza IBCPSession::BCOColFmt per convertire SQLDATETIME o SQLDATETIME in un tipo stringa, un valore frazionario viene esportato. Quando ad esempio si converte il tipo SQLDATETIME nel tipo SQLNVARCHARMAX, le versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client restituiscono<br /><br /> 1989-02-01 00:00:00. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 e versioni successive restituiscono 1989-02-01 00:00:00.0000000.|  
|Le dimensioni dei dati inviati devono corrispondere alla lunghezza specificata in SQL_LEN_DATA_AT_EXEC.|Quando si utilizza SQL_LEN_DATA_AT_EXEC, le dimensioni dei dati devono corrispondere alla lunghezza specificata con SQL_LEN_DATA_AT_EXEC. È possibile utilizzare SQL_DATA_AT_EXEC ma l'utilizzo di SQL_LEN_DATA_AT_EXEC comporta vantaggi potenziali in termini di prestazioni.|  
|Le applicazioni personalizzate che utilizzano l'API BCP ora possono visualizzare un avviso.|L'API BCP genererà un messaggio di avviso se la lunghezza dei dati di tutti i tipi è superiore a quella specificata per un campo. In precedenza, questo avviso veniva visualizzato solo per i dati di tipo carattere e non per tutti i tipi.|  
|Inserimento di una stringa vuota in un **sql_variant** associato come tipo Data/ora genera un errore.|In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 l'inserimento di una stringa vuota in un **sql_variant** associato come tipo Data/ora non ha generato un errore. In questa situazione in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 e versioni successive viene correttamente generato un errore.|  
|Convalida dei parametri SQL_C_TYPE _TIMESTAMP e DBTYPE_DBTIMESTAMP più restrittiva.|Prima di [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client, **datetime** i valori sono stati arrotondati in base alla scala di **datetime** e **smalldatetime** colonne da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client (e versioni successive) applica le regole di convalida più restrittive definite nella specifica ODBC per i secondi frazionari. Se non è possibile convertire il valore di un parametro nel tipo SQL utilizzando la scala specificata o implicita dell'associazione client senza causare il troncamento delle cifre finali, viene restituito un errore.|  
|Quando è in esecuzione un trigger, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] potrebbe restituire risultati diversi.|Le modifiche introdotte in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] potrebbe causare risultati diversi restituiti da un'istruzione che ha causato un trigger per l'esecuzione quando a un'applicazione **NOCOUNT OFF** attivo. In una situazione di questo tipo l'applicazione potrebbe generare un errore. Per risolvere questo problema, impostare **NOCOUNT ON** nel trigger o chiamare SQLMoreResults per passare al risultato successivo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione in SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
