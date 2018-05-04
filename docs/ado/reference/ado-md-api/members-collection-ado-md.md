---
title: Raccolta di membri (ADO MD) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Level::Members
- Members
- Position::Members
helpviewer_keywords:
- Members collection [ADO MD]
ms.assetid: 3a647cde-efdc-4394-b1b9-8cbb1b9d689f
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 18a3fac9cff0a41c9d1e7dc820d68ae77c294d4a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="members-collection-ado-md"></a>Raccolta di membri (ADO MD)
Contiene il [membro](../../../ado/reference/ado-md-api/member-object-ado-md.md) gli oggetti di un livello o una posizione lungo un asse.  
  
## <a name="remarks"></a>Osservazioni  
 Oggetto **membri** insieme viene utilizzato per contenere i seguenti tipi di membri:  
  
-   I membri che costituiscono un livello in un cubo. Sono contenute nel **membri** raccolta di un [livello](../../../ado/reference/ado-md-api/level-object-ado-md.md) oggetto. Ad esempio, usando l'esempio da [Panoramica di schemi e dati multidimensionali](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md), quattro membri del livello di paesi sono Canada, Stati Uniti, Regno Unito e Germania.  
  
-   I membri che sono figli di un membro specifico all'interno di una gerarchia. Questi membri vengono restituiti dal [figli](../../../ado/reference/ado-md-api/children-property-ado-md.md) proprietà dell'elemento padre **membro** oggetto. Ad esempio, utilizzando lo stesso campione, sono i due elementi figlio del membro Canada Canada-est e Ovest Canada.  
  
-   I membri che definiscono una posizione specifica lungo un asse di un [set di celle](../../../ado/reference/ado-md-api/cellset-object-ado-md.md). Utilizzando il set di celle da [utilizzo di dati multidimensionali](../../../ado/guide/multidimensional/working-with-multidimensional-data.md) ad esempio, i due membri della prima posizione sull'asse x sono otto posizioni a Seattle. Questi membri sono inclusi il **membri** raccolta di un [posizione](../../../ado/reference/ado-md-api/position-object-ado-md.md) oggetto.  
  
 **I membri** è un insieme standard di ADO. Con le proprietà e metodi di una raccolta, è possibile eseguire le operazioni seguenti:  
  
-   Ottenere il numero di oggetti nella raccolta con il [conteggio](../../../ado/reference/ado-api/count-property-ado.md) proprietà.  
  
-   Restituire un oggetto dalla raccolta con il valore predefinito [elemento](../../../ado/reference/ado-api/item-property-ado.md) proprietà.  
  
-   Aggiornare gli oggetti nella raccolta dal provider con il [aggiornamento](../../../ado/reference/ado-api/refresh-method-ado.md) metodo.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi](../../../ado/reference/ado-md-api/members-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di membri (VBScript)](../../../ado/reference/ado-md-api/members-example-vbscript.md)   
 [Oggetto Member (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)
