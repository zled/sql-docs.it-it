---
title: Oggetto di proprietà (ADOX) | Documenti Microsoft
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
helpviewer_keywords:
- Property object [ADOX]
ms.assetid: 6a56def6-dbe6-4ccc-a491-8d076889f019
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 80af9304927f526422650f63264f06539cb14b29
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="property-object-adox"></a>Oggetto di proprietà (ADOX)
Rappresenta una caratteristica di un oggetto ADOX.  
  
## <a name="remarks"></a>Osservazioni  
 Gli oggetti ADOX dispongono di due tipi di proprietà: incorporato e dinamici.  
  
 Proprietà predefinite sono quelle immediatamente disponibili per qualsiasi nuovo oggetto, utilizzando la sintassi MyObject. Non vengono visualizzati come oggetti di proprietà in un oggetto [raccolta delle proprietà](../../../ado/reference/ado-api/properties-collection-ado.md), sebbene sia possibile modificare i relativi valori, è pertanto possibile modificare le relative caratteristiche.  
  
 Proprietà dinamiche sono definite dal provider di dati sottostante e vengono visualizzati nella raccolta delle proprietà per l'oggetto ADOX appropriato.  Proprietà dinamiche possono fare riferimento solo tramite la raccolta utilizzando la sintassi MyObject.Properties(0) o MyObject.  
  
 È possibile eliminare il tipo di proprietà.  
  
 Un oggetto dinamico di proprietà presenta quattro proprietà predefinite di un proprio:  
  
 Il [nome](../../../ado/reference/ado-api/name-property-ado.md) proprietà è una stringa che identifica la proprietà.  
  
 Il [tipo](../../../ado/reference/ado-api/type-property-ado.md) proprietà è un numero intero che specifica il tipo di dati di proprietà.  
  
 Il [valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà è una variabile variant contenente l'impostazione della proprietà. Valore è la proprietà predefinita per un oggetto di proprietà.  
  
 Il [attributi](../../../ado/reference/ado-api/attributes-property-ado.md) proprietà è un valore long che indica le caratteristiche della proprietà specifiche del provider.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi dell'oggetto Property ADOX](../../../ado/reference/adox-api/adox-property-object-properties-methods-and-events.md)
