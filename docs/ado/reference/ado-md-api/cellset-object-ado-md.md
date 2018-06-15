---
title: Oggetto Cellset (ADO MD) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cellset
helpviewer_keywords:
- Cellset object [ADO MD]
ms.assetid: 5e2452c0-cac0-49b2-8099-836c35794d50
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6437c17c80c85e535f6b1807f68c2755e1362d3c
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35283390"
---
# <a name="cellset-object-ado-md"></a>Oggetto Cellset (ADO MD)
Rappresenta i risultati di una query multidimensionale. È una raccolta di celle selezionate da cubi o altri set di celle.  
  
## <a name="remarks"></a>Remarks  
 Dati all'interno di un **set di celle** vengono recuperati utilizzando l'accesso diretto di tipo matrice. È possibile accedere a un membro specifico per ottenere i dati relativi a tale membro. Ad esempio, il codice seguente restituisce la didascalia del primo membro nella prima posizione del primo asse di un set di celle denominato `cst`:  
  
```  
cst.Axes(0).Positions(0).Members(0).Caption  
```  
  
## <a name="remarks"></a>Remarks  
 Non è prevista di una cella corrente all'interno di un set di celle. Al contrario, il [elemento](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) proprietà recupera una specifica [cella](../../../ado/reference/ado-md-api/cell-object-ado-md.md) oggetto dal set di celle. Gli argomenti del **elemento** proprietà determinare quale cella viene recuperata. È possibile specificare il valore ordinale univoco di una cella. È anche possibile recuperare le celle utilizzando i numeri di posizione lungo ogni asse del set di celle. Per ulteriori informazioni sul recupero di celle, vedere il [elemento](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) proprietà.  
  
 Con le raccolte, i metodi e proprietà di un **set di celle** dell'oggetto, è possibile eseguire le operazioni seguenti:  
  
-   Associare una connessione aperta con un **set di celle** oggetto impostando il relativo [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md) proprietà.  
  
-   Eseguire e recuperare i risultati di una query multidimensionale con il [aprire](../../../ado/reference/ado-md-api/open-method-ado-md.md) metodo.  
  
-   Recuperare un **cella** dal **set di celle** con il [elemento](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) proprietà.  
  
-   Restituire il [asse](../../../ado/reference/ado-md-api/axis-object-ado-md.md) oggetti che definiscono il **set di celle** con il [assi](../../../ado/reference/ado-md-api/axes-collection-ado-md.md) insieme.  
  
-   Recuperare le informazioni sulle dimensioni utilizzate per filtrare i dati di **set di celle** con il [FilterAxis](../../../ado/reference/ado-md-api/filteraxis-property-ado-md.md) proprietà.  
  
-   Restituire o specificare la query utilizzata per definire il **set di celle** con il [origine](../../../ado/reference/ado-md-api/source-property-ado-md.md) proprietà.  
  
-   Restituire lo stato corrente del **set di celle** (aperte, chiuse, l'esecuzione o la connessione) con il [stato](../../../ado/reference/ado-md-api/state-property-ado-md.md) proprietà.  
  
-   Chiudere un oggetto aperto **set di celle** con il [Chiudi](../../../ado/reference/ado-md-api/close-method-ado-md.md) metodo.  
  
-   Recuperare informazioni specifiche del provider di **set di celle** con ADO standard [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi](../../../ado/reference/ado-md-api/cellset-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di set di celle (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Raccolta assi (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)   
 [Oggetto Cell (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Oggetto di connessione (ADO.NET)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
