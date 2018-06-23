---
title: Impostare l'ambito di sincronizzazione (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f4a11e6-6151-47be-a43f-e3dbf6c0e737
caps.latest.revision: 6
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 02ff1a63d0d629b4da008d2a42bc5326857d1e77
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062352"
---
# <a name="set-synchronization-scope-report-builder-and-ssrs"></a>Impostare l'ambito di sincronizzazione (Generatore report e SSRS)
  Gli indicatori consentono di visualizzare i valori dei dati eseguendo la sincronizzazione nell'intervallo di valori dell'indicatore in un ambito specificato. Per impostazione predefinita, l'ambito è il contenitore padre dell'indicatore, ad esempio la tabella o la matrice in cui è contenuto l'indicatore. È possibile modificare la sincronizzazione dell'indicatore a seconda del layout del report. Se, ad esempio, un'area dati quale una tabella dispone di un gruppo di righe, è possibile specificare il gruppo come ambito dell'indicatore. L'indicatore può inoltre omettere la sincronizzazione.  
  
 Opzioni come le unità di misura possono essere impostate tramite espressioni. Per altre informazioni, vedere [Espressioni &#40;Generatore report e SSRS&#41;](expressions-report-builder-and-ssrs.md).  
  
 Per informazioni generali sull'impostazione dell'ambito all'interno dei report, vedere [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-synchronization-scope-of-an-indicator"></a>Per modificare l'ambito di sincronizzazione di un indicatore  
  
1.  Fare clic con il pulsante destro l'indicatore che si desidera modificare e fare clic su **proprietà indicatore**.  
  
2.  Scegliere **Valori e stati** dal riquadro sinistro.  
  
3.  Nell'elenco **Ambito sincronizzazione** fare clic sull'ambito da applicare.  
  
     L'opzione **(nessuno)** , che consente di rimuovere l'ambito di sincronizzazione dall'indicatore, è sempre disponibile. Le altre opzioni dipendono dal layout del report.  
  
     È possibile fare clic sul pulsante **Espressione** (*fx*) per modificare un'espressione che imposta l'ambito.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Indicatori &#40;Generatore report e SSRS&#41;](indicators-report-builder-and-ssrs.md)  
  
  