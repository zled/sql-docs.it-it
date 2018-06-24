---
title: Aggiornare le trasformazioni ricerca | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Lookup transformation and upgrading
- upgrading caching for Lookup transformation
- upgrading Lookup transformation
ms.assetid: d9b2c281-91ee-4e20-bdf0-0cd77d4a4241
caps.latest.revision: 16
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 214d915f16f15e81fe4fabbb44dd34f665fb5942
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064367"
---
# <a name="upgrade-lookup-transformations"></a>Aggiornare le trasformazioni Ricerca
  Quando si esegue l'aggiornamento da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], è consigliabile modificare il pacchetto per sfruttare le nuove caratteristiche della trasformazione Ricerca. La trasformazione supporta i tipi di memorizzazione nella cache e le opzioni di output dei dati disponibili in [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]. Per ulteriori informazioni su ulteriori gli output di dati e la memorizzazione nella cache, vedere [trasformazione ricerca](../../integration-services/data-flow/transformations/lookup-transformation.md).  
  
 In [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)], i tipi di memorizzazione nella cache disponibili sono di tipo completa, parziale e nessuna memorizzazione nella cache. In [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)], è possibile configurare una trasformazione Ricerca per utilizzare uno di questi tipi di memorizzazione nella cache. Per ulteriori informazioni su come implementare memorizzazione nella cache parziale o nessuna memorizzazione nella cache, vedere [implementazione di una ricerca in modalità di Cache parziale o No Cache](../../integration-services/data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md). Per informazioni su come implementare la memorizzazione nella cache completa, vedere [implementare una trasformazione ricerca in modalità Cache completo con la gestione connessione Cache](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md) e [implementare una trasformazione ricerca in modalità Cache completo con OLE Gestione connessione DB](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md).  
  
 In [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)], la trasformazione Ricerca aveva a disposizione un input, un output e un output errori. Le righe dell'input con le voci corrispondenti nel set di dati di riferimento erano gestite dall'output. Le righe nell'input che non avevano voci corrispondenti venivano considerate come errori e potevano essere reindirizzate all'output errori. In [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)], la trasformazione Ricerca presenta due output: un output con corrispondenze e uno senza corrispondenze.  
  
 Per impostazione predefinita, quando viene eseguita una trasformazione Ricerca creata in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] tratta le righe senza corrispondenze come errori e consente di reindirizzare le righe a un output degli errori. Si dispone dell'opzione di configurazione della trasformazione Ricerca per trattare le righe come non-errori e reindirizzare le righe all'output senza corrispondenza.  
  
 Per altre informazioni, vedere [Editor trasformazione ricerca &#40;generale&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Trasformazione Ricerca](../../integration-services/data-flow/transformations/lookup-transformation.md)  
  
  