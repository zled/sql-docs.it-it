---
title: L'elaborazione dei risultati | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, results processing
- OLE DB, processing results
- rowsets [SQL Server], results processing
- results [SQL Server Native Client]
ms.assetid: 20887ac4-f649-4e7f-92e6-f929e2e70952
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7b1f2d039cf88e8487433d0d92e2e0f6c265f637
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062170"
---
# <a name="processing-results"></a>Risultati dell'elaborazione
  Se un oggetto set di righe viene prodotto dall'esecuzione di un comando o dalla generazione di un oggetto set di righe direttamente dal provider, il consumer deve recuperare e accedere ai dati nel set di righe.  
  
 I set di righe sono gli oggetti centrali che consentono al provider OLE DB di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client di esporre dati in formato tabulare. Concettualmente, un set di righe è un set in cui ogni riga include dati di colonne Un oggetto set di righe espone interfacce, ad esempio **IRowset** (contiene metodi per il recupero delle righe dal set di righe in sequenza), **IAccessor** (consente la definizione di un gruppo di associazioni di colonna che descrive il modalità tabulare sono associati a variabili di programma consumer), **IColumnsInfo** (fornisce informazioni sulle colonne nel set di righe), e **IRowsetInfo** (vengono fornite informazioni sul set di righe).  
  
 Un consumer può chiamare la **IRowset:: GetData** metodo per recuperare una riga di dati dal set di righe in un buffer. Prima di **GetData** viene chiamato, il consumer descrive il buffer mediante un set di strutture DBBINDING. Ogni associazione descrive la modalità di archiviazione di una colonna in un set di righe in un buffer del consumer e contiene gli elementi seguenti:  
  
-   Ordinale della colonna, o parametro, a cui si applica l'associazione.  
  
-   Informazioni sugli elementi associati, ad esempio, valore dei dati, lunghezza dei dati e relativo stato dell'associazione.  
  
-   Informazioni sugli offset presenti nel buffer per ciascuna di queste parti.  
  
-   Lunghezza e tipo dei valori dei dati inclusi nel buffer del consumer.  
  
 Quando si recuperano i dati, il provider utilizza le informazioni presenti in ogni associazione per determinare dove e come recuperare i dati dal buffer del consumer. Durante l'impostazione dei dati nel buffer del consumer, il provider utilizza le informazioni presenti in ogni associazione per determinare dove e come restituire i dati all'interno del buffer.  
  
 Dopo aver specificate le strutture DBBINDING, viene creata una funzione di accesso (**IAccessor:: CreateAccessor**). Una funzione di accesso è una raccolta di associazioni e viene utilizzata per ottenere o impostare i dati nel buffer del consumer.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un'applicazione del Provider SQL Server Native Client OLE DB](creating-a-sql-server-native-client-ole-db-provider-application.md)   
 [Procedure relative a OLE DB](../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  