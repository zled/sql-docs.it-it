---
title: "Parametri di controllo di Controllo configurazione sistema | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installazione di SQL Server, controlli configurazione sistema"
  - "controlli della configurazione di sistema non riusciti [SQL Server]"
  - "verifica della configurazione prima dell'installazione"
  - "Controllo configurazione sistema [SQL Server]"
  - "controllo della configurazione di sistema"
  - "analisi del computer prima dell'installazione [SQL Server]"
  - "controllo della configurazione prima dell'installazione"
  - "informazioni sullo stato [SQL Server], controllo configurazione sistema"
  - "parametri [SQL Server], controllo configurazione sistema"
  - "controlli della configurazione [SQL Server]"
  - "installazione [SQL Server], controllo configurazione sistema"
ms.assetid: 8e712c15-6bfa-4d71-b303-9526101e5594
caps.latest.revision: 46
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 46
---
# Parametri di controllo di Controllo configurazione sistema
  Durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene eseguita l'analisi del computer in cui verrà installato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite Controllo configurazione sistema. Questo strumento consente di verificare le condizioni che impediscono la corretta installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Prima dell'avvio dell'installazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , lo strumento recupera le informazioni sullo stato di ciascun elemento. Il risultato viene confrontato con i requisiti, quindi vengono fornite indicazioni per la rimozione di eventuali problemi che impediscono di proseguire.  
  
 Con il controllo della configurazione di sistema viene generato un report con una breve descrizione di ogni regola eseguita, nonché lo stato dell'esecuzione. Il report di controllo della configurazione di sistema si trova nel percorso %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<AAAAMMGG_HHMM>\\.  
  
## Vedere anche  
 [Requisiti hardware e software per l'installazione di SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)   
 [Considerazioni sulla sicurezza per un'installazione di SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)   
 [Aggiornamenti di versione ed edizione supportati](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
  