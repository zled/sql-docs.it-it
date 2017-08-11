---
title: Modificare l'ordine di un parametro di Report (Generatore Report e SSRS) | Documenti Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: abd61e19-dba3-423c-a26c-e8bc43197d3f
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3377e943ddf7d8c7bd06aeab52ee263a754af25c
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="change-the-order-of-a-report-parameter-report-builder-and-ssrs"></a>Modificare l'ordine di un parametro del report (Generatore report e SSRS)
  Modificare l'ordine dei parametri del report quando un parametro dipendente è elencato prima del parametro da cui dipende. L'ordine dei parametri è importante quando sono presenti parametri di propagazione o quando si desidera indicare il valore predefinito di un parametro prima che gli utenti scelgano i valori per altri parametri. Un parametro dipendente del report contiene un riferimento, nella query dei valori predefiniti o in quella dei valori validi, a un parametro di query che punta a un parametro del report successivo nell'elenco dei parametri del riquadro dei **dati del report** .  
  
 L'ordine con cui i parametri vengono visualizzati nella barra degli strumenti del visualizzatore di report quando viene eseguito il report è determinato dall'ordine dei parametri nel riquadro dei **dati del report** e dalla posizione dei parametri nel riquadro dei parametri personalizzati. Per ulteriori informazioni, vedere [personalizzare il riquadro dei parametri in un Report &#40; Generatore report &#41;](../../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-change-the-order-of-report-parameters"></a>Per modificare l'ordine dei parametri del report  
  
È possibile modificare l'ordine dei parametri del report eseguendo una delle operazioni seguenti:  
  
-   Fare clic su un parametro nel riquadro dei **dati del report** e usare i pulsanti freccia Su e freccia Giù per spostare il parametro in una posizione superiore o inferiore nell'elenco, come mostrato nell'immagine seguente.  Quando si modifica l'ordine del parametro del riquadro dei **dati del report** , viene modificata la posizione del parametro nel riquadro.  
  
     ![Modificare l'ordine dei parametri nel riquadro dati Report](../../reporting-services/report-design/media/ssrs-changeorderofparameters-reportdata.png "modificare l'ordine dei parametri nel riquadro dati Report")  
  
-   Nel riquadro dei parametri trascinare il parametro in una nuova colonna o riga del riquadro. Quando si modifica la posizione del parametro nel riquadro, viene modificato l'ordine del parametro nel riquadro dei **dati del report** . Per ulteriori informazioni sullo spostamento nel riquadro dei parametri, vedere [personalizzare il riquadro dei parametri in un Report &#40; Generatore report &#41; ](../../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md).  
  
## <a name="see-also"></a>Vedere anche  
 [I parametri di report &#40; Generatore report e progettazione Report &#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Guida di Generatore report per finestre di dialogo, riquadri e procedure guidate](http://msdn.microsoft.com/en-us/2da24891-0b6d-4d3c-8b18-81b98752642f)   
 [Aggiungere parametri di propagazione a un Report &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Esercitazione: Aggiungere un parametro di Report &#40; Generatore report &#41;](../../reporting-services/tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Aggiungere i filtri di set di dati, i filtri di area dati e i filtri di gruppo &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Riferimenti alla raccolta di parametri &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/built-in-collections-parameters-collection-references-report-builder.md)  
  
  
