---
title: Concedere l'accesso utente a un server di report | Documenti Microsoft
ms.custom: 
ms.date: 05/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- removing role assignments
- permissions [Reporting Services], granting report server access
- roles [Reporting Services], assignments
- modifying role assignments
- deleting role assignments
ms.assetid: 2144c020-3253-4b47-8cda-e14c928bb471
caps.latest.revision: 54
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: a92c37165b8142b7e96a8bb99dee43ea5f12e247
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="grant-user-access-to-a-report-server"></a>Concedere l'accesso utente a un server di report

[!INCLUDE[ssrs-appliesto-sql2016-preview](../../includes/ssrs-appliesto-sql2016-preview.md)]

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] usa la sicurezza basata sui ruoli per concedere agli utenti l'accesso a un server di report. In una nuova installazione del server di report, solo gli utenti che appartengono al gruppo Administrators locale dispongono delle autorizzazioni per accedere al contenuto ed eseguire operazioni sul server di report. Per rendere disponibile il server di report agli altri utenti, è necessario creare assegnazioni di ruolo che associano gli account utente o gli account di gruppo a un ruolo predefinito che specifica una raccolta di attività.

 **Server di report in modalità SharePoint** : per un server di report configurato per la modalità integrata SharePoint, l'accesso da un sito di SharePoint viene configurato mediante le autorizzazioni relative. I livelli di autorizzazione sul sito di SharePoint determinano l'accesso al contenuto e alle operazioni del server di report. Per concedere le autorizzazioni a un sito di SharePoint, è necessario disporre dei privilegi di amministratore. Per altre informazioni, vedere [Concessione di autorizzazioni per elementi del server di report in un sito di SharePoint](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md).

 **Server di report in modalità nativa:** in questo argomento è incentrato su un server di report configurato per la modalità nativa e l'utilizzo del portale web per assegnare utenti a un ruolo. Sono disponibili due tipi di ruoli:

- Ruoli a livello di elemento, utilizzati per visualizzare, aggiungere e gestire contenuto del server di report, sottoscrizioni, elaborazione e cronologia dei report. I ruoli a livello di elemento vengono definiti per il nodo radice, ovvero la cartella Home, oppure per cartelle o elementi specifici nei livelli inferiori della gerarchia.

- Ruoli a livello di sistema, che concedono l'accesso a un'ampia gamma di operazioni sul sito non associate ad alcun elemento specifico, ad esempio l'utilizzo di Generatore report e di pianificazioni condivise.

    I due tipi di ruoli sono complementari e devono essere utilizzati insieme. Per questa ragione, l'aggiunta di un utente a un server di report è un'operazione suddivisa in due parti. Se si assegna un utente a un ruolo a livello di elemento, è necessario assegnarlo anche a un ruolo a livello di sistema. Quando si assegna un utente a un ruolo, è necessario selezionare un ruolo già definito. Per creare, modificare o eliminare ruoli, usare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Per altre informazioni, vedere [Creare, eliminare o modificare un ruolo &#40;Management Studio&#41;](../../reporting-services/security/role-definitions-create-delete-or-modify.md).

## <a name="before-you-start"></a>Prima di iniziare

Esaminare l'elenco seguente prima di aggiungere utenti a un server di report in modalità nativa.

- È necessario essere un membro del gruppo Administrators locale nel computer server di report. Se si distribuisce [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] o in Windows Server 2008, la configurazione aggiuntiva è obbligatoria per amministrare un server di report localmente. Per ulteriori informazioni, vedere [configurare un Server di Report in modalità nativa per l'amministrazione locale](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).

- Per delegare questa attività ad altri utenti, creare assegnazioni di ruolo che eseguono il mapping degli account utente ai ruoli Gestione contenuto e Amministratore sistema. Gli utenti che dispongono di queste autorizzazioni possono aggiungere utenti a un server di report.

- In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]visualizzare i ruoli predefiniti per i ruoli a livello di sistema e i ruoli utente, in modo da acquisire familiarità con i tipi di attività previsti da ogni ruolo. Le descrizioni delle attività non sono visibili nel portale web, pertanto è consigliabile avere familiarità con i ruoli prima di iniziare l'aggiunta di utenti.

- Facoltativamente, personalizzare i ruoli o definire ruoli aggiuntivi per includere la raccolta di attività necessarie. Se ad esempio si intende utilizzare impostazioni di sicurezza personalizzate per elementi singoli, è necessario creare una nuova definizione di ruolo che consenta di visualizzare le cartelle.

### <a name="to-add-a-user-or-group-to-a-system-role"></a>Per aggiungere un utente o un gruppo a un ruolo a livello di sistema

1. Avviare il [portale web](../web-portal-ssrs-native-mode.md).

2. Selezionare il *icona dell'ingranaggio* in alto a destra.

3. Selezionare **Impostazioni sito**.

4. Selezionare **Sicurezza**.

5. Selezionare **Aggiungi gruppo o utente**.

6. In **gruppo o utente**, immettere un utente di dominio di Windows o il gruppo di account nel formato: \<dominio >\\< account\>. 

    > [!NOTE]
    > Se si utilizza l'autenticazione basata su form o la sicurezza personalizzata, specificare l'account utente o di gruppo nel formato corretto per la propria distribuzione.

7. Selezionare un ruolo del sistema, quindi **OK**.

    Poiché i ruoli sono cumulativi, se si seleziona sia Amministratore sistema che Utente sistema, un utente o un gruppo sarà in grado di eseguire le attività in entrambi ruoli.

8. Ripetere le operazioni per creare assegnazioni per utenti o gruppi aggiuntivi.

### <a name="to-add-a-user-or-group-to-an-item-role"></a>Per aggiungere un utente o un gruppo a un ruolo a livello di elemento

1. Avviare il **portale web** e individuare l'elemento di report per cui si desidera aggiungere un utente o gruppo.

2. Selezionare il **...**  (puntini di sospensione) su un elemento.

3. Nel menu a discesa, selezionare **Gestisci**.

4. Selezionare **Sicurezza**.

5. Selezionare **Aggiungi gruppo o utente**.

    > [!NOTE]
    > Se un elemento eredita protezione da un elemento padre, selezionare **personalizzare sicurezza** nella barra degli strumenti per modificare le impostazioni di sicurezza. Selezionare quindi **Aggiungi gruppo o utente**.

6. In **gruppo o utente**, immettere un utente di dominio di Windows o il gruppo di account nel formato: \<dominio >\\< account\>. Se si utilizza l'autenticazione basata su form o la sicurezza personalizzata, specificare l'account utente o di gruppo nel formato corretto per la propria distribuzione.

7. Selezionare uno o più definizioni di ruolo che descrivono come utente o gruppo deve accedere all'elemento e quindi selezionare **OK**.

8. Ripetere le operazioni per creare assegnazioni per utenti o gruppi aggiuntivi.

## <a name="next-steps"></a>Passaggi successivi

[Creare e gestire assegnazioni di ruolo](../../reporting-services/security/create-and-manage-role-assignments.md)   
[Nuova assegnazione ruolo: Modifica pagina assegnazione di ruolo &#40; Gestione report &#41;](http://msdn.microsoft.com/library/3319ced0-4b86-42af-b18d-da41a625113c)   
[Pagina delle proprietà sicurezza, gli elementi di &#40; Gestione report &#41;](http://msdn.microsoft.com/library/351b8503-354f-4b1b-a7ac-f1245d978da0)   
[Assegnazioni di ruolo](../../reporting-services/security/role-assignments.md)   
[Definizioni di ruolo](../../reporting-services/security/role-definitions.md)  

Ulteriori domande? [Provare a porre il forum di Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
