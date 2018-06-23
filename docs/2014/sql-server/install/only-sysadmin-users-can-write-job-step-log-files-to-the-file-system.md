---
title: Solo gli utenti sysadmin possono scrivere file di log di passaggi di processo nel file System | Documenti Microsoft
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
- job step log files [SQL Server Agent]
- log files [SQL Server Agent]
- writing job step log files
ms.assetid: d26a7cef-1a60-4c95-b9df-f8b4fec59f9b
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e0b7638bbbf33cdd820467cd21edc40a6f5c42ee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069962"
---
# <a name="only-sysadmin-users-can-write-job-step-log-files-to-the-file-system"></a>Solo gli utenti sysadmin possono scrivere file di log dei passaggi del processo nel file system
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] scrive facoltativamente un log per ogni passaggio del processo.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
## <a name="description"></a>Description  
 In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent può scrivere log nel file System per i processi che sono proprietà dei membri del **sysadmin** ruolo predefinito del server. Se il proprietario del processo non è un membro del **sysadmin** ruolo e se l'account proxy è abilitato, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent può scrivere log nel file System utilizzando le credenziali dell'account proxy.  
  
 Dopo l'aggiornamento, i processi di proprietà da parte degli utenti che non sono membri del **sysadmin** ruolo predefinito del server non possono più scrivere log nel file System. Al contrario, questi utenti possono selezionare l'opzione per scrivere i log in una tabella di **msdb** database. I membri del **sysadmin** ruolo può ancora scrivere file di log nel file System.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Dopo l'aggiornamento, i processi di proprietà da parte degli utenti che non sono membri del **sysadmin** ruolo continua a essere eseguita, ma non verranno creati log. Per registrare i passaggi del processo in una tabella, gli utenti che non sono membri del **sysadmin** ruolo è necessario aggiornare manualmente i processi.  
  
 Per ulteriori informazioni, vedere gli argomenti "Creazione di processi", "Creazione di passaggi di processo" e "Gestione di più passaggi di processo" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento di SQL Server Agent](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  