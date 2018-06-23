---
title: Finestra di dialogo partizione (Analysis Services - dati multidimensionali) di tipo merge | Documenti Microsoft
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
- sql12.asvs.sqlserverstudio.mergepartition.f1
ms.assetid: 1c94e250-ee18-4f98-b112-985f6346102a
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: aae229b83f367613cc786a3910b00b45e64f31bd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157260"
---
# <a name="merge-partition-dialog-box-analysis-services---multidimensional-data"></a>Finestra di dialogo Unisci partizione (Analysis Services - Dati multidimensionali)
  Utilizzare la finestra di dialogo **Unisci partizione** in **SQL Server Management Studio** per unire le partizioni relative a un gruppo di misure in un cubo. Per visualizzare la finestra di dialogo **Unisci partizione** , è possibile fare clic con il pulsante destro del mouse sulla cartella Partizioni o su una partizione in **Esplora oggetti** e quindi scegliere **Unisci partizioni** dal menu di scelta rapida.  
  
## <a name="options"></a>Opzioni  
 **Server**  
 Consente di selezionare il nome dell'istanza di Analysis Services contenente la partizione di destinazione.  
  
 **Nome**  
 Consente di selezionare il nome di una partizione esistente da utilizzare come partizione di destinazione.  
  
 **Cartella**  
 Visualizza il nome della cartella contenente la partizione di destinazione se la partizione selezionata in Nome non utilizza la cartella predefinita relativa all'istanza di Analysis Services.  
  
 **Partizioni di origine**  
 Consente di visualizzare una griglia contenente le partizioni di origine che è possibile unire alla partizione di destinazione.  
  
> [!NOTE]  
>  È possibile unire solo le partizioni incluse nello stesso gruppo di misure che condividono la medesima struttura di aggregazione.  
  
 La griglia include le colonne seguenti:  
  
|colonna|Description|  
|------------|-----------------|  
|**Merge**|Consente di unire la partizione di origine alla partizione di destinazione.|  
|**Nome partizione**|Visualizza il nome della partizione di origine.|  
|**Ultima elaborazione**|Visualizza la data e l'ora dell'ultima elaborazione della partizione di origine.|  
  
## <a name="see-also"></a>Vedere anche  
 [Partizioni &#40;Analysis Services - dati multidimensionali&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)   
 [Unire partizioni in Analysis Services &#40;SSAS - multidimensionale&#41;](multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md)  
  
  