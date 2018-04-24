---
title: Oggetto di connessione (ADO) | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection
helpviewer_keywords:
- Connection object [ADO]
ms.assetid: ef6b1824-5b12-43db-89d7-8f3d13896d4d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 1354a3037c81d8d439908faf74caefd426f78d58
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="connection-object-ado"></a>Oggetto di connessione (ADO.NET)
Rappresenta una connessione aperta a un'origine dati.  
  
## <a name="remarks"></a>Osservazioni  
 Oggetto **connessione** oggetto rappresenta una sessione univoca con un'origine dati. In un sistema di database client/server, può essere equivalente a una connessione di rete effettiva al server. A seconda della funzionalità supportata dal provider, alcuni insiemi, metodi o proprietà di un **connessione** oggetto potrebbe non essere disponibile.  
  
 Con le raccolte, i metodi e proprietà di un **connessione** dell'oggetto, è possibile eseguire le operazioni seguenti:  
  
-   Configurare la connessione prima di aprirlo con le [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md), [ConnectionTimeout](../../../ado/reference/ado-api/connectiontimeout-property-ado.md), e [modalità](../../../ado/reference/ado-api/mode-property-ado.md) proprietà. **ConnectionString** è la proprietà predefinita di **connessione** oggetto.  
  
-   Impostare il [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) proprietà client per richiamare il [servizio cursore per OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md), che supporta gli aggiornamenti in blocco.  
  
-   Impostare il database predefinito per la connessione con il [DefaultDatabase](../../../ado/reference/ado-api/defaultdatabase-property.md) proprietà.  
  
-   Impostare il livello di isolamento per le transazioni aperte nella connessione con il [IsolationLevel](../../../ado/reference/ado-api/isolationlevel-property.md) proprietà.  
  
-   Specificare un provider OLE DB con il [Provider](../../../ado/reference/ado-api/provider-property-ado.md) proprietà.  
  
-   Stabilire e, successivamente, interrompere la connessione fisica all'origine dati con il [aprire](../../../ado/reference/ado-api/open-method-ado-connection.md) e [Chiudi](../../../ado/reference/ado-api/close-method-ado.md) metodi.  
  
-   Eseguire un comando per la connessione con il [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) (metodo) e configurare l'esecuzione con il [CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md) proprietà.  
  
    > [!NOTE]
    >  Per eseguire una query senza utilizzare un oggetto comando, passare una stringa di query per il **Execute** metodo di un **connessione** oggetto. Tuttavia, un [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto sono obbligatorie quando si desidera mantenere il testo del comando ed eseguirla nuovamente o utilizzare i parametri di query.  
  
-   Gestire le transazioni per la connessione aperta, incluse le transazioni nidificate, se il provider supporta, con la [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md), [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md), e [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) metodi e [attributi](../../../ado/reference/ado-api/attributes-property-ado.md) proprietà.  
  
-   Esaminare gli errori restituiti dall'origine dati con il [errori](../../../ado/reference/ado-api/errors-collection-ado.md) insieme.  
  
-   Leggere la versione da utilizzare con l'implementazione di ADO la [versione](../../../ado/reference/ado-api/version-property-ado.md) proprietà.  
  
-   Ottenere informazioni sullo schema relative al database con il [OpenSchema](../../../ado/reference/ado-api/openschema-method.md) metodo.  
  
 È possibile creare **connessione** oggetti in modo indipendente da qualsiasi altro oggetto definito in precedenza.  
  
 È possibile eseguire comandi denominati o le stored procedure come se fossero metodi nativi in una **connessione** dell'oggetto, come illustrato nella sezione successiva. Quando un comando denominato ha lo stesso nome di una stored procedure, è possibile richiamare la chiamata di metodo nativo"" in un **connessione** oggetto eseguire sempre il comando denominato anziché la stored procedure.  
  
> [!NOTE]
>  Non utilizzare questa funzionalità (la chiamata di una stored procedure o un comando denominato come se fosse un metodo nativo sul **connessione** oggetto) in un'applicazione di Microsoft® .NET Framework, perché l'implementazione sottostante dei conflitti di funzionalità con la modalità di .NET Framework interagisce con COM.  
  
## <a name="execute-a-command-as-a-native-method-of-a-connection-object"></a>Eseguire un comando come metodo nativo di un oggetto di connessione  
 Per eseguire un comando, assegnargli un nome utilizzando il **comando** oggetto [nome](../../../ado/reference/ado-api/name-property-ado.md) proprietà. Impostare il **ActiveConnection** proprietà del **comando** oggetto per la connessione. Quindi eseguire un'istruzione in cui il nome del comando viene utilizzato come se fosse un metodo sul **connessione** oggetto, seguito da eventuali parametri e un **Recordset** se vengono restituite tutte le righe dell'oggetto. Impostare il **Recordset** le proprietà per personalizzare il valore risultante **Recordset**. Esempio:  
  
```  
Dim cnn As New ADODB.Connection  
Dim cmd As New ADODB.Command  
Dim rst As New ADODB.Recordset  
...  
cnn.Open "..."  
cmd.Name = "yourCommandName"  
cmd.ActiveConnection = cnn  
...  
'Your command name, any parameters, and an optional Recordset.  
cnn. "parameter", rst  
```  
  
## <a name="execute-a-stored-procedure-as-a-native-method-of-a-connection-object"></a>Eseguire una stored procedure come metodo nativo di un oggetto di connessione  
 Per eseguire una stored procedure, eseguire un'istruzione in cui il nome della stored procedure viene utilizzato come se fosse un metodo sul **connessione** oggetto, seguito da eventuali parametri. ADO consentirà una "stima" dei tipi di parametro. Esempio:  
  
```  
Dim cnn As New ADODB.Connection  
...  
'Your stored procedure name and any parameters.  
cnn. "parameter"  
```  
  
 Il **connessione** oggetto è sicuro per lo script.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Le proprietà dell'oggetto connessione, metodi ed eventi](../../../ado/reference/ado-api/connection-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Raccolta di errori (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Appendice A: Provider](../../../ado/guide/appendixes/appendix-a-providers.md)
