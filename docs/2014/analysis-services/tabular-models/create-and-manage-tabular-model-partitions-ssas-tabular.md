---
title: Creare e gestire partizioni di modelli tabulari (SSAS tabulare) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dab72cf0-95bc-4b63-95dc-505b5cd881c1
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5cd7eb0621d95d11c29db213cfcff654da3f1240
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054598"
---
# <a name="create-and-manage-tabular-model-partitions-ssas-tabular"></a>Creare e gestire partizioni di modelli tabulari (SSAS tabulare)
  Le partizioni consentono di dividere una tabella in parti logiche. Ogni partizione può quindi essere elaborata (aggiornata) indipendentemente dalle altre. Le partizioni definite per un modello durante la relativa creazione vengono duplicate in un modello distribuito. Una volta distribuite, tali partizioni possono essere gestite tramite la finestra di dialogo **Partizioni** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o tramite uno script. Nelle attività presentate in questo argomento viene descritto come creare e gestire partizioni per un modello distribuito.  
  
 In questo argomento sono incluse le attività seguenti:  
  
-   [Per creare una nuova partizione](#bkmk_create_new)  
  
-   [Per copiare una partizione](#bkmk_copy)  
  
-   [Per unire due o più partizioni](#bkmk_merge)  
  
-   [Per eliminare una partizione](#bkmk_delete)  
  
## <a name="tasks"></a>Attività  
 Per creare e gestire partizioni per un database modello tabulare distribuito si utilizzerà la finestra di dialogo **Partizioni** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Per visualizzare la finestra di dialogo **Partizioni** , in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]fare clic con il pulsante destro del mouse su una tabella, quindi selezionare **Partizioni**.  
  
###  <a name="bkmk_create_new"></a> Per creare una nuova partizione  
  
1.  Nella finestra di dialogo **Partizioni** fare clic sul pulsante **Nuova** .  
  
2.  In **Nome partizione**digitare un nome per la partizione. Per impostazione predefinita, il nome della partizione predefinita sarà numerato in modo incrementale per ogni nuova partizione.  
  
3.  In **Istruzione SQL**digitare o incollare un'istruzione di query SQL che consente di definire le colonne e tutte le clausole che si desidera includere nella partizione nella finestra Query.  
  
4.  Per convalidare l'istruzione, fare clic su **Controlla sintassi**.  
  
###  <a name="bkmk_copy"></a> Per copiare una partizione  
  
1.  Nell'elenco **Partizioni** della **relativa finestra** di dialogo selezionare la partizione che si desidera copiare, quindi fare clic sul pulsante **Copia**.   
  
2.  In **Nome partizione**digitare un nuovo nome per la partizione.  
  
3.  In **Istruzione SQL**modificare l'istruzione di query SQL.  
  
###  <a name="bkmk_merge"></a> Per unire due o più partizioni  
  
-   Nel **partizioni** della finestra di dialogo il **partizioni** elenco, utilizzare Ctrl + fare clic per selezionare le partizioni da unire e quindi fare clic sul **Merge** pulsante.  
  
> [!IMPORTANT]  
>  L'unione delle partizioni non consente di aggiornare i metadati della partizione. Gli amministratori devono modificare l'istruzione SQL per la partizione risultante per assicurare che tramite le operazioni di elaborazione vengano elaborati tutti i dati nella partizione unita.  
  
###  <a name="bkmk_delete"></a> Per eliminare una partizione  
  
-   Nell'elenco **Partizioni** della **relativa finestra** di dialogo selezionare la partizione che si desidera eliminare, quindi fare clic sul pulsante **Elimina**.  
  
## <a name="see-also"></a>Vedere anche  
 [Partizioni di modelli tabulari &#40;tabulare di SSAS&#41;](partitions-ssas-tabular.md)   
 [Elaborare partizioni di modelli tabulari &#40;tabulare di SSAS&#41;](process-tabular-model-partitions-ssas-tabular.md)  
  
  