---
title: Modificare il nome dell'attributo e un tipo di dati (Master Data Services) | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [Master Data Services], changing name
ms.assetid: d348f238-f59d-41c7-ad20-3ccd55bfd9e5
caps.latest.revision: 9
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a1c9e79f7485db3577a17147e2d187d2acc6c521
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="change-an-attribute-name-and-data-type-master-data-services"></a>Modificare il nome e il tipo di dati di un attributo (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]è possibile modificare il nome di un attributo.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Amministrazione sistema** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-change-an-attribute-name-and-type"></a>Per modificare il nome e il tipo di un attributo  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Nella pagina **Gestisci modelli** selezionare un modello dalla griglia, quindi fare clic su **Entità**.  
  
3.  Nella pagina **Gestisci entità** selezionare la riga dell'entità per la quale si vuole creare un attributo.  
  
4.  Fare clic su **Attributi**.  
  
5.  Nella pagina **Gestisci attributi** eseguire una delle operazioni seguenti.  
  
    -   Se l'attributo è per i membri foglia, selezionare **Foglia** nella casella di riepilogo **Tipo di membro** .  
  
    -   Se l'attributo è per i membri consolidati, selezionare **Consolidato** nella casella di riepilogo **Tipo di membro** .  
  
    -   Se l'attributo è per le raccolte, selezionare **Raccolta** nella casella di riepilogo **Tipo di membro** .  
  
6.  Selezionare la riga per l'attributo che si vuole modificare e quindi fare clic su **Modifica**.  
  
7.  Nella casella **Nome** digitare il nome aggiornato dell'attributo. Per un elenco di parole che non vanno usate come nomi di attributo, vedere [Parole riservate &#40;Master Data Services&#41;](../master-data-services/reserved-words-master-data-services.md).  
  
8.  Nell'elenco **Tipo attributo** selezionare un altro tipo.  
  
9. Fare clic su **Salva**.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare un attributo di testo &#40; Master Data Services &#41;](../master-data-services/create-a-text-attribute-master-data-services.md)   
 [Eliminare un attributo &#40; Master Data Services &#41;](../master-data-services/delete-an-attribute-master-data-services.md)   
 [Attributi &#40; Master Data Services &#41;](../master-data-services/attributes-master-data-services.md)  
  
  
