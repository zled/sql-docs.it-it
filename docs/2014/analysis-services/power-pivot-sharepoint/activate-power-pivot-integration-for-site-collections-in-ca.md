---
title: Attivare integrazione delle funzionalità di PowerPivot per le raccolte siti in Amministrazione centrale | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62a27e53-446a-42d7-b5db-c009e02d4904
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 00e8f0336c075c14feb8c4e3b4a8b43e0ebdaf9e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158084"
---
# <a name="activate-powerpivot-feature-integration-for-site-collections-in-central-administration"></a>Attivare l'integrazione delle funzionalità di PowerPivot per le raccolte siti in Amministrazione centrale
  L'attivazione dell'integrazione della caratteristica PowerPivot per raccolte siti specifiche è obbligatoria se è stata utilizzata l'opzione di installazione Farm esistente per installare SQL Server PowerPivot per SharePoint. Se PowerPivot per SharePoint è stato installato utilizzando l'opzione Nuovo server, è possibile ignorare questa attività perché il programma di installazione di SQL Server ha già attivato l'integrazione della caratteristica PowerPivot per la raccolta siti radice durante la configurazione della distribuzione.  
  
 L'attivazione della caratteristica a livello di raccolta siti è necessaria per rendere disponibili pagine e modelli ai siti, incluse le pagine di configurazione per l'aggiornamento dei dati pianificato e le pagine dell'applicazione per Raccolta PowerPivot e raccolte Feed di dati.  
  
 È necessario attivare l'integrazione PowerPivot per ogni raccolta siti in cui è supportata l'elaborazione di query PowerPivot.  
  
## <a name="prerequisites"></a>Prerequisiti  
 È necessario essere un amministratore della raccolta siti.  
  
## <a name="activate-powerpivot-features"></a>Attivare le caratteristiche di PowerPivot  
  
1.  Da un sito di SharePoint scegliere **Azioni sito**.  
  
     Per impostazione predefinita, l'accesso alle applicazioni Web SharePoint viene effettuato tramite la porta 80. Ciò significa che è possibile accedere spesso un sito di SharePoint immettendo http://\<nome computer > per aprire la raccolta siti radice.  
  
2.  Fare clic su **Impostazioni sito**.  
  
3.  In Amministrazione raccolta siti selezionare **Caratteristiche raccolta siti**.  
  
4.  Scorrere verso il basso la pagina fino a individuare **funzionalità di raccolta siti di integrazione PowerPivot**.  
  
5.  Fare clic su **Attiva**.  
  
6.  Ripetere per le raccolte siti aggiuntive aprendo ogni sito e facendo clic su **Azioni sito**.  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione Server PowerPivot e la configurazione in Amministrazione centrale](power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [Configurazione iniziale &#40;PowerPivot per SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)   
 [Installazione PowerPivot per SharePoint 2010](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  