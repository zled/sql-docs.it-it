---
title: Nuovo ruolo del sistema (Management Studio) | Documenti Microsoft
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
f1_keywords:
- sql13.swb.reportserver.newsystemrole.f1
ms.assetid: 7b4a0b98-975b-478a-8359-7db39ccbb347
caps.latest.revision: 28
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: f4917fea7fbaa0f652287a08e0a3a5727feaad9e
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="new-system-role-management-studio"></a>Nuovo ruolo a livello di sistema (Management Studio)
  Utilizzare questa pagina per creare una definizione di ruolo a livello di sistema. Tramite una definizione di ruolo a livello di sistema è possibile specificare un set di attività a livello di sistema consentite per un server di report nel suo complesso.  
  
> [!NOTE]  
>  Le definizioni di ruolo vengono utilizzate solo in un server di report in esecuzione in modalità nativa. Se il server di report è configurato per l'integrazione con SharePoint, questa pagina non è disponibile.  
  
## <a name="options"></a>Opzioni  
 **Nome**  
 Consente di digitare la definizione del ruolo. I nomi di definizione di ruolo devono essere univoci nell'ambito dello spazio dei nomi del server di report. Il nome deve includere almeno un carattere alfanumerico. È inoltre possibile utilizzare spazi e alcuni simboli. Il nome non può contenere i caratteri seguenti:  
  
 ; ? : @ & = + , $ / * < >  
  
 " /  
  
 **Description**  
 Consente di digitare una descrizione per illustrare le modalità di utilizzo del ruolo ed elencare le azioni supportate.  
  
 **Attività**  
 Consente di selezionare le attività a livello di sistema che possono essere eseguite tramite questo ruolo. Non è possibile creare nuove attività o modificare attività esistenti supportate da [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Non è possibile selezionare attività a livello di elemento per una definizione di ruolo a livello di sistema.  
  
 **Descrizione dell'attività**  
 Visualizza una descrizione dell'attività, che include le operazioni o autorizzazioni supportate.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida sensibile al contesto del server di report in Management Studio](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Definizioni di ruolo](../../reporting-services/security/role-definitions.md)  
  
  

