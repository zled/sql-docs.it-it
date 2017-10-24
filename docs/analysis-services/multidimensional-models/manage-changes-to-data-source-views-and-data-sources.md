---
title: Gestire le modifiche a viste origine dati e origini dati | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying data sources
- modifying data source views
- data source views [Analysis Services], schema updates
- data sources [Analysis Services], schema updates
ms.assetid: 928c9f63-365a-43fd-9bbd-78828cc7e54d
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3b1913d392467f4ba78976d9ab73919e7ac06051
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="manage-changes-to-data-source-views-and-data-sources"></a>Gestire modifiche a viste origine dati e origini dati
  Quando si riesegue la Generazione guidata schema, vengono riutilizzate la stessa origine dei dati e la stessa vista origine dati utilizzate durante la generazione originale. Se si aggiunge un'origine dei dati oppure una vista origine dati, il nuovo elemento verrà ignorato dalla procedura guidata. Se si elimina l'origine dei dati o la vista origine dati originale dopo la generazione iniziale, sarà necessario eseguire la procedura guidata dall'inizio. Verranno inoltre eliminate tutte le impostazioni precedenti della procedura guidata. Tutti gli oggetti esistenti in un database sottostante associati a un'origine dei dati o una vista origine dati eliminata verranno considerati come oggetti creati dall'utente durante la successiva esecuzione della Generazione guidata schema.  
  
 Se la vista origine dati non riflette lo stato effettivo del database sottostante al momento della generazione, è possibile che nella Generazione guidata schema vengano rilevati errori durante la generazione dello schema del database dell'area di interesse. Se il tipo di dati specificato per una colonna nella vista origine dati è **int**ma il tipo di dati effettivo della colonna è **string**, ad esempio, il tipo di dati per la chiave esterna verrà impostato nella Generazione guidata schema su **INT** in conformità con la vista origine dati e si verificherà quindi un errore durante la creazione della relazione poiché il tipo effettivo è **string**.  
  
 Se invece si modifica la stringa di connessione dell'origine dei dati impostando un database diverso rispetto alla generazione precedente, non verrà generato alcun errore. Verrà utilizzato il nuovo database senza alcuna modifica al database precedente.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sulla generazione incrementale](../../analysis-services/multidimensional-models/understanding-incremental-generation.md)  
  
  

