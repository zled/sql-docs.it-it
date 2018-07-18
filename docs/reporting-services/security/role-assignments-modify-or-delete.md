---
title: Modificare o eliminare un'assegnazione di ruolo (Gestione report) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: security
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- roles [Reporting Services], assignments
- system roles [Reporting Services]
- modifying role assignments
- deleting role assignments
ms.assetid: 523bdd32-92cb-4b48-a3a9-d58b2385bde7
caps.latest.revision: 45
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 112f4056b084e183d4651517c99d02b0335a3d36
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="role-assignments---modify-or-delete"></a>Assegnazioni di ruolo - Modificare o eliminare
  Un'assegnazione di ruolo esegue il mapping di un account utente o di gruppo a una definizione di ruolo predefinita che include le attività che possono essere eseguite e determina i tipi di operazioni che un utente può eseguire in relazione a una cartella, un report, un modello o ad altro tipo di contenuto. Per creare, modificare o eliminare assegnazioni di ruolo, utilizzare Gestione report. Dopo avere creato un'assegnazione di ruolo per un particolare utente o gruppo, è possibile modificarla in un secondo momento selezionando un ruolo diverso. Se si desidera revocare autorizzazioni a un server di report, è possibile eliminare un'assegnazione di ruolo dal server di report stesso.  
  
 A seconda degli scopi, alcuni approcci potrebbero essere più appropriati rispetto ad altri. Gli esempi includono la personalizzazione o la creazione di una nuova definizione di ruolo o la modifica dell'appartenenza di un account di gruppo in Active Directory.  
  
 Se ad esempio un gruppo di utenti deve gestire completamente il contenuto, ma non deve disporre del set completo di autorizzazioni associato a Gestione contenuto, è possibile creare una nuova definizione di ruolo denominata Gestione contenuto reparto, in cui sono incluse tutte le attività di Gestione contenuto ad eccezione di **Set security policies for items**(Impostazione dei criteri di sicurezza per gli elementi).  
  
 Analogamente, se per un amministratore di sistema o di rete è più semplice gestire account di gruppo di Active Directory rispetto alle assegnazioni di ruolo in Gestione report, è possibile ridurre l'overhead della gestione delle assegnazioni di ruolo creando una sola assegnazione per un account di gruppo e successivamente adattare l'appartenenza a un gruppo quando gli utenti non richiedono più l'accesso ai report.  
  
 Se si stabilisce che la modifica o l'eliminazione di un'assegnazione di ruolo costituisce l'approccio migliore, tenere presente di controllare che le assegnazioni di ruolo vengano eseguite sia a livello di sistema che di elemento. Ogni tipo di assegnazione di ruolo viene configurato tramite pagine diverse in Gestione report.  
  
### <a name="to-modify-or-delete-a-system-role-assignment"></a>Per eliminare o modificare un'assegnazione di ruolo a livello di sistema  
  
1.  Avviare [Gestione report &#40;modalità nativa SSRS&#41;](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896).  
  
2.  Fare clic su **Impostazioni sito**.  
  
3.  Fare clic su **Sicurezza**. Tutte le assegnazioni di ruolo a livello di sistema definite attualmente per il server o la distribuzione con scalabilità orizzontale vengono elencate in base al nome dell'account.  
  
4.  Individuare l'assegnazione di ruolo da modificare o eliminare.  
  
5.  Per aggiungere o rimuovere il ruolo per un particolare utente o gruppo, fare clic su **Modifica**.  
  
6.  Per eliminare un'assegnazione di ruolo, fare clic sulla casella di controllo accanto al nome dell'utente o del gruppo, quindi fare clic su **Elimina**.  
  
### <a name="to-modify-or-delete-an-item-role-assignment"></a>Per modificare o eliminare un'assegnazione di ruolo a livello di elemento  
  
1.  Avviare **Gestione report** e individuare l'elemento per il quale si desidera modificare o eliminare un'assegnazione di ruolo.  
  
2.  Posizionare il puntatore del mouse sull'elemento, quindi fare clic sulla freccia a discesa.  
  
3.  Scegliere **Sicurezza**dal menu a discesa.  
  
4.  Individuare l'assegnazione di ruolo da modificare o eliminare.  
  
5.  Per aggiungere o rimuovere il ruolo per un particolare utente o gruppo, fare clic su **Modifica**.  
  
6.  Per eliminare un'assegnazione di ruolo, fare clic sulla casella di controllo accanto al nome dell'utente o del gruppo, quindi fare clic su **Elimina**.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare e gestire assegnazioni di ruolo](../../reporting-services/security/create-and-manage-role-assignments.md)   
 [Assegnazioni di ruolo](../../reporting-services/security/role-assignments.md)   
 [Pagina Impostazioni sito &#40;Gestione report&#41;](http://msdn.microsoft.com/library/4d67a01c-eae4-49ba-a6e8-8e983c0248f5)   
 [Pagina Nuova assegnazione ruolo a livello di sistema: Modifica assegnazioni ruolo a livello di sistema &#40;Gestione report&#41;](http://msdn.microsoft.com/library/62a22ab9-1eb4-4ce5-8dd7-06b5ed2d9a2a)  
  
  
