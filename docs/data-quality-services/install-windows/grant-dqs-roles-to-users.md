---
title: Concedere ruoli DQS agli utenti | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- data-quality-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afb445b5-bdbe-4bfe-844f-344766cdc2b2
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 805020ab366ec0e993c8f4be54a4d18a22510911
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="grant-dqs-roles-to-users"></a>Concedere ruoli DQS agli utenti
  In questo argomento si descrive come creare account di accesso SQL in un'entità di Windows e come assegnare i ruoli [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) nel database DQS_MAIN.  
  
## <a name="prerequisites"></a>Prerequisiti  
  
-   È necessario aver completato l'installazione di [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] tramite l'esecuzione del file DQSInstaller.exe. Per altre informazioni, vedere [Eseguire DQSInstaller.exe per completare l'installazione del server DQS](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
-   L'account utente di Windows deve essere un membro del ruolo predefinito del server appropriato, ad esempio securityadmin, serveradmin o sysadmin, per creare account di accesso SQL e assegnare loro ruoli DQS.  
  
### <a name="to-create-sql-login-and-grant-dqs-roles"></a>Per creare account di accesso SQL e concedere ruoli DQS  
  
1.  Avviare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
2.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]espandere l'istanza di SQL Server, quindi espandere **Sicurezza**.  
  
3.  Fare clic con il pulsante destro del mouse sulla cartella **Sicurezza** scegliere **Nuovo**, quindi selezionare **Account di accesso**.  
  
4.  Nella casella **Nome account di accesso** della finestra di dialogo **Account di accesso - Nuovo** specificare il nome di un utente di Windows, il tipo di autenticazione come **Autenticazione di Windows**e fare clic su **Cerca** per convalidare l'utente.  
  
5.  Al termine della convalida dell'utente, nel riquadro sinistro fare clic su **Mapping utenti** .  
  
6.  Nel riquadro destro selezionare la casella di controllo sotto la colonna **Mappa** per il database **DQS_MAIN** , quindi selezionare la casella di controllo **dqs_administrator**, **dqs_kb_editor**o **dqs_kb_operator** nel riquadro **Appartenenza a ruoli del database per: DQS_MAIN** , a seconda del livello di accesso necessario all'utente. Per informazioni su questi tre ruoli DQS, vedere [DQS Security](../../data-quality-services/dqs-security.md).  
  
7.  Nella finestra di dialogo **Account di accesso - Nuovo** fare clic su **OK** per applicare le modifiche.  
  
    > [!NOTE]  
    >  Se si concede il ruolo **dqs_administrator** a un utente, applicare le modifiche, quindi verificare di nuovo le autorizzazioni utente. Risulteranno selezionate anche le altre due caselle di controllo dei ruoli DQS, cioè**dq_kb_editor** e **dqs_kb_operator**.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Provare ad accedere a [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] utilizzando l'account utente di Windows per cui è stato appena creato un account di accesso SQL e a cui è stato concesso un ruolo DQS.  
  
## <a name="see-also"></a>Vedere anche  
 [Installare Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)   
 [Creare un account di accesso](../../relational-databases/security/authentication-access/create-a-login.md)  
  
  

