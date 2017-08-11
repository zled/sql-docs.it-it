---
title: Ruoli e autorizzazioni (Reporting Services) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- access controls [Reporting Services]
- permissions [Reporting Services], about permissions
- security [Reporting Services], identity and access control
- authentication [Reporting Services]
- permissions [Reporting Services]
- security [Reporting Services], role-based
- identity [Reporting Services]
ms.assetid: eea655fe-43ed-418d-8233-b288a8f4daa4
caps.latest.revision: 18
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ea2b4cba953b6622811b80c7f6c60838ce0a6f91
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="roles-and-permissions-reporting-services"></a>Ruoli e autorizzazioni (Reporting Services)
  In Reporting Services sono disponibili un sottosistema di autenticazione e un modello di autorizzazione basata sui ruoli. I modelli di autenticazione e autorizzazione variano a seconda che il server di report sia in esecuzione in modalità nativa o in modalità SharePoint. Se il server di report fa parte di una distribuzione di SharePoint, con le autorizzazioni di SharePoint è possibile determinare gli utenti che possono accedere al server di report.  
  
## <a name="identity-and-access-control-for-native-mode"></a>Controllo di identità e accesso per la modalità nativa  
 L'autenticazione predefinita è basata sull'autenticazione di Windows e sulla sicurezza integrata. È possibile modificare le impostazioni di autenticazione per consentire al server di report di rispondere a richieste di autenticazione diverse o anche sostituire le funzionalità di sicurezza predefinite con un'estensione di autenticazione personalizzata fornita dall'utente.  
  
 L'autorizzazione è basata su ruoli che vengono assegnati a un'entità. Ogni ruolo è costituito da un set di attività correlate, a loro volta composte da operazioni correlate. Ad esempio, l'attività **Gestione di report** concede l'accesso alle operazioni seguenti sul server di report: visualizzazione, aggiunta, aggiornamento, eliminazione e pianificazione di report, nonché aggiornamento delle relative proprietà.  
  
## <a name="identity-and-access-control-for-sharepoint-mode"></a>Controllo di identità e accesso per la modalità SharePoint  
 In modalità integrata SharePoint l'autenticazione e l'autorizzazione vengono gestite sul sito di SharePoint, prima che le richieste raggiungano il server di report. A seconda della modalità di configurazione dell'autenticazione, le richieste provenienti da un sito di SharePoint includono un token di sicurezza o un nome utente attendibile. Le autorizzazione impostate per gli utenti e i gruppi di SharePoint autorizzano l'accesso agli elementi del server di report inseriti nelle raccolte di SharePoint.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Concessione di autorizzazioni in un Server di Report in modalità nativa](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
 Viene descritto il modello di autorizzazione basata sui ruoli che fornisce l'accesso al contenuto e alle operazioni.  
  
 [Concessione di autorizzazioni per elementi di Server di Report in un sito di SharePoint](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
 Viene illustrato l'utilizzo di gruppi, livelli di autorizzazione e autorizzazioni di SharePoint per il controllo dell'accesso a un server di report.  
  
## <a name="see-also"></a>Vedere anche  
 [Autenticazione con il Server di Report](../../reporting-services/security/authentication-with-the-report-server.md)   
 [Concessione di autorizzazioni in un Server di Report in modalità nativa](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
  
  
