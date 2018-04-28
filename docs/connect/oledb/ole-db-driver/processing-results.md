---
title: L'elaborazione dei risultati | Documenti Microsoft
description: L'elaborazione dei risultati
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb-driver-for-sql-server
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, results processing
- OLE DB, processing results
- rowsets [SQL Server], results processing
- results [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 706b47396ef0c9ff57f39f144a9545d7eec68da8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="processing-results"></a>Risultati dell'elaborazione
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Se un oggetto set di righe viene prodotto dall'esecuzione di un comando o dalla generazione di un oggetto set di righe direttamente dal provider, il consumer deve recuperare e accedere ai dati nel set di righe.  
  
 Set di righe sono gli oggetti centrali che consentono il Driver OLE DB per SQL Server per esporre i dati in formato tabulare. Concettualmente, un set di righe è un set in cui ogni riga include dati di colonne Un oggetto set di righe espone interfacce come **IRowset** (contiene metodi per il recupero delle righe dal set di righe in sequenza), **IAccessor** (consente la definizione di un gruppo di associazioni di colonna che descrive la modalità di associazione dei dati tabulari alle variabili di programma consumer), **IColumnsInfo** (fornisce informazioni sulle colonne nel set di righe), e **IRowsetInfo** (fornisce informazioni sul set di righe).  
  
 Un consumer può chiamare il **IRowset:: GetData** metodo per recuperare una riga di dati dal set di righe in un buffer. Prima di **GetData** viene chiamato, il consumer descrive il buffer mediante un set di strutture DBBINDING. Ogni associazione descrive la modalità di archiviazione di una colonna in un set di righe in un buffer del consumer e contiene gli elementi seguenti:  
  
-   Ordinale della colonna, o parametro, a cui si applica l'associazione.  
  
-   Informazioni sugli elementi associati, ad esempio, valore dei dati, lunghezza dei dati e relativo stato dell'associazione.  
  
-   Informazioni sugli offset presenti nel buffer per ciascuna di queste parti.  
  
-   Lunghezza e tipo dei valori dei dati inclusi nel buffer del consumer.  
  
 Quando si recuperano i dati, il provider utilizza le informazioni presenti in ogni associazione per determinare dove e come recuperare i dati dal buffer del consumer. Durante l'impostazione dei dati nel buffer del consumer, il provider utilizza le informazioni presenti in ogni associazione per determinare dove e come restituire i dati all'interno del buffer.  
  
 Dopo aver specificate le strutture DBBINDING, viene creata una funzione di accesso (**IAccessor:: CreateAccessor**). Una funzione di accesso è una raccolta di associazioni e viene utilizzata per ottenere o impostare i dati nel buffer del consumer.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un Driver OLE DB per SQL Server applicazione](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)   
 [Procedure per OLE DB](../../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
