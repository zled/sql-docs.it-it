---
title: Nomi dell'entità servizio (SPN) nelle connessioni Client (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: e212010e-a5b6-4ad1-a3c0-575327d3ffd3
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 74bd1f2482825fa2a8115df018d8a86b8f34845f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37409670"
---
# <a name="service-principal-names-spns-in-client-connections-ole-db"></a>Nomi SPN (Service Principal Name) nelle connessioni client (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  In questo argomento vengono descritte le funzioni membro e le proprietà OLE DB che supportano i nomi SPN (Service Principal Name) nelle applicazioni client. Per altre informazioni sui nomi SPN nelle applicazioni client, vedere [nome dell'entità servizio &#40;SPN&#41; supporto nelle connessioni Client](../../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md). Per un esempio, vedere [l'autenticazione integrata di Kerberos &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-how-to/integrated-kerberos-authentication-ole-db.md).  
  
## <a name="provider-initialization-string-keywords"></a>Parole chiave della stringa di inizializzazione del provider  
 Le seguenti parole chiave della stringa di inizializzazione del provider supportano i nomi SPN nelle applicazioni OLE DB. Nella tabella seguente, i valori nella colonna (parola chiave) vengono utilizzati per la stringa del provider di IDBInitialize:: Initialize. Quando ci si connette tramite ADO o IDataInitialize:: GetDatasource, nelle stringhe di inizializzazione vengono utilizzati i valori nella colonna Descrizione.  
  
|Parola chiave|Description|valore|  
|-------------|-----------------|-----------|  
|ServerSPN|SPN server|Nome SPN del server. Il valore predefinito è una stringa vuota, che in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client causa l'utilizzo del nome SPN predefinito generato dal provider.|  
|FailoverPartnerSPN|Nome SPN del partner di failover|Nome SPN del partner di failover. Il valore predefinito è una stringa vuota, che in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client causa l'utilizzo del nome SPN predefinito generato dal provider.|  
  
## <a name="data-source-initialization-properties"></a>Proprietà di inizializzazione dell'origine dati  
 Le proprietà seguenti nella **DBPROPSET_SQLSERVERDBINIT** set di proprietà consentono alle applicazioni di specificare i nomi SPN.  
  
|nome|Tipo|Utilizzo|  
|----------|----------|-----------|  
|SSPROP_INIT_SERVERSPN|VT_BSTR, lettura/scrittura|Specifica il nome SPN per il server. Il valore predefinito è una stringa vuota, che in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client causa l'utilizzo del nome SPN predefinito generato dal provider.|  
|SSPROP_INIT_FAILOVERPARTNERSPN|VT_BSTR, lettura/scrittura|Specifica il nome SPN per il partner di failover. Il valore predefinito è una stringa vuota, che in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client causa l'utilizzo del nome SPN predefinito generato dal provider.|  
  
## <a name="data-source-properties"></a>Proprietà dell'origine dati  
 Le proprietà seguenti nella **DBPROPSET_SQLSERVERDATASOURCEINFO** set di proprietà consentono alle applicazioni di individuare il metodo di autenticazione.  
  
|nome|Tipo|Utilizzo|  
|----------|----------|-----------|  
|SSPROP_INTEGRATEDAUTHENTICATIONMETHOD|VT_BSTR, sola lettura|Restituisce il metodo di autenticazione utilizzato per la connessione. Il valore restituito all'applicazione è il valore che Windows restituisce a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Di seguito sono indicati i valori possibili: <br />"NTLM", restituito quando una connessione viene aperta utilizzando l'autenticazione NTLM.<br />"Kerberos", restituito quando una connessione viene aperta utilizzando l'autenticazione Kerberos.<br /><br /> Se è stata aperta una connessione ed è impossibile determinare il metodo di autenticazione, viene restituito VT_EMPTY.<br /><br /> Questa proprietà può essere letta solo quando è stata inizializzata un'origine dati. IDBProperties::GetProperies restituirà DB_S_ERRORSOCCURRED o DB_E_ERRORSOCCURRED, a seconda se si prova a leggere la proprietà prima che sia stata inizializzata un'origine dati, e verrà impostato DBPROPSTATUS_NOTSUPPORTED in DBPROPSET_PROPERTIESINERROR per questa proprietà. Questo comportamento è conforme alla specifica OLE DB principale.|  
|SSPROP_MUTUALLYAUTHENICATED|VT_BOOL, sola lettura|Restituisce VARIANT_TRUE se nella connessione è stata eseguita un'autenticazione reciproca dei server. In caso contrario, restituisce VARIANT_FALSE.<br /><br /> Questa proprietà può essere letta solo quando è stata inizializzata un'origine dati. Se viene eseguito un tentativo di leggere la proprietà prima che sia stata inizializzata un'origine dati, IDBProperties::GetProperies restituirà DB_S_ERRORSOCCURRED o DB_E_ERRORSOCCURRED, a seconda e verrà impostato DBPROPSTATUS_NOTSUPPORTED in DBPROPSET_ PROPERTIESINERROR per questa proprietà. Questo comportamento è conforme alla specifica OLE DB principale<br /><br /> Se viene eseguita una query su questo attributo per una connessione in cui non è stata utilizzata l'autenticazione di Windows, viene restituito VARIANT_FALSE.|  
  
## <a name="ole-db-api-support-for-spns"></a>Supporto dell'API OLE DB per i nomi SPN  
 Nella tabella seguente vengono descritte le funzioni membro OLE DB che supportano i nomi SPN nelle connessioni client:  
  
|Funzione membro|Description|  
|---------------------|-----------------|  
|IDataInitialize::GetDataSource|*pwszInitializationString* può contenere le nuove parole chiave **ServerSPN** e **FailoverPartnerSPN**.|  
|IDataInitialize::GetInitializationString|Se SSPROP_INIT_SERVERSPN e SSPROP_INIT_FAILOVERPARTNERSPN dispongono di valori non predefiniti, verranno inclusi nella stringa di inizializzazione attraverso *ppwszInitString* come valori di parola chiave per **ServerSPN**e **FailoverPartnerSPN**. In caso contrario, queste parole chiave non saranno incluse nella stringa di inizializzazione.|  
|IDBInitialize::Initialize|Se la richiesta viene abilitata impostando DBPROP_INIT_PROMPT nelle proprietà di inizializzazione dell'origine dati, verrà visualizzata la finestra di dialogo di accesso OLE DB. Ciò consente di immettere i nomi SPN per il server principale e per il relativo partner di failover.<br /><br /> La stringa del provider in DPPROP_INIT_PROVIDERSTRING, se impostata, riconoscerà le nuove parole chiave **ServerSPN** e **FailoverPartnerSPN** e usare i relativi valori, se presente, per inizializzare SSPROP_INIT_SERVER_ Nome dell'entità servizio e SSPROP_INIT_FAILOVER_PARTNER_SPN.<br /><br /> IDBProperties:: SetProperties può essere chiamato per impostare le proprietà SSPROP_INIT_SERVER_SPN e SSPROP_INIT_FAILOVER_PARTNER_SPN prima che venga chiamato IDBInitialize:: Initialize. Si tratta di un'alternativa all'utilizzo di una stringa del provider.<br /><br /> Se una proprietà viene impostata in più posizioni, un valore impostato a livello di programmazione ha la precedenza su un valore impostato nella stringa del provider. Un valore impostato in una stringa di inizializzazione ha la precedenza su un valore impostato in una finestra di dialogo.<br /><br /> Se la stessa parola chiave viene visualizzata più volte nella stringa del provider, il valore della prima occorrenza avrà la precedenza.|  
|IDBProperties::GetProperties|IDBProperties:: GetProperties può essere chiamato per ottenere i valori delle nuove proprietà origine dati inizializzazione SSPROP_INIT_SERVERSPN e SSPROP_INIT_FAILOVERPARTNERSPN e delle nuove proprietà origine dati sprop_authenticationmethod e SSPROP_ MUTUALLYAUTHENTICATED.|  
|IDBProperties::GetPropertyInfo|IDBProperties:: GetPropertyInfo includerà la nuova origine proprietà di inizializzazione dati SSPROP_INIT_SERVERSPN e SSPROP_INIT_FAILOVERPARTNERSPN oppure le nuove proprietà di origine dati sprop_authenticationmethod e SSPROP_MUTUALLYAUTHENTICATED.|  
|IDBProperties::SetProperties|IDBProperties:: SetProperties può essere chiamato per impostare i valori della nuova origine dati SSPROP_INITSERVERSPN e SSPROP_INIT_FAILOVERPARTNERSPN le proprietà di inizializzazione.<br /><br /> È possibile impostare queste proprietà in qualsiasi momento; tuttavia, se l'origine dati è già aperta, verrà restituito il seguente errore: DB_E_ERRORSOCCURRED, "Si sono verificati errori in un'operazione OLE DB composta da più passaggi. Controllare i singoli valori di stato OLE DB, se disponibili. Nessuna operazione eseguita".|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
