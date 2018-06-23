---
title: Spostare membri all'interno di una gerarchia (Master Data Services) | Documenti Microsoft
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
- hierarchies [Master Data Services], moving members
- explicit hierarchies, moving members
- derived hierarchies, moving members
- members [Master Data Services], moving
ms.assetid: 049c9a15-89c1-478c-8438-028fffc9e187
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: d5e8bf5a041458614422b3c89666ea3ffc9f5a86
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069174"
---
# <a name="move-members-within-a-hierarchy-master-data-services"></a>Spostare membri all'interno di una gerarchia (Master Data Services)
  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] è possibile spostare i membri all'interno di una gerarchia per modificarne l'assegnazione della posizione o dell'elemento padre.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre dell'autorizzazione per accedere all'area funzionale **Esplora** .  
  
-   Per le gerarchie esplicite, è necessario disporre di almeno **aggiornamento** delle autorizzazioni necessarie per l'entità.  
  
-   Per le gerarchie derivate, è necessario disporre di almeno **aggiornamento** al modello e per gli attributi basati su dominio utilizzati nella gerarchia.  
  
### <a name="to-move-members-within-a-hierarchy"></a>Per spostare membri in una gerarchia  
  
1.  Nella home page di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] selezionare un modello nell'elenco **Modello** .  
  
2.  Selezionare una versione dall'elenco **Versione** .  
  
3.  Fare clic su **Esplora**.  
  
4.  Dalla barra dei menu, scegliere **gerarchie** e fare clic su *hierarchy_name*.  
  
5.  Nel **gerarchia** riquadro, in cui la gerarchia viene visualizzata in una struttura ad albero, fare clic sulla casella di controllo per ogni membro che si desidera spostare.  
  
6.  Nella parte superiore del **gerarchia** riquadro, fare clic su **Taglia**.  
  
7.  Nel **gerarchia** riquadro, fare clic sulla casella di controllo per il membro che si desidera spostare i membri.  
  
8.  Fare clic su **Incolla**.  
  
    > [!NOTE]  
    >  Nelle gerarchie derivate è possibile spostare i membri solo nello stesso livello. Non è inoltre possibile modificare l'ordinamento dei membri.  
  
## <a name="see-also"></a>Vedere anche  
 [Spostare membri di gerarchie esplicite tramite il processo di gestione temporanea &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md)   
 [Gerarchie derivate &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)   
 [Gerarchie esplicite &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  