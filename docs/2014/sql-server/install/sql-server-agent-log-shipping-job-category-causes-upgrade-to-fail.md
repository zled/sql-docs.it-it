---
title: Categoria di processi di distribuzione dei log di SQL Server Agent impedisce esito negativo dell'aggiornamento | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server Agent]
- job categories [SQL Server Agent]
ms.assetid: ef05ce53-c6ce-42ec-9df8-46c951626424
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 61b488250267e497541f15033b347074648d3c9d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48086151"
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
  
  
