---
title: "Attivare l'integrazione di Power Pivot per le raccolte siti in Autorità di certificazione | Documenti Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62a27e53-446a-42d7-b5db-c009e02d4904
caps.latest.revision: "8"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b30104f3965fcb3df53140010c84425e392c5db3
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="activate-power-pivot-integration-for-site-collections-in-ca"></a>Attivare l'integrazione di Power Pivot per le raccolte siti in Autorità di certificazione
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]L'attivazione [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] integrazione delle funzionalità per le raccolte siti specifiche è necessario se si utilizza l'opzione di installazione Farm esistente per installare SQL Server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint. Se [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint è stato installato usando l'opzione Nuovo server, è possibile ignorare questa attività perché il programma di installazione di SQL Server ha già attivato l'integrazione della caratteristica [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per la raccolta siti radice durante la configurazione della distribuzione.  
  
 L'attivazione della caratteristica a livello di raccolta siti è necessaria per rendere disponibili pagine e modelli ai siti, incluse le pagine di configurazione per l'aggiornamento dei dati pianificato e le pagine dell'applicazione per Raccolta [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] e raccolte Feed di dati.  
  
 È necessario attivare l'integrazione [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per ogni raccolta siti in cui è supportata l'elaborazione di query [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
## <a name="prerequisites"></a>Prerequisiti  
 È necessario essere un amministratore della raccolta siti.  
  
## <a name="activate-power-pivot-features"></a>Attivare le funzionalità di Power Pivot  
  
1.  Da un sito di SharePoint scegliere **Azioni sito**.  
  
     Per impostazione predefinita, l'accesso alle applicazioni Web SharePoint viene effettuato tramite la porta 80. Ciò significa che è possibile accedere spesso a un sito di SharePoint immettendo http://\<nome computer > per aprire la raccolta siti radice.  
  
2.  Fare clic su **Impostazioni sito**.  
  
3.  In Amministrazione raccolta siti selezionare **Caratteristiche raccolta siti**.  
  
4.  Scorrere la pagina verso il basso fino a trovare **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Caratteristica della raccolta siti per l'integrazione**di .  
  
5.  Fare clic su **Attiva**.  
  
6.  Ripetere per le raccolte siti aggiuntive aprendo ogni sito e facendo clic su **Azioni sito**.  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione e configurazione del server PowerPivot in Amministrazione centrale](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [Configurazione iniziale (Power Pivot per SharePoint)](http://msdn.microsoft.com/en-us/3a0ec2eb-017a-40db-b8d4-8aa8f4cdc146)   
 [Installazione di Power Pivot per SharePoint 2010](http://msdn.microsoft.com/en-us/8d47dde7-c941-4280-a934-e2fe3f9a938f)  
  
  
