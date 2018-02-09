---
title: Provider Microsoft OLE DB per Microsoft Active Directory Service | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ADSI provider [ADO]
- Active Directory Service Interfaces provider [ADO]
- providers [ADO], OLE DB provider for Active Directory service
- OLE DB provider for Active Directory service [ADO]
ms.assetid: f9e81452-5675-4cfc-9949-cfbd2fe57534
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3824623cb28c6902b4a96542f149e537df41cb5d
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="microsoft-ole-db-provider-for-microsoft-active-directory-service"></a>Provider Microsoft OLE DB per Microsoft Active Directory Service
Il Provider di Active Directory Service Interfaces (ADSI) consente di ADO per connettersi a servizi di directory eterogenei tramite ADSI. In questo modo le applicazioni ADO accesso in sola lettura per i servizi directory Microsoft Windows NT 4.0 e Microsoft Windows 2000, oltre a qualsiasi servizio di directory compatibile con LDAP e Novell Directory Services. ADSI è basato su un modello di provider, in modo che se è presente un nuovo provider che fornisce l'accesso a un'altra directory, l'applicazione ADO sarà in grado di accedervi. Il provider ADSI è a thread libero e abilitato per Unicode.  
  
## <a name="connection-string-parameters"></a>Parametri di stringa di connessione  
 Per connettersi a questo provider, impostare il **Provider** argomento del [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) proprietà per le operazioni seguenti:  
  
```  
ADSDSOObject  
```  
  
 Lettura di [Provider](../../../ado/reference/ado-api/provider-property-ado.md) restituirà anche questa stringa.  
  
## <a name="typical-connection-string"></a>Stringa di connessione tipica  
 Una stringa di connessione tipica per questo provider è il seguente:  
  
```  
"Provider=ADSDSOObject;User ID=MyUserID;Password=MyPassword;"  
```  
  
 La stringa è costituita da parole chiave seguenti.  
  
|Parola chiave|Description|  
|-------------|-----------------|  
|**Provider**|Specifica il Provider OLE DB per il servizio Active Directory.|  
|**ID utente**|Specifica il nome utente. Se questa parola chiave viene omesso, viene utilizzato l'account di accesso corrente.|  
|**Password**|Specifica la password dell'utente. Se si omette questa parola chiave. Viene quindi utilizzato l'account di accesso corrente.|  
  
> [!NOTE]
>  Se ci si connette a un provider dell'origine dati che supporta l'autenticazione di Windows, è necessario specificare **Trusted_Connection = yes** o **Integrated Security = SSPI** anziché l'ID utente e password informazioni nella stringa di connessione.  
  
## <a name="command-text"></a>Testo comando  
 Una stringa di testo del comando in quattro parti è riconosciuta dal provider nella sintassi seguente:  
  
```  
"Root; Filter; Attributes[; Scope]"  
```  
  
|Valore|Description|  
|-----------|-----------------|  
|*Root*|Indica il **ADsPath** oggetto da cui iniziare la ricerca (ovvero, la radice della ricerca).|  
|*Filtra*|Indica il filtro di ricerca nel formato RFC 1960.|  
|*Attributi*|Indica un elenco delimitato da virgole di attributi da restituire.|  
|*Ambito*|Facoltativa. Oggetto **stringa** che specifica l'ambito della ricerca. I possibili valori sono i seguenti:<br /><br /> -Base, Eseguire la ricerca solo l'oggetto di base (radice della ricerca).<br />-OneLevel: La ricerca solo un livello.<br />-Sottoalbero, Eseguire la ricerca del sottoalbero intero.|  
  
 Esempio:  
  
```  
"<LDAP://DC=ArcadiaBay,DC=COM>;(objectClass=*);sn, givenName; subtree"  
```  
  
 Il provider supporta anche SQL SELECT per il testo del comando. Esempio:  
  
```  
"SELECT title, telephoneNumber From 'LDAP://DC=Microsoft, DC=COM' WHERE   
objectClass='user' AND objectCategory='Person'"  
```  
  
## <a name="remarks"></a>Osservazioni  
 Il provider non accetta chiamate di stored procedure o i nomi di tabella semplice (ad esempio, il [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) proprietà sarà sempre **adCmdText**). Vedere la documentazione di Active Directory Service Interfaces per una descrizione più completa degli elementi di testo di comando.  
  
## <a name="recordset-behavior"></a>Comportamento di recordset  
 Le tabelle seguenti elencano le funzionalità disponibili in un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto aperto tramite questo provider. Solo il tipo di cursore statico (**adOpenStatic**) è disponibile.  
  
 Per ulteriori informazioni su **Recordset** comportamento per la configurazione di provider, eseguire il [supporta](../../../ado/reference/ado-api/supports-method.md) metodo ed enumerare il [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme il  **Recordset** per determinare se sono presenti proprietà dinamiche specifiche del provider.  
  
 **Disponibilità di proprietà Recordset ADO standard:**  
  
|Proprietà|Disponibilità|  
|--------------|------------------|  
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|lettura/scrittura|  
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|lettura/scrittura|  
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|Sola lettura|  
|[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|Sola lettura|  
|[Bookmark](../../../ado/reference/ado-api/bookmark-property-ado.md)|lettura/scrittura|  
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|lettura/scrittura|  
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|always **adUseServer**|  
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|sempre **adOpenStatic**|  
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|sempre **adEditNone**|  
|[EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|Sola lettura|  
|[Filtra](../../../ado/reference/ado-api/filter-property.md)|lettura/scrittura|  
|[Tipo di blocco](../../../ado/reference/ado-api/locktype-property-ado.md)|lettura/scrittura|  
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|non disponibile|  
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|lettura/scrittura|  
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|Sola lettura|  
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|lettura/scrittura|  
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|Sola lettura|  
|[Origine](../../../ado/reference/ado-api/source-property-ado-recordset.md)|lettura/scrittura|  
|[State](../../../ado/reference/ado-api/state-property-ado.md)|Sola lettura|  
|[Stato](../../../ado/reference/ado-api/status-property-ado-recordset.md)|Sola lettura|  
  
 **Disponibilità dei metodi di Recordset ADO standard:**  
  
|Metodo|Disponibile?|  
|------------|----------------|  
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|no|  
|[Annulla](../../../ado/reference/ado-api/cancel-method-ado.md)|no|  
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|no|  
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|no|  
|[Clone](../../../ado/reference/ado-api/clone-method-ado.md)|Sì|  
|[Chiudi](../../../ado/reference/ado-api/close-method-ado.md)|Sì|  
|[Elimina](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|no|  
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|Sì|  
|[Sposta](../../../ado/reference/ado-api/move-method-ado.md)|Sì|  
|[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Sì|  
|[MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Sì|  
|[Metodo MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Sì|  
|[MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Sì|  
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|Sì|  
|[Apertura](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Sì|  
|[Requery](../../../ado/reference/ado-api/requery-method.md)|Sì|  
|[Risincronizzazione](../../../ado/reference/ado-api/resync-method.md)|Sì|  
|[Supporti](../../../ado/reference/ado-api/supports-method.md)|Sì|  
|[Update](../../../ado/reference/ado-api/update-method.md)|no|  
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|no|  
  
 Per ulteriori informazioni su ADSI e le specifiche del provider, consultare la documentazione di Active Directory Service Interfaces o visitare la pagina Web ADSI.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà CommandType (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md)   
 [Proprietà ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md)   
 [Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Proprietà del provider (ADO)](../../../ado/reference/ado-api/provider-property-ado.md)   
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Metodo Supports](../../../ado/reference/ado-api/supports-method.md)
