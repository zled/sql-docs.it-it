---
title: Assegnare autorizzazioni per oggetti modello (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], assigning object permissions
- permissions [Master Data Services], assigning model object permissions
ms.assetid: 4b80148d-2318-415c-9479-28c240e48bcd
caps.latest.revision: 5
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 0a81b831ea324d71e6c5ac6c7cef92549e76cc65
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37309951"
---
# <a name="assign-model-object-permissions-master-data-services"></a>Assegnare autorizzazioni per oggetti modello (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]assegnare autorizzazioni agli oggetti modello quando è necessario concedere un accesso utente o gruppo ai dati nell'area funzionale **Esplora** di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]o quando è necessario rendere un utente o un gruppo un amministratore.  
  
> [!NOTE]  
>  Quando si assegna l'autorizzazione per un modello, viene implicitamente negata l'autorizzazione per tutti gli altri modelli. La mancata assegnazione di autorizzazioni dell'oggetto modello determina l'impossibilità da parte dell'utente o gruppo di accedere ai dati in **Esplora**.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Autorizzazioni utenti e gruppi** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-assign-model-object-permissions"></a>Per assegnare autorizzazioni dell'oggetto modello  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Autorizzazioni utenti e gruppi**.  
  
2.  Nella pagina **Utenti** o **Gruppi** selezionare la riga relativa all'utente o al gruppo che si desidera modificare.  
  
3.  Fare clic su **Modifica utente selezionato**.  
  
4.  Fare clic sulla scheda **Modelli** .  
  
5.  Facoltativamente selezionare un modello nell'elenco **Modello** .  
  
6.  Fare clic su **Modifica**.  
  
7.  Espandere l'albero e selezionare l'oggetto modello al quale si desidera assegnare le autorizzazioni.  
  
8.  Nel menu, selezionare **Read-only**, **Update**, o **Deny**.  
  
9. Fare clic su **Salva**.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
-   (Facoltativo) [Assegnare autorizzazioni membri gerarchia &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Elimina autorizzazioni per oggetti modello &#40;Master Data Services&#41;](../../2014/master-data-services/delete-model-object-permissions-master-data-services.md)   
 [Autorizzazioni per oggetti modello &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Creare un amministratore di modelli &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-administrator-master-data-services.md)  
  
  
