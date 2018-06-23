---
title: Eseguire una valutazione su richiesta utilizzando server registrati | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c14034ef-6e0b-4df5-8072-bfb8d90b3172
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f7deecbab3fceb117bfb3d237cf5940fdc34f5bc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055624"
---
# <a name="perform-an-on-demand-evaluation-by-using-registered-servers"></a>Esecuzione di una valutazione su richiesta utilizzando Server registrati
  È possibile eseguire una valutazione su richiesta dei criteri per procedure consigliate in una o più istanze di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tramite Server registrati. È possibile utilizzare gruppi di server locali o un server di gestione centrale.  
  
> [!NOTE]  
>  È possibile eseguire una valutazione su richiesta dei criteri per procedure consigliate in membri del gruppo di server che eseguono [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] o una versione più recente di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Tuttavia, è possibile ricevere un errore di eccezione se i criteri fanno riferimento a proprietà non supportate in [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] o [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)].  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa attività è necessario aver configurato una o più registrazioni di server in Server registrati. Per altre informazioni, vedere gli argomenti seguenti:  
  
-   [Creare o modificare un gruppo di server &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
-   [Registrare un Server connesso &#40;SQL Server Management Studio&#41;](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md).  
  
-   [Creare un server di gestione centrale e un gruppo di server &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-evaluate-best-practices-policies-against-a-server-group"></a>Per valutare i criteri per procedure consigliate in un gruppo di server  
  
1.  In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]scegliere **Server registrati** dal menu **Visualizza**.  
  
2.  Espandere **motore di Database**, quindi espandere **gruppi di Server locali**, o **server di gestione centrale**, a seconda della configurazione.  
  
3.  Effettuare una delle operazioni seguenti:  
  
    -   Per valutare i criteri rispetto a tutti i server gestiti dal gruppo di server locale oppure il server di gestione centrale, fare doppio clic sul nome del gruppo di server locale o il nome del server di gestione centrale e quindi fare clic su **valuta criteri** .  
  
        > [!NOTE]  
        >  Quando si valutano i criteri mediante un server di gestione centrale, tali criteri non vengono valutati nel server di gestione centrale stesso.  
  
    -   Per valutare i criteri rispetto a un server specifico o un gruppo di server, espandere **gruppi di Server locali** o il server di gestione centrale nome pulsante destro del mouse il server o un gruppo di server che si desidera valutare i criteri rispetto a e quindi fare clic su **Valutare i criteri**.  
  
4.  Nel **valuta criteri** accanto alla finestra di dialogo il **origine** fare clic sui puntini di sospensione (**...** ) pulsante.  
  
5.  Nel **Seleziona origine** della finestra di dialogo è possibile selezionare **file** o **Server** come origine dei file di criteri da valutare. Se si fa clic su **Server**, è possibile eseguire una valutazione su richiesta di eventuali criteri consigliate precedentemente importati nella gestione basata su criteri in un server locale o remoto. In questa esercitazione, potrà fare clic su **file**e quindi selezionare i file dei criteri individuali che si desidera valutare. A tale scopo, eseguire le operazioni seguenti:  
  
    1.  Fare clic su **file**.  
  
    2.  Accanto a **file**, fare clic sui puntini di sospensione (**...** ) pulsante.  
  
    3.  Selezionare uno o più file con estensione XML dei criteri per valutare e quindi fare clic su **Open**.  
  
         Verrà visualizzato l'elenco di file selezionati nel **file** casella.  
  
    4.  Nel **Seleziona origine** finestra di dialogo, fare clic su **OK**.  
  
    5.  Se il **caricamento criteri** verrà visualizzata la finestra di dialogo, fare clic su **Chiudi**.  
  
     I criteri selezionati vengono elencati nella **selezione criteri** pagina. L'icona di avviso accanto ai criteri indica che questi contengono script.  
  
6.  Fare clic su **Evaluate** per valutare i criteri.  
  
7.  Per alcuni errori relativi ai criteri, la gestione basata su criteri consente di applicare immediatamente la conformità di criteri nella destinazione. Per questo tipo di errori verrà visualizzata una casella di controllo accanto ai criteri che presentano errori. Se si seleziona la casella di controllo, o fare clic sulla riga con i criteri non riuscite, caselle di controllo vengono visualizzate nel **dettagli destinazione** riquadro accanto a istanze di destinazione che non hanno superato la valutazione. Se una delle caselle di controllo sono selezionata, il **applica** diventa disponibile. Quando fa clic su **applica**, verrà aggiornata automaticamente l'impostazione non conforme nelle istanze di destinazione selezionato.  
  
    > [!CAUTION]  
    >  Assicurarsi di aver compreso a pieno tutte le impostazioni dei criteri prima di aggiornare automaticamente un'istanza di destinazione. È consigliabile che dopo aver selezionato una o più caselle di controllo, si fa clic su **Script**, scegliere un percorso di output in modo che è possibile esaminare sottostante [!INCLUDE[tsql](../includes/tsql-md.md)] prima di applicare le modifiche del codice.  
  
8.  Per visualizzare i risultati dettagliati per un criterio, fare clic sul criterio nel **risultati** tabella. Il **dettagli destinazione** tabella vengono illustrati i dettagli per ogni istanza.  
  
## <a name="next-lesson"></a>Lezione successiva  
 [Lezione 2: Valutare i criteri consigliate in base a una pianificazione](../../2014/tutorials/lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)   
 [Amministrare più server tramite server di gestione centrale](../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  