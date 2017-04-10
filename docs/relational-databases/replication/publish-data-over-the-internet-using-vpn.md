---
title: "Pubblicazione dei dati su Internet utilizzando VPN | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "reti VPN [replica di SQL Server]"
  - "pubblicazione sul Web [replica di SQL Server], VPN"
  - "Internet [replica di SQL Server], VPN"
ms.assetid: 9ffb6546-9973-4574-aaa0-8fe0017e3601
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# Pubblicazione dei dati su Internet utilizzando VPN
  La reti private virtuali (VPN) consentono a utenti domestici, succursali, client remoti e altre società di connettersi a una rete aziendale tramite Internet senza alcun rischio di protezione per le comunicazioni. Gli utenti possono utilizzare l'autenticazione di Windows come se fossero connessi a una rete locale (LAN). Tutti i tipi di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la replica può replicare dati in una rete VPN, ma è consigliabile utilizzare la sincronizzazione Web se si utilizza la replica di tipo merge, perché la sincronizzazione Web elimina la necessità di una connessione VPN. Per ulteriori informazioni, vedere [sincronizzazione Web per la replica di tipo Merge](../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
 In un sistema VPN è incluso il software client che consente ai computer di connettersi tramite Internet o, in casi speciali, tramite una rete Intranet al programma di un computer o server dedicato. Facoltativamente, vengono utilizzati la crittografia sia nell'origine che nella destinazione, nonché i metodi di autenticazione degli utenti. Dal punto di vista logico, la connessione VPN su Internet opera analogamente a un collegamento su rete WAN tra siti.  
  
 La rete VPN consente la connessione dei componenti di una rete tramite un'altra rete. Per connettersi, l'utente esegue il tunneling in Internet o in un'altra rete pubblica tramite un protocollo, ad esempio [!INCLUDE[msCoName](../../includes/msconame-md.md)] Point-to-Point Tunneling Protocol (PPTP) o Layer Two Tunneling Protocol (L2TP). Questo processo garantisce la stessa sicurezza e le stesse caratteristiche disponibili in precedenza solo nelle reti private. PPTP è disponibile con Microsoft Windows NT versione 4.0 e [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 (e versioni successive) sistemi operativi. L2TP è disponibile con Windows 2000 e versioni successive.  
  
 L'infrastruttura di routing intermedia di Internet non è visibile all'utente e i dati sembrano essere inviati tramite un collegamento dedicato privato. Dal punto di vista degli utenti, la rete VPN è una connessione point-to-point tra il computer dell'utente e il server dell'azienda.  
  
 Dopo la configurazione del client remoto per la connessione tramite una rete VPN, l'impostazione dell'accesso a Internet e la connessione del client alla rete LAN aziendale, è possibile configurare la replica come se il client fosse connesso direttamente alla LAN. Per motivi di sicurezza, è possibile rendere disponibili risorse di rete diverse per gli utenti connessi tramite VPN e per gli utenti connessi direttamente tramite la rete LAN.  
  
 Per ulteriori informazioni sulla configurazione di una rete VPN, vedere la documentazione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
## Vedere anche  
 [Replica su Internet](../../relational-databases/replication/replication-over-the-internet.md)  
  
  