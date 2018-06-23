---
title: Categoria di processi di distribuzione dei log di SQL Server Agent impedisce esito negativo dell'aggiornamento | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- log shipping [SQL Server Agent]
- job categories [SQL Server Agent]
ms.assetid: ef05ce53-c6ce-42ec-9df8-46c951626424
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 47d7d5024d234478b8b54e3c05b3c22335758782
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068180"
---
# <a name="sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail"></a>La categoria di processi per il log shipping di SQL Server Agent impedisce il completamento dell'aggiornamento
  Il processo di aggiornamento non verrà completato se esiste una categoria di processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent denominata Log shipping.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
## <a name="description"></a>Description  
 Esiste una categoria di processi di sistema denominata Log shipping. Se una delle installazioni da aggiornare contiene già una categoria di processi creata dall'utente denominata Log shipping, sarà necessario rinominarla prima dell'aggiornamento. In caso contrario, l'aggiornamento non verrà completato.  
  
## <a name="see-also"></a>Vedere anche  
 [Il log shipping non verrà eseguito dopo l'aggiornamento](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)   
 [L'aggiornamento verrà modificato l'Account Proxy utente di SQL Server Agent dall'account temporaneo UpgradedProxyAccount](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)   
 [Problemi di aggiornamento di SQL Server Agent](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  