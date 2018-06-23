---
title: 'Attività 6: Impostazione di sinonimi | Documenti Microsoft'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7d35ee9-d1c9-41d9-bbc5-0ca7db93e54d
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 3019c7cf3466fae5579548e3aa8fa9c028145f98
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063216"
---
# <a name="task-6-setting-synonyms"></a>Attività 6: Impostazione di sinonimi
  In questa attività si definiscono due valori di dominio, **USA** e **United States**, del **paese** dominio come sinonimi con **Italia** come il valore iniziale. Poiché il **utilizza valori iniziali** è stata selezionata l'opzione quando si crea il **paese** dominio, qualsiasi **USA** i valori per il **paese** dominio verranno restituiti come **Italia** (quanto United States è il valore iniziale). Vedere [Change Domain Values](http://msdn.microsoft.com/library/hh510408.aspx) per altri dettagli.  
  
1.  Selezionare **paese** dall'elenco di domini.  
  
2.  Passare il **i valori di dominio** scheda.  
  
3.  Fare clic su **Aggiungi nuovo valore dominio** pulsante sulla barra degli strumenti.  
  
4.  Tipo di **USA** per il valore e premere **invio**.  
  
5.  La selezione multipla **Italia** e **USA** tenendo premuto CTRL o MAIUSC, fare doppio clic su elementi selezionati e quindi fare clic su **impostati come sinonimi**. Tramite DQS questi valori vengono raggruppati e uno di essi viene definito come valore iniziale con cui vengono sostituiti gli altri valori.  
  
     ![Menu Imposta come sinonimi](../../2014/tutorials/media/et-settingsynonyms-01.jpg "Menu Imposta come sinonimi")  
  
6.  Si noti che **Italia** è impostato come valore iniziale. Se si desidera USA come valore iniziale, è possibile fare clic su USA e selezionare **imposta come iniziale** opzione. Per questa esercitazione, utilizziamo **Italia** come valore iniziale.  
  
     ![Stati Uniti e USA come sinonimi](../../2014/tutorials/media/et-settingsynonyms-02.jpg "negli Stati Uniti e USA come sinonimi")  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 7: Creazione di un dominio composito](../../2014/tutorials/task-7-creating-a-composite-domain.md)  
  
  