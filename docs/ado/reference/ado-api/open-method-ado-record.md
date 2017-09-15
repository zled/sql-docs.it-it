---
title: Open (metodo) (Record ADO) | Documenti Microsoft
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
- _Record::raw_Open
- _Record::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: ab79a623-88a9-40b6-a017-a658bf19b778
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c7e7f1c5e35ced700818954056b380a44c75570c
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="open-method-ado-record"></a>Open (metodo) (Record ADO)
Apre un oggetto esistente [Record](../../../ado/reference/ado-api/record-object-ado.md) oggetto oppure crea un nuovo elemento rappresentato dal **Record**, ad esempio un file o directory.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Open Source, ActiveConnection, Mode, CreateOptions, Options, UserName, Password  
```  
  
#### <a name="parameters"></a>Parametri  
 *Origine*  
 Facoltativa. Oggetto **Variant** che può rappresentare l'URL dell'entità per essere rappresentato da questo **Record** oggetto, un **comando**, open [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) o un altro **Record** oggetto, una stringa che contiene un'istruzione SQL SELECT o un nome di tabella.  
  
 *ActiveConnection*  
 Facoltativa. Oggetto **Variant** che rappresenta la stringa di connessione o aprire [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto.  
  
 *Mode*  
 Facoltativa. Oggetto [ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md) valore che specifica la modalità di accesso per i risultanti **Record** oggetto. Valore predefinito è **adModeUnknown**.  
  
 *CreateOptions*  
 Facoltativa. Oggetto [RecordCreateOptionsEnum](../../../ado/reference/ado-api/recordcreateoptionsenum.md) valore che specifica se deve essere aperto un file o directory esistente o se deve essere creata un nuovo file o directory. Valore predefinito è **adFailIfNotExists**. Se impostata sul valore predefinito, la modalità di accesso viene ottenuta dal [modalità](../../../ado/reference/ado-api/mode-property-ado.md) proprietà. Questo parametro viene ignorato quando il *origine* parametro non contiene un URL.  
  
 *Opzioni*  
 Facoltativa. Oggetto [RecordOpenOptionsEnum](../../../ado/reference/ado-api/recordopenoptionsenum.md) valore che specifica le opzioni per l'apertura di **Record**. Valore predefinito è **adOpenRecordUnspecified dell'oggetto**. Questi valori possono essere combinati.  
  
 *UserName*  
 Facoltativa. Oggetto **stringa** valore che contiene l'ID utente, se necessario, si autorizza l'accesso a *origine*.  
  
 *Password*  
 Facoltativa. Oggetto **stringa** valore contenente la password che, se necessario, verifica *UserName*.  
  
## <a name="remarks"></a>Osservazioni  
 *Origine* potrebbe essere:  
  
-   UN URL. Se il protocollo per l'URL è http, il Provider Internet verrà richiamato per impostazione predefinita. Se l'URL punta a un nodo che contiene uno script eseguibile (ad esempio un. La pagina ASP), un **Record** contenente l'origine anziché eseguito contenuto viene aperto per impostazione predefinita. Utilizzare il *opzioni* argomento per modificare questo comportamento.  
  
-   Oggetto **Record** oggetto. Oggetto **Record** oggetto aperto da un altro **Record** verrà clonare originale **Record** oggetto.  
  
-   Oggetto **comando** oggetto. L'apertura **Record** oggetto rappresenta la riga singola restituita eseguendo il **comando**. Se i risultati contengono più di una singola riga, il contenuto della prima riga viene inserito nel record e può essere aggiunto un errore per il **errori** insieme.  
  
-   Un'istruzione SQL SELECT. L'apertura **Record** oggetto rappresenta la riga singola restituita eseguendo il contenuto della stringa. Se i risultati contengono più di una singola riga, il contenuto della prima riga viene inserito nel record e può essere aggiunto un errore per il **errori** insieme.  
  
-   Un nome di tabella.  
  
 Se il **Record** oggetto rappresenta un'entità che non è possibile accedere con un URL (ad esempio, una riga di un **Recordset** derivato da un database), i valori di entrambi i [ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md)proprietà e il campo a cui si accede con il **adRecordURL** costante sono null.  
  
> [!NOTE]
>  Gli URL che utilizzano lo schema http richiamerà automaticamente il [il Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Per ulteriori informazioni, vedere [URL assoluti e relativi](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto di record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Open (metodo) (connessione ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open (metodo) (Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open (metodo) (flusso ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Metodo OpenSchema](../../../ado/reference/ado-api/openschema-method.md)
