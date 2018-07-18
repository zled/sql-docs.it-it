---
title: Eseguire il backup chiave di crittografia (modalità nativa SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.backupencryptionkey.F1
ms.assetid: eb8c82be-323b-4d86-ab10-c1bf69a4abe3
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 89d5ffa496220bc14b963ebbad08b89b919eec3d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37191242"
---
# <a name="backup-encryption-key-ssrs-native-mode"></a>Backup della chiave di crittografia (modalità nativa SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Usa una chiave di crittografia per proteggere i dati sensibili archiviati nel database del server di report. Disporre di un backup di questa chiave è essenziale per assicurare accesso continuo a stringhe di connessione e credenziali crittografate. È necessario disporre di una copia di backup di questa chiave se si sposta il database del server di report in un altro computer o si modifica il nome utente o la password dell'account del servizio del server di report. Per entrambe le operazioni è necessario ripristinare la chiave da una copia di backup creata in precedenza.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Per aprire la finestra di dialogo chiave di crittografia di Backup, fare clic su **chiavi di crittografia** nel riquadro di spostamento delle [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager e quindi fare clic su **Backup**. Questa finestra di dialogo viene visualizzata anche quando si aggiorna l'account del servizio usando la pagina Account servizio di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager. Per altre informazioni sul [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, consultare [Gestione configurazione Reporting Services &#40;in modalità nativa&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Opzioni  
 **Percorso del file**  
 Specificare un nome di file e il percorso per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] alla chiave simmetrica. La chiave simmetrica non viene mai archiviata in testo non crittografato. Per la protezione del file, è necessario digitare una password.  
  
 **Password**  
 Consente di digitare una password per proteggere il file dall'accesso non autorizzato. Solo gli utenti che conoscono la password saranno in grado di ripristinare la chiave bloccata nel file. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Applica criteri password complessi. La password deve contenere almeno 8 caratteri e includere una combinazione di caratteri alfanumerici maiuscoli e minuscoli e almeno un simbolo.  
  
 **Conferma password**  
 Consente di digitare nuovamente la password immessa.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli argomenti della Guida F1 di Gestione configurazione di Reporting Services &#40;modalità nativa SSRS&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Eseguire il backup e il ripristino delle chiavi di crittografia di Reporting Services](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)   
 [Eliminare e ricreare chiavi di crittografia &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)   
 [Inizializzare un server di report &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)   
 [Archiviare i dati crittografati del server di report &#40;Gestione configurazione SSRS &#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)   
 [Le chiavi di crittografia &#40;modalità nativa SSRS&#41;](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md)  
  
  
