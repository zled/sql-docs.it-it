---
title: Errori | Documenti Microsoft
description: Errori
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 2c94e2beaf56e6987bf49bb73e8629f33a775496
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2018
ms.locfileid: "35665241"
---
# <a name="errors"></a>Errori
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Gli oggetti OLE/COM segnalano gli errori tramite il codice restituito HRESULT delle funzioni membro oggetto. Un HRESULT OLE/COM è una struttura costituita da pacchetti di byte. OLE fornisce macro che risolvono i riferimenti dei membri di struttura.  
  
 OLE/COM specifica il **IErrorInfo** interfaccia. L'interfaccia espone i metodi, ad esempio **GetDescription**. In questo modo, i client possono estrarre i dettagli relativi agli errori dai server OLE/COM. OLE DB estende **IErrorInfo** da supportare la restituzione di più pacchetti di informazioni di errore nell'esecuzione di una funzione con singolo membro.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] può restituire più errori. Un'applicazione può recuperare gli errori del server uno alla volta chiamando [IMultipleResults:: GetResult](http://go.microsoft.com/fwlink/?LinkId=129630) combinato con ISQLErrorInfo e IErrorRecords.  
  
 Il Driver OLE DB per SQL Server espone OLE DB ottimizzata per i record **IErrorInfo**, l'oggetto personalizzato **ISQLErrorInfo**e le specifiche del provider [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) errore interfacce dell'oggetto.  
  
 Per informazioni sulla traccia degli errori, vedere [traccia di accesso ai dati](http://go.microsoft.com/fwlink/?LinkId=125805). Per informazioni sui miglioramenti apportati alla traccia di errori aggiunta in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], vedere [l'accesso a informazioni di diagnostica nel Log degli eventi estesi](../../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Codici restituiti](../../oledb/ole-db-errors/return-codes.md)  
  
-   [Informazioni nelle interfacce di errore](../../oledb/ole-db-errors/information-in-error-interfaces.md)  
  
-   [Dettagli relativi agli errori di SQL Server](../../oledb/ole-db-errors/sql-server-error-detail.md)  
  
-   [Recupero delle informazioni sugli errori](../../oledb/ole-db-errors/retrieving-error-information.md)  
  
-   [Risultati dei messaggi di SQL Server](../../oledb/ole-db-errors/sql-server-message-results.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per programmazione con SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
