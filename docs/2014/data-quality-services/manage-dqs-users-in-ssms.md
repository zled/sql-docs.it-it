---
title: Gestire utenti DQS in SSMS | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 955af01d-00da-4c51-9311-f3848749df54
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a6115b9b28b4c27c6b3cddccd1f83ec1aef02ab3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169741"
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
  
  