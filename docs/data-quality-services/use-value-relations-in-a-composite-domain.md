---
title: Usare le relazioni di valori in un dominio composito | Microsoft Docs
ms.custom: 
ms.date: 11/22/2011
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- data-quality-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dqs.dm.cdvaluerelations.f1
ms.assetid: 5ee468f0-8538-4620-90e8-63f466c9000e
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c42159a2477e4eeba0afbaa536427cace2a5aafc
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="use-value-relations-in-a-composite-domain"></a>Utilizzare le relazioni di valori in un dominio composito
  In questo argomento viene descritto come visualizzare le combinazioni di valori presenti nel dominio composito durante il processo di individuazione delle informazioni in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). In questa pagina viene illustrato il numero di occorrenze delle combinazioni di valori. La gestione dei valori non è supportata per i domini compositi, pertanto non è possibile eseguire alcuna operazione su questi valori.  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
 Per visualizzare le relazioni di valori, è necessario avere creato e aperto un dominio composito.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Per visualizzare le relazioni di valori in un dominio composito, è necessario disporre del ruolo dqs_kb_editor o dqs_administrator nel database DQS_MAIN.  
  
##  <a name="Use"></a> Visualizzare le relazioni di valori  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Eseguire l'applicazione Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Nella schermata iniziale del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] aprire o creare una Knowledge Base. Selezionare **Gestione dominio** come attività, quindi fare clic su **Apri** o **Crea**. Per ulteriori informazioni, vedere [Create a Knowledge Base](../data-quality-services/create-a-knowledge-base.md) o [Open a Knowledge Base](../data-quality-services/open-a-knowledge-base.md).  
  
3.  **Dall'elenco di domini** nella pagina **Gestione dominio** selezionare il dominio composito per il quale si desidera creare una regola di dominio o creare un nuovo dominio composito. Se è necessario creare un nuovo dominio, vedere [Create a Composite Domain](../data-quality-services/create-a-composite-domain.md).  
  
4.  Fare clic sulla scheda **Relazioni valore** .  
  
5.  Visualizzare le frequenze riportate per ogni combinazione di valori.  
  
    > [!NOTE]  
    >  Nella tabella **Valore** viene visualizzata ogni combinazione di valori presente nel dominio composito. Ogni valore viene mostrato nel singolo dominio a cui si applica. L'ordinamento predefinito della tabella delle relazioni di valori è per frequenza, ma è possibile fare clic su un'altra colonna per ordinare in base a tale colonna. Vengono visualizzati solo i valori con una frequenza maggiore o uguale a 20.  
  
6.  Non è possibile modificare alcun valore nella tabella. Se sono state eseguite le altre operazioni, fare clic su **Fine** per completare l'attività di gestione del dominio. In caso contrario, fare clic su **Annulla**.  
  
##  <a name="FollowUp"></a> Completamento: fasi successive alla visualizzazione delle relazioni di valori  
 Dopo avere visualizzato le relazioni di valori, è possibile eseguire ulteriori attività di gestione del dominio, quali l'individuazione delle informazioni per aggiungere informazioni al dominio o l'aggiunta di criteri di corrispondenza al dominio. Per altre informazioni, vedere [Eseguire l'individuazione delle informazioni](../data-quality-services/perform-knowledge-discovery.md), [Gestione di un dominio](../data-quality-services/managing-a-domain.md) o [Creare criteri di corrispondenza](../data-quality-services/create-a-matching-policy.md).  
  
  

