---
title: Connetti al server (Reporting Services) | Microsoft Docs
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
- sql13.swb.connection.login.reportserver.f1
ms.assetid: ef81b658-8eb5-4636-ac81-eead10cc7b9f
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f48f75a346c30a4a142a67e83949b7f420030726
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="connect-to-server-reporting-services"></a>Connetti al server (Reporting Services)
Usare questa finestra di dialogo per visualizzare o specificare le opzioni per la connessione a [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion_md.md)].  
  
## <a name="options"></a>Opzioni  
**Tipo server**  
Per la registrazione di un server da **Esplora oggetti**, selezionare il tipo di server a cui connettersi: [!INCLUDE[ssDE](../../includes/ssde_md.md)], Analysis Services, Reporting Services o Integration Services. Nelle altre parti della finestra di dialogo vengono visualizzate solo le opzioni applicabili al tipo di server selezionato. Durante la registrazione di un server da **Server registrati**, la casella **Tipo server** è di sola lettura e corrisponde al tipo di server visualizzato nel componente **Server registrati** . Per registrare un tipo diverso di server, selezionare [!INCLUDE[ssDE](../../includes/ssde_md.md)], Analysis Services, Reporting Services o Integration Services nella barra degli strumenti **Server registrati** prima di avviare la registrazione di un nuovo server.  
  
**Nome server**  
La modalità server dell'istanza del server di report a cui ci si connette determina il valore che è necessario immettere.  
  
Per un server di report in esecuzione in modalità nativa, specificare l'istanza del server di report a cui connettersi. Se si utilizza l'istanza predefinita, il nome del server corrisponde in genere al nome del computer. Se è stata installata un'istanza denominata, aggiungere il nome dell'istanza al nome del server in questo formato: <servername>\\<InstanceName>. Reporting Services utilizza il carattere barra rovesciata per delimitare il nome dell'istanza.  
  
Per un server di report in esecuzione in modalità integrata SharePoint, è necessario specificare un sito di SharePoint. È possibile specificare qualsiasi sito di una raccolta siti integrata con [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion_md.md)]. L'URL specificato deve includere il prefisso HTTP o HTTPS. Per connettersi al sito in Management Studio, è necessario disporre delle autorizzazioni necessarie per accedere al sito di SharePoint. Il livello di autorizzazione assegnato determinerà gli elementi che è possibile visualizzare e gestire. Per altre informazioni, vedere [Procedura: Registrazione e connessione a un server di report](http://msdn.microsoft.com/en-us/c875ff87-ee7d-443a-a702-bdb4b6c27c6e).  
  
**Autenticazione**  
[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion_md.md)] può essere configurato per accettare richieste di autenticazione di Windows o richieste di autenticazione basata su form gestite da un'estensione di autenticazione personalizzata definita. Selezionare una delle modalità di autenticazione seguenti per la connessione a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion_md.md)]:  
  
**Modalità di autenticazione di Windows (Autenticazione di Windows)**  
Consente di connettersi a un'istanza del server di report tramite le credenziali di [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows.  
  
**Autenticazione di base**  
Consente di connettersi mediante la modalità di **Autenticazione di base** se l'installazione di Reporting Services è configurata per usarla.  
  
**Autenticazione basata su form**  
Consente di connettersi mediante la modalità **Autenticazione basata su form** se l'installazione di Reporting Services è configurata per usare un'estensione di autenticazione personalizzata.  
  
**Nome utente**  
Immettere il nome account di accesso da utilizzare per la connessione. Questa opzione è disponibile solo se si è scelto di utilizzare l'autenticazione di base ****  o basata su form ****.  
  
**Password**  
Immettere la password associata al nome utente. Questa opzione può essere modificata solo se si è scelto di utilizzare l'autenticazione di base ****  o basata su form ****.  
  
**Connetti**  
Fare clic su questo pulsante per connettersi al server selezionato.  
  
**Opzioni**  
Fare clic su questo pulsante per visualizzare ulteriori opzioni per la connessione al server, come le opzioni per la registrazione di un server e la memorizzazione della password.  
  
## <a name="see-also"></a>Vedere anche  
[Configurazione di una connessione a un server di report](http://msdn.microsoft.com/en-us/9759a9fb-35e9-4215-969b-a9f1fea18487)  
[Procedura: Registrazione e connessione a un server di report](http://msdn.microsoft.com/en-us/c875ff87-ee7d-443a-a702-bdb4b6c27c6e)  
[Configurazione dell'autenticazione in Reporting Services](http://msdn.microsoft.com/en-us/753c2542-0e97-4d8f-a5dd-4b07a5cd10ab)  
  

