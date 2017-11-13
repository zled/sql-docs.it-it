---
title: Open (metodo) (connessione ADO) | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Connection15::raw_Open
- Connection15::Open
- _Connection::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: 663defab-5545-4973-9036-24d5882c9737
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c61284bb59c01e22ef4f2cb46664fe7d7f7bbd2f
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="open-method-ado-connection"></a>Open (metodo) (connessione ADO)
Apre una connessione a un'origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
connection.Open ConnectionString, UserID, Password, Options  
```  
  
#### <a name="parameters"></a>Parametri  
 *ConnectionString*  
 Facoltativa. Oggetto **stringa** valore che contiene informazioni di connessione. Vedere il [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) proprietà per informazioni dettagliate sulle impostazioni valide.  
  
 *ID utente*  
 Facoltativa. Oggetto **stringa** valore che contiene un nome utente da utilizzare per stabilire la connessione.  
  
 *Password*  
 Facoltativa. Oggetto **stringa** valore che contiene una password da utilizzare per stabilire la connessione.  
  
 *Opzioni*  
 Facoltativa. Oggetto [ConnectOptionEnum](../../../ado/reference/ado-api/connectoptionenum.md) valore che determina se questo metodo deve essere restituito dopo (in modo sincrono) o prima (in modo asincrono) in cui viene stabilita la connessione.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzando il **aprire** metodo su un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto stabilisce la connessione fisica a un'origine dati. Dopo il metodo viene completato correttamente, viene stabilita la connessione ed è possibile eseguire comandi su di esso e a elaborare i risultati.  
  
 Utilizzare l'opzione facoltativa *ConnectionString* argomento per specificare una stringa di connessione che contiene una serie di *argomento* *= valore* istruzioni separate da punti e virgola o un risorsa file o directory identificata da un URL. Il **ConnectionString** proprietà eredita automaticamente il valore utilizzato per il *ConnectionString* argomento. Pertanto, è possibile impostare il **ConnectionString** proprietà del **connessione** oggetto prima di aprirlo oppure utilizzare il *ConnectionString* argomento per impostare o eseguire l'override i parametri di connessione corrente durante il **aprire** chiamata al metodo.  
  
 Se si passa l'utente e password informazioni sia il *ConnectionString* argomento e nella facoltativa *UserID* e *Password* argomenti, il *UserID*  e *Password* argomenti sostituiranno i valori specificati in *ConnectionString*.  
  
 Quando si hanno concluso le operazioni attraverso un **connessione**, utilizzare il [Chiudi](../../../ado/reference/ado-api/close-method-ado.md) metodo per liberare le risorse di sistema associate. Chiusura di un oggetto senza rimuoverlo dalla memoria. è possibile modificare le impostazioni delle proprietà e utilizzare il **aprire** metodo aprirlo più tardi. Per eliminare completamente l'oggetto dalla memoria, impostare la variabile oggetto *nulla*.  
  
> [!NOTE]
>  **Utilizzo del servizio dati remoti** quando utilizzato sul lato client **connessione** oggetto, il **aprire** metodo non stabilisce una connessione al server fino a quando un [Recordset ](../../../ado/reference/ado-api/recordset-object-ado.md) viene aperta sul **connessione** oggetto.  
  
> [!NOTE]
>  Gli URL che utilizzano lo schema http richiamerà automaticamente il [il Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Per ulteriori informazioni, vedere [URL assoluti e relativi](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto di connessione (ADO.NET)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodi di apertura e chiusura (VB)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Esempio di metodi di apertura e chiusura (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Esempio di metodi di apertura e chiusura (VC + +)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Open (metodo) (Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open (metodo) (Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open (metodo) (flusso ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Metodo OpenSchema](../../../ado/reference/ado-api/openschema-method.md)

