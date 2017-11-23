---
title: NULL (SQLXML 4.0) di gestione | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- updg:nullvalue attribute
- updategrams [SQLXML], null values
- nullvalue attribute
- null values [SQLXML]
ms.assetid: 5e11eebb-d94e-4ce6-a6d0-870225706bc1
caps.latest.revision: "23"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 73ea8f9fb9e98a174e93ab2e300a96468af02d09
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="null-handling-sqlxml-40"></a>Gestione dei valori Null (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]La sintassi XML il valore NULL indica un'assenza. Se, ad esempio, un valore di attributo o di elemento è Null, tale attributo o elemento è assente nel documento XML. In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML, il **updg: NullValue** attributo consente di specificare NULL per un valore dell'elemento o attributo.  
  
 Ad esempio, l'updategram seguente garantisce che il **titolo** valore per un contatto con **ContactID** 64 è NULL e quindi aggiorna il **titolo** valore di "Mr." per questo contatto.  
  
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
  
 Quando i parametri vengono passati a un updategram, è possibile passare Null come valore del parametro. Questa operazione viene eseguita specificando il **nullvalue** attributo la  **\<updg:header >** blocco. Per un esempio, vedere [passaggio di parametri per gli updategram &#40; SQLXML 4.0 &#41; ](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/passing-parameters-to-updategrams-sqlxml-4-0.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Considerazioni sulla sicurezza di updategram &#40; SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
