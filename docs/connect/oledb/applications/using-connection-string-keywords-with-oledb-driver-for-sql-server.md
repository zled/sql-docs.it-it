---
title: Utilizzo di parole chiave delle stringhe di connessione con il Driver OLE DB per SQL Server | Documenti Microsoft
description: Utilizzo di parole chiave delle stringhe di connessione con il Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- sql13.swb.connecttoserver.options.registeredservers.f1
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], connection string keywords
- MSOLEDBSQL, connection string keywords
- connection strings [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, connection string keywords
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 776562d89a12b544d6edbe475358067b39b58988
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2018
---
# <a name="using-connection-string-keywords-with-ole-db-driver-for-sql-server"></a>Utilizzo di parole chiave delle stringhe di connessione con il Driver OLE DB per SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Alcuni Driver OLE DB per SQL Server API utilizzare stringhe di connessione per specificare gli attributi di connessione. Le stringhe di connessione sono elenchi di parole chiave con i relativi valori associati. Ogni parola chiave identifica un particolare attributo di connessione.  
  
> **Nota:** il Driver OLE DB per SQL Server supporta l'ambiguità nelle stringhe di connessione per mantenere la compatibilità con le versioni precedenti (ad esempio, alcune parole chiave possono essere specificati più di una volta e possono essere consentite parole chiave in conflitto con una risoluzione basata sulla posizione o precedenza). Nelle versioni future di Driver OLE DB per SQL Server potrebbero non consentire l'ambiguità nelle stringhe di connessione. È buona norma quando si modifica alle applicazioni di utilizzare il Driver OLE DB per SQL Server per eliminare qualsiasi dipendenza dall'ambiguità delle stringhe di connessione.  
  
 Le sezioni seguenti descrivono le parole chiave che possono essere usate con il Driver OLE DB per SQL Server e gli oggetti ADO (ActiveX Data) quando si utilizza il Driver OLE DB per SQL Server come il provider di dati.  

  
## <a name="ole-db-driver-connection-string-keywords"></a>OLE DB Driver Connection String Keywords  
 Quando si utilizzano le applicazioni OLE DB, è possibile inizializzare gli oggetti origine dati in due modi diversi:  
  
-   **IDBInitialize:: Initialize**  
  
-   **IDataInitialize:: GetDatasource**  
  
 Nel primo caso è possibile utilizzare una stringa del provider per inizializzare le proprietà di connessione impostando la proprietà DBPROP_INIT_PROVIDERSTRING nel set di proprietà DBPROPSET_DBINIT. Nel secondo caso, una stringa di inizializzazione può essere passata a **IDataInitialize:: GetDatasource** metodo per inizializzare le proprietà di connessione. Entrambi i metodi inizializzano le stesse proprietà di connessione OLE DB, sebbene con set di parole chiave differenti. Il set di parole chiave utilizzate dal **IDataInitialize:: GetDatasource** è al minimo la descrizione delle proprietà all'interno del gruppo di proprietà di inizializzazione.  
  
 Per qualsiasi impostazione di stringa del provider con una proprietà OLE DB corrispondente impostata su un valore predefinito o impostata in modo esplicito su un valore, tramite il valore della proprietà OLE DB verrà eseguito l'override dell'impostazione nella stringa del provider.  
  
 Per le proprietà booleane impostate nelle stringhe del provider mediante i valori DBPROP_INIT_PROVIDERSTRING vengono utilizzati i valori "yes" e "no". Le proprietà booleane impostate nelle stringhe di inizializzazione utilizzando **IDataInitialize:: GetDatasource** vengono impostate utilizzando i valori "true" e "false".  
  
 Applicazioni che usano **IDataInitialize:: GetDatasource** inoltre possibile utilizzare le parole chiave utilizzate dal **IDBInitialize:: Initialize** ma solo per le proprietà che non contengono un valore predefinito. Se un'applicazione utilizza sia il **IDataInitialize:: GetDatasource** (parola chiave) e **IDBInitialize:: Initialize** parola chiave nella stringa di inizializzazione, il **IDataInitialize:: GetDatasource** viene utilizzata l'impostazione della parola chiave. È consigliabile che le applicazioni non utilizzano **IDBInitialize:: Initialize** parole chiave in **IDataInitialize: GetDatasource** stringhe di connessione, perché questo comportamento potrebbe non essere supportato nelle versioni successive.  
  
> [!NOTE]  
>  Una stringa di connessione passata a **IDataInitialize:: GetDatasource** viene convertita in proprietà e applicata tramite **IDBProperties:: SetProperties**. Se Servizi componenti ha rilevato la descrizione della proprietà in **IDBProperties:: GetPropertyInfo**, questa proprietà verrà applicata come autonoma. In caso contrario, verrà applicata mediante la proprietà DBPROP_PROVIDERSTRING. Ad esempio, se si specifica una stringa di connessione **origine dati = server1; Server = server2**, **origine dati** verrà impostato come proprietà, ma **Server** entra in una stringa del provider.  
  
 Se si indicano più istanze per la stessa proprietà specifica del provider, verrà utilizzato il primo valore della prima proprietà.  
  
 Stringhe di connessione utilizzate nelle applicazioni OLE DB utilizzando DBPROP_INIT_PROVIDERSTRING con **IDBInitialize:: Initialize** presentano la sintassi seguente:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 È consigliabile racchiudere i valori di attributo tra parentesi graffe per evitare i problemi determinati dalla presenza di caratteri non alfanumerici nei valori di attributo. Poiché si suppone che la prima parentesi graffa chiusa indichi la fine del valore, l'uso di tali parentesi nei valori non è consentito.  
  
 Uno spazio dopo il segno = in una parola chiave di una stringa di connessione verrà interpretato come valore letterale, anche se il valore è racchiuso tra virgolette.  
  
 Nella tabella seguente vengono descritte le parole chiave che possono essere utilizzate con DBPROP_INIT_PROVIDERSTRING.  
  
|Parola chiave|Proprietà di inizializzazione|Description|  
|-------------|-----------------------------|-----------------|  
|**Addr**|SSPROP_INIT_NETWORKADDRESS|Sinonimo di "Address".|  
|**Indirizzo**|SSPROP_INIT_NETWORKADDRESS|Indirizzo di rete del server che esegue un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **Indirizzo** è in genere il nome di rete del server, ma può corrispondere ad altri nomi, ad esempio una pipe, un indirizzo IP o un indirizzo socket e delle porte TCP/IP.<br /><br /> Se si specifica un indirizzo IP, assicurarsi che i protocolli TCP/IP o Named Pipes siano abilitati in Gestione configurazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Il valore di **indirizzo** ha la precedenza sul valore passato a **Server** nelle stringhe di connessione quando si utilizza il Driver OLE DB per SQL Server. Si noti inoltre che `Address=;` si connetterà al server specificato nella **Server** (parola chiave), mentre `Address= ;, Address=.;`, `Address=localhost;`, e `Address=(local);` verrà stabilita una connessione al server locale.<br /><br /> La sintassi completa per la **indirizzo** (parola chiave) è il seguente:<br /><br /> [*protocollo ***:**]*indirizzo*[* *, * * * porta &#124;\pipe\pipename*]<br /><br /> *protocol* può essere **tcp** (TCP/IP), **lpc** (memoria condivisa) o **np** (named pipe). Per ulteriori informazioni sui protocolli, vedere [configurazione di protocolli Client](../../../database-engine/configure-windows/configure-client-protocols.md).<br /><br /> Se non si specifica *protocollo* né la **rete** (parola chiave) è specificato, il Driver OLE DB per SQL Server utilizzerà l'ordine dei protocolli specificato in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> *porta* è la porta a cui connettersi nel server specificato. Per impostazione predefinita, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene utilizzata la porta 1433.|   
|**APP**|SSPROP_INIT_APPNAME|Stringa che identifica l'applicazione.|  
|**ApplicationIntent**|SSPROP_INIT_APPLICATIONINTENT|Dichiara il tipo di carico di lavoro dell'applicazione in caso di connessione a un server. I valori possibili sono **ReadOnly** e **ReadWrite**.<br /><br /> Il valore predefinito è **ReadWrite**. Per altre informazioni sui Driver OLE DB per il supporto di SQL Server per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [Driver OLE DB per SQL Server il supporto per il ripristino di emergenza a disponibilità elevata](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**AttachDBFileName**|SSPROP_INIT_FILENAME|Nome del file primario, incluso il nome completo del percorso, di un database collegabile. Per utilizzare **AttachDBFileName**, è necessario specificare anche il nome del database con la parola chiave Database della stringa del provider. Se il database è stato collegato in precedenza, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non lo ricollega e utilizza il database collegato come impostazione predefinita per la connessione.|  
|**Conversione automatica**|SSPROP_INIT_AUTOTRANSLATE|Sinonimo di "AutoTranslate".|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Configura la conversione dei caratteri OEM/ANSI. I valori riconosciuti sono "yes" e "no".|  
|**Database**|DBPROP_INIT_CATALOG|Nome del database.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Specifica la modalità di gestione dei tipi di dati da utilizzare. I valori riconosciuti sono "0" per i tipi di dati del provider e "80" per i tipi di dati di SQL Server 2000.|  
|**Encrypt**|SSPROP_INIT_ENCRYPT|Specifica se i dati devono essere crittografati prima del relativo invio in rete. I valori possibili sono "yes" e "no". Il valore predefinito è "no".|  
|**FailoverPartner**|SSPROP_INIT_FAILOVERPARTNER|Nome del server di failover utilizzato per il mirroring del database.|  
|**FailoverPartnerSPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Nome SPN del partner di failover. Il valore predefinito è una stringa vuota. Una stringa vuota fa sì che il Driver OLE DB per SQL Server da utilizzare il valore predefinito, generato dal provider SPN.|  
|**Lingua**|SSPROPT_INIT_CURRENTLANGUAGE|Lingua di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**MarsConn**|SSPROP_INIT_MARSCONNECTION|Abilita o disabilita MARS (Multiple Active Result Sets) nella connessione se il server è [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva. I valori possibili sono "yes" e "no". Il valore predefinito è "no".|  
|**Net**|SSPROP_INIT_NETWORKLIBRARY|Sinonimo di "Network".|  
|**Network**|SSPROP_INIT_NETWORKLIBRARY|Libreria di rete utilizzata per stabilire una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.|  
|**Libreria di rete**|SSPROP_INIT_NETWORKLIBRARY|Sinonimo di "Network".|  
|**PacketSize**|SSPROP_INIT_PACKETSIZE|Dimensioni del pacchetto di rete. Il valore predefinito è 4096.|  
|**PersistSensitive**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accetta le stringhe "yes" e "no" come valori. Se impostata su "no", l'oggetto origine dati non è in grado di rendere persistenti le informazioni di autenticazione riservate|  
|**PWD**|DBPROP_AUTH_PASSWORD|Password di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Server**|DBPROP_INIT_DATASOURCE|Nome di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il valore deve corrispondere al nome di un server in rete, a un indirizzo IP o al nome di un alias di Gestione configurazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Se non viene specificato un nome, viene stabilita una connessione all'istanza predefinita nel computer locale.<br /><br /> Il **indirizzo** (parola chiave) esegue l'override di **Server** (parola chiave).<br /><br /> È possibile connettersi all'istanza predefinita nel server locale specificando uno dei valori seguenti:<br /><br /> **Server=;**<br /><br /> **Server=.;**<br /><br /> **Server=(local);**<br /><br /> **Server=(local);**<br /><br /> **Server=(localhost);**<br /><br /> **Server=(LocalDB)\\**  *NomeIstanza* **;**<br /><br /> Per ulteriori informazioni sul supporto del database locale, vedere [Driver OLE DB per SQL Server il supporto per LocalDB](../../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md).<br /><br /> Per specificare un'istanza denominata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], aggiungere  **\\ ***NomeIstanza*.<br /><br /> Quando si specifica alcun server, viene stabilita una connessione all'istanza predefinita nel computer locale.<br /><br /> Se si specifica un indirizzo IP, assicurarsi che il TCP/IP o i protocolli named pipe siano abilitati in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> La sintassi completa per la **Server** (parola chiave) è il seguente:<br /> <br /> **Server =**[*protocollo***:**] *Server*[**, * * * la porta*]<br /><br /> *protocol* può essere **tcp** (TCP/IP), **lpc** (memoria condivisa) o **np** (named pipe).<br /><br /> Nell'esempio seguente si illustra come specificare una named pipe:<br /><br /> `np:\\.\pipe\MSSQL$MYINST01\sql\query`<br /><br /> Questa riga specifica un protocollo Named Pipes, una named pipe nel computer locale (`\\.\pipe`), il nome dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (`MSSQL$MYINST01`) e il nome predefinito della named pipe (`sql/query`).<br /><br /> Se non si specifica un *protocollo* né la **rete** (parola chiave) è specificato, il Driver OLE DB per SQL Server utilizzerà l'ordine dei protocolli specificato in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> *porta* è la porta a cui connettersi nel server specificato. Per impostazione predefinita, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene utilizzata la porta 1433.<br /><br /> Gli spazi vengono ignorati all'inizio del valore passato a **Server** nelle stringhe di connessione quando si utilizza il Driver OLE DB per SQL Server.|   
|**ServerSPN**|SSPROP_INIT_SERVERSPN|Nome SPN del server. Il valore predefinito è una stringa vuota. Una stringa vuota fa sì che il Driver OLE DB per SQL Server da utilizzare il valore predefinito, generato dal provider SPN.|  
|**Timeout**|DBPROP_INIT_TIMEOUT|Tempo di attesa in secondi per il completamento dell'inizializzazione dell'origine dati.|  
|**Trusted_Connection**|DBPROP_AUTH_INTEGRATED|Quando "yes", indica al Driver OLE DB per SQL Server per utilizzare l'autenticazione di Windows per la convalida dell'account di accesso. In caso contrario, indica il Driver OLE DB per SQL Server da usare un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è necessario specificare nome utente e password per la convalida dell'accesso e le parole chiave UID e PWD.|  
|**TrustServerCertificate**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accetta le stringhe "yes" e "no" come valori. Il valore predefinito è "no", il quale indica che il certificato server verrà convalidato.|  
|**UID**|DBPROP_AUTH_USERID|Nome dell'account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**UseProcForPrepare**|SSPROP_INIT_USEPROCFORPREP|Questa parola chiave è deprecata e relativa impostazione viene ignorata dal Driver OLE DB per SQL Server.|  
|**WSID**|SSPROP_INIT_WSID|Identificatore della workstation.|  
  
 Stringhe di connessione utilizzate nelle applicazioni OLE DB utilizzando **IDataInitialize:: GetDatasource** presentano la sintassi seguente:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[quote]attribute-value[quote]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 `quote ::= " | '`  
  
 L'utilizzo delle proprietà deve essere conforme alla sintassi consentita nel relativo ambito.  Ad esempio, **WSID** utilizzate le parentesi graffe (**{}**) virgolette e **nome applicazione** vengono utilizzate (**'**) o doppie (**"**) virgolette. Solo per le proprietà delle stringhe è possibile utilizzare le virgolette. Se si tenta di utilizzare le virgolette con una proprietà Integer o enumerata, verrà generato un errore che indica che la stringa di connessione non è conforme alla specifica OLE DB.  
  
 È consigliabile racchiudere i valori di attributo tra virgolette semplici o doppie per evitare i problemi determinati dalla presenza di caratteri non alfanumerici nei valori. Se raddoppiato, il carattere virgoletta può essere visualizzato anche per i valori.  
  
 Uno spazio dopo il segno = in una parola chiave di una stringa di connessione verrà interpretato come valore letterale, anche se il valore è racchiuso tra virgolette.  
  
 Se una stringa di connessione include più di una delle proprietà elencate nella tabella seguente, verrà utilizzato il valore dell'ultima proprietà.  
  
 Nella tabella seguente vengono descritte le parole chiave che possono essere utilizzate con **IDataInitialize:: GetDatasource**:  
  
|Parola chiave|Proprietà di inizializzazione|Description|  
|-------------|-----------------------------|-----------------|  
|**Application Name**|SSPROP_INIT_APPNAME|Stringa che identifica l'applicazione.|  
|**Finalità dell'applicazione**|SSPROP_INIT_APPLICATIONINTENT|Dichiara il tipo di carico di lavoro dell'applicazione in caso di connessione a un server. I valori possibili sono **ReadOnly** e **ReadWrite**.<br /><br /> Il valore predefinito è **ReadWrite**. Per altre informazioni sui Driver OLE DB per il supporto di SQL Server per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [Driver OLE DB per SQL Server il supporto per il ripristino di emergenza a disponibilità elevata](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Conversione automatica**|SSPROP_INIT_AUTOTRANSLATE|Sinonimo di "AutoTranslate".|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Configura la conversione dei caratteri OEM/ANSI. I valori riconosciuti sono "true" e "false".|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|Tempo di attesa in secondi per il completamento dell'inizializzazione dell'origine dati.|  
|**Lingua corrente**|SSPROPT_INIT_CURRENTLANGUAGE|Nome della lingua di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Data Source**|DBPROP_INIT_DATASOURCE|Nome di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Se non viene specificato un nome, viene stabilita una connessione all'istanza predefinita nel computer locale.<br /><br /> Per ulteriori informazioni sulla sintassi per gli indirizzi validi, vedere la descrizione del **Server** (parola chiave), in questo argomento.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Specifica la modalità di gestione dei tipi di dati da utilizzare. I valori riconosciuti sono "0" per i tipi di dati del provider e "80" per i tipi di dati di [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)].|  
|**Partner di failover**|SSPROP_INIT_FAILOVERPARTNER|Nome del server di failover utilizzato per il mirroring del database.|  
|**Partner di failover SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Nome SPN del partner di failover. Il valore predefinito è una stringa vuota. Una stringa vuota fa sì che il Driver OLE DB per SQL Server da utilizzare il valore predefinito, generato dal provider SPN.|  
|**Catalogo iniziale**|DBPROP_INIT_CATALOG|Nome del database.|  
|**Nome File iniziale**|SSPROP_INIT_FILENAME|Nome del file primario, incluso il nome completo del percorso, di un database collegabile. Per utilizzare **AttachDBFileName**, è necessario specificare anche il nome del database con la parola chiave DATABASE della stringa del provider. Se il database è stato collegato in precedenza, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non lo ricollega e utilizza il database collegato come impostazione predefinita per la connessione.|  
|**Sicurezza integrata**|DBPROP_AUTH_INTEGRATED|Accetta il valore "SSPI" per l'autenticazione di Windows.|  
|**Connessione MARS**|SSPROP_INIT_MARSCONNECTION|Abilita o disabilita MARS (Multiple Active Result Sets) nella connessione. I valori riconosciuti sono "true" e "false". Il valore predefinito è "false".|  
|**Indirizzo di rete**|SSPROP_INIT_NETWORKADDRESS|Indirizzo di rete di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Per ulteriori informazioni sulla sintassi per gli indirizzi validi, vedere la descrizione del **indirizzo** (parola chiave), in questo argomento.|  
|**Libreria di rete**|SSPROP_INIT_NETWORKLIBRARY|Libreria di rete utilizzata per stabilire una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|Dimensioni del pacchetto di rete. Il valore predefinito è 4096.|  
|**Password**|DBPROP_AUTH_PASSWORD|Password di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accetta le stringhe "true" e "false" come valori. Se il valore è impostato su "false", l'oggetto origine dati non è in grado di rendere persistenti le informazioni di autenticazione riservate|  
|**Provider**||Per Driver OLE DB per SQL Server, deve essere "MSOLEDBSQL".|  
|**SPN server**|SSPROP_INIT_SERVERSPN|Nome SPN del server. Il valore predefinito è una stringa vuota. Una stringa vuota fa sì che il Driver OLE DB per SQL Server da utilizzare il valore predefinito, generato dal provider SPN.|  
|**TrustServerCertificate**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accetta le stringhe "true" e "false" come valori. Il valore predefinito è "false", il quale indica che il certificato server verrà convalidato.|  
|**Use Encryption for Data**|SSPROP_INIT_ENCRYPT|Specifica se i dati devono essere crittografati prima del relativo invio in rete. I valori possibili sono "true" e "false". Il valore predefinito è "false".|  
|**ID utente**|DBPROP_AUTH_USERID|Nome dell'account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**ID workstation**|SSPROP_INIT_WSID|Identificatore della workstation.|  
  
 **Nota** nella stringa di connessione, la proprietà "Vecchia Password" imposta SSPROP_AUTH_OLD_PASSWORD, ovvero la password corrente (probabilmente scaduta) che non è disponibile tramite una proprietà di stringa del provider.  
  
## <a name="activex-data-objects-ado-connection-string-keywords"></a>Parole chiave delle stringhe di connessione per gli oggetti ADO (ActiveX Data Objects)  
 Applicazioni ADO impostano la **ConnectionString** proprietà di **ADODBConnection** oggetti o fornire una stringa di connessione come parametro per il **aprire** metodo **ADODBConnection** oggetti.  
  
 Applicazioni ADO possono inoltre utilizzare le parole chiave utilizzate da OLE DB **IDBInitialize:: Initialize** (metodo), ma solo per le proprietà che non contengono un valore predefinito. Se un'applicazione utilizza entrambe le parole chiave ADO e **IDBInitialize:: Initialize** parole chiave nella stringa di inizializzazione, l'impostazione della parola chiave ADO verranno utilizzate. Nelle applicazioni è consigliabile utilizzare solo le parole chiave delle stringhe di connessione ADO.  
  
 Le stringhe di connessione utilizzate da ADO presentano la sintassi seguente:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=["]attribute-value["]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 È consigliabile racchiudere i valori di attributo tra virgolette doppie per evitare i problemi determinati dalla presenza di caratteri non alfanumerici nei valori. I valori attributo non possono contenere virgolette doppie.  
  
 Nella tabella seguente vengono descritte le parole chiave che possono essere utilizzate con una stringa di connessione ADO:  
  
|Parola chiave|Proprietà di inizializzazione|Description|  
|-------------|-----------------------------|-----------------|  
|**Finalità dell'applicazione**|SSPROP_INIT_APPLICATIONINTENT|Dichiara il tipo di carico di lavoro dell'applicazione in caso di connessione a un server. I valori possibili sono **ReadOnly** e **ReadWrite**.<br /><br /> Il valore predefinito è **ReadWrite**. Per altre informazioni sui Driver OLE DB per il supporto di SQL Server per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [Driver OLE DB per SQL Server il supporto per il ripristino di emergenza a disponibilità elevata](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Application Name**|SSPROP_INIT_APPNAME|Stringa che identifica l'applicazione.|  
|**Conversione automatica**|SSPROP_INIT_AUTOTRANSLATE|Sinonimo di "AutoTranslate".|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Configura la conversione dei caratteri OEM/ANSI. I valori riconosciuti sono "true" e "false".|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|Tempo di attesa in secondi per il completamento dell'inizializzazione dell'origine dati.|  
|**Lingua corrente**|SSPROPT_INIT_CURRENTLANGUAGE|Nome della lingua di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Data Source**|DBPROP_INIT_DATASOURCE|Nome di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Se non viene specificato un nome, viene stabilita una connessione all'istanza predefinita nel computer locale.<br /><br /> Per ulteriori informazioni sulla sintassi per gli indirizzi validi, vedere la descrizione del **Server** (parola chiave), in questo argomento.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Specifica la modalità di gestione dei tipi di dati che verrà utilizzata. I valori riconosciuti sono "0" per i tipi di dati del provider e "80" per i tipi di dati di SQL Server 2000.|  
|**Partner di failover**|SSPROP_INIT_FAILOVERPARTNER|Nome del server di failover utilizzato per il mirroring del database.|  
|**Partner di failover SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Nome SPN del partner di failover. Il valore predefinito è una stringa vuota. Una stringa vuota fa sì che il Driver OLE DB per SQL Server da utilizzare il valore predefinito, generato dal provider SPN.|  
|**Catalogo iniziale**|DBPROP_INIT_CATALOG|Nome del database.|  
|**Nome File iniziale**|SSPROP_INIT_FILENAME|Nome del file primario, incluso il nome completo del percorso, di un database collegabile. Per utilizzare **AttachDBFileName**, è necessario specificare anche il nome del database con la parola chiave DATABASE della stringa del provider. Se il database è stato collegato in precedenza, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non lo ricollega e utilizza il database collegato come impostazione predefinita per la connessione.|  
|**Sicurezza integrata**|DBPROP_AUTH_INTEGRATED|Accetta il valore "SSPI" per l'autenticazione di Windows.|  
|**Connessione MARS**|SSPROP_INIT_MARSCONNECTION|Abilita o disabilita MARS (Multiple Active Result Sets) nella connessione se il server è [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva. I valori riconosciuti sono "true" e "false". Il valore predefinito è "false".|  
|**Indirizzo di rete**|SSPROP_INIT_NETWORKADDRESS|Indirizzo di rete di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Per ulteriori informazioni sulla sintassi per gli indirizzi validi, vedere la descrizione del **indirizzo** (parola chiave), in questo argomento.|  
|**Libreria di rete**|SSPROP_INIT_NETWORKLIBRARY|Libreria di rete utilizzata per stabilire una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|Dimensioni del pacchetto di rete. Il valore predefinito è 4096.|  
|**Password**|DBPROP_AUTH_PASSWORD|Password di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accetta le stringhe "true" e "false" come valori. Se il valore è impostato su "false", l'oggetto origine dati non è in grado di rendere persistenti le informazioni di autenticazione riservate.|  
|**Provider**||Per Driver OLE DB per SQL Server, deve essere "MSOLEDBSQL".|  
|**SPN server**|SSPROP_INIT_SERVERSPN|Nome SPN del server. Il valore predefinito è una stringa vuota. Una stringa vuota fa sì che il Driver OLE DB per SQL Server da utilizzare il valore predefinito, generato dal provider SPN.|  
|**TrustServerCertificate**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accetta le stringhe "true" e "false" come valori. Il valore predefinito è "false", il quale indica che il certificato server verrà convalidato.|  
|**Use Encryption for Data**|SSPROP_INIT_ENCRYPT|Specifica se i dati devono essere crittografati prima del relativo invio in rete. I valori possibili sono "true" e "false". Il valore predefinito è "false".|  
|**ID utente**|DBPROP_AUTH_USERID|Nome dell'account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**ID workstation**|SSPROP_INIT_WSID|Identificatore della workstation.|  
  
 **Nota** nella stringa di connessione, la proprietà "Vecchia Password" imposta SSPROP_AUTH_OLD_PASSWORD, ovvero la password corrente (probabilmente scaduta) che non è disponibile tramite una proprietà di stringa del provider.  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni con il Driver OLE DB per SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
