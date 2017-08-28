---
title: "Proprietà dell'origine OData | Documenti Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fde5bb0-6d78-4ec4-8f0b-67f91c53fe99
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: ee79d0f1b31963b7d13aa07bf4603246139c3a7c
ms.openlocfilehash: 64e297a37c3b6449551968b5788f8c2c0ddd4ab6
ms.contentlocale: it-it
ms.lasthandoff: 08/23/2017

---
# <a name="odata-source-properties"></a>Proprietà dell'origine OData
Quando si fa clic su **origine OData** nel flusso di dati e fare clic su **proprietà**, per visualizzare le proprietà per il **origine OData** componente il **proprietà** finestra.  

## <a name="properties"></a>Proprietà 
|Proprietà|Description|  
|-|-|  
|CollectionName|Nome della raccolta da recuperare dal servizio OData. La proprietà **CollectionName** viene utilizzata quando **UseResourcePath** è False.<br /><br /> Questa proprietà è expressionable, che consente di impostare il valore in fase di esecuzione. Tuttavia, se i metadati della raccolta non corrispondono ai metadati esistenti in fase di progettazione, la convalida si verifica un errore, che causa l'errore di esecuzione del flusso di dati.|  
|DefaultStringLength|Con questo valore viene specificata la lunghezza predefinita per le colonne stringa che sono prive della lunghezza massima.<br /><br /> **Valore predefinito:** 4000|  
|Query|Parametri della query OData. Questa proprietà è expressionable e può essere impostata in fase di esecuzione.|  
|ResourcePath|Utilizzare questa proprietà quando è necessario specificare un percorso completo della risorsa, anziché selezionare semplicemente il nome di una raccolta. Questa proprietà viene utilizzata quando **UseResourcePath** è True.|  
|UseResourcePath|Quando impostato su True, il valore di **ResourcePath** viene aggiunto all'URL di base per determinare il percorso del feed OData. Quando impostato su False, viene utilizzato il valore di **CollectionName** .<br /><br /> **Valore predefinito:** False|  
  
## <a name="see-also"></a>Vedere anche
[Origine OData](odata-source.md)

