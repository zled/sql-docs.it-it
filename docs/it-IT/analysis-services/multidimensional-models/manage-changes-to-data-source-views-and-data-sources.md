---
title: Gestire le modifiche a viste origine dati e origini dati | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f05b2c694148d911258e4910d6137dafc08df304
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="manage-changes-to-data-source-views-and-data-sources"></a>Gestire modifiche a viste origine dati e origini dati
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Quando si riesegue la Generazione guidata schema, vengono riutilizzate la stessa origine dei dati e la stessa vista origine dati utilizzate durante la generazione originale. Se si aggiunge un'origine dei dati oppure una vista origine dati, il nuovo elemento verrà ignorato dalla procedura guidata. Se si elimina l'origine dei dati o la vista origine dati originale dopo la generazione iniziale, sarà necessario eseguire la procedura guidata dall'inizio. Verranno inoltre eliminate tutte le impostazioni precedenti della procedura guidata. Tutti gli oggetti esistenti in un database sottostante associati a un'origine dei dati o una vista origine dati eliminata verranno considerati come oggetti creati dall'utente durante la successiva esecuzione della Generazione guidata schema.  
  
 Se la vista origine dati non riflette lo stato effettivo del database sottostante al momento della generazione, è possibile che nella Generazione guidata schema vengano rilevati errori durante la generazione dello schema del database dell'area di interesse. Se il tipo di dati specificato per una colonna nella vista origine dati è **int**ma il tipo di dati effettivo della colonna è **string**, ad esempio, il tipo di dati per la chiave esterna verrà impostato nella Generazione guidata schema su **INT** in conformità con la vista origine dati e si verificherà quindi un errore durante la creazione della relazione poiché il tipo effettivo è **string**.  
  
 Se invece si modifica la stringa di connessione dell'origine dei dati impostando un database diverso rispetto alla generazione precedente, non verrà generato alcun errore. Verrà utilizzato il nuovo database senza alcuna modifica al database precedente.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sulla generazione incrementale](../../analysis-services/multidimensional-models/understanding-incremental-generation.md)  
  
  
