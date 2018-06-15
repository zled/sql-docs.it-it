---
title: Utilizzo di servizi desktop remoto con connessione ODBC pool | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connection pooling in RDS [ADO]
ms.assetid: e8b912c1-da5b-4e85-a000-1e6648a94237
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 416cbadf4d77ab9c7325c5f874f9818c4e05d8e5
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35274650"
---
# <a name="using-rds-with-odbc-connection-pooling"></a>Utilizzo di servizi desktop remoto con connessione ODBC pool
Se si utilizza un'origine dati ODBC, è possibile utilizzare il pool di connessioni opzione in Internet Information Services (IIS) per ottenere una gestione ad alte prestazioni del carico del client. Il pool di connessioni è un gestore delle risorse per le connessioni, mantenere lo stato aperto per le connessioni utilizzate di frequente.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Per abilitare il pool di connessioni, vedere la documentazione di Internet Information Services.  
  
 Si noti che l'abilitazione del pool di connessioni può comportare il server Web di altre restrizioni, come illustrato nella documentazione di Microsoft Internet Information Services.  
  
 Per garantire che il pool di connessioni è stabile e offre ulteriori miglioramenti delle prestazioni, è necessario configurare Microsoft SQL Server per utilizzare la libreria di rete TCP/IP Socket.  
  
 A tale scopo, è necessario:  
  
-   Configurare il computer SQL Server per l'utilizzo di socket TCP/IP.  
  
-   Configurare il server Web per l'utilizzo di socket TCP/IP.  
  
## <a name="configuring-the-sql-server-computer-to-use-tcpip-sockets"></a>Configurazione del Computer SQL Server per l'utilizzo di socket TCP/IP  
 Nel computer SQL Server, eseguire il programma di installazione di SQL Server in modo che le interazioni con l'origine dati utilizzano la libreria di rete TCP/IP Socket.  
  
### <a name="to-specify-the-tcpip-socket-network-library-on-the-sql-server-computer"></a>Per specificare la libreria di rete del Socket TCP/IP nel computer SQL Server  
  
### <a name="in-microsoft-sql-server-65"></a>In Microsoft SQL Server 6.5:  
  
1.  Dal menu Start, scegliere Programmi Microsoft SQL Server 6.5 e quindi fare clic su installazione di SQL.  
  
2.  Fare clic su Continua due volte.  
  
3.  In Microsoft SQL Server, ovvero la finestra di dialogo Opzioni, selezionare il supporto di rete di modifica e quindi fare clic su Continua.  
  
4.  Assicurarsi che sia selezionata la casella di controllo socket TCP/IP e fare clic su OK.  
  
5.  Fare clic su Continua per terminare e uscire dall'installazione.  
  
### <a name="in-microsoft-sql-server-70"></a>In Microsoft SQL Server 7.0:  
  
1.  Dal menu Start, scegliere Programmi Microsoft SQL Server 7.0 e quindi fare clic su Utilità di rete del Server.  
  
2.  Nella scheda Generale della finestra di dialogo, fare clic su Aggiungi.  
  
3.  Nella finestra di dialogo Aggiungi configurazione libreria di rete, fare clic su TCP/IP.  
  
4.  Nelle caselle indirizzo Proxy e il numero di porta, immettere l'indirizzo della porta del proxy e del numero fornito dall'amministratore di rete.  
  
5.  Fare clic su OK per completare e uscire dall'installazione.  
  
## <a name="configuring-the-web-server-to-use-tcpip-sockets"></a>Configurazione del Server Web per l'utilizzo di socket TCP/IP  
 Sono disponibili due opzioni per la configurazione del server Web per usare i socket TCP/IP. Operazioni varia a seconda se tutti i server SQL sono accessibili dal server Web, o un Server SQL specifico è accessibile dal server Web.  
  
 Se tutti i server SQL sono accessibili dal server Web, è necessario eseguire l'utilità di configurazione di SQL Server Client sul computer server Web. La procedura seguente modifica la libreria di rete predefinita per tutte le connessioni di SQL Server eseguita dal server Web IIS per usare la libreria di rete TCP/IP Sockets.  
  
### <a name="to-configure-the-web-server-all-sql-servers"></a>Per configurare il server Web (tutti i server SQL)  
  
### <a name="for-microsoft-sql-server-65"></a>Per Microsoft SQL Server 6.5:  
  
1.  Dal menu Start, scegliere Programmi Microsoft SQL Server 6.5 e quindi fare clic su Utilità di configurazione Client di SQL.  
  
2.  Fare clic sulla scheda Libreria di rete.  
  
3.  Nella finestra di rete predefinito, selezionare i socket TCP/IP.  
  
4.  Fare clic su Fine per salvare le modifiche e uscire dall'utilità.  
  
### <a name="for-microsoft-sql-server-70"></a>Per Microsoft SQL Server 7.0:  
  
1.  Dal menu Start, scegliere Programmi Microsoft SQL Server 7.0 e quindi fare clic su configurazione di rete Client.  
  
2.  Fare clic sulla scheda Generale.  
  
3.  Nella casella di libreria di rete predefinito, fare clic su TCP/IP.  
  
4.  Fare clic su OK per salvare le modifiche e chiudere l'utilità.  
  
 Se si accede a un Server SQL specifico da un server Web, è necessario eseguire l'utilità di configurazione di SQL Server Client sul computer server Web. Per modificare la libreria di rete per una connessione di SQL Server specifica, configurare il software Client di SQL Server sul computer server Web come indicato di seguito.  
  
### <a name="to-configure-the-web-server-a-specific-sql-server"></a>Per configurare il server Web (un Server SQL specifico)  
  
### <a name="for-microsoft-sql-server-65"></a>Per Microsoft SQL Server 6.5:  
  
1.  Dal menu Start, scegliere Programmi Microsoft SQL Server 6.5 e quindi fare clic su Utilità di configurazione Client di SQL.  
  
2.  Fare clic sulla scheda avanzata.  
  
3.  Nella finestra di Server, digitare il nome del server a cui connettersi tramite TCP/IP Sockets.  
  
4.  Nella casella nome della DLL, selezionare i socket TCP/IP.  
  
5.  Fare clic su Aggiungi/modifica. Tutte le origini dati che punta al server utilizzeranno i socket TCP/IP.  
  
6.  Fare clic su Fine.  
  
### <a name="for-microsoft-sql-server-70"></a>Per Microsoft SQL Server 7.0:  
  
1.  Dal menu Start, scegliere Programmi Microsoft SQL Server 7.0 e quindi fare clic su Utilità di configurazione Client.  
  
2.  Fare clic sulla scheda Generale.  
  
3.  Fare clic su Aggiungi.  
  
4.  Immettere l'alias del server nella casella dell'alias di Server. Nella casella di librerie di rete, fare clic su TCP/IP. Nella casella Nome Computer, immettere il nome del computer del computer in cui è in ascolto per i client TCP/IP Sockets. Nella casella Numero porta, immettere la porta su cui è in ascolto il Server SQL.  
  
5.  Fare clic su OK e quindi di nuovo OK per uscire dall'utilità.  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali su RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)






















