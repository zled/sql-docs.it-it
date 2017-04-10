---
title: "Definizioni di ruolo | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ruoli [Reporting Services], creazione"
  - "ruoli [Reporting Services], sicurezza"
  - "sicurezza [Reporting Services], definizioni ruoli"
  - "sicurezza basata su ruoli [Reporting Services], definizioni ruoli"
ms.assetid: d1b8dbf0-4462-402e-92dd-0e4835002b6e
caps.latest.revision: 44
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 44
---
# Definizioni di ruolo
  In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], per *definizione**di ruolo* si intende una raccolta denominata di attività che definiscono le operazioni disponibili in un server di report. Le definizioni di ruolo rendono disponibili le regole utilizzate dal server di report per implementare la sicurezza. Quando un utente tenta di eseguire un'attività, ad esempio la pubblicazione di un report, nel server di report viene innanzitutto valutata l'assegnazione di ruolo dell'utente per stabilire se questa attività è inclusa nella relativa definizione di ruolo. Se l'attività è inclusa nella definizione di ruolo, la richiesta viene inoltrata.  
  
## Utilizzo dei ruoli per autorizzare l'accesso al server di report  
 Un ruolo diventa operativo solo quando viene utilizzato in un'assegnazione di ruolo. Per altre informazioni sulla sicurezza tramite i ruoli, vedere [Assegnazioni di ruolo](../../reporting-services/security/role-assignments.md).  
  
## Tipi di definizioni di ruolo  
 Le definizioni di ruolo possono essere a livello di elemento o a livello di sistema. Una *definizione di ruolo a livello di elemento* descrive le attività correlate a elementi archiviati e gestiti in un server di report, ad esempio report, cartella e modelli. La gestione di report, la visualizzazione di cartelle e la gestione di singole sottoscrizioni sono esempi di attività che è possibile includere nelle definizioni di ruolo a livello di elemento. Una *definizione di ruolo a livello di sistema* include le attività applicabili al sito nell'insieme. La visualizzazione delle proprietà del server di report è un esempio di attività che è possibile includere in questo ruolo di sistema.  
  
## Predefined Roles  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] include ruoli predefiniti che corrispondono a livelli diversi di interazione dell'utente. Nell'elenco seguente sono riportati i ruoli predefiniti che è possibile utilizzare:  
  
-   Gestione contenuto, Server di pubblicazione, Visualizzazione, Generatore report e Report personali sono definizioni di ruolo a livello di elemento che è possibile utilizzare quando si creano le assegnazioni di ruolo per l'accesso al contenuto del server di report.  
  
-   Amministratore sistema e Utente sistema sono definizioni di ruolo a livello di sistema che è possibile utilizzare per autorizzare l'accesso alle operazioni nel sito.  
  
 Per altre informazioni, vedere [Ruoli predefiniti](../../reporting-services/security/predefined-roles.md).  
  
## Creazione di una definizione di ruolo  
 Per creare un ruolo, utilizzare Management Studio per specificare un nome e le attività che contiene. È necessario creare una definizione di ruolo distinta per le attività a livello di elemento e di sistema. Nei ruoli è possibile includere attività a livello di sistema o di elemento, ma non entrambe. Per creare una definizione di ruolo è necessario specificare un nome e scegliere un set di attività per questa definizione. Per creare una definizione di ruolo, è necessario disporre delle autorizzazioni appropriate. Queste autorizzazioni vengono concesse tramite l'attività "Impostazione della sicurezza per singoli elementi". Per impostazione predefinita, questa attività può essere eseguita dagli amministratori e dagli utenti con ruolo predefinito **Gestione contenuto**.  
  
 Un ruolo deve avere un nome univoco. Per essere valida, la definizione deve contenere almeno un'attività. Per altre informazioni, vedere [Attività e autorizzazioni](../../reporting-services/security/tasks-and-permissions.md).  
  
 Per creare una definizione di ruolo, usare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Per altre informazioni, vedere [Creare, eliminare o modificare un ruolo &#40;Management Studio&#41;](../../reporting-services/security/create-delete-or-modify-a-role-management-studio.md).  
  
 Dopo aver creato una definizione di ruolo, è possibile utilizzarla selezionandola in un'assegnazione di ruolo. Per altre informazioni, vedere [Concedere l'accesso utente a un server di report &#40;Gestione report&#41;](../../reporting-services/security/grant-user-access-to-a-report-server-report-manager.md).  
  
## Personalizzare o eliminare una definizione di ruolo  
 I ruoli predefiniti possono essere modificati o sostituiti con ruoli personalizzati. Per modificare un ruolo, aggiungere o rimuovere attività dalla definizione di ruolo. Non è possibile rinominare un ruolo. Le eventuali modifiche apportate vengono applicate immediatamente a tutte le assegnazioni di ruolo che includono questa definizione.  
  
 È possibile eliminare una definizione di ruolo se non la si utilizza più. Non è possibile eliminare la definizione di ruolo selezionata per la funzionalità Report personali, se questa funzionalità è attivata. Prima di eliminare la definizione di ruolo utilizzata per la funzionalità Report personali, è necessario disabilitare la funzionalità oppure associarvi un'altra definizione di ruolo.  
  
## Vedere anche  
 [Attività e autorizzazioni](../../reporting-services/security/tasks-and-permissions.md)   
 [Concessione di autorizzazioni in un server di report in modalità nativa](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)   
 [Creare, eliminare o modificare un ruolo &#40;Management Studio&#41;](../../reporting-services/security/create-delete-or-modify-a-role-management-studio.md)   
 [Concedere l'accesso utente a un server di report &#40;Gestione report&#41;](../../reporting-services/security/grant-user-access-to-a-report-server-report-manager.md)   
 [Modificare o eliminare un'assegnazione di ruolo &#40;Gestione report&#41;](../../reporting-services/security/modify-or-delete-a-role-assignment-report-manager.md)   
 [Impostare autorizzazioni per gli elementi del server di report in un sito di SharePoint &#40;Reporting Services in modalità integrata SharePoint&#41;](../../reporting-services/security/set permissions for report server items on a sharepoint site.md)  
  
  