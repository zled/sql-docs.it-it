---
title: Associare un parametro di Query con un parametro di Report (Generatore Report e SSRS) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [Reporting Services], parameters
- parameters [Reporting Services], queries
ms.assetid: 6d297e1a-ff71-472a-addc-349e863092b5
caps.latest.revision: 49
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6a1efe67725037c9d47f20209c2831db3faef65e
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="associate-a-query-parameter-with-a-report-parameter-report-builder-and-ssrs"></a>Associazione di un parametro di query a un parametro di report (Generatore report e SSRS)
  Quando si definisce una query del set di dati contenente una variabile di query, il comando della query viene analizzato. Per ogni variabile di query, vengono creati un parametro del set di dati e un parametro del report corrispondenti. Il parametro del set di dati punta al parametro del report. Questo consente di immettere un valore che viene passato direttamente alla query. Ogni volta che si modifica il comando della query, si verifica lo stesso processo.  
  
 Per rinominare un parametro di report associato a un parametro di query, è necessario collegare manualmente i parametri di query al parametro di report rinominato utilizzando la procedura illustrata in questo argomento.  
  
> **NOTA:** [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-associate-a-query-parameter-with-a-report-parameter"></a>Per associare un parametro di query a un parametro di report  
  
1.  Nel riquadro dei dati del report fare clic con il pulsante destro del mouse sul set di dati, fare clic su **Proprietà set di dati**, quindi scegliere **Parametri**.  
  
    > **NOTA:** se il riquadro Dati report non è visualizzato, scegliere **Dati report** dal menu **Visualizza** .  
  
2.  Nella colonna **Nome parametro**individuare il nome del parametro di query. I nomi dei parametri vengono popolati automaticamente in base alla query. Ogni volta che si modifica la query, vengono verificati i nuovi parametri della query. I parametri di query creati manualmente non vengono modificati quando la query cambia.  
  
    -   In **Nome parametro**individuare il nome del parametro di query così come è riportato nella query. È anche possibile aggiungere manualmente un nuovo parametro di query e specificare un nome.  
  
    -   In **Valore parametro**digitare o selezionare un'espressione che restituisca il valore da passare al parametro di query. Si tratta in genere del nome del parametro di report.  
  
        > **NOTA:** non è obbligatorio utilizzare i parametri di report come valori per un parametro di query. È infatti possibile utilizzare qualsiasi espressione che restituisca un valore per il parametro.  
  
3.  Ripetere il passaggio 2 per gli altri parametri di query.  
  
## <a name="see-also"></a>Vedere anche  
 [Set di dati condivisi e incorporati del report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   

  
  

