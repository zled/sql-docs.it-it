---
title: Visualizzazione di set di dati nascosti per i valori dei parametri di dati multidimensionali (Generatore Report e SSRS) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb01c4ca-4fd6-4629-b595-f0d2565915df
caps.latest.revision: 6
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 89df13eecdce33869199e0b5a8e82b0395679475
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064199"
---
# <a name="show-hidden-datasets-for-parameter-values-for-multidimensional-data-report-builder-and-ssrs"></a>Visualizzare set di dati nascosti per i valori dei parametri di dati multidimensionali (Generatore report e SSRS)
  Il report potrebbe includere set di dati generati automaticamente (noti anche come set di dati nascosti) che per impostazione predefinita non vengono visualizzati nel riquadro dei dati del report. Tali set di dati vengono creati nei modi seguenti:  
  
-   In alcune finestre Progettazione query per i database multidimensionali, è possibile specificare i campi da filtrare nell'area del filtro del riquadro Query e scegliere se creare un parametro di query per il filtro. Se si seleziona l'opzione del parametro, i set di dati del report vengono creati automaticamente per fornire i valori validi per il parametro del report.  
  
-   Se si importa una query basata su database multidimensionali, è possibile inoltre includere set di dati nascosti nel report.  
  
 I set di dati nascosti non possono essere utilizzati da una procedura guidata.  
  
 È possibile modificare la vista nel riquadro dei dati del report per visualizzare tutti i set di dati nel report.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-hidden-datasets"></a>Per visualizzare set di dati nascosti  
  
-   Nel riquadro dei dati del report fare clic con il pulsante destro del mouse sulla cartella Datasets e quindi fare clic su **Mostra set di dati nascosti**.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestre di progettazione query &#40;Generatore report&#41;](../query-designers-report-builder.md)   
 [Strumenti di progettazione query in Reporting Services](../reporting-services-query-designers.md)   
 [Set di dati condivisi e incorporati del report &#40;Generatore report e SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Aggiungere dati a un Report &#40;SSRS e Generatore Report&#41;](report-datasets-ssrs.md)  
  
  