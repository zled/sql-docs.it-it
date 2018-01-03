---
title: "Oggetto di proprietà (ADO) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: Property
helpviewer_keywords: Property object [ADO]
ms.assetid: b2a4767c-03c7-4935-a3bc-df3e1a38a009
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c43ea682cb6ca8e0dc7767cd0372fa258cea27db
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="property-object-ado"></a>Oggetto di proprietà (ADO)
Rappresenta una caratteristica dinamica di un oggetto ADO definito dal provider.  
  
## <a name="remarks"></a>Osservazioni  
 Gli oggetti ADO hanno due tipi di proprietà: incorporato e dinamici.  
  
 Le proprietà predefinite corrispondono alle proprietà implementate in ADO e immediatamente disponibili per qualsiasi nuovo oggetto tramite il `MyObject.Property` sintassi. Non vengono visualizzati come **proprietà** oggetti in un oggetto [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme, sebbene sia possibile modificare i relativi valori, è pertanto possibile modificare le relative caratteristiche.  
  
 Proprietà dinamiche sono definite dal provider di dati sottostante e vengono visualizzati di **proprietà** raccolta per l'oggetto ADO appropriato. Ad esempio, una proprietà specifica del provider può indicare se un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto supporta le transazioni o l'aggiornamento. Queste proprietà aggiuntive verranno visualizzate come **proprietà** gli oggetti che **Recordset** dell'oggetto **proprietà** insieme. È possibile fare riferimento a proprietà dinamiche solo tramite la raccolta, usando il `MyObject.Properties(0)` o `MyObject.Properties("Name")` sintassi.  
  
 È possibile eliminare il tipo di proprietà.  
  
 Dinamico **proprietà** oggetto dispone di un proprio quattro proprietà predefinite:  
  
-   Il [nome](../../../ado/reference/ado-api/name-property-ado.md) proprietà è una stringa che identifica la proprietà.  
  
-   Il [tipo](../../../ado/reference/ado-api/type-property-ado.md) proprietà è un numero intero che specifica il tipo di dati di proprietà.  
  
-   Il [valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà è una variabile variant contenente l'impostazione della proprietà. **Valore** la proprietà predefinita per un **proprietà** oggetto.  
  
-   Il [attributi](../../../ado/reference/ado-api/attributes-property-ado.md) proprietà è un valore long che indica le caratteristiche della proprietà specifiche del provider.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà dell'oggetto proprietà, metodi ed eventi](../../../ado/reference/ado-api/property-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Oggetto di connessione (ADO.NET)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Oggetto Field](../../../ado/reference/ado-api/field-object.md)   
 [Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
