---
title: "Gruppi di disponibilità con scalabilità in lettura | Microsoft Docs"
ms.custom: 
ms.date: 04/11/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 6dfa046a07b9fd5a3eddbe474b5ea63c1163c26c
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="read-scale-availability-groups"></a>Gruppi di disponibilità con scalabilità in lettura
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

Oltre a riunire le migliori funzionalità a disponibilità elevata per SQL Server, un gruppo di disponibilità è una soluzione completa che offre anche soluzioni integrate di scalabilità. In un'applicazione di database tipica ci sono più client eseguono vari tipi di carichi di lavoro e talvolta si possono causare colli di bottiglia dovuti ai vincoli delle risorse. È possibile liberare risorse e ottenere una velocità effettiva maggiore del carico di lavoro OLTP o fornire prestazioni migliori con scalabilità in sola lettura dei carichi di lavoro. A questo scopo, è possibile sfruttare la tecnologia di replica più veloce per SQL Server, creando un gruppo di database replicati per ripartire i carichi di lavoro di report e analisi nelle repliche di sola lettura. 

Con i gruppi di disponibilità è possibile configurare una o più repliche secondarie per supportare l'accesso in sola lettura ai database secondari.

Le applicazioni client che eseguono i carichi di lavoro di analisi e report possono connettersi direttamente ai database secondari. In alternativa, il cliente può configurare un elenco di routing di sola lettura e connettersi alla replica primaria che inoltra la richiesta di connessione a ognuna delle repliche secondarie dell'elenco di routing in base a un meccanismo round robin.

## <a name="read-scale-availability-groups-without-cluster"></a>Gruppi di disponibilità con scalabilità in lettura senza cluster

In [!INCLUDE[sssql15 md](..\..\..\includes\sssql15-md.md)] e versioni precedenti, per tutti i gruppi di disponibilità è necessario un cluster. Il cluster fornisce continuità aziendale: disponibilità elevata e ripristino di emergenza (HADR). Inoltre, le repliche secondarie possono essere configurate per le operazioni di lettura. La configurazione e il funzionamento di un cluster implicano un sovraccarico operativo maggiore, se la disponibilità elevata non è l'obiettivo. SQL Server 2017 introduce i gruppi di disponibilità con scalabilità in lettura senza cluster. 

Se i requisiti aziendali prevedono di risparmiare risorse per carichi di lavoro di importanza critica in esecuzione nella replica primaria, gli utenti possono ora usare il routing di sola lettura o connettersi direttamente alle repliche secondarie leggibili, senza dipendere dall'integrazione con altre tecnologie di clustering. Queste nuove funzionalità sono disponibili per SQL Server 2017 in esecuzione su piattaforme Windows e Linux.

>[!IMPORTANT]
>Non si tratta di un'installazione a disponibilità elevata. Non ci sono infrastrutture per monitorare e coordinare il rilevamento degli errori e il failover automatico. Per gli utenti che necessitano di funzionalità HADR, usare uno strumento di gestione cluster (WSFC per Windows o Pacemaker per Linux). 

## <a name="use-distributed-availability-groups-for-geographic-read-scale"></a>Usare gruppi di disponibilità distribuiti per la scalabilità in lettura a livello geografico

Soluzioni separate geograficamente possono implementare soluzioni con scalabilità in lettura con gruppi di disponibilità distribuiti. In questo modo è possibile ripartire i carichi di lavoro di lettura dalla replica primaria alle repliche secondarie leggibili ai siti che sono più vicini all'origine dei carichi di lavoro di lettura. Tale soluzione non solo riduce l'utilizzo delle risorse nella replica primaria, ma migliora anche la velocità effettiva di lettura riducendo la latenza di rete e sfruttando risorse dedicate.

Un singolo gruppo di disponibilità distribuito può avere fino a 17 repliche secondarie leggibili. Per accrescere la capacità di scalabilità, è possibile interconnettere più gruppi di disponibilità con la tecnica del daisy chain e aumentare ulteriormente il numero di repliche leggibili. È inoltre possibile distribuire due gruppi di disponibilità distribuiti dallo stesso gruppo di disponibilità per letture a bassa latenza in ambienti dislocati in località geografiche diverse.




## <a name="next-steps"></a>Passaggi successivi 

[Configurare un gruppo di disponibilità con scalabilità in lettura per Linux](../../../linux/sql-server-linux-availability-group-configure-rs.md)

## <a name="see-also"></a>Vedere anche  
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  

