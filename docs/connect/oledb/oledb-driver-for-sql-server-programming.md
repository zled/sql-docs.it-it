---
title: Driver OLE DB per la programmazione di SQL Server | Documenti Microsoft
description: Driver OLE DB per la programmazione di SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: OLE DB Driver
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
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
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 1a3d642eb3cef1f9f01accd8b50f571f5e4903ac
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2018
---
# <a name="ole-db-driver-for-sql-server-programming"></a>Driver OLE DB per la programmazione di SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il Driver OLE DB per SQL Server è una dati autonomo accesso API application programming interface (), utilizzata per OLE DB, che è stata introdotta in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Il Driver OLE DB per SQL Server offre il driver OLE DB per SQL in una libreria di collegamento dinamico (DLL). Fornisce inoltre nuove funzionalità che estendono quelle fornite da Windows Data Access Components (Windows DAC, applicazione livello dati, precedentemente noto come Microsoft Data Access Components o MDAC). Il Driver OLE DB per SQL Server può essere utilizzato per creare nuove applicazioni o migliorare le applicazioni esistenti per trarre vantaggio dalle funzionalità introdotte in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], ad esempio multiple active result set (MARS), tipi di dati definito dall'utente (UDT), query supporta le notifiche, isolamento dello snapshot e tipo di dati XML.  
  
> [!NOTE]  
>  Per un elenco delle differenze tra il Driver OLE DB per SQL Server e Windows DAC, oltre a informazioni sui problemi da considerare prima di aggiornare un'applicazione livello dati di Windows per il Driver OLE DB per SQL Server, vedere [aggiornamento di un'applicazione al Driver OLE DB per SQL Server da MDAC](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  
  
 Il Driver OLE DB per SQL Server è utilizzabile in combinazione con servizi principali OLE DB fornito con Windows DAC, ma questo non è un requisito; la scelta di utilizzare servizi di base o non dipende dai requisiti dell'applicazione specifica (ad esempio, se il pool di connessioni è obbligatorio).  
  
 Le applicazioni di dati oggetto ADO (ActiveX) possono utilizzare il Driver OLE DB per SQL Server, ma è consigliabile utilizzare ADO in combinazione con il **DataTypeCompatibility** parola chiave di stringa di connessione (o corrispondente  **Origine dati** proprietà). Quando si utilizza il Driver OLE DB per SQL Server, le applicazioni ADO possono sfruttare le nuove caratteristiche introdotte [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] che sono disponibili tramite il Driver OLE DB per SQL Server tramite parole chiave delle stringhe di connessione o le proprietà OLE DB o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Per ulteriori informazioni sull'utilizzo di queste caratteristiche con ADO, vedere [utilizzo di ADO con il Driver OLE DB per SQL Server](../oledb/applications/using-ado-with-oledb-driver-for-sql-server.md).  
  
 Il Driver OLE DB per SQL Server è stato progettato per fornire un metodo semplificato per ottenere l'accesso ai dati nativo a SQL Server tramite OLE DB. Fornisce un modo per innovazione e sviluppare nuove funzioni di accesso ai dati senza modificare i componenti Windows DAC correnti, che ora fanno parte della piattaforma Microsoft Windows.  
  
 Il Driver OLE DB per SQL Server utilizza componenti Windows DAC, ma non in modo esplicito dipendenti a una particolare versione di Windows DAC. È possibile utilizzare il Driver OLE DB per SQL Server con la versione di Windows DAC che viene installato con un sistema operativo supportato dal Driver OLE DB per SQL Server.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Driver OLE DB per SQL Server](../oledb/oledb-driver-for-sql-server.md)  
 Elenca le significative nuovo Driver OLE DB per le funzionalità di SQL Server.  
  
 [Quando utilizzare OLE DB Driver per SQL Server](../oledb/when-to-use-oledb-driver-for-sql-server.md)  
 Viene illustrato come integrare il Driver OLE DB per SQL Server con i dati di Microsoft tecnologie di accesso, viene presentato un confronto con Windows DAC e ADO.NET e vengono fornite informazioni utili per decidere quale tecnologia utilizzare di accesso ai dati.  
  
 [Driver OLE DB per la funzionalità di SQL Server](../oledb/features/oledb-driver-for-sql-server-features.md )  
 Vengono descritte le funzionalità supportate dal Driver OLE DB per SQL Server.  
  
 [Compilazione di applicazioni con il Driver OLE DB per SQL Server](../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
 Viene fornita una panoramica del Driver OLE DB per lo sviluppo di SQL Server, incluse le differenze rispetto a Windows DAC, i componenti utilizzati e la modalità di utilizzo di ADO con esso.  
  
 In questa sezione viene inoltre Driver OLE DB per l'installazione di SQL Server e distribuzione, incluso come ridistribuire il Driver OLE DB per la libreria di SQL Server.  
  
 [Requisiti di sistema per il Driver OLE DB per SQL Server](../oledb/system-requirements-for-oledb-driver-for-sql-server.md)  
 Vengono illustrate le risorse di sistema necessarie per l'utilizzo del Driver OLE DB per SQL Server.  
  
 [Driver OLE DB per SQL Server &#40;OLE DB&#41;](../oledb/ole-db/oledb-driver-for-sql-server-ole-db.md)  
 Vengono fornite informazioni sull'utilizzo del Driver OLE DB per SQL Server.  
  
 [Ricerca di ulteriori OLE DB Driver per informazioni su SQL Server](../oledb/finding-more-oledb-driver-for-sql-server-information.md)  
 Fornisce risorse aggiuntive su Driver OLE DB per SQL Server, inclusi i collegamenti a risorse esterne e istruzioni per ottenere assistenza.  
  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiornamento di un'applicazione da SQL Server 2005 Native Client](../oledb/applications/updating-an-application-from-sql-server-2005-native-client.md)    
 [Procedure per OLE DB](../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
