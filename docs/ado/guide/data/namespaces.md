---
title: Gli spazi dei nomi | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- namespaces in ADO
ms.assetid: efff5569-db52-451d-a039-2e74870534da
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5553072dcea3ed64ef8454019892ac5790c7a142
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2018
ms.locfileid: "51600111"
---
# <a name="namespaces"></a>Spazi dei nomi
Il formato di persistenza XML ADO utilizza i seguenti quattro spazi dei nomi.  
  
## <a name="remarks"></a>Note  
 Il formato di persistenza XML ADO utilizza i seguenti quattro spazi dei nomi.  
  
|Prefisso|Description|  
|------------|-----------------|  
|s|Fa riferimento allo spazio dei nomi "XML-Data" che contiene gli elementi e attributi che definiscono lo schema del set di record corrente.|  
|DT|Fa riferimento alla specifica di definizioni del tipo di dati.|  
|rs|Fa riferimento agli elementi che lo contiene lo spazio dei nomi e gli attributi specifici per le proprietà di Recordset ADO e attributi.|  
|z|Fa riferimento allo schema del set di righe corrente.|  
  
 Un client non deve aggiungere dei tag corrispondenti a questi spazi dei nomi, come definito dalla specifica. Ad esempio, un client non deve definire uno spazio dei nomi come "urn: schemas-microsoft-com: rowset" e quindi scrivere un valore, ad esempio "rs: MyOwnTag." Per altre informazioni sugli spazi dei nomi, vedere la [W3C raccomandazione Namespaces in XML](https://www.w3.org/TR/REC-xml-names/).  
  
> [!IMPORTANT]
>  L'ID per il tag dello schema deve essere "RowsetSchema", e lo spazio dei nomi usato per fare riferimento allo schema del set di righe corrente deve puntare a "#RowsetSchema."  
  
 Si noti che il prefisso dello spazio dei nomi, ovvero la parte tra i due punti e il segno di uguale, ovvero è arbitrario.  
  
```  
xmlns:rs="urn:schemas-microsoft-com:rowset"  
```  
  
 L'utente può definire questo è un nome qualsiasi, purché questo nome viene usato in modo coerente in tutto il documento XML. ADO scrive sempre "s", "rs", "td" e "z", ma questi nomi di prefisso non sono impostate come hardcoded nel componente di caricamento.  
  
## <a name="see-also"></a>Vedere anche  
 [Persistenza di record in formato XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
