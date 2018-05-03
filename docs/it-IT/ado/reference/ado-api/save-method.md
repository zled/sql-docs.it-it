---
title: Save (metodo) | Documenti Microsoft
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
- _Recordset::Save
- _Recordset::raw_Save
helpviewer_keywords:
- Save method [ADO]
ms.assetid: ed3d9678-5c28-4e61-8bb3-7dfb66d99cf5
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cffcb7b23487201605ff2ced489cf0078c3c1272
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="save-method"></a>Save (metodo)
Salva il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) in un file o [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
recordset.Save Destination, PersistFormat  
```  
  
#### <a name="parameters"></a>Parametri  
 *Destinazione*  
 Facoltativa. Oggetto **Variant** che rappresenta il nome di percorso completo del file in cui il **Recordset** deve essere salvato, o un riferimento a un **flusso** oggetto.  
  
 *PersistFormat*  
 Facoltativa. Oggetto [PersistFormatEnum](../../../ado/reference/ado-api/persistformatenum.md) valore che specifica il formato in cui il **Recordset** deve essere salvato (XML o ADTG). Il valore predefinito è **adPersistADTG**.  
  
## <a name="remarks"></a>Osservazioni  
 Il [metodo Save](../../../ado/reference/ado-api/save-method.md) metodo può essere richiamato solo su un oggetto aperto **Recordset**. Utilizzare il [Open (metodo) (Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md) metodo di ripristino successive il **Recordset** da *destinazione*.  
  
 Se il [proprietà Filter](../../../ado/reference/ado-api/filter-property.md) è attiva per il **Recordset**, quindi vengono salvate solo le righe accessibili in base al filtro. Se il **Recordset** è di tipo gerarchico, quindi l'elemento figlio corrente **Recordset** e relativi elementi figlio viene salvati, incluso l'elemento padre **Recordset**. Se il metodo Save di un elemento figlio **Recordset** viene chiamato, l'elemento figlio e i relativi elementi figlio viene salvati, ma non è l'elemento padre.  
  
 La prima volta che salva il **Recordset**, è possibile specificare facoltativamente *destinazione*. Se si omette *destinazione*, verrà creato un nuovo file con un nome impostato sul valore della proprietà dell'origine di **Recordset**.  
  
 Omettere *destinazione* quando si chiama successivamente **salvare** dopo il primo salvataggio o un errore di run-time si verificherà. Se si chiama successivamente **salvare** con un nuovo *destinazione*, **Recordset** viene salvato nella nuova destinazione. Tuttavia, la nuova destinazione e la destinazione originale sia sarà aperti.  
  
 **Salvare** non chiude il **Recordset** o *destinazione*, pertanto è possibile continuare a lavorare con i **Recordset** e salvare le modifiche più recenti. *Destinazione* rimane aperto fino a quando il **Recordset** viene chiuso.  
  
 Per motivi di sicurezza, il **salvare** metodo consente solo l'utilizzo di impostazioni di protezione basso e personalizzato da uno script eseguito da Microsoft Internet Explorer.  
  
 Se il **salvare** metodo viene chiamato durante asincrono **Recordset** recuperare, eseguire o aggiornare operazione è in corso, quindi **salvare** attende fino a quando l'operazione asincrona è stata completata.  
  
 I record vengono salvati a partire dalla prima riga del **Recordset**. Quando il **salvare** metodo termina, la posizione della riga corrente viene spostata nella prima riga del **Recordset**.  
  
 Per ottenere risultati ottimali, impostare il [proprietà CursorLocation (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md) proprietà **adUseClient** con **salvare**. Se il provider non supporta tutte le funzionalità necessarie per salvare **Recordset** oggetti, il servizio cursore fornirà tale funzionalità.  
  
 Quando un **Recordset** vengono rese persistenti con la **CursorLocation** proprietà impostata su **adUseServer**, la funzionalità di aggiornamento per il **Recordset**è limitato. In genere, gli aggiornamenti a tabella singola, inserimenti ed eliminazioni sono consentite (dipende dalla funzionalità del provider). Il [metodo Resync](../../../ado/reference/ado-api/resync-method.md) metodo inoltre è disponibile in questa configurazione.  
  
> [!NOTE]
>  Salvataggio di un **Recordset** con **campi** di tipo **adVariant**, **adIDispatch**, o **adIUnknown** è non è supportato da ADO e può provocare risultati imprevisti.  
  
 Filtra solo in forma di stringhe di criteri (ad esempio DataOrdine > ' 12/31/1999 ') influiscono sul contenuto di un persistente **Recordset**. I filtri creati con una matrice di **segnalibri** o utilizzando un valore di [FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md) non influenzerà il contenuto di persistente **Recordset**. Queste regole si applicano a **Recordset**creata con i cursori sul lato client o sul lato server.  
  
 Poiché il *destinazione* parametro può accettare qualsiasi oggetto che supporta l'interfaccia IStream OLE DB, è possibile salvare un **Recordset** direttamente all'oggetto ASP Response. Per ulteriori informazioni, vedere il **Scenario persistenza Recordset XML**.  
  
 È inoltre possibile salvare un **Recordset** in formato XML in un'istanza di un oggetto DOM MSXML, come è illustrato nel codice Visual Basic seguente:  
  
```  
Dim xDOM As New MSXML.DOMDocument  
Dim rsXML As New ADODB.Recordset  
Dim sSQL As String, sConn As String  
  
sSQL = "SELECT customerid, companyname, contactname FROM customers"  
sConn="Provider=Microsoft.Jet.OLEDB.4.0;Data Source=Northwind.mdb"  
rsXML.Open sSQL, sConn  
rsXML.Save xDOM, adPersistXML   'Save Recordset directly into a DOM tree.  
...  
```  
  
> [!NOTE]
>  Due limitazioni quando si salva il recordset gerarchici (forme di dati) in formato XML. Se non è possibile salvare in XML la gerarchica **Recordset** contiene gli aggiornamenti, in sospeso e non è possibile salvare un parametri gerarchici **Recordset**.  
  
 Oggetto **Recordset** salvato in formato XML formato viene salvato nel formato UTF-8. Quando uno di questi file verrà caricato in un flusso ADO, l'oggetto di flusso non tenterà di aprire un **Recordset** dal flusso, a meno che la proprietà set di caratteri del flusso è impostata sul valore appropriato per il formato UTF-8.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Salvare e aprire l'esempio di metodi (VB)](../../../ado/reference/ado-api/save-and-open-methods-example-vb.md)   
 [Salvare e aprire l'esempio di metodi (VC + +)](../../../ado/reference/ado-api/save-and-open-methods-example-vc.md)   
 [Open (metodo) (Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open (metodo) (flusso ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Metodo SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)
