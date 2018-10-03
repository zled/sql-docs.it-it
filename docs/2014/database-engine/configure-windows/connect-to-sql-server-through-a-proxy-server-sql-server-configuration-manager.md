---
title: Connettersi a SQL Server tramite un Server Proxy (Gestione configurazione SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Remote WinSock
- RWS
- LATs
- proxy servers [SQL Server]
- connections [SQL Server], proxy server
- Microsoft Proxy Server [SQL Server]
- local address tables [SQL Server]
ms.assetid: 39714de0-2a1f-4179-9091-5c3fa4612545
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 790aaf6091772bd051d100d9ed2410094c8eb16a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087871"
---
# <a name="connect-to-sql-server-through-a-proxy-server-sql-server-configuration-manager"></a>Connessione a SQL Server tramite un server proxy (Gestione configurazione SQL Server)
  In questo argomento viene illustrato come connettersi a SQL Server tramite un server proxy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando Gestione configurazione SQL Server. Per l'attesa da postazioni remote tramite Remote WinSock (RWS), definire la tabella di indirizzi locali (LAT, Local Address Table) per il server proxy, in modo che l'indirizzo del nodo di attesa non sia compreso nell'intervallo degli indirizzi della tabella LAT.  
  
##  <a name="SSMSProcedure"></a> Uso di Gestione configurazione SQL Server  
  
#### <a name="to-enable-connections-to-sql-server-through-microsoft-proxy-server"></a>Per consentire le connessioni a SQL Server tramite Microsoft Proxy Server  
  
1.  Seguire i passaggi in [Configurazione di un server per l'attesa su una porta TCP specifica &#40;Gestione configurazione SQL Server&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md) per determinare le porte TCP/IP usate dal [!INCLUDE[ssDE](../../includes/ssde-md.md)] o per configurare il [!INCLUDE[ssDE](../../includes/ssde-md.md)] per l'uso della porta desiderata.  
  
2.  Nel server proxy definire la tabella di indirizzi locali (LAT) per il server proxy, affinché l'indirizzo del nodo di attesa non sia compreso nell'intervallo delle voci della tabella LAT. Per ulteriori informazioni, vedere la documentazione del server proxy.  
  
  
