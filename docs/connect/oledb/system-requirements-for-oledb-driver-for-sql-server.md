---
title: Requisiti di sistema per il Driver OLE DB per SQL Server | Documenti Microsoft
description: Requisiti per il Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- system requirements [OLE DB Driver for SQL Server]
- data access [OLE DB Driver for SQL Server], system requirements
- OLE DB Driver for SQL Server, system requirements
- MSOLEDBSQL, system requirements
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: e109f228d8b902e5c34b4ed5731b80e315fffe3c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="system-requirements-for-ole-db-driver-for-sql-server"></a>Requisiti di sistema per il Driver OLE DB per SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  Per usare le caratteristiche di accesso ai dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio MARS, è necessario verificare che sia installato il software indicato di seguito:  

-   Driver OLE DB per SQL Server nel client.  

-   Un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sul server.   

> [!NOTE]  
>  Assicurarsi di accedere con privilegi di amministratore prima di installare il software.  

## <a name="operating-system-requirements"></a>Requisiti del sistema operativo  
 Per un elenco di sistemi operativi che supportano il Driver OLE DB per SQL Server, vedere [supporta i criteri per il Driver OLE DB per SQL Server](../oledb/applications/support-policies-for-oledb-driver-for-sql-server.md).  

## <a name="sql-server-requirements"></a>Requisiti di SQL Server  
 Per utilizzare il Driver OLE DB per SQL Server per accedere ai dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, è necessario disporre di un'istanza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installato.  

 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] supporta connessioni da tutte le versioni di MDAC, Windows Data Access Components e tutte le versioni di Driver OLE DB per SQL Server. Quando si stabilisce una connessione tra una versione client meno recente e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], i tipi di dati del server non riconosciuti dal client vengono mappati a tipi compatibili con la versione client. Per altre informazioni, vedere Compatibilità dei tipi di dati per le versioni client, più avanti in questo argomento.  

## <a name="cross-language-requirements"></a>Requisiti per lingue diverse  
 La versione in lingua inglese del Driver OLE DB per SQL Server è supportata in tutte le versioni localizzate dei sistemi operativi supportati. Le versioni localizzate di Driver OLE DB per SQL Server sono supportate nei sistemi operativi localizzati nella lingua stesso come il localizzata Driver OLE DB per SQL Server versione. Le versioni localizzate di Driver OLE DB per SQL Server sono supportate anche nelle versioni in lingua inglese dei sistemi operativi supportati, purché le impostazioni della lingua corrispondente sono installate.  

 Per gli aggiornamenti:  

-   Versioni in lingua inglese del Driver OLE DB per SQL Server possono essere aggiornate a una versione localizzata di Driver OLE DB per SQL Server.  

-   Le versioni localizzate di Driver OLE DB per SQL Server possono essere aggiornate alle versioni localizzate di Driver OLE DB per SQL Server nella stessa lingua.  

-   Versione localizzata del Driver OLE DB per SQL Server può essere aggiornata alla versione in lingua inglese di Driver OLE DB per SQL Server.  

-   Impossibile aggiornare le versioni localizzate di Driver OLE DB per SQL Server a localizzata Driver OLE DB per SQL Server versione di una lingua diversa.  

## <a name="data-type-compatibility-for-client-versions"></a>Compatibilità dei tipi di dati per le versioni client  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e il Driver OLE DB per SQL Server mappa nuovi tipi di dati meno recenti che sono compatibili con i client legacy, come illustrato nella tabella seguente.  

 Le applicazioni OLE DB e ADO possono utilizzare il **DataTypeCompatibility** parola chiave di stringa di connessione con il Driver OLE DB per SQL Server per il funzionamento con tipi di dati precedenti. Quando **DataTypeCompatibility = 80**, i client OLE DB si connetteranno utilizzando il [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] del flusso di dati tabulari, versione (TDS Tabular) anziché la versione TDS. Ciò significa che per [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e tipi di dati successivi, conversione di livello inferiore verranno eseguiti dal server anziché dal Driver OLE DB per SQL Server. Significa inoltre che le caratteristiche disponibili nella connessione saranno limitate al set di funzionalità di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. I tentativi di usare nuovi tipi di dati o caratteristiche vengono rilevati il prima possibile nelle chiamate API e, anziché tentare di passare richieste non valide al server, vengono restituiti errori all'applicazione chiamante.   


 IDBInfo:: GetKeywords restituirà sempre un elenco di parole chiave che corrisponde alla versione del server per la connessione e non è interessato dalle **DataTypeCompatibility**.  

|Tipo di dati|SQL Server Native Client<br /><br />SQL Server 2005|SQL Server Native Client 11.0<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|Driver OLE DB per SQL Server|Applicazioni OLE DB di Windows Data Access Components, MDAC e<br /><br /> Driver OLE DB per le applicazioni OLE DB per SQL Server con DataTypeCompatibility = 80|  
|---------------|--------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|  
|CLR UDT (\<= 8Kb)|udt|udt|udt|Varbinary|  
|varbinary(max)|varbinary|varbinary|varbinary|image|  
|ntext|varchar|varchar|varchar|Text|  
|nvarchar(max)|nvarchar|nvarchar|nvarchar|Ntext|  
|xml|xml|xml|xml|Ntext|  
|CLR UDT (> 8Kb)|varbinary|udt|udt|image|  
|data|varchar|data|data|Varchar|  
|datetime2|varchar|datetime2|datetime2|Varchar|  
|datetimeoffset|varchar|datetimeoffset|datetimeoffset|Varchar|  
|time|varchar|time|time|Varchar|  

## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per SQL Server](../oledb/oledb-driver-for-sql-server.md)   
 [Installazione del driver OLE DB per SQL Server](../oledb/applications/installing-oledb-driver-for-sql-server.md)  
