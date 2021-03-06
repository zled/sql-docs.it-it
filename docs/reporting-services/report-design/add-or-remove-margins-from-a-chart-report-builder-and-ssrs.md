---
title: Aggiungere o rimuovere i margini da un grafico (Generatore report e SSRS) | Microsoft Docs
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 91c43f58-5771-4d33-a54d-0e802d2f5cba
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e718b04a9a2fa16375f6c347246fc3e862f22511
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50029290"
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
 [Formattazione delle etichette degli assi in un grafico &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Finestra di dialogo Proprietà asse, Opzioni asse &#40;Generatore report e SSRS&#41;](https://msdn.microsoft.com/library/b276e210-7a12-48ae-971b-7dabae51df11)   
 [Specificare un intervallo dell'asse &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/specify-an-axis-interval-report-builder-and-ssrs.md)   
 [Formattazione delle etichette degli assi come date o valute &#40;Generatore report e SSRSSSRS&#41;](../../reporting-services/report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [Grafici &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
