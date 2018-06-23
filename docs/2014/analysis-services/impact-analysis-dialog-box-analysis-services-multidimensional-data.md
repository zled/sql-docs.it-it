---
title: Influire sulla finestra di dialogo Analisi (Analysis Services - dati multidimensionali) | Documenti Microsoft
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
- sql12.asvs.process.impactanalysisdialog.f1
ms.assetid: 208268eb-4e14-44db-9c64-6f74b776adb6
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: da3a687a637dee6b3b9df59eecebf957f06e64be
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054392"
---
# <a name="impact-analysis-dialog-box-analysis-services---multidimensional-data"></a>Finestra di dialogo Analisi di impatto (Analysis Services - Dati multidimensionali)
  Utilizzare la finestra di dialogo **Analisi di impatto** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] e in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] per identificare ed eventualmente elaborare gli oggetti dipendenti sui quali influisce l'elaborazione degli oggetti elencati nella finestra di dialogo **Elabora** . Per visualizzare la finestra di dialogo **Analisi di impatto** , è possibile fare clic su **Analisi di impatto** nella finestra di dialogo **Elabora** .  
  
> [!NOTE]  
>  Vengono visualizzate più occorrenze di uno stesso oggetto qualora quest'ultimo sia interessato da più eventi.  
  
## <a name="options"></a>Opzioni  
 **Elenco oggetti**  
 Visualizza l'elenco degli oggetti dipendenti in una griglia. La griglia include le colonne seguenti:  
  
 **nome oggetto**  
 Visualizza il nome dell'oggetto dipendente che può essere necessario elaborare. L'icona a sinistra del nome indica il tipo di oggetto.  
  
 **Tipo**  
 Indica il tipo di oggetto dipendente che può essere necessario elaborare.  
  
 **Tipo impatto**  
 Indica l'effetto che l'elaborazione degli oggetti elencati nella finestra di dialogo **Elabora** avrà sull'oggetto dipendente. Nella tabella seguente vengono elencati i possibili effetti dell'elaborazione, ognuno dei quali viene individuato come la causa di un avviso o di un errore.  
  
|Impatto|Message|  
|------------|-------------|  
|L'oggetto verrà cancellato (non elaborato)|Avviso|  
|L'oggetto risulterà non valido|Errore|  
|L'aggregazione verrà rimossa|Avviso|  
|L'aggregazione flessibile verrà rimossa|Avviso|  
|Gli indici verranno rimossi|Avviso|  
|Gli oggetti che non sono figli verranno elaborati|Avviso|  
  
 **Oggetto del processo**  
 Consente di selezionare gli oggetti dipendenti che si desidera includere nell'operazione di elaborazione. Sarà necessario elaborare gli oggetti dipendenti non selezionati al termine dell'operazione di elaborazione. In caso contrario, non sarà possibile utilizzarli.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestre di progettazione e finestre di dialogo di Analysis Services &#40;dati multidimensionali&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Elaborare la finestra di dialogo &#40;Analysis Services - dati multidimensionali&#41;](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  