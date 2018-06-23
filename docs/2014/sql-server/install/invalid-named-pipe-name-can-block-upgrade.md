---
title: Nome di named pipe non valido può bloccare l'aggiornamento | Documenti Microsoft
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
- invalid named pipes [SQL Server]
- named pipes
ms.assetid: 58c2199c-4fdf-4d43-ac1c-842703344b75
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c94c1eeff18bff698e2a6353e29b72dd33278d03
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065522"
---
# <a name="invalid-named-pipe-name-can-block-upgrade"></a>Un nome di named pipe non valido può bloccare l'aggiornamento
  L'aggiornamento non riesce se il protocollo Named Pipes non è configurato correttamente.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Durante l'aggiornamento, viene avviato il programma di installazione di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] istanza con supporto della memoria condivisa, una named pipe che accetta solo connessioni locali. Se il nome di pipe specificato nel server non è vuoto, deve iniziare con la stringa "\\\\. \pipe\\" sia valido. Se il nome non è valido, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] non verrà avviato e l'installazione non verrà completata.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Usare la  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilità Configurazione di rete** per attribuire un nome valido alla named pipe, quindi eseguire l'installazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
