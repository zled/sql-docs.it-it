---
title: Aggiunta o rimozione dei margini da un grafico (Generatore Report e SSRS) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91c43f58-5771-4d33-a54d-0e802d2f5cba
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 795435899de548848ca64cec26d212fd8a80f900
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="add-or-remove-margins-from-a-chart-report-builder-and-ssrs"></a>Aggiungere o rimuovere i margini da un grafico (Generatore report e SSRS)
Negli istogrammi e nei grafici a dispersione a dispersione dei report impaginati di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , i margini laterali alle estremità dell'asse X vengono aggiunti automaticamente. Nei tipi di grafico a barre vengono automaticamente aggiunti margini laterali alle estremità dell'asse Y. In tutti gli altri tipi di grafico non vengono aggiunti margini laterali. Non è possibile modificare le dimensioni del margine.  
  
 Questo argomento non è applicabile per grafici a torta, ad anello, a imbuto o a piramide.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-enable-or-disable-side-margins"></a>Per abilitare o disabilitare i margini laterali  
  
1.  Fare clic con il pulsante destro del mouse sull'asse e selezionare **Proprietà asse**. Verrà visualizzata la finestra di dialogo **Proprietà asse verticale** o **orizzontale** .  
  
2.  Nella pagina **Opzioni asse** impostare la proprietà **Margini laterali** :  
  
    -   **Automatico** Il grafico determinerà se aggiungere o meno un margine laterale in base al tipo di grafico.  
  
    -   **Disabilitato** I grafici a barre, a dispersione e gli istogrammi non disporranno di margini laterali.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Formattazione delle etichette dell'asse in un grafico &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Finestra di dialogo Proprietà asse, opzioni asse &#40; Generatore report e SSRS &#41;](http://msdn.microsoft.com/library/b276e210-7a12-48ae-971b-7dabae51df11)   
 [Specificare un intervallo dell'asse &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/specify-an-axis-interval-report-builder-and-ssrs.md)   
 [Formattare le etichette dell'asse come date o valute &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [Grafici &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
