---
title: Il software antivirus - Analitica Platform System | Documenti Microsoft
description: Se il centro dati richiede un software antivirus, è possibile utilizzare queste linee guida per installare il software antivirus nel sistema di piattaforma Analitica. Si consiglia di non installare il software antivirus a meno che non è un requisito rigorosi a livello del data center.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: ed050520a53aea596b2f315047c68d593c578f27
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="antivirus-software-for-analytics-platform-system"></a>Software antivirus per Analitica Platform System
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
  
***appliance_domain *-AD01** e ***appliance_domain *-AD02**  
  
-   Nessuna restrizione  
  
**Macchine virtuali del nodo di calcolo**  
  
-   C:\windows\cluster\  
  
-   G:\  
  
***appliance_domain*-VMM**  
  
-   Nessuna restrizione  
  
***appliance_domain*-WDS**  
  
-   Nessuna restrizione  
  
***appliance_domain*-ISCSI01**  
  
-   C:\iscsitarget  
  
## <a name="see-also"></a>Vedere anche  
[Attività di gestione dello strumento &#40;Analitica Platform System&#41;](appliance-management-tasks.md)  
  
