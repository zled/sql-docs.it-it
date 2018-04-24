---
title: Spazi dei nomi | Documenti Microsoft
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
helpviewer_keywords:
- namespaces in ADO
ms.assetid: efff5569-db52-451d-a039-2e74870534da
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1838b0ab342a2c9748ef856aea9bbf08e523c64b
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="namespaces"></a>Spazi dei nomi
Il formato di persistenza XML in ADO utilizza i seguenti quattro spazi dei nomi.  
  
## <a name="remarks"></a>Osservazioni  
 Il formato di persistenza XML in ADO utilizza i seguenti quattro spazi dei nomi.  
  
|Prefisso|Description|  
|------------|-----------------|  
|s|Si intende lo spazio dei nomi "XML-Data" che contiene gli elementi e attributi che definiscono lo schema dell'oggetto Recordset.|  
|DT|Fa riferimento a una specifica di definizioni del tipo di dati.|  
|rs|Fa riferimento agli elementi che contiene lo spazio dei nomi e gli attributi specifici di proprietà Recordset ADO e attributi.|  
|z|Fa riferimento allo schema del set di righe corrente.|  
  
 Un client deve aggiungere il proprio tag a questi spazi dei nomi, come definito dalla specifica. Ad esempio, un client non deve definire un spazio dei nomi "urn: schemas-microsoft-com: rowset" e quindi scrivere un elemento, ad esempio "rs: MyOwnTag". Per ulteriori informazioni sugli spazi dei nomi, vedere il [W3C raccomandazione Namespaces in XML](http://www.w3.org/TR/REC-xml-names/).  
  
> [!IMPORTANT]
>  L'ID del tag dello schema deve essere "RowsetSchema" e lo spazio dei nomi utilizzato per fare riferimento allo schema del set di righe corrente deve puntare a "#RowsetSchema".  
  
 Si noti che il prefisso dello spazio dei nomi, ovvero la parte tra i due punti e il segno di uguale, è arbitrario.  
  
```  
xmlns:rs="urn:schemas-microsoft-com:rowset"  
```  
  
 L'utente può definire che un nome qualsiasi, purché questo nome viene utilizzato in modo coerente in tutto il documento XML. ADO scrive sempre "s", "rs", "td" e "z", ma questi nomi con prefisso non sono hardcoded del componente di caricamento.  
  
## <a name="see-also"></a>Vedere anche  
 [Persistenza di record in formato XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
