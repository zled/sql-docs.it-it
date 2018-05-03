---
title: Driver OLE DB per SQL Server | Documenti Microsoft
description: Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: OLE DB Driver
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server
- MSOLEDBSQL
- native data access [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 30ca6b7e894482aa2a94c778cc44bfcbba2a759e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="ole-db-driver-for-sql-server"></a>Driver OLE DB per SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  Il Driver OLE DB per SQL Server è una dati autonomo accesso API application programming interface (), utilizzata per OLE DB, che è stata introdotta in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Il Driver OLE DB per SQL Server offre il driver OLE DB per SQL in una libreria di collegamento dinamico (DLL). Fornisce inoltre nuove funzionalità che estendono quelle fornite da Windows Data Access Components (Windows DAC, applicazione livello dati, precedentemente noto come Microsoft Data Access Components o MDAC). Il Driver OLE DB per SQL Server può essere utilizzato per creare nuove applicazioni o migliorare le applicazioni esistenti per trarre vantaggio dalle funzionalità introdotte in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], ad esempio multiple active result set (MARS), tipi di dati definito dall'utente (UDT), query supporta le notifiche, isolamento dello snapshot e tipo di dati XML.  
  
> [!NOTE]  
>  Per un elenco delle differenze tra il Driver OLE DB per SQL Server e Windows DAC, oltre a informazioni sui problemi da considerare prima di aggiornare un'applicazione livello dati di Windows per il Driver OLE DB per SQL Server, vedere [aggiornamento di un'applicazione al Driver OLE DB per SQL Server da MDAC](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  
  
 Il Driver OLE DB per SQL Server è utilizzabile in combinazione con servizi principali OLE DB fornito con Windows DAC, ma questo non è un requisito; la scelta di utilizzare servizi di base o non dipende dai requisiti dell'applicazione specifica (ad esempio, se il pool di connessioni è obbligatorio).  
  
 Le applicazioni di dati oggetto ADO (ActiveX) possono utilizzare il Driver OLE DB per SQL Server, ma è consigliabile utilizzare ADO in combinazione con il **DataTypeCompatibility** parola chiave di stringa di connessione (o corrispondente  **Origine dati** proprietà). Quando si utilizza il Driver OLE DB per SQL Server, le applicazioni ADO possono sfruttare le nuove caratteristiche introdotte [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] che sono disponibili tramite il Driver OLE DB per SQL Server tramite parole chiave delle stringhe di connessione o le proprietà OLE DB o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Per ulteriori informazioni sull'utilizzo di queste caratteristiche con ADO, vedere [utilizzo di ADO con il Driver OLE DB per SQL Server](../oledb/applications/using-ado-with-oledb-driver-for-sql-server.md).  
  
 Il Driver OLE DB per SQL Server è stato progettato per fornire un metodo semplificato per ottenere l'accesso ai dati nativo a SQL Server tramite OLE DB. Fornisce un modo per innovazione e sviluppare nuove funzioni di accesso ai dati senza modificare i componenti Windows DAC correnti, che ora fanno parte della piattaforma Microsoft Windows.  
  
 Il Driver OLE DB per SQL Server utilizza componenti Windows DAC, ma non in modo esplicito dipendenti a una particolare versione di Windows DAC. È possibile utilizzare il Driver OLE DB per SQL Server con la versione di Windows DAC che viene installato con un sistema operativo supportato dal Driver OLE DB per SQL Server.  

 ## <a name="different-generations-of-ole-db-drivers"></a>Diverse generazioni di driver OLE DB

Esistono tre generazioni distinte di provider Microsoft OLE DB per SQL Server.

### <a name="1-microsoft-ole-db-provider-for-sql-server-sqloledb"></a>1. Provider Microsoft OLE DB per SQL Server (SQLOLEDB)
Il [il Provider Microsoft OLE DB per SQL Server](../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) (SQLOLEDB) ancora fornito come parte di [Windows Data Access Components](https://msdn.microsoft.com/en-us/library/ms692897.aspx). Non è più gestito e non è consigliabile utilizzare il driver per i nuovi sviluppi.

### <a name="2-sql-server-native-client-snac"></a>2. SQL Server Native Client (SNAC)
A partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], il [SQL Server Native Client (SNAC)](../../relational-databases/native-client/sql-server-native-client.md) include un'interfaccia di provider OLE DB (SQLNCLI) e il provider OLE DB fornito con [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] tramite [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].

Era [deprecati nel 2011](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/) e non è consigliabile utilizzare il driver per i nuovi sviluppi. Per ulteriori informazioni sul ciclo di vita SNAC e download disponibili, consultare [ciclo di vita SNAC illustrato](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/).

### <a name="3-microsoft-ole-db-driver-for-sql-server-msoledbsql"></a>3. Driver Microsoft OLE DB per SQL Server (MSOLEDBSQL)
OLE DB non è [undeprecated](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/) e rilasciato nel 2018.

Il nuovo provider OLE DB viene chiamato il Driver OLE DB Microsoft per SQL Server (MSOLEDBSQL). Il nuovo provider verrà aggiornato con le funzionalità di server più recenti in futuro.

> [!NOTE]
> Per utilizzare il nuovo Microsoft Driver OLE DB per SQL Server nelle applicazioni esistenti, è consigliabile pianificare convertire le stringhe di connessione da SQLOLEDB o SQLNCLI, a MSOLEDBSQL.
  
## <a name="in-this-section"></a>Contenuto della sezione  
[Quando utilizzare il driver OLE DB per SQL Server](../oledb/when-to-use-oledb-driver-for-sql-server.md)  
 Viene illustrato come integrare il Driver OLE DB per SQL Server con i dati di Microsoft tecnologie di accesso, viene presentato un confronto con Windows DAC e ADO.NET e vengono fornite informazioni utili per decidere quale tecnologia utilizzare di accesso ai dati.  
  
 [Driver OLE DB per funzionalità di SQL Server](../oledb/features/oledb-driver-for-sql-server-features.md )  
 Vengono descritte le funzionalità supportate dal Driver OLE DB per SQL Server.  
  
 [Compilazione di applicazioni con il driver OLE DB per SQL Server](../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
 Viene fornita una panoramica del Driver OLE DB per lo sviluppo di SQL Server, incluse le differenze rispetto a Windows DAC, i componenti utilizzati e la modalità di utilizzo di ADO con esso.  
  
 In questa sezione viene inoltre Driver OLE DB per l'installazione di SQL Server e distribuzione, incluso come ridistribuire il Driver OLE DB per la libreria di SQL Server.  
  
 [Requisiti di sistema per driver OLE DB per SQL Server](../oledb/system-requirements-for-oledb-driver-for-sql-server.md)  
 Vengono illustrate le risorse di sistema necessarie per l'utilizzo del Driver OLE DB per SQL Server.  
  
 [Driver OLE DB per programmazione con SQL Server](../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
 Vengono fornite informazioni sull'utilizzo del Driver OLE DB per SQL Server.  
  
 [Ricerca di ulteriori driver OLE DB per informazioni su SQL Server](../oledb/finding-more-oledb-driver-for-sql-server-information.md)  
 Fornisce risorse aggiuntive su Driver OLE DB per SQL Server, inclusi i collegamenti a risorse esterne e istruzioni per ottenere assistenza.  
  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiornamento di un'applicazione da SQL Server 2005 Native Client](../oledb/applications/updating-an-application-from-sql-server-2005-native-client.md)    
 [Procedure per OLE DB](../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
