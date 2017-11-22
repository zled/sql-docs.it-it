---
title: "Elemento proprietà (ADO MD Cellset) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Item
- Cellset::Item
helpviewer_keywords: Item property [ADO MD]
ms.assetid: 0e93d79b-b12e-4e98-889e-c2dfcca20fd0
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 34b0d4a5f2104d625091a0b39f1b009b933bedbe
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="item-property-ado-md-cellset"></a>Proprietà dell'elemento (ADO MD Cellset)
Recupera una cella da un [set di celle](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) utilizzando le coordinate.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Set  
Cell = Cellset.Item ( Positions)  
```  
  
## <a name="parameters"></a>Parametri  
 *Posizioni*  
 Oggetto **VariantArray** di valori che specificano in modo univoco una cella. *Posizioni* può essere uno dei seguenti:  
  
-   Matrice di numeri di posizione  
  
-   Una matrice di nomi di membro  
  
-   La posizione ordinale  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **elemento** proprietà per restituire un [cella](../../../ado/reference/ado-md-api/cell-object-ado-md.md) oggetto all'interno di un [set di celle](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) oggetto. Se il **elemento** proprietà non è possibile trovare la cella corrispondente il *posizioni* si verifica un errore di argomento.  
  
 Il **elemento** proprietà è la proprietà predefinita per il **set di celle** oggetto. Le forme di sintassi seguenti sono intercambiabili:  
  
```  
  
Cellset.Item ( Positions )Cellset ( Positions )  
```  
  
## <a name="remarks"></a>Osservazioni  
 Il *posizioni* argomento specifica la cella da restituire. È possibile specificare la cella in base alla posizione ordinale o dalla posizione lungo ogni asse. Quando si specifica la cella in base alla posizione lungo ogni asse, è possibile specificare il valore numerico della posizione o i nomi dei membri per ogni posizione.  
  
 La posizione ordinale è un numero che identifica in modo univoco una cella all'interno di **set di celle**. Concettualmente, le celle sono numerate in un **set di celle** come se il **set di celle** sono stati un *p*-matrice dimensionale, dove *p* è il numero di assi. Le celle sono indirizzate in ordine di riga. Di seguito è la formula per calcolare il numero ordinale di una cella:  
  
 Se i nomi dei membri vengono passati come stringhe a **elemento**, i membri devono essere elencati in ordine crescente di identificatori numerici dell'asse. All'interno di un asse, i membri devono essere elencati in ordine crescente di nidificazione di dimensione, vale a dire, il membro della dimensione più esterna viene considerato per primo, seguiti dai membri delle dimensioni interne. Ogni dimensione deve essere rappresentato da una stringa distinta e l'elenco di stringhe di membro deve essere separato da virgole.  
  
> [!NOTE]
>  Il recupero di celle in base al nome di membro potrebbe non essere supportato da provider di dati. Vedere la documentazione del provider per ulteriori informazioni.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Cellset (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Cell (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Oggetto Cellset (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)
