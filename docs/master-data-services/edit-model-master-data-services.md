---
title: Modifica modello (Master Data Services) | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- models [Master Data Services], changing name
ms.assetid: 399eed32-7c61-4239-9c06-996a65219518
caps.latest.revision: 9
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 08291f09ed7bc172fe22534e82b79ecc47ce55e1
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="edit-model-master-data-services"></a>Modifica modello (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], è possibile modificare il nome e descrizione di un modello e indicare per quanti giorni si vogliono conservare i log delle transazioni.  
  
 Per altre informazioni, vedere [Transazioni &#40;Master Data Services&#41;](../master-data-services/transactions-master-data-services.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Amministrazione sistema** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-change-a-model"></a>Per modificare il modello  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Nella pagina **Vista modelli** scegliere **Gestisci** dalla barra dei menu, quindi fare clic su **Modelli**.  
  
3.  Dalla griglia della pagina **Gestione modelli** selezionare la riga per il modello con il nome o la descrizione che si vogliono modificare.  
  
4.  Fare clic su **Modifica**.  
  
5.  Nella casella **Nome** digitare il nome aggiornato del modello.  
  
6.  Nel campo **Descrizione** digitare la descrizione aggiornata del modello.  
  
7.  Nel campo **Giorni di conservazione log** selezionare una delle opzioni per la conservazione dei dati del log. Il valore predefinito è **Impostazione di sistema**, che indica che il valore viene ereditato dalle impostazioni di sistema nel [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Per altre informazioni, vedere [Impostazioni di sistema &#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md).  
  
     Per ignorare l'impostazione di sistema e non rimuovere i dati del log delle transazioni, selezionare **NO**. Per conservare solo i dati del log di oggi e troncare i dati del log relativi a tutti i giorni precedenti, selezionare **SÌ** e impostare il campo **Giorni** su 0. Per conservare i dati del log per un numero specificato di giorni, selezionare **SÌ** e impostare il campo **Giorni** sul numero di giorni.  
  
8.  Fare clic su **Salva modello**.  
  
 La colonna **Stato** nella griglia mostra lo stato dell'operazione sul modello. Quando si fa clic il **Salva modello** pulsante, il ![aggiornamento](../master-data-services/media/mds-model-status-updating.png "aggiornamento") viene visualizzata l'immagine, che indica che il modello sta aggiornando. Se si verificano errori durante la creazione o modifica di un modello, il ![errore](../master-data-services/media/mds-model-status-error.png "errore") viene visualizzata l'immagine. In caso contrario, lo stato è OK e viene visualizzata l'immagine ![OK](../master-data-services/media/mds-model-status-ok.png "OK") .  
  
## <a name="see-also"></a>Vedere anche  
 [Creare un modello di &#40; Master Data Services &#41;](../master-data-services/create-a-model-master-data-services.md)   
 [Eliminare un modello di &#40; Master Data Services &#41;](../master-data-services/delete-a-model-master-data-services.md)   
 [Modelli &#40;Master Data Services&#41;](../master-data-services/models-master-data-services.md)  
  
  
