---
title: "La qualità dei dati corrispondenti alle colonne (componente aggiuntivo MDS per Excel) | Documenti Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f683fdc6-0d4c-4793-8143-567616cb2094
caps.latest.revision: 9
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4ce8ddcdbf8c29663640025ad40b4e01e44d99c1
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="data-quality-matching-columns-mds-add-in-for-excel"></a>Colonne corrispondenti Data Quality (componente aggiuntivo MDS per Excel)
  Nel [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], dopo corrispondenza dei dati, nel **Data Quality** gruppo della barra multifunzione, è possibile fare clic su **Mostra dettagli** per visualizzare le colonne che forniscono informazioni dettagliate sulla corrispondenza.  
  
 Nella tabella seguente vengono illustrate le colonne visualizzate quando si verifica la corrispondenza dei dati.  
  
|Nome|Description|  
|----------|-----------------|  
|**CLUSTER_ID**|Identificatore univoco utilizzato per raggruppare record simili. Il valore di **CLUSTER_ID**è lo stesso per tutte le righe simili. Se non è visualizzato alcun valore **CLUSTER_ID** per una riga, non sono stati trovati record simili.|  
|**RECORD_ID**|Identificatore univoco utilizzato per identificare i record. Simile al valore Codice archiviato nel repository MDS, è un valore utilizzato per identificare un record. Viene generato automaticamente ogni volta che viene eseguita la ricerca della corrispondenza.|  
|**PIVOT_MARK**|Record arbitrario con cui vengono confrontati gli altri record. Non dispone di un valore di punteggio.|  
|**SCORE**|Rappresenta il livello di analogia dei record del gruppo con il record pivot. Il punteggio è determinato da DQS. Se non viene visualizzato alcun punteggio, il record rappresenta il pivot per gli altri record oppure non è stata trovata alcuna corrispondenza.|  
  
## <a name="see-also"></a>Vedere anche  
 [Corrispondenza Data Quality nel componente aggiuntivo MDS per Excel](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Corrispondenza simile di dati &#40; Il componente aggiuntivo MDS per Excel &#41;](../../master-data-services/microsoft-excel-add-in/match-similar-data-mds-add-in-for-excel.md)   
 [Corrispondenza di dati](../../data-quality-services/data-matching.md)  
  
  
