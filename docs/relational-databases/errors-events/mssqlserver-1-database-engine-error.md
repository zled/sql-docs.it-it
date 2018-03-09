---
title: MSSQLSERVER_-1 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- "-1"
helpviewer_keywords:
- -1 (Database Engine error)
ms.assetid: bad25b91-eaed-46c0-a5b7-71117a32304c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 048db39c941cd54977c09450097724ebc7a2c584
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver-1"></a>MSSQLSERVER_-1
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|-1|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico||  
|Testo del messaggio|Si è verificato un errore durante il tentativo di stabilire una connessione al server.  Quando ci si connette a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], questo errore potrebbe essere provocato dal fatto che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non ammette connessioni remote sotto le impostazioni predefinite. (provider: interfacce di rete SQL, errore: 28 - Il server non supporta il protocollo richiesto) (Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Errore: -1)|  
  
## <a name="explanation"></a>Spiegazione  
Non è possibile stabilire la connessione tra il client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e il server. L'errore può essere causato da uno dei problemi seguenti:  
  
-   Un nome di istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specificato non è valido.  
  
-   Il protocollo TCP o i protocolli named pipe non sono abilitati.  
  
-   La connessione è stata rifiutata dal firewall del server.  
  
-   Il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser (sqlbrowser) non è stato avviato.  
  
## <a name="user-action"></a>Azione dell'utente  
Per risolvere l'errore, eseguire una delle operazioni seguenti:  
  
-   Controllare l'ortografia del nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specificato nella stringa di connessione.  
  
-   Usare lo strumento Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per consentire a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di accettare le connessioni remote tramite protocolli TCP o Named Pipes. Per altre informazioni su come accettare le connessioni remote, vedere [Abilitare o disabilitare un protocollo di rete del server](~/database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md).  
  
-   Assicurarsi di avere configurato il firewall nell'istanza server di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per aprire porte per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e la porta di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser (UDP 1434).  
  
-   Assicurarsi che il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser sia stato avviato nel server.  
  
## <a name="see-also"></a>Vedere anche  
[Configurare Windows Firewall per l'accesso al motore di database](~/database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)  
[Configurare i protocolli client](~/database-engine/configure-windows/configure-client-protocols.md)  
[Protocolli e librerie di rete](~/sql-server/install/network-protocols-and-network-libraries.md)  
[Configurazione di rete dei client](~/database-engine/configure-windows/client-network-configuration.md)  
[Configurare i protocolli client](~/database-engine/configure-windows/configure-client-protocols.md)  
[Abilitare o disabilitare un protocollo di rete del server](~/database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
