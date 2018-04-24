---
title: Close (metodo) (ADO) | Documenti Microsoft
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
- Recordset15::Close
- _Stream::Close
- _Record::Close
helpviewer_keywords:
- Close method [ADO]
ms.assetid: 3cdf27d1-a180-4cff-8e42-95dec5fb1b55
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 996da92c866789b91a317c152449f7ca2540d273
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="close-method-ado"></a>Close (metodo) (ADO)
Chiude un oggetto aperto e gli eventuali oggetti dipendenti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.Close  
```  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **chiudere** metodo per chiudere un [connessione](../../../ado/reference/ado-api/connection-object-ado.md), [Record](../../../ado/reference/ado-api/record-object-ado.md), [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), o un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto Per liberare le risorse di sistema associate. Chiusura di un oggetto senza rimuoverlo dalla memoria. è possibile modificare le impostazioni delle proprietà e aprirlo più tardi. Per eliminare completamente l'oggetto dalla memoria, chiudere l'oggetto e quindi impostare la variabile oggetto *nulla* (in Visual Basic).  
  
## <a name="connection"></a>Connessione  
 Utilizzando il **chiudere** metodo per chiudere un **connessione** oggetto e inoltre chiude qualsiasi attivo **Recordset** oggetti associati alla connessione. A [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto associato di **connessione** oggetto che si sta chiudendo verrà mantenuti, ma non è più associato un **connessione** oggetto, vale a dire il relativo [ ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) verrà impostata su **nulla**. Inoltre, il **comando** dell'oggetto [parametri](../../../ado/reference/ado-api/parameters-collection-ado.md) verrà cancellato l'insieme di tutti i parametri definito dal provider.  
  
 Successivamente è possibile chiamare il [aprire](../../../ado/reference/ado-api/open-method-ado-connection.md) metodo per ristabilire la connessione alle stesse o un'altra origine dati. Mentre il **connessione** oggetto è chiuso, chiamare i metodi che richiedono una connessione aperta all'origine dati genera un errore.  
  
 Chiusura un **connessione** oggetto mentre sono aperti **Recordset** oggetti per la connessione rollback di eventuali modifiche in sospeso in tutti i **Recordset** oggetti. Chiusura in modo esplicito un **connessione** oggetto (chiamata di **Chiudi** (metodo)) mentre una transazione è in corso genera un errore. Se un **connessione** oggetto non rientra nell'ambito quando è in corso una transazione, ADO automaticamente il rollback della transazione.  
  
## <a name="recordset-record-stream"></a>Recordset, Record, Stream  
 Utilizzo di **chiudere** metodo per chiudere un **Recordset**, **Record**, o **flusso** oggetto rilascia i dati associati e accesso esclusivo invece si ai dati tramite questo particolare oggetto. Successivamente è possibile chiamare il [aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md) metodo per riaprire l'oggetto con lo stesso, o modificata, gli attributi.  
  
 Mentre un **Recordset** oggetto è chiuso, chiamare i metodi che richiedono un cursore in tempo reale genera un errore.  
  
 Se una modifica è in corso in modalità di aggiornamento immediato, la chiamata di **Chiudi** metodo genera un errore; in alternativa, chiamare il [aggiornare](../../../ado/reference/ado-api/update-method.md) o [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) metodo prima. Se si chiude il **Recordset** oggetto mentre è in modalità di aggiornamento batch, tutte le modifiche apportate dall'ultimo [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) chiamata vengono persi.  
  
 Se si utilizza il [Clone](../../../ado/reference/ado-api/clone-method-ado.md) metodo per creare copie di un oggetto aperto **Recordset** oggetto originale o un clone di chiusura non influisce sulle altre copie.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Oggetto Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodi di apertura e chiusura (VB)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Esempio di metodi di apertura e chiusura (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Esempio di metodi di apertura e chiusura (VC + +)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Open (metodo) (connessione ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open (metodo) (Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Metodo Save](../../../ado/reference/ado-api/save-method.md)
