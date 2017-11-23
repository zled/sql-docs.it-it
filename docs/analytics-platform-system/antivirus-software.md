---
title: Software antivirus (Analitica piattaforma sistema)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 60ab9a88-d339-4917-a38b-f9481aef38fd
caps.latest.revision: "29"
ms.openlocfilehash: f1d5c81381b486ec89198fed6aa22ccff22a544a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="antivirus-software"></a>Software antivirus
Se il centro dati richiede un software antivirus, è possibile utilizzare queste linee guida per installare il software antivirus nel sistema di piattaforma Analitica. Si consiglia di non installare il software antivirus a meno che non è un requisito rigorosi a livello del data center.  
  
> [!WARNING]  
> È consigliabile valutare singolarmente per ogni computer e per il sistema della piattaforma Analitica nel suo complesso il rischio di sicurezza e di selezionare gli strumenti appropriati per il livello di rischio per la sicurezza di ogni computer. Inoltre, è consigliabile che prima di distribuire qualsiasi progetto di protezione da virus, provare l'intero sistema sotto un carico completo per misurare le modifiche alla stabilità e prestazioni.  
>   
> Protezione da virus richiede alcune risorse di sistema per l'esecuzione. È necessario eseguire il test prima e dopo l'installazione del software antivirus per determinare se è presente alcun effetto sulle prestazioni del sistema di piattaforma Analitica.  
  
Questo argomento è basato sulle indicazioni fornite in [come scegliere il software antivirus in esecuzione in computer che eseguono SQL Server](http://support.microsoft.com/kb/309422) e [961804 articolo KB](http://support.microsoft.com/kb/961804/en-us).  
  
## <a name="exclusion-list-for-physical-hosts"></a>Elenco di esclusione per gli host fisici  
Per installare il software antivirus in host fisici, escludere il seguente elenco di directory e processi. Questi non da analizzare, il software antivirus.  
  
**Escludi directory seguenti:**  
  
-   C:\ProgramData\Microsoft\Windows\Hyper-V - directory di configurazione macchina virtuale  
  
-   Dischi rigidi C:\Users\Public\Documents\Hyper-V\Virtual - directory di unità disco rigido virtuale predefinita  
  
-   C:\clusterStorage - directory unità disco rigido virtuale  
  
**Escludere questi processi:**  
  
-   Virtual machine management (Vmms.exe)  
  
-   Processi di lavoro di macchina virtuale (Vmwp.exe)  
  
## <a name="exclusion-list-for-virtual-machines-vms"></a>Elenco di esclusione per le macchine virtuali (VM)  
Per installare il software antivirus in macchine virtuali, escludere il seguente elenco di file e directory. Questi non da analizzare, il software antivirus.  
  
***PDW_region*-CTL01**  
  
-   C:\windows\cluster\  
  
-   G:\  
  
***appliance_domain*-AD01** e  ***appliance_domain*-AD02**  
  
-   Nessuna restrizione  
  
**Macchine virtuali del nodo di calcolo**  
  
-   C:\windows\cluster\  
  
-   G:\  
  
***appliance_domain*- VMM**  
  
-   Nessuna restrizione  
  
***appliance_domain*- servizi di distribuzione Windows**  
  
-   Nessuna restrizione  
  
***appliance_domain*-ISCSI01**  
  
-   C:\iscsitarget  
  
## <a name="see-also"></a>Vedere anche  
[Attività di gestione dispositivo &#40; Sistema della piattaforma Analitica &#41;](appliance-management-tasks.md)  
  
