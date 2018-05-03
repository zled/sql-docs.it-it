---
title: Nomi dell'entità servizio (SPN) nelle connessioni Client (OLE DB) | Documenti Microsoft
description: Nomi dell'entità servizio (SPN) nelle connessioni client (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 16414064b705920006a1b0542f4cf500d1db222b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="service-principal-names-spns-in-client-connections-ole-db"></a>Nomi SPN (Service Principal Name) nelle connessioni client (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]


  In questo argomento vengono descritte le funzioni membro e le proprietà OLE DB che supportano i nomi SPN (Service Principal Name) nelle applicazioni client. Per ulteriori informazioni sui nomi SPN nelle applicazioni client, vedere [nome dell'entità servizio &#40;SPN&#41; supporto nelle connessioni Client](../../oledb/features/service-principal-name-spn-support-in-client-connections.md). Per un esempio, vedere [l'autenticazione Kerberos integrata &#40;OLE DB&#41;](../../oledb/ole-db-how-to/integrated-kerberos-authentication-ole-db.md).  
  
## <a name="provider-initialization-string-keywords"></a>Parole chiave della stringa di inizializzazione del provider  
 Le seguenti parole chiave della stringa di inizializzazione del provider supportano i nomi SPN nelle applicazioni OLE DB. Nella tabella seguente, vengono utilizzati i valori nella colonna parola chiave per la stringa del provider di IDBInitialize:: Initialize. I valori nella colonna Descrizione vengono utilizzati nelle stringhe di inizializzazione durante la connessione ADO o IDataInitialize:: GetDatasource.  
  
|Parola chiave|Description|Value|  
|-------------|-----------------|-----------|  
|ServerSPN|SPN server|Nome SPN del server. Il valore predefinito è una stringa vuota, che fa sì che il Driver OLE DB per SQL Server da utilizzare il valore predefinito, generato dal provider SPN.|  
|FailoverPartnerSPN|Nome SPN del partner di failover|Nome SPN del partner di failover. Il valore predefinito è una stringa vuota, che fa sì che il Driver OLE DB per SQL Server da utilizzare il valore predefinito, generato dal provider SPN.|  
  
## <a name="data-source-initialization-properties"></a>Proprietà di inizializzazione dell'origine dati  
 Le seguenti proprietà per il **DBPROPSET_SQLSERVERDBINIT** set di proprietà consentono alle applicazioni di specificare i nomi SPN.  
  
|Nome|Tipo|Utilizzo|  
|----------|----------|-----------|  
|SSPROP_INIT_SERVERSPN|VT_BSTR, lettura/scrittura|Specifica il nome SPN per il server. Il valore predefinito è una stringa vuota, che fa sì che il Driver OLE DB per SQL Server da utilizzare il valore predefinito, generato dal provider SPN.|  
|SSPROP_INIT_FAILOVERPARTNERSPN|VT_BSTR, lettura/scrittura|Specifica il nome SPN per il partner di failover. Il valore predefinito è una stringa vuota, che fa sì che il Driver OLE DB per SQL Server da utilizzare il valore predefinito, generato dal provider SPN.|  
  
## <a name="data-source-properties"></a>Proprietà dell'origine dati  
 Le seguenti proprietà per il **DBPROPSET_SQLSERVERDATASOURCEINFO** set di proprietà consentono alle applicazioni di individuare il metodo di autenticazione.  
  
|Nome|Tipo|Utilizzo|  
|----------|----------|-----------|  
|SSPROP_INTEGRATEDAUTHENTICATIONMETHOD|VT_BSTR, sola lettura|Restituisce il metodo di autenticazione utilizzato per la connessione. Il valore restituito per l'applicazione è il valore restituito di Windows per il Driver OLE DB per SQL Server. Di seguito sono indicati i valori possibili: <br />"NTLM", restituito quando una connessione viene aperta utilizzando l'autenticazione NTLM.<br />"Kerberos", restituito quando una connessione viene aperta utilizzando l'autenticazione Kerberos.<br /><br /> Se è stata aperta una connessione ed è impossibile determinare il metodo di autenticazione, viene restituito VT_EMPTY.<br /><br /> Questa proprietà può essere letta solo quando è stata inizializzata un'origine dati. Se si tenta di leggere la proprietà prima di un'origine dati è stata inizializzata, IDBProperties::GetProperies restituirà DB_S_ERRORSOCCURRED o DB_E_ERRORSOCCURRED, come appropriato, e verrà impostato DBPROPSTATUS_NOTSUPPORTED in DBPROPSET_PROPERTIESINERROR per questa proprietà. Questo comportamento è conforme alla specifica OLE DB principale.|  
|SSPROP_MUTUALLYAUTHENICATED|VT_BOOL, sola lettura|Restituisce VARIANT_TRUE se nella connessione è stata eseguita un'autenticazione reciproca dei server. In caso contrario, restituisce VARIANT_FALSE.<br /><br /> Questa proprietà può essere letta solo quando è stata inizializzata un'origine dati. Se viene eseguito un tentativo di leggere la proprietà prima di un'origine dati è stata inizializzata, IDBProperties::GetProperies restituirà DB_S_ERRORSOCCURRED o DB_E_ERRORSOCCURRED, come appropriato, e verrà impostato DBPROPSTATUS_NOTSUPPORTED in DBPROPSET_ PROPERTIESINERROR per questa proprietà. Questo comportamento è conforme alla specifica OLE DB principale<br /><br /> Se viene eseguita una query su questo attributo per una connessione in cui non è stata utilizzata l'autenticazione di Windows, viene restituito VARIANT_FALSE.|  
  
## <a name="ole-db-api-support-for-spns"></a>Supporto dell'API OLE DB per i nomi SPN  
 Nella tabella seguente vengono descritte le funzioni membro OLE DB che supportano i nomi SPN nelle connessioni client:  
  
|Funzione membro|Description|  
|---------------------|-----------------|  
|IDataInitialize::GetDataSource|*pwszInitializationString* può contenere le nuove parole chiave **ServerSPN** e **FailoverPartnerSPN**.|  
|IDataInitialize::GetInitializationString|Se SSPROP_INIT_SERVERSPN e SSPROP_INIT_FAILOVERPARTNERSPN dispongono di valori non predefiniti, verranno inclusi nella stringa di inizializzazione tramite *ppwszInitString* come valori di parola chiave per **ServerSPN**e **FailoverPartnerSPN**. In caso contrario, queste parole chiave non saranno incluse nella stringa di inizializzazione.|  
|IDBInitialize::Initialize|Se la richiesta viene abilitata impostando DBPROP_INIT_PROMPT nelle proprietà di inizializzazione dell'origine dati, verrà visualizzata la finestra di dialogo di accesso OLE DB. Ciò consente di immettere i nomi SPN per il server principale e per il relativo partner di failover.<br /><br /> La stringa del provider in DPPROP_INIT_PROVIDERSTRING, se impostata, riconoscerà le nuove parole chiave **ServerSPN** e **FailoverPartnerSPN** e utilizzare i relativi valori, se presente, per inizializzare SSPROP_INIT_SERVER_ Nome SPN e SSPROP_INIT_FAILOVER_PARTNER_SPN.<br /><br /> IDBProperties:: SetProperties può essere chiamato per impostare le proprietà SSPROP_INIT_SERVER_SPN e SSPROP_INIT_FAILOVER_PARTNER_SPN prima che venga chiamato IDBInitialize:: Initialize. Si tratta di un'alternativa all'utilizzo di una stringa del provider.<br /><br /> Se una proprietà viene impostata in più posizioni, un valore impostato a livello di programmazione ha la precedenza su un valore impostato nella stringa del provider. Un valore impostato in una stringa di inizializzazione ha la precedenza su un valore impostato in una finestra di dialogo.<br /><br /> Se la stessa parola chiave viene visualizzata più volte nella stringa del provider, il valore della prima occorrenza avrà la precedenza.|  
|IDBProperties::GetProperties|IDBProperties::GetProperties può essere chiamato per ottenere i valori delle nuove proprietà origine dati inizializzazione SSPROP_INIT_SERVERSPN e SSPROP_INIT_FAILOVERPARTNERSPN e delle nuove proprietà origine dati sprop_authenticationmethod e SSPROP_ MUTUALLYAUTHENTICATED.|  
|IDBProperties::GetPropertyInfo|IDBProperties:: GetPropertyInfo includerà le nuove proprietà origine dati inizializzazione SSPROP_INIT_SERVERSPN e SSPROP_INIT_FAILOVERPARTNERSPN oppure le nuove proprietà di origine dati sprop_authenticationmethod e SSPROP_MUTUALLYAUTHENTICATED.|  
|IDBProperties::SetProperties|Per impostare i valori di una nuova origine dati SSPROP_INITSERVERSPN e SSPROP_INIT_FAILOVERPARTNERSPN le proprietà di inizializzazione può essere chiamato IDBProperties:: SetProperties.<br /><br /> È possibile impostare queste proprietà in qualsiasi momento; tuttavia, se l'origine dati è già aperta, verrà restituito il seguente errore: DB_E_ERRORSOCCURRED, "Si sono verificati errori in un'operazione OLE DB composta da più passaggi. Controllare i singoli valori di stato OLE DB, se disponibili. Nessuna operazione eseguita".|  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per programmazione con SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
