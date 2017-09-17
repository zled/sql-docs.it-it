---
title: Protezione delle applicazioni di servizi desktop remoto | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDS security [ADO]
ms.assetid: 82fb1330-d6c6-4c17-ad3e-d417ff822b25
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 72a46915beed5bb65953788b2b1b7283d90cb8e5
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="securing-rds-applications"></a>Protezione delle applicazioni di servizi desktop remoto
In questo argomento vengono fornite informazioni di sicurezza per RDS.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="microsoft-internet-explorer-security-issues"></a>Problemi di sicurezza di Microsoft Internet Explorer  
 Con i nuovi miglioramenti della sicurezza aggiunti a Microsoft Internet Explorer, alcuni oggetti ADO e servizi desktop remoto sono limitate ai solo l'esecuzione in un ambiente in modalità "sicuro". È necessario che siano a conoscenza di questi problemi, quali aree diverse, i livelli di sicurezza, comportamento restrittivo, operazioni non sicure e di impostazioni di sicurezza personalizzate.  
  
## <a name="security-and-your-web-server"></a>Sicurezza e il Server Web  
 Se si utilizza il [RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) dell'oggetto sul server Web Internet, ricordare che tale crea quindi un potenziale rischio di sicurezza. Gli utenti esterni che ottenere il nome di origine dati valido (DSN), ID utente e informazioni relative alle password possono scrivere pagine per inviare query all'origine dati. Se si desidera un accesso più limitato a un'origine dati, un'opzione è per annullare la registrazione ed eliminare il **RDSServer** (msadcf) dell'oggetto e utilizzare oggetti business personalizzata con query a livello di codice.  
  
 Per ulteriori informazioni sulle implicazioni di sicurezza di utilizzo dell'oggetto RDSServer, vedere il Bollettino Microsoft sulla sicurezza di Microsoft MS99-025 sul sito Web Microsoft Security.  
  
## <a name="client-impersonation-and-security"></a>Sicurezza e la rappresentazione del client  
 Se il **l'autenticazione di Password** proprietà per il server Web IIS è impostato su autenticazione di Windows NT Challenge/Response (per Windows NT 4.0) o per l'autenticazione integrata di Windows (per Windows 2000), quindi sono oggetti business richiamato nel contesto di sicurezza del client. Si tratta di una nuova funzionalità di servizi desktop remoto 1.5 che consente la rappresentazione del Client su HTTP. Quando si utilizza questa modalità, l'accesso al server Web (IIS) non è anonimo, ma utilizza l'ID utente e password che il computer client è in esecuzione. Se il DSN ODBC sono configurate per utilizzare una connessione Trusted, quindi l'accesso ai database, ad esempio SQL Server, anche nel contesto di sicurezza del client. Ma funziona solo se il database nello stesso computer come IIS. le credenziali del client non possono essere trasferite a un altro computer.  
  
 Ad esempio, un client, John Doe, con userid = "LucaD" e la password = "segreto" è connesso a un computer client. Peter esegue un'applicazione basata su browser che richiede l'accesso di **RDSServer** oggetto per creare un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) eseguendo una query SQL sul computer "MyServer" che esegue IIS. MyServer, un sistema che esegue Windows NT Server 4.0, viene impostato per utilizzare l'autenticazione di Windows NT Challenge/Response, il DSN ODBC è "Usa connessione Trusted" selezionato e il server contiene anche l'origine dati SQL Server. Quando viene ricevuta una richiesta nel server Web, richiede il client per l'ID utente e password. Di conseguenza, la richiesta viene registrata in MyServer come proveniente da "LucaD" / "Segreto" anziché da IUSER_MyServer (ovvero l'impostazione predefinita quando l'autenticazione anonima Password si trova su). Analogamente, quando si accede a SQL Server, "LucaD" / "Segreto" viene utilizzato.  
  
 Di conseguenza, la modalità di autenticazione IIS Windows NT Challenge/Response consente pagine HTML da creare senza che venga richiesta in modo esplicito per le informazioni di ID e la password utente necessarie per accedere al database utente. Se fosse utilizzata l'autenticazione di base di IIS, quindi anche corrisponderà a obbligatorio.  
  
## <a name="password-authentication"></a>Autenticazione di password  
 Servizi Desktop remoto può comunicare con un server Web IIS in esecuzione in una delle tre modalità di autenticazione di Password: anonima, base, o l'autenticazione di NT Challenge/Response (nota come autenticazione integrata di Windows in Windows 2000). Queste impostazioni definiscono come un server Web controlla l'accesso attraverso di esso, ad esempio richiedere che un computer client dispongano di privilegi di accesso nel server Web NT.



