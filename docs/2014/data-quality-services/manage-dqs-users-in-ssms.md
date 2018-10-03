---
title: Gestione di utenti DQS in SSMS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
ms.topic: conceptual
ms.assetid: 955af01d-00da-4c51-9311-f3848749df54
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4b269ec84e2aa2227cc8edf8a0808fc7df0dce31
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48077469"
---
# <a name="manage-dqs-users-in-ssms"></a>Gestione di utenti DQS in SSMS
  In questo argomento viene descritto come creare utenti aggiuntivi nell'istanza di SQL Server utilizzando SQL Server Management Studio e come assegnare loro ruoli [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) nel database DQS_MAIN.  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 L'account utente di Windows deve essere un membro del ruolo predefinito del server appropriato, ad esempio securityadmin, serveradmin o sysadmin, per creare account di accesso SQL e assegnare a questi i ruoli DQS appropriati.  
  
##  <a name="GrantRoles"></a> Creare un account di accesso SQL e concessione del ruolo DQS  
  
1.  Avviare Microsoft SQL Server Management Studio.  
  
2.  In Microsoft SQL Server Management Studio espandere l'istanza di SQL Server, quindi espandere **Sicurezza**.  
  
3.  Fare clic con il pulsante destro del mouse sulla cartella **Sicurezza**scegliere **Nuovo**, quindi selezionare **Account di accesso**.  
  
4.  Nella casella **Nome account di accesso** della finestra di dialogo **Account di accesso - Nuovo** specificare il nome di un utente di Windows, il tipo di autenticazione come **Autenticazione di Windows**e fare clic su **Cerca** per convalidare l'utente.  
  
    > [!NOTE]  
    >  DQS supporta sola l'autenticazione di Windows; l'autenticazione di SQL Server non è supportata.  
  
5.  Al termine della convalida dell'utente, nel riquadro sinistro fare clic su **Mapping utenti** .  
  
6.  Nel riquadro destro selezionare la casella di controllo sotto la colonna **Mappa** per il database **DQS_MAIN**, quindi selezionare la casella di controllo **dqs_administrator**, **dqs_kb_editor** o **dqs_kb_operator** nel riquadro **Appartenenza a ruoli del database per: DQS_MAIN**, a seconda del livello di accesso necessario all'utente.  
  
7.  Nella finestra di dialogo **Account di accesso - Nuovo** fare clic su **OK** per applicare le modifiche.  
  
    > [!NOTE]  
    >  Se si concede il ruolo **dqs_administrator** a un utente, applicare le modifiche, quindi verificare di nuovo le autorizzazioni utente. Risulteranno selezionate anche le altre due caselle di controllo dei ruoli DQS, cioè **dq_kb_editor** e **dqs_kb_operator**.  
  
  
