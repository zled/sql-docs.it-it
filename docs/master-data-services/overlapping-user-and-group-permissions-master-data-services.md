---
title: "Autorizzazioni utenti e gruppi sovrapposte (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "utenti [Master Data Services], risoluzione delle autorizzazioni"
  - "autorizzazioni [Master Data Services], utenti e gruppi sovrapposti"
  - "gruppi [Master Data Services], risoluzione delle autorizzazioni"
ms.assetid: 31c3cf7d-17d4-4474-b6a7-ffcb9fc45b37
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Autorizzazioni utenti e gruppi sovrapposte (Master Data Services)
  Le autorizzazioni di un utente si basano su:  
  
-   Autorizzazioni ereditate dalle appartenenze a gruppi.  
  
-   Autorizzazioni assegnate in modo esplicito all'utente.  
  
 Se un utente è un membro di più gruppi e questi gruppi dispongono dell'accesso a [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], si applicano le regole seguenti:  
  
-   **Deny** sostituisce tutte le altre autorizzazioni. Se l'autorizzazione per gli oggetti è **Deny** in un gruppo, l'autorizzazione effettiva è deny.  
  
-   L'autorizzazioni di accesso è un'unione di tutte le autorizzazioni valide per un gruppo. Se l'autorizzazione per gli oggetti è **Create** da un gruppo e **Update** da altro gruppo, l'autorizzazione valida è **Create** e **Update**.  
  
 Queste regole si applicano a entrambe le schede **Modelli** e **Membri gerarchia**. Le autorizzazioni vengono risolte per ogni scheda e quindi combinate. Per altre informazioni, vedere [Modalità di determinazione delle autorizzazioni &#40;Master Data Services&#41;](../master-data-services/how-permissions-are-determined-master-data-services.md).  
  
> [!NOTE]  
>  Nell'interfaccia utente è possibile visualizzare la risoluzione delle autorizzazioni di utenti e gruppi sovrapposte. Nelle schede **Modelli** e **Membri gerarchia** è presente un elenco a discesa da cui è possibile scegliere **Valide** per visualizzare le autorizzazioni valide.  
  
## Esempio 1  
 ![mds_conc_user_group_ex_1](../master-data-services/media/mds-conc-user-group-ex-1.gif "mds_conc_user_group_ex_1")  
  
 L'utente appartiene al Gruppo 1 e al Gruppo 2.  
  
 L'utente ha l'autorizzazione **Read** per l'entità Product.  
  
 Il gruppo 1 ha l'autorizzazione **Update** per l'entità Product.  
  
 Il gruppo 2 ha l'autorizzazione **Read** per l'entità Product.  
  
 Risultato: l'autorizzazione valida dell'utente è **Update** per l'entità Product.  
  
## Esempio 2  
 ![mds_conc_user_group_ex_2](../master-data-services/media/mds-conc-user-group-ex-2.gif "mds_conc_user_group_ex_2")  
  
 L'utente appartiene al Gruppo 1 e al Gruppo 2.  
  
 L'utente ha l'autorizzazione **Read** per l'entità Product.  
  
 Il gruppo 1 ha l'autorizzazione **Update** per l'entità Product.  
  
 Il gruppo 2 ha l'autorizzazione **Deny** per l'entità Product.  
  
 Risultato: l'autorizzazione valida dell'utente è **Deny** per l'entità Product.  
  
## Esempio 3  
 ![mds_conc_user_group_ex_3](../master-data-services/media/mds-conc-user-group-ex-3.gif "mds_conc_user_group_ex_3")  
  
 L'utente appartiene al Gruppo 1 e al Gruppo 2.  
  
 L'utente dispone dell'autorizzazione **Update** per un gruppo di membri in un nodo gerarchia.  
  
 Il gruppo 1 ha l'autorizzazione **Read** per un gruppo di membri in un nodo gerarchia.  
  
 Il gruppo 2 ha l'autorizzazione **Read** per un gruppo di membri in un nodo gerarchia.  
  
 Risultato: l'autorizzazione utente valida è **Update** per i membri.  
  
## Vedere anche  
 [Modalità di determinazione delle autorizzazioni &#40;Master Data Services&#41;](../master-data-services/how-permissions-are-determined-master-data-services.md)   
 [Autorizzazioni per modelli e membri sovrapposte &#40;Master Data Services&#41;](../master-data-services/overlapping-model-and-member-permissions-master-data-services.md)  
  
  