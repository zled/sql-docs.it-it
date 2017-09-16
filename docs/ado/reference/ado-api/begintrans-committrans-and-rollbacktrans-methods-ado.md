---
title: BeginTrans, CommitTrans e RollbackTrans metodi (ADO) | Documenti Microsoft
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
- Connection15::raw_RollbackTrans
- Connection15::CommitTrans
- Connection15::raw_CommitTrans
- Connection15::raw_BeginTrans
- Connection15::BeginTrans
- Connection15::RollbackTrans
helpviewer_keywords:
- BeginTrans method [ADO]
- CommitTrans method [ADO]
- RollbackTrans method [ADO]
ms.assetid: d4683472-4120-4236-8640-fa9ae289e23e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3e973503fcdd7a524bab21364428be6b955017af
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="begintrans-committrans-and-rollbacktrans-methods-ado"></a>BeginTrans, CommitTrans e RollbackTrans metodi (ADO)
Questi metodi gestiscono l'elaborazione all'interno delle transazioni un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) come illustrato di seguito:  
  
-   **BeginTrans** inizia una nuova transazione.  
  
-   **CommitTrans** Salva le modifiche e termina la transazione corrente. È possibile anche avviare una nuova transazione.  
  
-   **RollbackTrans** Annulla tutte le modifiche apportate durante la transazione corrente e termina la transazione. È possibile anche avviare una nuova transazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
level = object.BeginTrans()  
object.BeginTrans  
object.CommitTrans  
object.RollbackTrans  
```  
  
## <a name="return-value"></a>Valore restituito  
 **BeginTrans** può essere chiamato come una funzione che restituisce un **lungo** variabile che indica il livello di nidificazione della transazione.  
  
#### <a name="parameters"></a>Parametri  
 *oggetto*  
 Oggetto **connessione** oggetto.  
  
## <a name="connection"></a>Connessione  
 Utilizzare questi metodi con un **connessione** oggetto quando si desidera salvare o annullare una serie di modifiche apportate ai dati di origine come singola unità. Ad esempio, per trasferire denaro tra conti, sottrarre un importo sia aggiungere la stessa quantità a altra. Se l'aggiornamento ha esito negativo, l'account non è più bilanciare. Queste modifiche all'interno di una transazione aperta garantisce che tutte o nessuna delle modifiche passino.  
  
> [!NOTE]
>  Non tutti i provider supportano le transazioni. Verificare che la proprietà definito dal provider "**Transaction DDL**" viene visualizzato nel **connessione** dell'oggetto [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) raccolta, che indica che il provider supporta transazioni. Se il provider non supporta le transazioni, una chiamata a uno di questi metodi restituirà un errore.  
  
 Dopo aver chiamato il **BeginTrans** metodo, il provider eseguirà non immediatamente il commit le modifiche apportate fino a quando non si chiama **CommitTrans** o **RollbackTrans** per terminare il transazione.  
  
 Per i provider che supportano le transazioni nidificate, la chiamata di **BeginTrans** metodo all'interno di una transazione aperta avvia una transazione nidificata. Il valore restituito indica il livello di annidamento: indica di un valore restituito pari a "1" è stata aperta una transazione di primo livello (ovvero, la transazione non sia annidata all'interno di un'altra transazione), "2" indica che è stata aperta una transazione di secondo livello (a transazione annidata all'interno di una transazione di primo livello), e così via. La chiamata **CommitTrans** o **RollbackTrans** interessa solo la maggior parte delle transazioni aperti di recente, è necessario chiudere o il rollback della transazione corrente prima che è possibile risolvere le transazioni di livello superiore.  
  
 La chiamata di **CommitTrans** metodo salva le modifiche apportate all'interno di una transazione aperta per la connessione e termina la transazione. La chiamata di **RollbackTrans** metodo inverte le modifiche apportate all'interno di una transazione aperta e termina la transazione. Chiamare il metodo quando non sono presenti transazioni aperte genera un errore.  
  
 A seconda di **connessione** dell'oggetto [attributi](../../../ado/reference/ado-api/attributes-property-ado.md) proprietà, una chiamata al **CommitTrans** o **RollbackTrans** metodi potrebbero Avvia automaticamente una nuova transazione. Se il **attributi** è impostata su **adXactCommitRetaining**, il provider avvia automaticamente una nuova transazione dopo un **CommitTrans** chiamare. Se il **attributi** è impostata su **adXactAbortRetaining**, il provider avvia automaticamente una nuova transazione dopo un **RollbackTrans** chiamare.  
  
## <a name="remote-data-service"></a>Remote Data Service  
 Il **BeginTrans**, **CommitTrans**, e **RollbackTrans** metodi non sono disponibili sul lato client **connessione** oggetto.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto di connessione (ADO.NET)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [BeginTrans, CommitTrans e RollbackTrans metodi esempio (VB)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vb.md)   
 [BeginTrans, CommitTrans e RollbackTrans metodi esempio (VC + +)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vc.md)   
 [Proprietà Attributes (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)

