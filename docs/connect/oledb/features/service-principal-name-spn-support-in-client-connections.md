---
title: Supporto per il nome dell'entità servizio (SPN) nelle connessioni Client | Documenti Microsoft
description: Supporto del nome dell'entità servizio (SPN) nelle connessioni client
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, SPNs
- OLE DB, SPNs
- SPNs [SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 83487ad72148e7b82ccb20194032a4df09175668
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2018
---
# <a name="service-principal-name-spn-support-in-client-connections"></a>Supporto per nomi SPN nelle connessioni client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  A partire da [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], supporto per i nomi dell'entità servizio (SPN) è stato esteso per consentire l'autenticazione reciproca in tutti i protocolli. Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], i nomi SPN sono supportati solo per Kerberos tramite TCP quando il valore predefinito SPN per il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] istanza è stata registrata con Active Directory.  
  
 Gli SPN vengono utilizzati dal protocollo di autenticazione per determinare l'account in cui un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene eseguita l'istanza. Se l'account dell'istanza è noto, è possibile usare l'autenticazione Kerberos per fornire autenticazione reciproca dal client e dal server. Se l'account dell'istanza non è noto, viene usata l'autenticazione NTLM, che fornisce solo l'autenticazione del client da parte del server. Attualmente, il Driver OLE DB per SQL Server esegue la ricerca di autenticazione, deducendo SPN dalle proprietà di connessione istanza nome e la rete. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tenteranno di registrare SPN all'avvio o possono essere registrati manualmente. La registrazione, tuttavia, non riuscirà se l'account dispone di diritti di accesso insufficienti per la registrazione dei nomi SPN.  
  
 Gli account di dominio e del computer vengono registrati automaticamente in Active Directory. Questi possono essere usati come SPN oppure gli amministratori possono definire i propri SPN. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] rende l'autenticazione più gestibile e affidabile consentendo ai client di specificare direttamente il nome SPN da utilizzare.  
  
> [!NOTE]  
>  Un nome SPN specificato da un'applicazione client viene usato solo quando viene stabilita una connessione con sicurezza integrata di Windows.  
  
> [!TIP]  
>  **[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Kerberos Configuration Manager per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]** è uno strumento di diagnostica che semplifica la risoluzione dei problemi di connettività correlati a Kerberos con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [Microsoft Kerberos Configuration Manager per SQL Server](http://www.microsoft.com/download/details.aspx?id=39046).  
  
 Per altre informazioni su Kerberos, vedere gli articoli seguenti:  
  
-   [Supplemento tecnico Kerberos per Windows](http://go.microsoft.com/fwlink/?LinkId=101449)  
  
-   [Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkID=100758)  
  
## <a name="usage"></a>Utilizzo  
 Nella tabella seguente vengono descritti gli scenari più comuni in cui le applicazioni client possono abilitare l'autenticazione protetta.  
  
|Scenario|Description|  
|--------------|-----------------|  
|Un'applicazione legacy non specifica un nome SPN.|Questo scenario di compatibilità garantisce che non vi saranno differenze di comportamento per le applicazioni sviluppate per le versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Se non viene specificato alcun nome SPN, l'applicazione si basa sui nomi SPN generati e non è in grado di identificare il metodo di autenticazione usato.|  
|Un'applicazione client utilizzando la versione corrente del Driver OLE DB per SQL Server specifica un nome SPN nella stringa di connessione come account utente o un computer di dominio, come nome SPN specifico dell'istanza o come una stringa definita dall'utente.|È possibile usare la parola chiave **ServerSPN** in una stringa del provider, di inizializzazione o di connessione per effettuare le operazioni seguenti:<br /><br /> -Specificare l'account utilizzato per il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] istanza per una connessione. Questa operazione semplifica l'accesso all'autenticazione Kerberos. Se è presente un centro distribuzione chiavi (KDC, Key Distribution Center) Kerberos ed è stato specificato l'account corretto, è più probabile che venga usata l'autenticazione Kerberos anziché l'autenticazione NTLM. Il centro distribuzione chiavi si trova in genere nello stesso computer del controller di dominio.<br /><br /> -Specificare un nome SPN per cercare l'account del servizio per il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] istanza. Per ogni [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] istanza, i nomi SPN vengono generati due predefiniti che possono essere utilizzato per questo scopo. Non è tuttavia garantito che tali chiavi siano presenti in Active Directory, pertanto in questa situazione non è garantita neanche l'autenticazione Kerberos.<br /><br /> -Specificare un nome SPN che verrà utilizzato per cercare l'account del servizio per il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] istanza. Può trattarsi di qualsiasi stringa definita dall'utente di cui è stato eseguito il mapping all'account del servizio. In questo caso, la chiave deve essere registrata manualmente nel centro distribuzione chiavi e deve essere conforme alle regole relative ai nomi SPN definiti dall'utente.<br /><br /> È possibile usare la parola chiave **FailoverPartnerSPN** per specificare il nome SPN per il server partner di failover. L'intervallo di valori per gli account e per le chiavi di Active Directory coincide con i valori che è possibile specificare per il server principale.|  
|Un'applicazione OLE DB specifica un nome SPN come proprietà di inizializzazione dell'origine dati per il server principale o per un server partner di failover.|È possibile usare la proprietà di connessione **SSPROP_INIT_SERVER_SPN** nel set di proprietà **DBPROPSET_SQLSERVERDBINIT** per specificare il nome SPN per una connessione.<br /><br /> È possibile usare la proprietà di connessione **SSPROP_INIT_FAILOVER_PARTNER_SPN** nel set di proprietà **DBPROPSET_SQLSERVERDBINIT** per specificare il nome SPN per il server partner di failover.|   
|L'utente specifica un nome SPN per un server o per un server partner di failover in una finestra di dialogo **Collegamento dati** o **Account di accesso** OLE DB.|È possibile specificare il nome SPN in una finestra di dialogo **Collegamento dati** o **Account di accesso** .|   
|Un'applicazione OLE DB determina il metodo di autenticazione usato per stabilire una connessione.|Se una connessione è stata aperta correttamente, un'applicazione può eseguire una query sulla proprietà di connessione **SSPROP_AUTHENTICATION_METHOD** nel set di proprietà **DBPROPSET_SQLSERVERDATASOURCEINFO** per determinare il metodo di autenticazione usato. Alcuni dei valori possibili sono **NTLM** e **Kerberos**.|  
  
## <a name="failover"></a>Failover  
 I nomi SPN non vengono archiviati nella cache di failover e pertanto non possono essere passati tra connessioni. I nomi SPN verranno usati in tutti i tentativi di connessione al server principale e al partner se specificati nella stringa di connessione o negli attributi di connessione.  
  
## <a name="connection-pooling"></a>Pool di connessioni  
 Nelle applicazioni è necessario tenere presente che la specifica dei nomi SPN solo in alcune stringhe di connessione può implicare la frammentazione del pool.  
  
 Le applicazioni possono specificare a livello di programmazione i nomi SPN come attributi di connessione anziché specificare parole chiave della stringa di connessione. In questo modo, viene semplificata la gestione della frammentazione del pool di connessioni.  
  
 Nelle applicazioni è inoltre necessario tenere presente che i nomi SPN nelle stringhe di connessione possono essere sostituiti dagli attributi di connessione corrispondenti, mentre le stringhe di connessione utilizzate dal pool di connessioni utilizzeranno i valori della stringa di connessione ai fini del pool.  
  
## <a name="down-level-server-behavior"></a>Comportamento dei server legacy  
 Poiché il nuovo comportamento di connessione viene implementato dal client, non è specifico di una determinata versione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="linked-servers-and-delegation"></a>Server collegati e delega  
 Quando si creano server collegati, la **@provstr** parametro di [sp_addlinkedserver](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) può essere utilizzato per specificare il server partner di failover, i nomi SPN. L'uso di questo parametro offre gli stessi vantaggi ottenuti specificando i nomi SPN nelle stringhe di connessione del client e consente di stabilire in modo più semplice e affidabile connessioni che usano l'autenticazione Kerberos.  
  
 La delega con server collegati richiede l'autenticazione Kerberos.  
  
## <a name="management-aspects-of-spns-specified-by-applications"></a>Aspetti correlati alla gestione dei nomi SPN specificati dalle applicazioni  
 Nel determinare se specificare nomi SPN in un'applicazione (tramite stringhe di connessione) o a livello di programmazione tramite proprietà di connessione (anziché basandosi sui nomi SPN generati dal provider predefinito), considerare gli aspetti seguenti:  
  
-   Sicurezza: verificare se il nome SPN specificato comporta la divulgazione di informazioni protette.  
  
-   Affidabilità: Per abilitare l'utilizzo di nomi SPN predefiniti, l'account del servizio in cui il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] esecuzione dell'istanza devono disporre di privilegi sufficienti per l'aggiornamento di Active Directory nel centro distribuzione CHIAVI.  
  
-   Utilità e trasparenza a livello di posizione: valutare le conseguenze sui nomi SPN di un'applicazione se il database viene spostato in un'istanza diversa di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Questa considerazione si applica sia al server principale sia al relativo partner di failover se si usa il mirroring del database. Se una modifica apportata al server comporta la modifica dei nomi SPN, valutare le conseguenze sulle applicazioni e determinare se sarà possibile gestire tutte le modifiche.  
  
## <a name="specifying-the-spn"></a>Definizione del nome SPN  
 È possibile specificare un nome SPN nelle finestre di dialogo e nel codice. In questa sezione viene descritto come specificare un nome SPN.  
  
 La lunghezza massima consentita per un nome SPN è 260 caratteri.  
  
 Di seguito viene indicata la sintassi usata per i nomi SPN nella stringa di connessione o negli attributi di connessione:  
  
|Sintassi|Description|  
|------------|-----------------|  
|MSSQLSvc/*fqdn*|Nome SPN predefinito generato dal provider per un'istanza predefinita quando si utilizza un protocollo diverso da TCP.<br /><br /> *fqdn* è un nome di dominio completo.|  
|MSSQLSvc/*fqdn*:*port*|Nome SPN predefinito generato dal provider quando si usa il protocollo TCP.<br /><br /> *port* è un numero di porta TCP.|  
|MSSQLSvc/*fqdn*:*InstanceName*|Nome SPN predefinito generato dal provider per un'istanza denominata quando si usa un protocollo diverso da TCP.<br /><br /> *InstanceName* è un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nome dell'istanza.|  
|HOST/*fqdn*<br /><br /> HOST/*MachineName*|Nome SPN di cui viene eseguito il mapping ad account del computer predefiniti registrati automaticamente in Windows.|  
|*Username*@*Domain*|Specifica diretta di un account di dominio.<br /><br /> *Username* è un nome di account utente di Windows.<br /><br /> *Domain* è un nome di dominio di Windows o un nome di dominio completo.|  
|*MachineName*$@*Domain*|Specifica diretta di un account del computer.<br /><br /> Se il server a cui si stabilisce la connessione viene eseguito usando l'account di sistema locale o del servizio di rete, per ottenere l'autenticazione Kerberos **ServerSPN** può usare il formato *MachineName*$@*Domain* .|  
|*KDCKey*/*MachineName*|Nome SPN specificato dall'utente.<br /><br /> *KDCKey* è una stringa alfanumerica conforme alle regole relative alle chiavi KDC.|  
  
## <a name="ole-db-syntax-supporting-spns"></a>OLE DB sintassi che supportano i nomi SPN  
 Per informazioni specifiche della sintassi, vedere gli argomenti seguenti:  
  
-   [Nomi dell'entità servizio &#40;i nomi SPN&#41; nelle connessioni Client &#40;OLE DB&#41;](../../oledb/ole-db/service-principal-names-spns-in-client-connections-ole-db.md)  
  
 Per informazioni sulle applicazioni di esempio in cui viene illustrata questa funzionalità, vedere la pagina relativa agli [esempi di programmazione dati di SQL Server](http://msftdpprodsamples.codeplex.com/).  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per la funzionalità di SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)   
 [Registrazione di un nome dell'entità servizio per le connessioni Kerberos](../../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md)  
  
