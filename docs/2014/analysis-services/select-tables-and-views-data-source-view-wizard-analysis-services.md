---
title: Selezione tabelle e viste (Creazione guidata vista origine di dati) (Analysis Services) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.datasourceviewwizard.selecttablesandviews.f1
ms.assetid: ea7d1232-f213-46e9-90d9-0fd616ca003d
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 8bf3897fe2466b00c0346590147884696b632b7b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068794"
---
# <a name="select-tables-and-views-data-source-view-wizard-analysis-services"></a>Selezione tabelle e viste (Creazione guidata vista origine dati) (Analysis Services)
  La pagina **Selezione tabelle e viste** consente di selezionare le tabelle o le viste dall'origine dati da includere nella vista origine dati.  
  
## <a name="options"></a>Opzioni  
 **Oggetti disponibili**  
 Elenca le tabelle e le viste nello schema dell'origine dei dati. Se è presente più di uno schema, il nome dello schema viene anteposto al nome dei singoli oggetti. Se è presente un solo schema, ai nomi degli oggetti non verrà anteposto il nome dello schema.  
  
 Per riordinare l'elenco in ordine crescente o decrescente, fare clic su **Nome** o **Tipo**.  
  
 **Oggetti inclusi**  
 Elenca le tabelle e le viste nella vista origine dati.  
  
 Per riordinare l'elenco in ordine crescente o decrescente, fare clic su **Nome** o **Tipo**.  
  
 **Filter**  
 Filtra gli oggetti elencati in **Oggetti disponibili**. Digitare una stringa e quindi fare clic su **Filtro** per elencare solo i nomi che contengono la stringa specificata. Per ricercare una stringa esatta di caratteri, racchiudere la stringa tra virgolette doppie. Il filtro non supporta la distinzione tra maiuscole e minuscole.  
  
 È possibile includere i caratteri jolly inclusi nella tabella seguente in qualsiasi punto della stringa di filtro.  
  
|Carattere jolly|valore|  
|------------------------|-----------|  
|**\***|Qualsiasi stringa di caratteri|  
|**%**|Qualsiasi stringa di caratteri|  
|**?**|Un singolo carattere|  
|**"** *string* **"**|Una stringa letterale di caratteri. Questo carattere jolly corrisponderà a qualsiasi sottostringa nel nome dell'oggetto.|  
  
 **Mostra oggetti di sistema**  
 Mostra gli oggetti di sistema in **Oggetti disponibili**. Questa opzione è disponibile solo se il provider dell'origine dei dati espone gli oggetti di sistema. Se si rimuove un oggetto di sistema dall'elenco **Oggetti inclusi** , questa opzione viene automaticamente selezionata.  
  
 **Aggiungere tabelle correlate**  
 Aggiunge tutte le tabelle correlate a quelle elencate in **Oggetti inclusi**. Questa opzione non consente di aggiungere visualizzazioni, bensì permette di aggiungere tabelle partizionate. Se si seleziona un criterio di corrispondenza dei nomi nella pagina **Corrispondenza nomi** della procedura guidata, questa opzione include anche le tabelle logicamente correlate in base al criterio selezionato. Vengono inoltre incluse le tabelle correlate a nuove tabelle correlate aggiunte e quelle che presentano una struttura identica alla tabella originale.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida F1 del Creazione guidata vista origine dati &#40;Analysis Services&#41;](data-source-view-wizard-f1-help-analysis-services.md)   
 [Viste origine dati nei modelli multidimensionali](multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  