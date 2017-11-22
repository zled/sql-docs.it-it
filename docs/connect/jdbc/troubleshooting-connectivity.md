---
title: "Risoluzione dei problemi di connettività | Documenti Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bfba0b49-2e1f-411d-a625-d25fad9ea12d
caps.latest.revision: "23"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 1566b30797b45a0eaa40491658f4fc3381c683f9
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="troubleshooting-connectivity"></a>Risoluzione dei problemi di connettività
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] richiede che TCP/IP sia installato e in esecuzione per comunicare con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database. È possibile utilizzare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Configuration Manager per verificare quali protocolli di libreria di rete sono installati.  
  
 Sono molti i motivi per cui una connessione di database può avere esito negativo, tra cui i seguenti:  
  
-   TCP/IP non è abilitato per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], o il numero di porta o server specificato non è corretto. Verificare che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è in ascolto con TCP/IP sul server specificato e sulla porta. Questa condizione potrebbe essere segnalata da un'eccezione simile alla seguente: "Accesso non riuscito. La connessione TCP/IP all'host ha avuto esito negativo." In questo caso è possibile che si sia verificata una delle seguenti condizioni:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]viene installato ma TCP/IP non è stato installato come protocollo di rete per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] utilizzando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] utilità Configurazione di rete per [!INCLUDE[ssVersion2000](../../includes/ssversion2000_md.md)], o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Configuration Manager per [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] e versioni successive.  
  
    -   TCP/IP viene installato come un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] protocollo, ma non è in ascolto sulla porta specificata nell'URL della connessione JDBC. La porta predefinita è 1433, ma [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] può essere configurato al momento dell'installazione del prodotto per l'ascolto su qualsiasi porta. Assicurarsi che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è in ascolto sulla porta 1433. In alternativa, se la porta è stata modificata, assicurarsi che la porta specificata nell'URL della connessione JDBC corrisponda al nuovo valore. Per ulteriori informazioni sugli URL delle connessioni JDBC, vedere [creazione dell'URL di connessione](../../connect/jdbc/building-the-connection-url.md).  
  
    -   L'indirizzo del computer in cui è specificato nella connessione JDBC URL non fa riferimento a un server in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è installato e avviato.  
  
    -   L'operazione di rete di TCP/IP tra il client e server che esegue [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] non è eseguibile. È possibile verificare la connettività TCP/IP per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] mediante telnet. Ad esempio, al prompt dei comandi, digitare `telnet 192.168.0.0 1433` in cui 192.168.0.0 è l'indirizzo del computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e 1433 è la porta di attesa. Se si riceve un messaggio di errore "Impossibile connettersi Telnet", TCP/IP non è in ascolto su tale porta per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] le connessioni. Utilizzare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] utilità Configurazione di rete per [!INCLUDE[ssVersion2000](../../includes/ssversion2000_md.md)], o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Configuration Manager per [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] e versioni successive per assicurarsi che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è configurato per utilizzare TCP/IP sulla porta 1433.  
  
    -   La porta utilizzata dal server non è stata aperta nel firewall. In questo modo viene inclusa la porta utilizzata dal server o, facoltativamente, la porta associata a un'istanza denominata del server.  
  
-   Il nome del database specificato non è corretto. Assicurarsi che si accede a un oggetto esistente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database.  
  
-   Il nome utente o la password non sono corretti. Assicurarsi di disporre dei valori corretti.  
  
-   Quando si utilizza [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] l'autenticazione, il driver JDBC richiede che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] viene installato con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] l'autenticazione, che non è il valore predefinito. Assicurarsi che questa opzione è inclusa quando si installa o configura l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [La diagnosi di problemi con il Driver JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)   
 [Connessione a SQL Server con il driver JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
