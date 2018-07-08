---
title: L'elaborazione dei risultati | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-provider
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, results processing
- OLE DB, processing results
- rowsets [SQL Server], results processing
- results [SQL Server Native Client]
ms.assetid: 20887ac4-f649-4e7f-92e6-f929e2e70952
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3c8b6a1653fa089b5ef78211c4dd1ab4896dbcf6
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425900"
---
# <a name="processing-results"></a>Risultati dell'elaborazione
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Se un oggetto set di righe viene prodotto dall'esecuzione di un comando o dalla generazione di un oggetto set di righe direttamente dal provider, il consumer deve recuperare e accedere ai dati nel set di righe.  
  
 I set di righe sono gli oggetti centrali che consentono al provider OLE DB di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client di esporre dati in formato tabulare. Concettualmente, un set di righe è un set in cui ogni riga include dati di colonne Un oggetto set di righe espone interfacce, ad esempio **IRowset** (contiene i metodi per il recupero di righe dal set di righe in sequenza), **IAccessor** (consente la definizione di un gruppo di associazioni di colonna che descrive il dati tabulari modo in cui sono associati alle variabili di programma consumer), **IColumnsInfo** (fornisce informazioni sulle colonne nel set di righe), e **IRowsetInfo** (fornisce informazioni sui set di righe).  
  
 Un consumer può chiamare le **IRowset:: GetData** metodo per recuperare una riga di dati dal set di righe in un buffer. Prima di **GetData** viene chiamato, il consumer descrive il buffer mediante un set di strutture DBBINDING. Ogni associazione descrive la modalità di archiviazione di una colonna in un set di righe in un buffer del consumer e contiene gli elementi seguenti:  
  
-   Ordinale della colonna, o parametro, a cui si applica l'associazione.  
  
-   Informazioni sugli elementi associati, ad esempio, valore dei dati, lunghezza dei dati e relativo stato dell'associazione.  
  
-   Informazioni sugli offset presenti nel buffer per ciascuna di queste parti.  
  
-   Lunghezza e tipo dei valori dei dati inclusi nel buffer del consumer.  
  
 Quando si recuperano i dati, il provider utilizza le informazioni presenti in ogni associazione per determinare dove e come recuperare i dati dal buffer del consumer. Durante l'impostazione dei dati nel buffer del consumer, il provider utilizza le informazioni presenti in ogni associazione per determinare dove e come restituire i dati all'interno del buffer.  
  
 Dopo aver specificate le strutture DBBINDING, viene creata una funzione di accesso (**IAccessor:: CreateAccessor**). Una funzione di accesso è una raccolta di associazioni e viene utilizzata per ottenere o impostare i dati nel buffer del consumer.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un'applicazione del Provider SQL Server Native Client OLE DB](../../relational-databases/native-client-ole-db-provider/creating-a-sql-server-native-client-ole-db-provider-application.md)   
 [Procedure relative a OLE DB](../../relational-databases/native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
