---
title: Colonne corrispondenti Data Quality (componente aggiuntivo MDS per Excel) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f683fdc6-0d4c-4793-8143-567616cb2094
caps.latest.revision: 8
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 97395c646ce05f3946b036eda5df922c91580b18
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37172882"
---
# <a name="data-quality-matching-columns-mds-add-in-for-excel"></a>Colonne corrispondenti Data Quality (componente aggiuntivo MDS per Excel)
  In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]dopo avere verificato la corrispondenza dei dati, nel gruppo **Data Quality** sulla barra multifunzione è possibile fare clic su **Mostra dettagli** per visualizzare le colonne con informazioni dettagliate sulla corrispondenza.  
  
 Nella tabella seguente vengono illustrate le colonne visualizzate quando si verifica la corrispondenza dei dati.  
  
|nome|Description|  
|----------|-----------------|  
|**CLUSTER_ID**|Identificatore univoco utilizzato per raggruppare record simili. Il valore di **CLUSTER_ID**è lo stesso per tutte le righe simili. Se non è visualizzato alcun valore **CLUSTER_ID** per una riga, non sono stati trovati record simili.|  
|**RECORD_ID**|Identificatore univoco utilizzato per identificare i record. Simile al valore Codice archiviato nel repository MDS, è un valore utilizzato per identificare un record. Viene generato automaticamente ogni volta che viene eseguita la ricerca della corrispondenza.|  
|**PIVOT_MARK**|Record arbitrario con cui vengono confrontati gli altri record. Non dispone di un valore di punteggio.|  
|**SCORE**|Rappresenta il livello di analogia dei record del gruppo con il record pivot. Il punteggio è determinato da DQS. Se non viene visualizzato alcun punteggio, il record rappresenta il pivot per gli altri record oppure non è stata trovata alcuna corrispondenza.|  
  
## <a name="see-also"></a>Vedere anche  
 [Corrispondenza Data Quality nel componente aggiuntivo MDS per Excel](data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Cercare la corrispondenza tra dati simili &#40;componente aggiuntivo MDS per Excel&#41;](match-similar-data-mds-add-in-for-excel.md)   
 [Corrispondenza di dati](../../data-quality-services/data-matching.md)  
  
  
