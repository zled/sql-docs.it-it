---
title: Ripristinare la chiave di crittografia (modalità nativa SSRS) | Microsoft Docs
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
- SQL12.rsconfigtool.restoreencryptionkey.F1
ms.assetid: 11ce51e5-f5d4-40b6-88d8-9360fb50e66c
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: d9a048a70beb3fa22ab250316b6e630b845e7ca7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37303631"
---
# <a name="restore-encryption-key-ssrs-native-mode"></a>Ripristino della chiave di crittografia (modalità nativa SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Usa una chiave di crittografia per proteggere i dati sensibili archiviati nel database del server di report. Per garantire di disporre di accesso continuo ai dati crittografati, è importante creare una copia di backup della chiave di crittografia qualora sia necessario ripristinarla in seguito a causa di modifiche all'account del servizio o come parte di una migrazione pianificata. In questo argomento viene fornita una panoramica di come usare il [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager per ripristinare le chiavi.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Per ripristinare la chiave, è necessario avere precedentemente salvato una copia di backup della chiave in un file protetto da password. Durante il ripristino della chiave, il server di report sostituirà una chiave esistente con la chiave inclusa nel file protetto da password. La chiave inclusa nel file deve essere identica a quella utilizzata per crittografare e decrittografare i dati.  
  
 Per verificare che la chiave ripristinata sia valida, utilizzare Gestione report per visualizzare le sottoscrizioni o tutti i report che dispongono di un'origine dati che utilizza credenziali archiviate. Se durante il tentativo di apertura di una pagina di definizione della sottoscrizione viene visualizzato il messaggio di errore "Il server di report non è in grado di accedere ai dati crittografati" o se viene richiesto di immettere le credenziali quando si tenta di aprire un report che in precedenza utilizzava credenziali archiviate per l'origine dati del report, la chiave ripristinata non è valida.  
  
 Se è stata ripristinata una chiave non valida diversa da quella utilizzata per crittografare i dati, non sarà possibile decrittografare i dati archiviati nel database del server di report. Se la chiave ripristinata non è valida, è necessario ripristinare immediatamente una copia di backup, se disponibile, della chiave corretta. Se non si dispone di una copia di backup della chiave utilizzata per crittografare i dati, è necessario eliminare tutti i dati crittografati. Fare clic sui **eliminare** pulsante il [chiavi di crittografia](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md) pagina per eseguire questo passaggio. Dopo avere eliminato il contenuto crittografato, è necessario aggiornare manualmente tutte le sottoscrizioni e specificare nuovamente tutte le credenziali archiviate definite per i report e le sottoscrizioni basate sui dati nel server di report.  
  
## <a name="restore-encryption-key-dialog"></a>Finestra di dialogo Ripristina chiave di crittografia  
 Per informazioni su dove trovare le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, consultare [Gestione configurazione Reporting Services &#40;in modalità nativa&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 Per aprire la finestra di dialogo Ripristina chiave di crittografia, fare clic su **chiavi di crittografia** nel riquadro di spostamento delle [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager e quindi fare clic su **ripristinare**. Questa finestra di dialogo viene visualizzata anche quando si aggiorna l'account del servizio usando la pagina Account servizio di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager. Per ulteriori informazioni su  
  
## <a name="options"></a>Opzioni  
 **Percorso del file**  
 Selezionare il file protetto da password che contiene una copia della chiave simmetrica. L'estensione predefinita è snk.  
  
 **Password**  
 Immettere la password per sbloccare il file. Solo gli utenti che conoscono la password possono ripristinare la chiave. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Applica criteri password complessi. La password deve contenere almeno 8 caratteri e includere una combinazione di caratteri alfanumerici maiuscoli e minuscoli e almeno un simbolo.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli argomenti della Guida F1 di Gestione configurazione di Reporting Services &#40;modalità nativa SSRS&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Eseguire il backup e il ripristino delle chiavi di crittografia di Reporting Services](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)   
 [Eliminare e ricreare chiavi di crittografia &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)   
 [Inizializzare un server di report &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)   
 [Archiviare i dati crittografati del server di report &#40;Gestione configurazione SSRS &#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)   
 [Le chiavi di crittografia &#40;modalità nativa SSRS&#41;](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md)  
  
  
