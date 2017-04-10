---
title: "Creare e gestire assegnazioni di ruolo | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "rimozione di assegnazioni di ruolo"
  - "ruoli [Reporting Services], assegnazioni"
  - "sicurezza [Reporting Services], assegnazioni ruoli"
  - "modifica di assegnazioni di ruolo"
  - "eliminazione di assegnazioni di ruolo"
ms.assetid: 086d0987-b43c-4834-8372-e08fb4b432f8
caps.latest.revision: 39
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 39
---
# Creare e gestire assegnazioni di ruolo
  Un'*assegnazione di ruolo* rappresenta criteri di sicurezza che determinano se un utente o un gruppo può accedere a un elemento specifico del server di report oppure eseguire una determinata operazione. Un'assegnazione di ruolo è costituita da un unico nome di un account utente o di gruppo e da una o più definizioni di ruolo.  
  
 L'ambito delle assegnazioni di ruolo è definito a *livello di elemento* oppure a *livello di sistema*.  
  
-   Un'assegnazione di ruolo a livello di elemento viene sempre creata nel contesto di un elemento o di un ramo specifico nella gerarchia di cartelle del server di report. Per creare un'assegnazione di ruolo per una cartella o un elemento specifico, è necessario accedere a tale elemento o cartella.  
  
-   Le assegnazioni di ruolo a livello di sistema consentono agli utenti selezionati di eseguire attività che influiscono complessivamente sul sito del server di report. Sono comprese in tali attività la creazione di pianificazioni condivise, la gestione di processi, l'elaborazione di report in Generatore report e l'impostazione di proprietà. La sicurezza a livello di sistema non definisce le impostazioni di accesso agli elementi della gerarchia di cartelle del server di report.  
  
## Creazione di un'assegnazione di ruolo a livello di elemento  
 Per creare o gestire assegnazioni di ruolo, utilizzare Gestione report e aprire le pagine delle proprietà relative alla sicurezza dell'elemento da proteggere.  
  
 È necessario creare un'assegnazione di ruolo separata per ogni account utente o di gruppo che richiede l'accesso al server di report. Se l'account fa parte di un dominio diverso da quello in cui si trova il server di report, è necessario specificare il nome di dominio. Dopo aver specificato un account, è possibile scegliere una o più definizioni di ruolo. Le definizioni di ruolo si sommano tra loro, ovvero un'assegnazione supporta la combinazione di tutte le attività delle varie definizioni per un utente o un gruppo particolare.  
  
 Per consentire l'accesso al livello più generale possibile, è consigliabile scegliere un elemento nella parte alta della gerarchia di cartelle, ad esempio il nodo radice Home. In seguito sarà possibile creare assegnazioni di ruolo per impedire l'accesso ad aree specifiche della gerarchia di cartelle.  
  
 Per creare un'assegnazione di ruolo, è necessario appartenere al gruppo locale Administrators nel server di report. È possibile delegare tale compito assegnando altri utenti al ruolo **Gestione contenuto**.  
  
 Per altre informazioni, vedere [Concedere l'accesso utente a un server di report &#40;Gestione report&#41;](../../reporting-services/security/grant-user-access-to-a-report-server-report-manager.md).  
  
## Creazione di un'assegnazione di ruolo a livello di sistema  
 Per creare o gestire un'assegnazione di ruolo a livello di sistema, utilizzare Gestione report e aprire la pagina Impostazioni sito.  
  
 Le assegnazioni di ruolo a livello di sistema e di elemento sono associate. È necessario creare un'assegnazione di ruolo a livello di sistema per ogni utente o gruppo che dispone di un'assegnazione di ruolo a livello di elemento.  
  
 Le assegnazioni di ruolo a livello di sistema includono un'ampia gamma di autorizzazioni, ma non includono autorizzazioni appartenenti a un'assegnazione di ruolo a livello di elemento. Contrariamente alle autorizzazioni di sistema in un computer, i ruoli di sistema nei server di report non definiscono le autorizzazioni complete che includono il set completo di tutte le possibili operazioni, ma specificano solo un set di attività il cui ambito è il sito del server di report. Le autorizzazioni definite tramite assegnazioni di ruolo a livello di sistema determinano se gli utenti possono visualizzare proprietà dell'applicazione, ad esempio l'immagine o il titolo della Home page, visualizzare o gestire pianificazioni condivise o utilizzare Generatore report.  
  
 Per altre informazioni, vedere [Concedere l'accesso utente a un server di report &#40;Gestione report&#41;](../../reporting-services/security/grant-user-access-to-a-report-server-report-manager.md) e [Ruoli predefiniti](../../reporting-services/security/predefined-roles.md).  
  
## Modifica di assegnazioni di ruolo  
 Un'assegnazione di ruolo può essere modificata in qualsiasi momento. Le modifiche hanno effetto quando l'assegnazione viene salvata, ma non vengono applicate durante una sessione utente. Se infatti si modifica un'assegnazione di ruolo per negare l'accesso al report mentre è aperto da un utente, l'utente può comunque continuare a utilizzarlo fino a quando non chiude la propria sessione.  
  
 Se si aggiunge un account utente a un gruppo che fa già parte di un'assegnazione di ruolo, trascorrerà un certo periodo di tempo prima che l'account utente sia in grado di accedere agli elementi tramite i criteri dell'account di gruppo. Questo ritardo è dovuto alla memorizzazione nella cache dei token di autenticazione da parte di Internet Information Services (IIS). È possibile attendere che i token vengano aggiornati (in genere l'attesa è di quindici minuti) oppure reimpostare IIS in modo che la cache venga aggiornata immediatamente.  
  
 È possibile modificare una sola assegnazione di ruolo alla volta. Non è possibile eseguire un'operazione di ricerca e sostituzione globale per modificare i nomi delle definizioni di ruolo o le impostazioni delle assegnazioni di ruolo né per individuare tutte le assegnazioni di ruolo che includono un utente o un gruppo specifico.  
  
## Eliminazione di assegnazioni di ruolo  
 È possibile eliminare un'assegnazione di ruolo selezionando la casella di controllo accanto all'assegnazione che si vuole eliminare e quindi facendo clic su **Elimina**. È inoltre possibile eliminare assegnazioni di ruolo facendo clic su **Ripristina sicurezza padre**. Quando si fa clic su questo pulsante, le assegnazioni di ruolo esistenti per l'elemento vengono eliminate e al loro posto vengono utilizzate le assegnazioni di ruolo ereditate tramite un elemento padre.  
  
## Vedere anche  
 [Concedere l'accesso utente a un server di report &#40;Gestione report&#41;](../../reporting-services/security/grant-user-access-to-a-report-server-report-manager.md)   
 [Modificare o eliminare un'assegnazione di ruolo &#40;Gestione report&#41;](../../reporting-services/security/modify-or-delete-a-role-assignment-report-manager.md)   
 [Assegnazioni di ruolo](../../reporting-services/security/role-assignments.md)   
 [Definizioni di ruolo](../../reporting-services/security/role-definitions.md)   
 [Predefined Roles](../../reporting-services/security/predefined-roles.md)   
 [Concessione di autorizzazioni in un server di report in modalità nativa](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
  
  