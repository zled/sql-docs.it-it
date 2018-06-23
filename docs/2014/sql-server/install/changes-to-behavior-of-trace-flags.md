---
title: Modifiche al comportamento dei flag di traccia | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- trace flags [SQL Server], behavior changes
ms.assetid: d739df96-2659-4383-8e10-194657632526
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f03a9db47c6296e7d1c4ab764488c44d343393c7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070203"
---
# <a name="changes-to-behavior-of-trace-flags"></a>Modifiche al comportamento dei flag di traccia
  I flag di traccia globali impostati da una sessione diventano immediatamente effettivi nelle altre sessioni. Alcuni flag di traccia di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] non esistono in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Si consiglia di disabilitare tutti i flag di traccia prima di eseguire l'aggiornamento. I flag di traccia che modificano le modalità di disponibilità o il ripristino di database potrebbero impedire il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] da aggiornare correttamente l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È possibile attivare i flag di traccia dopo avere verificato che sono necessari e sono ancora validi in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Se è necessario riabilitare i flag di traccia, eseguire test aggiuntivi sull'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] supporta flag di traccia a livello di sessione e globale. In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] i flag di traccia possono essere specificati come locali o globali utilizzando un argomento aggiuntivo (-1) nel comando DBCC TRACEON. Se questo argomento non viene specificato, il valore predefinito è locale.  
  
 Inoltre, in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], un flag di traccia impostato nella sessione A non diventa automaticamente effettivo in una sessione b già esistente Al contrario, questo flag di traccia ha effetto solo dopo la prima volta che un flag di traccia viene impostato nella sessione B. Questo comportamento è non deterministico in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ed è deterministico in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive, dove i flag di traccia globali impostati nella sessione A vengono immediatamente impostati in altre sessioni simultanee.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
