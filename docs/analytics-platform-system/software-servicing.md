---
title: Software manutenzione - Analitica Platform System | Documenti Microsoft
description: Software di manutenzione in Analitica Platform System (AP).
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 7d9991dfb310e2cebc3c61bbd6f9f04a40a0f38e
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
ms.locfileid: "31538751"
---
# <a name="software-servicing-in-analytics-platform-system"></a>Software di manutenzione in Analitica Platform System
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
  
