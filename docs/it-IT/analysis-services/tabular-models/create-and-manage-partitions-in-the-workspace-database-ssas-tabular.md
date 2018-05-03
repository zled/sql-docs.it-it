---
title: Creare e gestire partizioni nel Database dell'area di lavoro | Documenti Microsoft
ms.custom: ''
ms.date: 02/22/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.asvs.bidtoolset.partitionmgr.f1
ms.assetid: 0b3027d6-652b-4eb3-a197-58b25df65218
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 416181764e71d923a55b6a6dbd0b1448dc619476
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="create-and-manage-partitions-in-the-workspace-database"></a>Creare e gestire partizioni nel database dell'area di lavoro 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Le partizioni consentono di dividere una tabella in parti logiche. Ogni partizione può quindi essere elaborata (aggiornata) indipendentemente o in parallelo ad altre. Le partizioni possono consentire di migliorare la scalabilità e la facilità di gestione di database grandi. Per impostazione predefinita, ogni tabella dispone di una partizione in cui sono incluse tutte le colonne. Attività in questo argomento viene descritto come creare e gestire partizioni nel database dell'area di lavoro modello tramite il **gestione partizioni** nella finestra di dialogo[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]  
  
 Dopo aver distribuito un modello in un'altra istanza di Analysis Services, gli amministratori di database possono creare e gestire partizioni nel modello (distribuito) utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Per ulteriori informazioni, vedere [creare e gestire partizioni di modelli tabulari](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md).  
  
> [!NOTE]  
>  Non è possibile unire partizioni nel database dell'area di lavoro modello tramite la finestra di dialogo Gestione partizioni. Le partizioni possono essere unite in un modello distribuito solo utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="tasks"></a>Attività  
 Per creare e gestire partizioni, usare la finestra di dialogo **Gestione partizioni** . Per visualizzare la finestra di dialogo **Gestione partizioni** , in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]fare clic sul menu **Tabella** e quindi scegliere **Partizioni**.  
  
###  <a name="bkmk_create_new"></a> Per creare una nuova partizione  
  
1.  In Progettazione modelli selezionare la tabella per cui si desidera definire una partizione.  
  
2.  Fare clic sul menu **Tabella** , quindi scegliere **Partizioni**.  
  
3.  Nella casella di riepilogo **Tabella**di **Gestione partizioni** verificare o selezionare la tabella che si vuole partizionare e quindi fare clic su **Nuova**.  
  
4.  In **Nome partizione**digitare un nome per la partizione. Per impostazione predefinita, il nome della partizione predefinita sarà numerato in modo incrementale per ogni nuova partizione.  
  
5.  È possibile selezionare le righe e le colonne da includere nella partizione utilizzando la modalità Anteprima tabella o una query SQL creata tramite la modalità Editor query.  
  
     Per usare la modalità Anteprima tabella (impostazione predefinita), fare clic sul pulsante **Anteprima tabella** in prossimità dell'angolo superiore destro della finestra di anteprima. Scegliere le colonne che si desidera includere nella partizione selezionando la casella di controllo accanto al nome della colonna. Per filtrare le righe, fare clic con il pulsante destro del mouse su un valore della cella e scegliere **Filtro in base al valore della cella selezionata**.  
  
     Per usare un'istruzione SQL, fare clic sul pulsante **Editor query** in prossimità dell'angolo superiore destro della finestra di anteprima e quindi digitare o incollare un'istruzione della query SQL nella finestra Query. Per convalidare l'istruzione, fare clic su **Convalida**. Per usare Progettazione query, fare clic su **Progettazione**.  
  
###  <a name="bkmk_copy"></a> Per copiare una partizione  
  
1.  Nella casella di riepilogo **Tabella**di **Gestione partizioni** verificare o selezionare la tabella contenente la partizione che si vuole copiare.  
  
2.  Dall'elenco **Partizioni** selezionare la partizione che si vuole copiare e quindi fare clic su **Copia**.  
  
3.  In **Nome partizione**digitare un nuovo nome per la partizione.  
  
###  <a name="bkmk_delete"></a> Per eliminare una partizione  
  
1.  Nella casella di riepilogo **Tabella**di **Gestione partizioni** verificare o selezionare la tabella contenente la partizione che si vuole eliminare.  
  
2.  Nell'elenco **Partizioni** selezionare la partizione che si vuole eliminare e quindi fare clic su **Elimina**.  
  
## <a name="see-also"></a>Vedere anche  
 [Partizioni](../../analysis-services/tabular-models/partitions-ssas-tabular.md)   
 [Elaborare partizioni nel database dell'area di lavoro](../../analysis-services/tabular-models/process-partitions-in-the-workspace-databse-ssas-tabular.md)  
  
  
