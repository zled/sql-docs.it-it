---
title: Convalidare un'installazione di SQL Server | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating installations [SQL Server]
ms.assetid: 1689af50-d2b8-4aa6-8f27-cc7127157fc8
caps.latest.revision: 31
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 341c3b515d346ee42c8f5e9b01a78b9f3ca08569
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="validate-a-sql-server-installation"></a>Convalidare un'installazione di SQL Server
  Il report sull'individuazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può essere utilizzato per verificare la versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e le caratteristiche di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installate nel computer. In **Report sull'individuazione delle funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installate** viene visualizzato un report di tutte le funzionalità e di tutti i prodotti di [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] e [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] installati nel server locale. Il report sull'individuazione delle funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è disponibile nella pagina **Strumenti** del Centro installazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Per eseguire il report sull'individuazione delle funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :**  
  
 Avviare Centro installazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] facendo clic sul pulsante **Start**, scegliendo **Tutti i programmi**, quindi **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\<nome versione>**, **Strumenti di configurazione** e quindi facendo clic su **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Centro installazione**. Per eseguire il report sull'individuazione delle funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], fare clic su **Strumenti** nell'area di navigazione a sinistra di **Centro installazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**, quindi fare clic su **Report sull'individuazione delle funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installate**.  
  
 Il report sull'individuazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene salvato in %Programmi%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<ultima sessione di installazione\>.  
  
 Tale report può essere generato anche tramite la riga di comando. Eseguire "Setup.exe /Action=RunDiscovery" da un prompt dei comandi. Se si aggiunge "/q" alla riga di comando riportata in precedenza, non viene visualizzata alcuna interfaccia utente, ma il report verrà comunque creato in %Programmi%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<ultima sessione di installazione\>.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e leggere i file di log del programma di installazione di SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
