---
title: Aggiornare tutti i server di destinazione prima di aggiornare il server master | Documenti Microsoft
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
- TSX [SQL Server Agent]
- target servers [SQL Server Agent]
- MSX [SQL Server Agent]
- master servers [SQL Server Agent]
ms.assetid: 2c231793-3878-4a5e-a425-1fa0d787ba84
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fdd218b1d5bfaacaffbd50c50d55dd47d613d207
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157416"
---
# <a name="upgrade-all-target-servers-before-upgrading-the-master-server"></a>Aggiornare tutti i server di destinazione prima di aggiornare il server master
  Prima di aggiornare il server master, aggiornare tutti i computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e che sono configurati come server di destinazione.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
## <a name="description"></a>Description  
 Per automatizzare l'amministrazione negli ambienti multiserver, è necessario disporre almeno di un server master e di un server di destinazione. Il server master distribuisce processi ai server di destinazione e riceve eventi da tali server. Nel server master è inoltre archiviata la copia centrale delle definizioni di processo per i processi eseguiti nei server di destinazione.  
  
 Se il server corrente è configurato come server master, prima di aggiornare il server master aggiornare tutti i server di destinazione.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Se non è possibile aggiornare tutti i server di destinazione prima di aggiornare il server master, è necessario escludere tutti i server di destinazione e reintegrarli dopo l'aggiornamento.  
  
 Per ulteriori informazioni, vedere gli argomenti "Automatizzazione dell'amministrazione in un'organizzazione", "Procedura: Esclusione di un server di destinazione da un server master" e "Procedura: Integrazione di un server di destinazione in un server master" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento di SQL Server Agent](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)   
 [Problemi di aggiornamento di SQL Server Agent](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  