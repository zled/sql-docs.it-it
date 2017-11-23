---
title: Requisiti di sistema per SQL Server Native Client | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- system requirements [SQL Server Native Client]
- data access [SQL Server Native Client], system requirements
- SQL Server Native Client, system requirements
- SQLNCLI, system requirements
ms.assetid: 1c8e2f8a-a440-44da-8e3a-af632d34c52c
caps.latest.revision: "60"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a83bab6263ca8812fb7909a92c48daab8ec96883
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="system-requirements-for-sql-server-native-client"></a>Requisiti di sistema per SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Per usare le caratteristiche di accesso ai dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio MARS, è necessario verificare che sia installato il software indicato di seguito:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sul client.  
  
-   Un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sul server.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client richiede Windows Installer 3.0. Windows Installer 3.0 è già installato nei sistemi operativi [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Per tutte le altre piattaforme è necessario installarlo in modo esplicito. Per ulteriori informazioni, vedere [Windows Installer 3.0 Redistributable](http://go.microsoft.com/fwlink/?LinkId=46459).  
  
> [!NOTE]  
>  Assicurarsi di accedere con privilegi di amministratore prima di installare il software.  
  
## <a name="operating-system-requirements"></a>Requisiti del sistema operativo  
 Per un elenco di sistemi operativi che supportano [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, vedere [criteri di supporto per SQL Server Native Client](../../relational-databases/native-client/applications/support-policies-for-sql-server-native-client.md).  
  
## <a name="sql-server-requirements"></a>Requisiti di SQL Server  
 Per usare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client per accedere ai dati nei database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è necessario che sia installata un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] supporta connessioni da tutte le versioni di MDAC, Windows Data Access Components e tutte le versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Quando si stabilisce una connessione tra una versione client meno recente e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], i tipi di dati del server non riconosciuti dal client vengono mappati a tipi compatibili con la versione client. Per altre informazioni, vedere Compatibilità dei tipi di dati per le versioni client, più avanti in questo argomento.  
  
## <a name="cross-language-requirements"></a>Requisiti per lingue diverse  
 La versione in lingua inglese di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client è supportata in tutte le versioni localizzate dei sistemi operativi supportati. Le versioni localizzate di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sono supportate in tutti i sistemi operativi localizzati, purché della stessa lingua della versione localizzata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Le versioni localizzate di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sono inoltre supportate in tutti i sistemi operativi in lingua inglese, purché siano installate le impostazioni nella lingua corrispondente.  
  
 Per gli aggiornamenti:  
  
-   Le versioni in lingua inglese di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client possono essere aggiornate a qualsiasi versione localizzata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
-   Le versioni localizzate di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client possono essere aggiornate alle versioni localizzate di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client nella stessa lingua.  
  
-   Le versioni localizzate di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client possono essere aggiornate alla versione in lingua inglese di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
-   Le versioni localizzate di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client non possono essere aggiornate alle versioni localizzate di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client in una lingua diversa.  
  
## <a name="data-type-compatibility-for-client-versions"></a>Compatibilità dei tipi di dati per le versioni client  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client i nuovi tipi di dati vengono mappati a tipi di dati meno recenti compatibili con client di versioni precedenti, come illustrato nella tabella riportata di seguito.  
  
 Le applicazioni OLE DB e ADO possono utilizzare il **DataTypeCompatibility** parola chiave di stringa di connessione con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client per funzionare con i tipi di dati meno recenti. Quando **DataTypeCompatibility = 80**, i client OLE DB si connetteranno utilizzando il [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] del flusso di dati tabulari, versione (TDS Tabular) anziché la versione TDS. Ciò significa che per i tipi di dati di [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e versioni successive, la conversione alle versioni precedenti verrà eseguita dal server e non da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Significa inoltre che le caratteristiche disponibili nella connessione saranno limitate al set di funzionalità di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. I tentativi di usare nuovi tipi di dati o caratteristiche vengono rilevati il prima possibile nelle chiamate API e, anziché tentare di passare richieste non valide al server, vengono restituiti errori all'applicazione chiamante.  
  
 Non esiste alcun **DataTypeCompatibility** controllo per ODBC.  
  
 IDBInfo:: GetKeywords restituirà sempre un elenco di parole chiave che corrisponde alla versione del server per la connessione e non è interessato dalle **DataTypeCompatibility**.  
  
|Tipo di dati|SQL Server Native Client<br /><br /> SQL Server 2005|SQL Server Native Client 11.0<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|Applicazioni OLE DB di Windows Data Access Components, MDAC e<br /><br /> SQL Server Native Client con DataTypeCompatibility=80|  
|---------------|--------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|  
|CLR definito dall'utente (\<= 8 Kb)|udt|Udt|Varbinary|  
|varbinary(max)|varbinary|varbinary|Immagine|  
|varchar(max)|varchar|varchar|Text|  
|nvarchar(max)|nvarchar|nvarchar|Ntext|  
|xml|xml|xml|Ntext|  
|CLR UDT (> 8Kb)|udt|varbinary|Immagine|  
|data|data|varchar|Varchar|  
|datetime2|datetime2|varchar|Varchar|  
|datetimeoffset|datetimeoffset|varchar|Varchar|  
|time|time|varchar|Varchar|  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di SQL Server Native Client](../../relational-databases/native-client/sql-server-native-client-programming.md)   
 [Installazione di SQL Server Native Client](../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
  
  
