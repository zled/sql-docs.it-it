---
title: Finestra di dialogo Proprietà credenziali (Generatore Report) dell'origine dati | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- "10017"
ms.assetid: 4531f09f-d653-4c05-a120-d7788838bc99
caps.latest.revision: 11
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 237e1c9ef26c5dba838fa8071b2dce7293f2077a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170733"
---
# <a name="data-source-properties-dialog-box-credentials-report-builder"></a>Finestra di dialogo Proprietà origine dati, Credenziali (Generatore report)
  Selezionare **Credenziali** nella finestra di dialogo **Proprietà origine dati** per visualizzare e modificare le credenziali per la connessione a un'origine dati incorporata nel report. Le credenziali fornite dall'utente vengono utilizzate per accedere all'origine dati per la visualizzazione in anteprima dei report. Per altre informazioni sulle credenziali, vedere [Specificare credenziali in Generatore report](../../2014/reporting-services/specify-credentials-in-report-builder.md).  
  
## <a name="options"></a>Opzioni  
 **Utilizzare l'autenticazione di Windows (sicurezza integrata)**  
 Selezionare questa opzione per utilizzare l'autenticazione di Windows.  
  
 **Usare questo nome utente e password**  
 Selezionare questa opzione per specificare nome utente e password specifici. Per le origini dei dati incorporate, quando si pubblica il progetto del server di report nel server di destinazione, il nome utente e la password vengono salvati come credenziali archiviate per il database. Se si desidera utilizzare il nome utente e la password come credenziali di Windows, è possibile modificare le proprietà dell'origine dati condivisa pubblicata nel server di destinazione. Per altre informazioni, vedere [Creare, eliminare o modificare un'origine dei dati condivisa &#40;Gestione report&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md) nella documentazione relativa a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] inclusa nella [documentazione online di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]](http://go.microsoft.com/fwlink/?linkid=121312).  
  
 **Nome utente**  
 Consente di digitare un nome utente da utilizzare per l'accesso all'origine dei dati.  
  
 **Password**  
 Consente di digitare una password da utilizzare per l'accesso all'origine dei dati.  
  
 **Richiedi credenziali**  
 Selezionare questa opzione per richiedere le credenziali durante l'esecuzione del report.  
  
 **Immettere stringa di messaggio di richiesta**  
 Digitare una frase con cui chiedere all'utente di specificare le credenziali di accesso per l'origine dati.  
  
 **Nessuna credenziale**  
 Selezionare questa opzione se non si desidera che vengano specificate credenziali per l'origine dati. Questa opzione funziona solamente se l'origine dati non accetta le credenziali o se il passaggio di queste ultime avviene in altro modo.  
  
 Da alcune estensioni per i dati è necessario configurare l'account di esecuzione automatica nel server di report.  
  
 Per altre informazioni, vedere l'argomento per il tipo di origine dati corrispondente in [Aggiungere dati da origini dati esterne &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md) e [Configurare l'account di esecuzione automatica &#40;Gestione configurazione SSRS&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) nella documentazione relativa a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] inclusa nella [documentazione online di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]](http://go.microsoft.com/fwlink/?linkid=121312).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di Generatore report per finestre di dialogo, riquadri e procedure guidate](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Finestra di dialogo Proprietà origine dati, Generale &#40;Generatore report&#41;](../../2014/reporting-services/data-source-properties-dialog-box-general-report-builder.md)   
 [Aggiungere e verificare una connessione dati o un'origine dati &#40;SSRS e Generatore Report&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)   
 [Aggiungere dati a un Report &#40;SSRS e Generatore Report&#41;](report-data/report-datasets-ssrs.md)  
  
  