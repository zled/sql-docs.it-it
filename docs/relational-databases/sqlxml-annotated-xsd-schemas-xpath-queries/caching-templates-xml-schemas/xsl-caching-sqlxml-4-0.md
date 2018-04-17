---
title: XSL la memorizzazione nella cache (SQLXML 4.0) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- XSL caching [SQLXML]
ms.assetid: 91994142-32f0-4d8d-a8cf-eb0d8b1f1999
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c14703a0156c420d072b28d726400a1331d06477
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="xsl-caching-sqlxml-40"></a>Memorizzazione nella cache file XSL (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  La memorizzazione nella cache di fogli di stile XSL migliora le prestazioni. Fino alla prima esecuzione, il foglio di stile XSL resta in memoria se la memorizzazione nella cache XSL è impostata su ON. Questa impostazione offre prestazioni migliori per l'elaborazione successiva. L'impostazione predefinita è ON.  
  
 È possibile impostare le dimensioni della cache per i file XSL aggiungendo la chiave seguente nel Registro di sistema:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\XSLCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 La cache dei file XSL deve essere impostata in base alla memoria disponibile e al numero di fogli di stile XSL utilizzati. Il valore predefinito di **XSLCacheSize** dimensioni pari a 31. È possibile aumentare le dimensioni della cache se l'accesso a XSL appare rallentato oppure diminuire le dimensioni della cache se la memoria risulta insufficiente.  
  
 Per ottenere prestazioni migliori, è consigliabile impostare **XSLCacheSize** superiore al numero di fogli di stile XSL utilizzati normalmente. Se **XSLCacheSize** è inferiore al numero di XSL fogli di stile si dispone, le prestazioni diminuiscono in quanto il numero di aumenta di fogli di stile XSL. Il **XSLCacheSize** può essere impostata su un massimo di 128.  
  
 Ogni volta che si utilizza il foglio di stile XSL memorizzato nella cache, viene verificata la durata delle modifiche del file XSL per determinare se deve essere aggiornato. Ciò accade in quanto la copia su disco è più recente della copia della cache.  
  
## <a name="see-also"></a>Vedere anche  
 [La cache dei modelli & #40; SQLXML 4.0 & #41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/template-caching-sqlxml-4-0.md)   
 [La memorizzazione nella cache di schema & #40; SQLXML 4.0 & #41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/schema-caching-sqlxml-4-0.md)  
  
  
