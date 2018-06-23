---
title: Parametri di controllo di Controllo configurazione sistema | Microsoft Docs
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
- installing SQL Server, system configuration checks
- failed system configuration checks [SQL Server]
- verifying configuration before installation
- SCC [SQL Server]
- system configuration checker
- scanning computer before installation [SQL Server]
- checking configuration before installation
- status information [SQL Server], system configuration checker
- parameters [SQL Server], system configuration checker
- configuration checkers [SQL Server]
- Setup [SQL Server], system configuration checker
ms.assetid: 8e712c15-6bfa-4d71-b303-9526101e5594
caps.latest.revision: 44
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6385a1174bdb5d64279dfcee18e71343bc98a77d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169054"
---
# <a name="check-parameters-for-the-system-configuration-checker"></a>Parametri di controllo di Controllo configurazione sistema
  Durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene eseguita l'analisi del computer in cui verrà installato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite Controllo configurazione sistema. Questo strumento consente di verificare le condizioni che impediscono la corretta installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Prima dell'avvio dell'installazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , lo strumento recupera le informazioni sullo stato di ciascun elemento. Il risultato viene confrontato con i requisiti, quindi vengono fornite indicazioni per la rimozione di eventuali problemi che impediscono di proseguire.  
  
 Con il controllo della configurazione di sistema viene generato un report con una breve descrizione di ogni regola eseguita, nonché lo stato dell'esecuzione. Il report controllo configurazione sistema si trova nel percorso % programfiles %\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< aaaammgg_hhmm >\\.  
  
## <a name="see-also"></a>Vedere anche  
 [Requisiti hardware e Software per l'installazione di SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)   
 [Considerazioni sulla sicurezza per un'installazione di SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)   
 [Aggiornamenti di versione ed edizione supportati](supported-version-and-edition-upgrades.md)  
  
  