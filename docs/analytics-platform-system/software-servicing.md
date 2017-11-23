---
title: Software per la manutenzione (Analitica piattaforma sistema)
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
ms.assetid: cec4d924-c88f-470c-84bb-0af3e21aabf1
caps.latest.revision: "33"
ms.openlocfilehash: 9741ca7440e8ec1dd0a40ff7e19a98ec6cc02cf2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="software-servicing"></a>Manutenzione del software
Questa sezione vengono riepilogati i requisiti per gli accessori Analitica Platform System, incluse le correzioni rapide WSUS e di sistema della piattaforma Analitica di manutenzione software.  
  
## <a name="Basics"></a>Nozioni fondamentali di manutenzione del software  
**WSUS:** dispositivo Analitica Platform System deve essere configurato per ricevere gli aggiornamenti da Windows Server Update Services (WSUS). Questi aggiornamenti includono importanti modifiche al software di dispositivo. Dopo averli configurati, molti aggiornamenti verranno installati automaticamente e non richiedono interventi di gestione. In genere, gli aggiornamenti di WSUS vengono configurati durante la [configurare Windows Server Update Services &#40; Windows Server Update Services &#41; &#40; Sistema della piattaforma Analitica &#41; ](configure-windows-server-update-services-wsus.md) passaggio eseguito durante l'installazione di nuovo dispositivo. In caso contrario, questo passaggio di configurazione può essere eseguito in un secondo momento. Per informazioni su WSUS, vedere il [sito Web WSUS Guida](http://go.microsoft.com/fwlink/?LinkId=202417).  
  
**Hotfix:** , inoltre, potrebbe essere necessario applicare aggiornamenti rapidi di sistema della piattaforma Analitica. Oggetto *hotfix* è un aggiornamento software che viene creato per un cliente specifico risolvere un problema con il software del sistema di piattaforma Analitica. Ogni aggiornamento rapido è un file eseguibile che installa la correzione per il problema specifico del cliente. Ogni aggiornamento rapido contiene inoltre un accumulo di tutti gli aggiornamenti software rilasciati in precedenza per Windows, SQL Server e il sistema di piattaforma Analitica. Se è necessario installare un hotfix, il supporto tecnico Microsoft sarà hotfix e le istruzioni.  
  
**Ambito degli aggiornamenti:** l'applicazione di un hotfix o service pack al sistema di piattaforma Analitica deve essere l'intero dispositivo offline. Vale a dire, saranno interessate aree PDW sia HDInsight.  
  
**Adattatore di destinazione di SSIS e gli strumenti Client:** quando l'applicazione di un hotfix che sono state apportate modifiche a SSIS destinazione Adapter MSI o MSI di strumenti Client, verranno aggiornati i file MSI nel **C:\PDWINST\ClientTools** directory del nodo di controllo. L'hotfix non installa automaticamente i componenti dal file MSI aggiornati. Per aggiornare tali componenti, il cliente deve disinstallare le versioni precedenti dei componenti e installare nuove versioni dei file MSI aggiornati. Durante la disinstallazione di un hotfix che sono state apportate modifiche a SSIS destinazione Adapter MSI o MSI strumenti Client, i file MSI per tali componenti verranno annullate le versioni precedenti. Per ripristinare tali componenti per una versione precedente, il cliente deve disinstallare le versioni esistenti (più recente) dei componenti e reinstallare le versioni precedenti dei file MSI ripristinati.  
  
## <a name="software-servicing-topics"></a>Argomenti di manutenzione del software  
Gli argomenti seguenti descrivono come gestire la manutenzione del software nel dispositivo:  
  
-   [Scaricare e applicare gli aggiornamenti di Microsoft &#40; Sistema della piattaforma Analitica &#41;](download-and-apply-microsoft-updates.md)  
  
-   [Disinstallare gli aggiornamenti di Microsoft &#40; Sistema della piattaforma Analitica &#41;](uninstall-microsoft-updates.md)  
  
-   [Applica gli hotfix del sistema di piattaforma Analitica &#40; Sistema della piattaforma Analitica &#41;](apply-analytics-platform-system-hotfixes.md)  
  
-   [Disinstallare gli aggiornamenti rapidi del sistema di piattaforma Analitica &#40; Sistema della piattaforma Analitica &#41;](uninstall-analytics-platform-system-hotfixes.md)  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
