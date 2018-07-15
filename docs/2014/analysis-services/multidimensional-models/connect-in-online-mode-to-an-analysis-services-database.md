---
title: Connettersi in modalità Online a un Database di Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, connecting
ms.assetid: 33041234-7106-404f-a289-8e904f32aff2
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 74aaef89542270af7be03d4e391a538d3ee33d09
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37286127"
---
# <a name="connect-in-online-mode-to-an-analysis-services-database"></a>Connettersi in modalità online a un database di Analysis Services
  È possibile connettersi direttamente a un database esistente di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e modificare gli oggetti al suo interno. In caso di connessione diretta a un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , le modifiche agli oggetti vengono implementate in modo immediato e non viene creato alcun progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
### <a name="to-connect-directly-to-an-analysis-services-database-by-using-sql-server-data-tools"></a>Per connettersi direttamente a un database di Analysis Services mediante gli strumenti dati di SQL Server  
  
1.  Aprire [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Scegliere **Apri** dal menu **File** e quindi fare clic su **Database di Analysis Services**.  
  
3.  Selezionare **Connetti a database esistente**.  
  
4.  Specificare il nome del server e il nome del database.  
  
     È possibile digitare il nome del database oppure eseguire una query sul server per visualizzare i database esistenti in tale server.  
  
5.  Fare clic su **OK**.  
  
     È ora possibile modificare direttamente qualsiasi oggetto all'interno del database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di Analysis Services progetti e database durante la fase di sviluppo](work-with-analysis-services-projects-and-databases-in-development.md)   
 [Creazione multidimensionali di modelli di utilizzo di SQL Server Data Tools &#40;SSDT&#41;](creating-multidimensional-models-using-sql-server-data-tools-ssdt.md)  
  
  
