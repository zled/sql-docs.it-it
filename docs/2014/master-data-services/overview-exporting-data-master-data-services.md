---
title: Esportazione dati (Master Data Services) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exporting data [Master Data Services]
- subscription views [Master Data Services]
- subscription views [Master Data Services], about subscription views
ms.assetid: 8b74409a-ea70-45f8-84c7-da6905e4901a
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 656578a35e70b8371056330e0edec69073816687
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067828"
---
# <a name="exporting-data-master-data-services"></a>Esportazione di dati (Master Data Services)
  È possibile esportare [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] dati nei sistemi di sottoscrizione creando viste delle sottoscrizioni. Qualsiasi sistema di sottoscrizione può visualizzare quindi i dati pubblicati nel database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Per altre informazioni sulle viste, vedere [Viste](../relational-databases/views/views.md).  
  
## <a name="subscription-view-formats"></a>Formati di vista sottoscrizioni  
 Quando si crea una vista in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], è possibile effettuare una scelta da un set di formati di viste standard disponibili in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Questi formati possono essere utilizzati per creare viste in cui sono visualizzati:  
  
-   Tutti i membri foglia e i relativi attributi.  
  
-   Tutti i membri consolidati e i relativi attributi.  
  
-   Tutte le raccolte e i relativi attributi.  
  
-   I membri aggiunti in modo esplicito a una raccolta.  
  
-   I membri in una gerarchia derivata, in formato padre-figlio o a livelli.  
  
-   I membri in tutte le gerarchie esplicite per un'entità, in formato padre-figlio o a livelli.  
  
## <a name="subscription-views-can-become-out-of-date"></a>Le viste delle sottoscrizioni possono diventare non aggiornate  
 Dopo avere creato una vista sottoscrizioni per un'entità o una gerarchia, le modifiche apportate agli oggetti modello associati non vengono applicate automaticamente nella vista. Può essere inoltre necessario rigenerare una vista sottoscrizioni in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] per applicare le modifiche apportate a oggetti modello. La colonna **Modificato** nella pagina **Esporta** viene aggiornata a **Vero** quando gli oggetti modello cambiano. **Vero** indica che è necessario modificare la vista sottoscrizioni e salvarla, in modo da rigenerarla.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Creare una vista sottoscrizioni dei dati master.|[Creare una vista sottoscrizioni &#40;Master Data Services&#41;](create-a-subscription-view-to-export-data-master-data-services.md)|  
|Eliminare una vista sottoscrizioni esistente.|[Eliminare una vista sottoscrizioni &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-subscription-view-master-data-services.md)|  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   [Formati di vista sottoscrizioni &#40;Master Data Services&#41;](../../2014/master-data-services/subscription-view-formats-master-data-services.md)  
  
-   [Viste](../relational-databases/views/views.md)  
  
  