---
title: Connetti al server (pagina Nome account di accesso) - Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttodtsserver.login.f1
- sql12.swb.connecttodts.login.f1
ms.assetid: 402c2de4-f4ea-40b0-909f-3ddf3bd59950
caps.latest.revision: 23
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 95eac72a39ec2d110411fbae2d2494108e5cff41
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43812397"
---
# <a name="connect-to-server-login-page-integration-services"></a>Connetti al server (pagina Nome account di accesso) - Integration Services
  Usare questa scheda per visualizzare o specificare le opzioni seguenti per la connessione a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
## <a name="options"></a>Opzioni  
 **Tipo server**  
 Per la registrazione di un server da Esplora oggetti, selezionare il tipo di server a cui connettersi, ovvero [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services o Integration Services. Nelle altre parti della finestra di dialogo vengono visualizzate solo le opzioni applicabili al tipo di server selezionato. Durante la registrazione di un server da Server registrati, la casella **Tipo server** è di sola lettura e corrisponde al tipo di server visualizzato nel componente Server registrati. Per registrare un tipo diverso di server, selezionare [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services o Integration Services nella barra degli strumenti Server registrati prima di avviare la registrazione di un nuovo server.  
  
 **Nome server**  
 Consente di selezionare il server a cui connettersi. Per impostazione predefinita verrà visualizzata l'ultima istanza del server a cui è stata effettuata la connessione.  
  
> [!NOTE]  
>  Non utilizzare  *\<nomeserver >*\\*\<NomeIstanza >* perché [!INCLUDE[ssIS](../includes/ssis-md.md)] non supporta più istanze in un computer.  
  
 **Autenticazione**  
 Solo l'autenticazione di [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows è disponibile per [!INCLUDE[ssIS](../includes/ssis-md.md)]. Tale modalità consente di connettersi tramite un account utente di Windows.  
  
 **Nome utente**  
 Questa opzione non è disponibile in quanto per [!INCLUDE[ssIS](../includes/ssis-md.md)]è possibile utilizzare solo l'autenticazione di Windows.  
  
 **Password**  
 Questa opzione non è disponibile in quanto per [!INCLUDE[ssIS](../includes/ssis-md.md)]è possibile utilizzare solo l'autenticazione di Windows.  
  
 **Memorizza password**  
 Questa opzione non è disponibile in quanto per [!INCLUDE[ssIS](../includes/ssis-md.md)]è possibile utilizzare solo l'autenticazione di Windows.  
  
 **Connect**  
 Consente di connettersi al server selezionato.  
  
 **Opzioni**  
 Fare clic su questo pulsante per modificare la finestra di dialogo e nascondere le opzioni aggiuntive per la connessione al server, ad esempio le opzioni per la memorizzazione della password.  
  
  
