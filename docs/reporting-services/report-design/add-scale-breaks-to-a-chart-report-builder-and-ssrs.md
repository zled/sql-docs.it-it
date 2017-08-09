---
title: Aggiunta di cambi di scala a un grafico (Generatore Report e SSRS) | Documenti Microsoft
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84d66436-ed62-4967-bbbd-b457593ee787
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: c348bd91264d6e3ea314750da62955378f518e2f
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---

# <a name="add-scale-breaks-to-a-chart-report-builder-and-ssrs"></a>Aggiungere cambi di scala a un grafico (Generatore report e SSRS)

  Un cambio di scala è una striscia disegnata attraverso l'area del tracciato del grafico per indicare un'interruzione nella continuità tra i valori massimo e minimo sull'asse dei valori, in genere l'asse verticale o y. Utilizzare un cambio di scala per visualizzare due intervalli distinti nella stessa area del grafico.  
  
 ![Grafico con cambio di scala](../../reporting-services/report-design/media/rs-multipledatarangeschart-scalebreak.gif "grafico con cambio di scala")  
  
> [!NOTE]  
>  Non è possibile specificare il punto in cui posizionare un cambio di scala sul grafico. Vengono utilizzati calcoli specifici in base ai valori del set di dati per determinare se la separazione tra gli intervalli di dati è sufficiente per disegnare un cambio di scala sull'asse dei valori (asse Y) in fase di esecuzione.  
  
 Un esempio di un grafico con cambi di scala è disponibile come report di esempio. Per ulteriori informazioni sul download di questo report di esempio e ad altri utenti, vedere [report di Generatore Report e progettazione Report di esempio](http://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-enable-scale-breaks-on-the-chart"></a>Per abilitare i cambi di scala sul grafico  
  
1.  Fare clic con il pulsante destro del mouse sull'asse verticale, quindi scegliere **Proprietà asse**. Viene visualizzata la finestra di dialogo **Proprietà asse verticale** .  
  
2.  Selezionare la casella di controllo **Abilita cambi di scala** .  
  
### <a name="to-change-the-style-of-the-scale-break"></a>Per modificare lo stile del cambio di scala  
  
1.  Aprire il riquadro Proprietà.  
  
2.  Nell'area di progettazione fare clic con il pulsante destro del mouse sull'asse Y del grafico. Nel riquadro Proprietà verranno visualizzate le proprietà dell'oggetto asse Y (denominato asse del grafico per impostazione predefinita).  
  
3.  Nel sezione **Scala** quindi espandere la proprietà ScaleBreakStyle.  
  
4.  Modificare i valori delle proprietà ScaleBreakStyle, ad esempio BreakLineType e Spacing. Per altre informazioni sulle proprietà del cambio di scala, vedere [Visualizzazione di una serie con più intervalli di dati in un grafico &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/displaying-a-series-with-multiple-data-ranges-on-a-chart.md).  

## <a name="next-steps"></a>Passaggi successivi

[Grafici](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
[Formattazione di un grafico](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
[Finestra di dialogo Proprietà asse, opzioni asse](http://msdn.microsoft.com/library/b276e210-7a12-48ae-971b-7dabae51df11)  

Ulteriori domande? [Provare a porre il forum di Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
