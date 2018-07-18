---
title: NULL (SQLXML 4.0) gestisce | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- updg:nullvalue attribute
- updategrams [SQLXML], null values
- nullvalue attribute
- null values [SQLXML]
ms.assetid: 5e11eebb-d94e-4ce6-a6d0-870225706bc1
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b53c3516dbe0ee87e23e9cb13ec441ef82a499c8
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38031419"
---
# <a name="null-handling-sqlxml-40"></a>Gestione dei valori Null (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Nella sintassi XML il valore Null indica un'assenza. Se, ad esempio, un valore di attributo o di elemento è Null, tale attributo o elemento è assente nel documento XML. Nelle [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML, il **updg: NullValue** attributo consente la specifica di NULL per un valore di attributo o elemento.  
  
 Ad esempio, l'updategram seguente verifica che il **Title** valore per un contatto con **ContactID** 64 sia NULL e quindi aggiorna il **titolo** valore di "Mr." per questo contatto.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync updg:nullvalue="IsNULL"  >  
    <updg:before>  
       <Person.Contact ContactID="64" Title="IsNULL" />  
    </updg:before>  
    <updg:after>  
       <Person.Contact ContactID="64" Title="Mr." />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Quando i parametri vengono passati a un updategram, è possibile passare Null come valore del parametro. Ciò avviene specificando il **nullvalue** attributo il  **\<updg:header >** blocco. Per un esempio, vedere [passaggio di parametri agli updategram &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/passing-parameters-to-updategrams-sqlxml-4-0.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Considerazioni sulla sicurezza degli updategram &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
