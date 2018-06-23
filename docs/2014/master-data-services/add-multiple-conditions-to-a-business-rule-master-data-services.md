---
title: Aggiungere più condizioni a una regola di business (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- business rules [Master Data Services], multiple conditions
ms.assetid: 5f0f6958-6cf2-444b-bdcd-05b887637a0b
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: e5ac7bab7712a268e3fe8fd37f1a5ae799ef55dc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155807"
---
# <a name="add-multiple-conditions-to-a-business-rule-master-data-services"></a>Aggiungere più condizioni a una regola business (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]aggiungere più condizioni **AND** o **OR** a una regola di business quando si vuole creare una regola più complessa.  
  
> [!NOTE]  
>  Se si crea una regola di business che usa l'operatore **OR** , considerare la possibilità di creare una regola separata per ogni istruzione condizionale che può essere valutata indipendentemente. È quindi possibile escludere regole in base alle esigenze, offrendo maggiore flessibilità e una più facile risoluzione dei problemi.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Amministrazione sistema** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   È necessario che sia presente una regola business. Per altre informazioni, vedere [Creare e pubblicare una regola di business &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md).  
  
### <a name="to-add-multiple-conditions-to-a-business-rule"></a>Per aggiungere più condizioni a una regola business  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Dalla barra dei menu scegliere **Gestisci** e fare clic su **Regole business**.  
  
3.  Nella pagina **Manutenzione regola business** selezionare un modello dall'elenco **Modello** .  
  
4.  Dall'elenco **Entità** selezionare un'entità.  
  
5.  Dal **tipo di membro** selezionare un tipo di membro.  
  
6.  Dall'elenco **Attributo** selezionare un attributo o lasciare inalterata l'impostazione predefinita **Tutti**.  
  
7.  Fare clic sulla riga della regola business che si desidera modificare.  
  
8.  Fare clic su **Modifica regola business selezionata**.  
  
9. Nel **componenti** riquadro espandere il **operatori logici** nodo.  
  
10. Fare clic su **AND** oppure **OR** e trascinarlo il **se** del riquadro **AND** etichetta.  
  
11. Nel riquadro **Componenti** espandere il nodo **Condizioni** .  
  
12. Fare clic su una condizione e trascinarla **IF** riquadro, per il **AND** o **OR** etichetta nel passaggio 10.  
  
13. Nel **attributi** riquadro, fare clic su un attributo e trascinarlo il **modifica condizione** del riquadro **attributo Select** etichetta.  
  
14. Nel **modifica condizione** riquadro, completare tutti i campi obbligatori.  
  
15. Nel riquadro **Modifica condizione** fare clic su **Salva elemento**.  
  
16. Facoltativamente, aggiungere altre condizioni, dal **componenti** riquadro, trascinare **AND** o **OR** a qualsiasi **AND** o **OR**nel **IF** riquadro. Seguire quindi i passaggi da 13 a 15.  
  
    > [!TIP]  
    >  Per eliminare una condizione, fare clic sul nome della condizione e nel **modifica condizione** riquadro, fare clic su **l'eliminazione dell'elemento**.  
  
## <a name="see-also"></a>Vedere anche  
 [Le regole di business &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)   
 [Modificare il nome di una regola business &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md)   
 [Configurare le regole di Business per inviare notifiche &#40;Master Data Services&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  