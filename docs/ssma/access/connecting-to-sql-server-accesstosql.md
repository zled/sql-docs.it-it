---
title: Connessione a SQL Server (AccessToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- authentication
- instance of SQL Server
- metadata, refreshing
- ports
- refreshing metadata
- spaces in database names
- special characters
- SQL Server
- SQL Server, connecting
- SQL Server, connecting to
- SQL Server, reconnecting
ms.assetid: f84cf007-ddf1-4396-a07c-3e0729abc769
caps.latest.revision: "24"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f282c03b5492ea05fefe3d65b968d42ce146333c
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="connecting-to-sql-server-accesstosql"></a>Connessione a SQL Server (AccessToSQL)
Per eseguire la migrazione di database di Access per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è necessario connettersi all'istanza di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Quando ci si connette, SSMA Ottiene i metadati relativi ai database nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e visualizza i metadati del database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati. SSMA archivia le informazioni sull'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] connessi, ma non archivia le password.  
  
La connessione a SQL Server rimane attiva finché non si chiude il progetto. Quando si riapre il progetto, è necessario riconnettersi a SQL Server se si desidera una connessione attiva al server. È possibile lavorare offline finché non si caricano gli oggetti di database SQL Server e la migrazione dei dati.  
  
I metadati sull'istanza di SQL Server non viene sincronizzato automaticamente. In alternativa, per aggiornare i metadati nel Visualizzatore metadati di SQL Server, è necessario aggiornare manualmente i metadati di SQL Server. Per ulteriori informazioni, vedere la sezione "La sincronizzazione di metadati di SQL Server" più avanti in questo argomento.  
  
## <a name="required-sql-server-permissions"></a>Autorizzazioni necessarie di SQL Server  
L'account utilizzato per connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] richiede autorizzazioni diverse a seconda delle azioni eseguite da quell'account.  
  
-   Per convertire oggetti di Access da [!INCLUDE[tsql](../../includes/tsql_md.md)] sintassi, per aggiornare i metadati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], o per salvare gli script convertita sintassi, l'account deve disporre dell'autorizzazione per accedere all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   Per caricare gli oggetti di database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e la migrazione dei dati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], i requisiti minimi di autorizzazione sono l'appartenenza di **db_owner** ruolo del database nel database di destinazione.  
  
## <a name="establishing-a-sql-server-connection"></a>Stabilire una connessione di SQL Server  
Prima di convertire oggetti di database di Access da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sintassi, è necessario stabilire una connessione all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] in cui si desidera eseguire la migrazione di database di Access.  
  
Quando si definiscono le proprietà di connessione, è inoltre possibile specificare il database in cui verranno migrati dati e oggetti. È possibile personalizzare il mapping a livello di accesso database dopo la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Per ulteriori informazioni, vedere [Mapping database di origine e destinazione](http://msdn.microsoft.com/en-us/69bee937-7b2c-49ee-8866-7518c683fad4)  
  
> [!IMPORTANT]  
> Prima di connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], assicurarsi che l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è in esecuzione e può accettare connessioni. Per ulteriori informazioni, vedere "connessione al [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] motore di Database" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
**Per connettersi a SQL Server**  
  
1.  Nel **File** dal menu **Connetti al Server SQL**.  
  
    Se si è connessi in precedenza per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], il nome di comando sarà **Riconnetti a SQL Server**.  
  
2.  Nel **nome Server** immettere o selezionare il nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
    -   Se ci si connette all'istanza predefinita nel computer locale, è possibile immettere **localhost** o un punto (**.**).  
  
    -   Se ci si connette all'istanza predefinita in un altro computer, immettere il nome del computer.  
  
    -   Se ci si connette a un'istanza denominata, immettere il nome del computer, una barra rovesciata e il nome dell'istanza. Ad esempio: MyServer\MyInstance.  
  
    -   Per connettersi a un'istanza utente attiva di [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)], la connessione tramite named pipe protocollo e specificando il nome della pipe, ad esempio \\ \\.\pipe\sql\query. Per altre informazioni, vedere la documentazione di [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)].  
  
3.  Se l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è configurato per accettare le connessioni su una porta non predefinito, immettere il numero di porta utilizzato per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] connessioni nel **porta Server** casella. Per l'istanza predefinita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], il numero di porta predefinito è 1433. Per le istanze denominate, SSMA tenterà di ottenere il numero di porta di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] servizio Browser.  
  
4.  Nel **Database** , immettere il nome del database di destinazione per la migrazione di oggetti e dati.  
  
    Questa opzione non è disponibile durante la riconnessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
    Il nome del database di destinazione non può contenere spazi o caratteri speciali. Ad esempio, è possibile migrare i database di Access per un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database denominato "abc". Ma è possibile eseguire la migrazione di database di Access per un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database denominato "a b, c".  
  
    Dopo la connessione, è possibile personalizzare questo mapping per ogni database. Per ulteriori informazioni, vedere [Mapping database di origine e destinazione](http://msdn.microsoft.com/en-us/69bee937-7b2c-49ee-8866-7518c683fad4)  
  
5.  Nel **autenticazione** -menu a discesa, seleziona il tipo di autenticazione da utilizzare per la connessione. Per utilizzare l'account di Windows, selezionare **l'autenticazione di Windows**. Per utilizzare un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] account di accesso, selezionare **autenticazione di SQL Server**, quindi specificare un nome utente e una password.  
  
6.  Per la connessione sicura, vengono aggiunti due controlli, **Encrypt Connection** casella di controllo e **TrustServerCertificate** casella di controllo. Solo quando **Encrypt Connection** casella di controllo è selezionata **TrustServerCertificate** casella di controllo è visibile. Quando **Encrypt Connection** è checked(true) e **TrustServerCertificate** è unchecked(false), convaliderà il certificato SSL di SQL Server. La convalida del certificato del server fa parte dell'handshake SSL e assicura che il server a cui si esegue la connessione sia quello corretto. A tale scopo, deve essere installato un certificato sul lato client e sul lato server.  
  
7.  Fare clic su **Connetti**.  
  
**Compatibilità di versione superiore**  
  
È possibile connettersi o riconnettersi a versioni successive di SQL Server.  
  
1.  Sarà in grado di connettersi a SQL Server 2008 o SQL Server 2012, quando il progetto creato è SQL Server 2005.  
  
2.  Sarà in grado di connettersi a SQL Server 2012, quando il progetto creato è SQL Server 2008, ma non è possibile connettersi a versioni precedenti, ad esempio SQL Server 2005.  
  
3.  Sarà in grado di connettersi a SQL Server 2012 solo quando il progetto creato è SQL Server 2012.  
  
4.  Compatibilità di versione superiore non è valida per SQL Azure.  
  
||||||||
|-|-|-|-|-|-|-|
|**VERSIONE SERVER di destinazione e tipo di progetto**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2005 (versione: 9)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2008 (versione: 10. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2012 (Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2014 (Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2016 (Version:13.x)|SQL Azure|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005|Sì|Sì|Sì|Sì|Sì||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008||Sì|Sì|Sì|Sì||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012|||Sì|Sì|Sì||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014||||Sì|Sì||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016|||||Sì||
|SQL Azure||||||Sì|
  
> [!IMPORTANT]  
> Conversione degli oggetti di database viene eseguita in base al tipo di progetto ma non per la versione di SQL Server connesso. In caso di progetto di SQL Server 2005, la conversione viene eseguita in base a SQL Server 2005, anche se si è connessi a una versione successiva di SQL Server (SQL Server 2008/SQL Server 2012 o SQL Server 2014/SQL Server 2016).  
  
## <a name="synchronizing-sql-server-metadata"></a>Sincronizzazione dei metadati SQL Server  
Se [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] schemi modificare dopo la connessione, è possibile sincronizzare i metadati con il server.  
  
**Per sincronizzare i metadati di SQL Server**  
  
-   In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati, fare clic destro **database**, quindi selezionare **Sincronizza con Database**.  
  
## <a name="reconnecting-to-sql-server"></a>Connettersi a SQL Server  
La connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] rimane attiva finché non si chiude il progetto. Quando si riapre il progetto, è necessario riconnettersi al [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] se si desidera una connessione attiva al server. È possibile lavorare offline solo dopo aver caricato gli oggetti di database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e la migrazione dei dati.  
  
La procedura per la riconnessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è uguale a quella per stabilire una connessione.  
  
## <a name="next-steps"></a>Passaggi successivi  
Se si desidera personalizzare il mapping tra i database di origine e di destinazione, vedere [Mapping database di origine e destinazione](http://msdn.microsoft.com/en-us/69bee937-7b2c-49ee-8866-7518c683fad4) in caso contrario, il passaggio successivo consiste per convertire gli oggetti di database per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] utilizzando la sintassi [convertire gli oggetti di database](http://msdn.microsoft.com/en-us/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database di Access a SQL Server](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
