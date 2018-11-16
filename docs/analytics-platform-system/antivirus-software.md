---
title: Il software antivirus - sistema di piattaforma Analitica | Microsoft Docs
description: Se il data center richiede un software antivirus, usare queste linee guida per installare il software antivirus nel sistema di piattaforma Analitica. È consigliabile non installare il software antivirus a meno che non è un requisito fisso del data center.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 2bf94fb04bd6f96de019c7e8543b8a626cebe439
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51699122"
---
# <a name="antivirus-software-for-analytics-platform-system"></a>Software antivirus per il sistema di piattaforma Analitica
Se il data center richiede un software antivirus, usare queste linee guida per installare il software antivirus nel sistema di piattaforma Analitica. È consigliabile non installare il software antivirus a meno che non è un requisito fisso del data center.  
  
> [!WARNING]  
> È consigliabile valutare singolarmente il rischio di sicurezza per ogni computer e per il sistema di piattaforma Analitica nel suo complesso e di selezionare gli strumenti appropriati per il livello di rischio di sicurezza di ciascun computer. Inoltre, è consigliabile che prima di distribuire qualsiasi progetto di protezione da virus, provare l'intero sistema sotto un carico completo per misurare le modifiche della stabilità e prestazioni.  
>   
> Protezione da virus richiede alcune risorse di sistema per l'esecuzione. È necessario eseguire test prima e dopo l'installazione del software antivirus per determinare se è presente alcun effetto sulle prestazioni del sistema di piattaforma Analitica.  
  
In questo argomento si basa sulle indicazioni fornite in [come scegliere il software antivirus per l'esecuzione nei computer che eseguono SQL Server](https://support.microsoft.com/kb/309422) e [KB articolo 961804](https://support.microsoft.com/kb/961804/en-us).  
  
## <a name="exclusion-list-for-physical-hosts"></a>Elenco di esclusione per gli host fisici  
Per installare il software antivirus in host fisici, escludere il seguente elenco di processi e le directory. Questi non devono essere analizzati con il software antivirus.  
  
**Escludere queste directory:**  
  
-   C:\programdata\microsoft\windows\hyper-v. - directory di configurazione macchina virtuale  
  
-   Dischi rigidi C:\Users\Public\Documents\Hyper-V\Virtual - directory unità disco rigido virtuale predefinita  
  
-   C:\clusterStorage - directory unità disco rigido virtuale  
  
**Escludere questi processi:**  
  
-   Gestione delle macchine virtuali (Vmms.exe)  
  
-   Processi di lavoro di macchina virtuale (Vmwp.exe)  
  
## <a name="exclusion-list-for-virtual-machines-vms"></a>Elenco di esclusione per le macchine virtuali (VM)  
Per installare il software antivirus nelle macchine virtuali, escludere nell'elenco seguente di file e directory. Questi non devono essere analizzati con il software antivirus.  
  
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
[Attività di gestione di Appliance &#40;sistema di piattaforma Analitica&#41;](appliance-management-tasks.md)  
  
