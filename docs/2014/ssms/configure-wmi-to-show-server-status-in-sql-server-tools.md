---
title: Configurare WMI per mostrare lo stato del server in Strumenti SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WMI Provider for Server Events, setting permissions
- WMI permissions [SQL Server]
ms.assetid: 7e97197b-ed4d-40d1-9a52-9ab1d92401d7
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d07c3fe77b0f371e6f01b0546c8fa9615e8bde32
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068623"
---
# <a name="configure-wmi-to-show-server-status-in-sql-server-tools"></a>Configurazione di WMI per mostrare lo stato del server in Strumenti SQL Server
  In questo argomento viene descritto come configurare WMI per mostrare lo stato del server negli strumenti di SQL Server in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Durante la connessione ai server i componenti Server registrati e Esplora oggetti di [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], nonché Gestione configurazione [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , utilizzano Strumentazione gestione Windows (WMI) per ottenere lo stato dei servizi [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (MSSQLSERVER) e [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent (MSSQLSERVER). Per visualizzare lo stato del servizio, l'utente deve disporre dei diritti per accedere in remoto all'oggetto WMI. Per configurare questa autorizzazione, nel server deve essere installato WMI.  
  
##  <a name="SSMSProcedure"></a> Per configurare l'autorizzazione WMI  
  
1.  Scegliere **Esegui** dal menu **Start**nel server remoto.  
  
2.  Nel **Open** digitare `wmimgmt.msc`, quindi fare clic su **OK**.  
  
3.  Nel programma **Windows Management Infrastructure** fare clic con il pulsante destro del mouse su **Controllo WMI (Locale)** e scegliere **Proprietà**.  
  
4.  Nella scheda **Sicurezza** della finestra di dialogo **Proprietà - Controllo WMI (Locale)** espandere **Radice**e fare clic su **CIMV2**.  
  
5.  Fare clic sul pulsante **Sicurezza** per aprire la finestra di dialogo **Sicurezza per ROOT\CIMV2** .  
  
6.  Aggiungere un gruppo o un utente alla casella **Nomi utente o gruppo** e selezionarlo.  
  
7.  Nel **le autorizzazioni per * * *\<utente o gruppo >* , quindi selezionare il **Consenti** colonna, per il **Abilita remoto** l'autorizzazione, per gli utenti a cui si desiderano in modalità remota rilevare lo stato del servizio.  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio, arresto o sospensione del servizio SQL Server Agent](agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  