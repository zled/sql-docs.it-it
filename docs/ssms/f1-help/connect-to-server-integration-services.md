---
title: Connetti al server (Integration Services) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.connection.login.dtsserver.f1
ms.assetid: 5be897bd-f36c-4c6a-a91a-13d0d016f8b6
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4d7f292d113fb3d9bc8197f7be3134524e8116af
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="connect-to-server-integration-services"></a>Connetti al server (Integration Services)
Usare questa finestra di dialogo per visualizzare o specificare le opzioni per la connessione a [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion_md.md)].  
  
## <a name="options"></a>Opzioni  
**Tipo server**  
Per la registrazione di un server da Esplora oggetti, selezionare il tipo di server a cui connettersi, ovvero [!INCLUDE[ssDE](../../includes/ssde_md.md)], Analysis Services, Reporting Services o Integration Services. Nelle altre parti della finestra di dialogo vengono visualizzate solo le opzioni applicabili al tipo di server selezionato. Durante la registrazione di un server da Server registrati, la casella Tipo server è di sola lettura e corrisponde al tipo di server visualizzato nel componente Server registrati. Per registrare un tipo diverso di server, selezionare [!INCLUDE[ssDE](../../includes/ssde_md.md)], Analysis Services, Reporting Services o Integration Services nella barra degli strumenti Server registrati prima di avviare la registrazione di un nuovo server.  
  
**Nome server**  
Consente di selezionare il server a cui connettersi. Per impostazione predefinita verrà visualizzata l'ultima istanza del server a cui è stata effettuata la connessione.  
  
> [!NOTE]  
> Non usare *<servername>*\\*<instancename>*, perché [!INCLUDE[ssIS](../../includes/ssis_md.md)] non supporta più di un'istanza in un computer.  
  
**Autenticazione**  
Solo l'autenticazione di [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows è disponibile per [!INCLUDE[ssIS](../../includes/ssis_md.md)]. Tale modalità consente di connettersi tramite un account utente di Windows.  
  
**Nome utente**  
Questa opzione non è disponibile in quanto per [!INCLUDE[ssIS](../../includes/ssis_md.md)]è possibile utilizzare solo l'autenticazione di Windows.  
  
**Password**  
Questa opzione non è disponibile in quanto per [!INCLUDE[ssIS](../../includes/ssis_md.md)]è possibile utilizzare solo l'autenticazione di Windows.  
  
**Connetti**  
Fare clic su questo pulsante per connettersi al server selezionato.  
  
**Opzioni**  
Fare clic su questo pulsante per visualizzare ulteriori opzioni per la connessione al server, come le opzioni per la registrazione di un server e la memorizzazione della password.  
  

