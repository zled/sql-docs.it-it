---
title: Distribuire criteri pianificati in più istanze | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f551b8e8-3668-4ed4-852f-bae826254f4f
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8331f0f33874c5bfbd0811231dc2cacf494b1d89
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158333"
---
# <a name="deploy-scheduled-policies-to-multiple-instances"></a>Distribuzione di criteri pianificati in istanze multiple
  Tramite Server registrati è possibile distribuire criteri pianificati a server gestiti da una posizione centralizzata. È possibile distribuire i criteri pianificati da un gruppo di server locali o da un server di gestione centrale.  
  
 In questa attività, verranno effettuate le operazioni seguenti:  
  
1.  Esportazione in una cartella dei criteri pianificati nell'attività precedente.  
  
2.  Distribuzione dei criteri pianificati a istanze di destinazione gestite mediante Server registrati.  
  
 Tali attività verranno eseguite nel computer utilizzato per completare le attività precedenti di questa lezione.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Di seguito vengono indicati i prerequisiti di questa attività:  
  
-   È necessario avere completato le attività precedenti di questa lezione.  
  
-   È necessario che nelle istanze in cui si desidera distribuire i criteri pianificati sia in esecuzione [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] o versione successiva. Ai fini dell'automazione è necessario che i criteri siano archiviati localmente, operazione non supportata nelle versioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] precedenti a [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].  
  
-   Il server in cui si desidera distribuire i criteri pianificati devono essere registrati in server registrati in entrambi i **gruppi di Server locali** o il **server di gestione centrale** nodo. Per altre informazioni, vedere gli argomenti seguenti:  
  
    -   [Creare o modificare un gruppo di server &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
    -   [Registrare un Server connesso &#40;SQL Server Management Studio&#41;](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md).  
  
    -   [Creare un server di gestione centrale e un gruppo di server &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-export-the-scheduled-policies-as-xml-files"></a>Per esportare i criteri pianificati come file xml  
  
1.  Nel server in cui è configurato i criteri pianificati nell'attività precedente, espandere **Management**, espandere **criteri di gestione**, quindi fare clic su **criteri**.  
  
2.  Scegliere **Dettagli Esplora oggetti** dal menu **Visualizza**.  
  
3.  Nel **dettagli Esplora oggetti** riquadro, selezionare tutte le procedure consigliate pianificati criteri che si desidera distribuire in altri server tramite server registrati.  
  
    > [!NOTE]  
    >  È possibile scegliere il **categoria** sull'intestazione per ordinare i criteri per categoria.  
  
4.  Destro la selezione e quindi fare clic su **Esporta criteri**.  
  
5.  Se si seleziona più criteri, esportare il **Sfoglia per cartelle** finestra di dialogo, selezionare una cartella di destinazione o creare una nuova cartella. Per questa lezione, creare una nuova cartella nel percorso **C:\Scheduled_BP_Policies**, quindi fare clic su **OK**.  
  
     Se è selezionato un solo criterio da esportare, nella **Esporta criterio** finestra di dialogo casella, creare una nuova cartella con il percorso **C:\Scheduled_BP_Policies**, fare clic su **aperta**e quindi fare clic su **Salvare**.  
  
     I file xml dei criteri vengono creati nel percorso della cartella.  
  
### <a name="to-deploy-the-scheduled-policies-to-servers-that-are-managed-through-registered-servers"></a>Per distribuire i criteri pianificati in server gestiti mediante Server registrati  
  
1.  Scegliere **Server registrati** dal menu **Visualizza**.  
  
2.  Espandere **motore di Database**, espandere **gruppi di Server locali** oppure **server di gestione centrale**, destro del mouse sul nodo che si desidera distribuire i criteri, quindi Fare clic su **Importa criteri**.  
  
    > [!NOTE]  
    >  Se si fa clic su **gruppi di Server locali** o Server di gestione centrale stesso, i criteri verranno distribuiti in tutti i server gestiti. Se si fa clic con il pulsante destro del mouse su un gruppo di server specifico, i criteri verranno distribuiti solo in tale gruppo. Se si fa clic con il pulsante destro del mouse su un server registrato specifico, i criteri verranno distribuiti solo in tale server.  
  
3.  Accanto a **i file da importare**, fare clic sul pulsante con puntini di sospensione (**...** ).  
  
4.  Nel **Seleziona criteri** della finestra di dialogo Sfoglia per il percorso della cartella in cui è stato salvato i criteri pianificati. Per questo esempio, passare al percorso **C:\Scheduled_BP_Policies**.  
  
5.  Selezionare i criteri che si desidera importare per le istanze di destinazione e quindi fare clic su **Open**.  
  
6.  Nel **importazione** della finestra di dialogo il **lo stato dei criteri** selezionare lo stato dei criteri desiderati. È possibile scegliere di mantenere lo stato dei criteri, abilitare o disabilitare i criteri durante l'importazione. Tenere presente che i criteri devono essere abilitati per poter essere eseguiti in base a una pianificazione.  
  
7.  Fare clic su **OK** per importare i criteri a tutte le istanze di destinazione.  
  
    > [!NOTE]  
    >  Se si verificano errori, il **importazione** finestra di dialogo non scomparsa. Fare clic sui **Log** pagina per esaminare i messaggi. Fare clic su **annullare** per chiudere la finestra di dialogo.  
  
8.  Per visualizzare i criteri da un'istanza di destinazione, connettersi all'istanza, aprire Esplora oggetti, espandere **Management**, quindi espandere **criteri**. Dovrebbe essere i criteri importati nel **criteri** nodo. Se si fa doppio clic su ciascuno dei criteri, è possibile visualizzare la pianificazione o modificare le impostazioni.  
  
    > [!NOTE]  
    >  Per visualizzare i risultati di valutazione dopo l'esecuzione di criteri pianificati, aprire il log Cronologia criteri nell'istanza di destinazione. Per aprire il registro, fare doppio clic su **criteri di gestione**, quindi fare clic su **Visualizza cronologia**.  
  
## <a name="summary"></a>Riepilogo  
 In questa esercitazione è stato illustrato come eseguire valutazioni su richiesta e pianificate dei criteri per procedure consigliate per una o più istanze di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="next"></a>Avanti  
 L'esercitazione è completata. Per tornare all'inizio, vedere [esercitazione: valutazione di procedure consigliate tramite la gestione basata su criteri](../../2014/tutorials/tutorial-evaluating-best-practices-by-using-policy-based-management.md).  
  
 Per visualizzare un elenco dei [!INCLUDE[ssDE](../includes/ssde-md.md)] esercitazioni, fare clic su [esercitazioni del motore di Database](../relational-databases/database-engine-tutorials.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione di server tramite la gestione basata su criteri](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  