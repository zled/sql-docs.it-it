---
title: Modello di memorizzazione nella cache (SQLXML 4.0) | Documenti di Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- templates [SQLXML], caching
ms.assetid: 73e151c6-b24e-4422-a116-51e0846bc6f5
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cade212f2f669190ce8c771c912a8d8147f7e161
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47704579"
---
# <a name="template-caching-sqlxml-40"></a>Memorizzazione nella cache dei modelli (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  La memorizzazione dei modelli nella cache migliora significativamente le prestazioni. Se è impostata, il modello rimane in memoria fino alla prima esecuzione. In questo modo vengono migliorate le prestazioni per l'esecuzione successiva.  
  
 È possibile impostare le dimensioni della cache dei modelli aggiungendo nel Registro di sistema la chiave seguente:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 È consigliabile impostare le dimensioni del modello in base alla memoria disponibile e al numero di modelli utilizzati. Il valore predefinito è **TemplateCacheSize** dimensione è 31. È possibile aumentare le dimensioni della cache se l'accesso al modello sembra lento o ridurle se la memoria è insufficiente.  
  
 Per ottenere prestazioni migliori, si consiglia di impostare **TemplateCacheSize** superiore al numero dei modelli utilizzati normalmente. Se **TemlateCacheSize** è minore rispetto al numero di modelli è, le prestazioni diminuiscono con il numero di aumento di modelli. Il **TemplateCacheSize** può essere impostata su un massimo di 128.  
  
 Ogni volta che viene utilizzato un modello memorizzato nella cache, viene controllata l'ora di modifica del file modello per vedere se deve essere aggiornata. Ciò accade in quanto la copia su disco è più recente della copia della cache.  
  
> [!NOTE]  
>  I parametri di modello e le proprietà dei comandi non vengono memorizzati nella cache.  
  
## <a name="see-also"></a>Vedere anche  
 [La cache dello schema &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/schema-caching-sqlxml-4-0.md)   
 [La memorizzazione nella cache di XSL &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/xsl-caching-sqlxml-4-0.md)  
  
  
