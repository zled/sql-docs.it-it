---
title: Eliminare le autorizzazioni membri gerarchia (Master Data Services) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting member permissions [Master Data Services]
- members [Master Data Services], deleting permissions
- permissions [Master Data Services], deleting member permissions
ms.assetid: 7f22d5e2-70c1-422c-99c2-e995a47d812a
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3c06cb0309491e9663e4b130b9a641bbbc3a07be
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="delete-hierarchy-member-permissions-master-data-services"></a>Eliminare le autorizzazioni membri gerarchia (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] eliminare le autorizzazioni dell'oggetto modello per rimuovere qualsiasi assegnazione attribuita.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Autorizzazioni utenti e gruppi** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-delete-hierarchy-member-permissions"></a>Per eliminare le autorizzazioni membri gerarchia  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Autorizzazioni utenti e gruppi**.  
  
2.  Nella pagina **Utenti** o **Gruppi** selezionare la riga relativa all'utente o al gruppo che si desidera modificare.  
  
3.  Fare clic su **Modifica utente selezionato**.  
  
4.  Fare clic sulla scheda **Membri gerarchia** .  
  
5.  Selezionare un modello dall'elenco **Modello** .  
  
6.  Selezionare una versione dall'elenco **Versione** .  
  
7.  Fare clic su **Modifica**.  
  
8.  Individuare il nodo dell'albero con l'autorizzazione nel panello **Autorizzazioni membri gerarchia** .  
  
9. Fare clic sul nodo dell'albero e quindi scegliere **Nessuno** dal menu di scelta rapida.  
  
    > [!NOTE]  
    >  Se l'autorizzazione viene ereditata da un gruppo, non sarà possibile rimuoverla da un utente. È necessario invece rimuovere l'autorizzazione dal gruppo.  
  
10. Fare clic su **Salva**.  
  
## <a name="see-also"></a>Vedere anche  
 [Le autorizzazioni membri gerarchia &#40; Master Data Services &#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Assegnare autorizzazioni membri gerarchia &#40; Master Data Services &#41;](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)  
  
  
