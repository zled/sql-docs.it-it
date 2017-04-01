---
title: "Sicurezza della replica su Internet | Microsoft Docs"
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
  - "sicurezza [replica di SQL Server], Internet"
  - "Internet [replica di SQL Server], sicurezza"
ms.assetid: 25b7af05-2721-4b24-9083-fb671e8bf4e0
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# Sicurezza della replica su Internet
  La replica su Internet garantisce una notevole flessibilità, in particolare ai Sottoscrittori mobili, tuttavia richiede una configurazione appropriata per assicurare un livello di sicurezza adeguato. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] consiglia di utilizzare una delle due tecniche per la condivisione protetta delle informazioni tramite Internet:  
  
-   Rete privata virtuale (VPN, Virtual Private Network)  
  
-   Opzione di sincronizzazione tramite il Web per la replica di tipo merge  
  
## Rete privata virtuale  
 Le reti private virtuali costituiscono un approccio semplice e affidabile, strutturato su più livelli, alla replica dei dati [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] su Internet. Dal punto di vista logico, la connessione VPN su Internet opera analogamente a un collegamento su rete WAN tra siti.  
  
 A tale scopo, consentendo all'utente di tunnel tramite Internet o un'altra rete pubblica utilizzando un protocollo, ad esempio [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Point to Point Tunneling Protocol (PPTP) disponibile con il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows NT versione 4.0 o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] sistema operativo Windows 2000 o Layer Two Tunneling Protocol (L2TP) disponibile con il sistema operativo Windows 2000. Questo processo consente di ottenere un livello di sicurezza e di caratteristiche simile a quello disponibile in una rete privata.  
  
 Per ulteriori informazioni sulla configurazione di una rete VPN, vedere la documentazione di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows.  
  
## Sincronizzazione tramite il Web con IIS  
 L'opzione di sincronizzazione tramite il Web per la replica di tipo merge consente di replicare i dati utilizzando il protocollo HTTPS e costituisce, pertanto, un approccio conveniente alla replica dei dati attraverso un firewall. Per ulteriori informazioni, vedere [Configura sincronizzazione Web](../../../relational-databases/replication/configure-web-synchronization.md) e [architettura di sicurezza per la sincronizzazione Web](../../../relational-databases/replication/security/security-architecture-for-web-synchronization.md).  
  
## Vedere anche  
 [Procedure consigliate per la sicurezza della replica](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Sicurezza e protezione & #40; Replica & #41;](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  