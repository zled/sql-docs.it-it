---
title: Software per la manutenzione (Analitica piattaforma sistema)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cec4d924-c88f-470c-84bb-0af3e21aabf1
caps.latest.revision: 33
ms.openlocfilehash: 8bddf00569ad4c5e5c78e801399b589a9f6d5f42
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="software-servicing"></a>Manutenzione del software
Questa sezione vengono riepilogati i requisiti per gli accessori Analitica Platform System, incluse le correzioni rapide WSUS e di sistema della piattaforma Analitica di manutenzione software.  
  
## <a name="Basics"></a>Nozioni fondamentali di manutenzione software  
**WSUS:** dispositivo Analitica Platform System deve essere configurato per ricevere gli aggiornamenti da Windows Server Update Services (WSUS). Questi aggiornamenti includono importanti modifiche al software di dispositivo. Dopo averli configurati, molti aggiornamenti verranno installati automaticamente e non richiedono interventi di gestione. In genere, gli aggiornamenti di WSUS vengono configurati durante la [configurare Windows Server Update Services &#40;WSUS&#41; &#40;Analitica Platform System&#41; ](configure-windows-server-update-services-wsus.md) passaggio eseguito durante l'installazione di nuovo dispositivo. In caso contrario, questo passaggio di configurazione può essere eseguito in un secondo momento. Per informazioni su WSUS, vedere il [sito Web WSUS Guida](http://go.microsoft.com/fwlink/?LinkId=202417).  
  
**Hotfix:** , inoltre, potrebbe essere necessario applicare aggiornamenti rapidi di sistema della piattaforma Analitica. Oggetto *hotfix* è un aggiornamento software che viene creato per un cliente specifico risolvere un problema con il software del sistema di piattaforma Analitica. Ogni aggiornamento rapido è un file eseguibile che installa la correzione per il problema specifico del cliente. Ogni aggiornamento rapido contiene inoltre un accumulo di tutti gli aggiornamenti software rilasciati in precedenza per Windows, SQL Server e il sistema di piattaforma Analitica. Se è necessario installare un hotfix, il supporto tecnico Microsoft sarà hotfix e le istruzioni.  
  
**Ambito degli aggiornamenti:** applicando un hotfix o service pack al sistema di piattaforma Analitica deve essere l'intero dispositivo offline. Vale a dire, saranno interessate aree PDW sia HDInsight.  
  
**Adattatore di destinazione SSIS e gli strumenti Client:** quando si applica un hotfix che sono state apportate modifiche a SSIS destinazione Adapter MSI o MSI di strumenti Client, verranno aggiornati i file con estensione MSI nel **C:\PDWINST\ClientTools** directory del nodo di controllo. L'hotfix non installa automaticamente i componenti dal file MSI aggiornati. Per aggiornare tali componenti, il cliente deve disinstallare le versioni precedenti dei componenti e installare nuove versioni dei file MSI aggiornati. Durante la disinstallazione di un hotfix che sono state apportate modifiche a SSIS destinazione Adapter MSI o MSI strumenti Client, i file MSI per tali componenti verranno annullate le versioni precedenti. Per ripristinare tali componenti per una versione precedente, il cliente deve disinstallare le versioni esistenti (più recente) dei componenti e reinstallare le versioni precedenti dei file MSI ripristinati.  
  
## <a name="software-servicing-topics"></a>Argomenti di manutenzione del software  
Gli argomenti seguenti descrivono come gestire la manutenzione del software nel dispositivo:  
  
-   [Scaricare e applicare gli aggiornamenti di Microsoft &#40;Analitica Platform System&#41;](download-and-apply-microsoft-updates.md)  
  
-   [Disinstallazione di aggiornamenti Microsoft &#40;Analitica Platform System&#41;](uninstall-microsoft-updates.md)  
  
-   [Applicare aggiornamenti rapidi di sistema della piattaforma Analitica &#40;Analitica Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
  
-   [Disinstallare Analitica piattaforma sistema hotfix &#40;Analitica Platform System&#41;](uninstall-analytics-platform-system-hotfixes.md)  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
