---
title: Modello di memorizzazione nella cache (SQLXML 4.0) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- templates [SQLXML], caching
ms.assetid: 73e151c6-b24e-4422-a116-51e0846bc6f5
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4107a253b7fc82f3961caa08b005c33a95d46a4c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36066712"
---
# <a name="template-caching-sqlxml-40"></a>Memorizzazione nella cache dei modelli (SQLXML 4.0)
  La memorizzazione dei modelli nella cache migliora significativamente le prestazioni. Se è impostata, il modello rimane in memoria fino alla prima esecuzione. In questo modo vengono migliorate le prestazioni per l'esecuzione successiva.  
  
 È possibile impostare le dimensioni della cache dei modelli aggiungendo nel Registro di sistema la chiave seguente:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 È consigliabile impostare le dimensioni del modello in base alla memoria disponibile e al numero di modelli utilizzati. Il valore predefinito **TemplateCacheSize** dimensioni sono pari a 31. È possibile aumentare le dimensioni della cache se l'accesso al modello sembra lento o ridurle se la memoria è insufficiente.  
  
 Per ottenere prestazioni migliori, è consigliabile impostare **TemplateCacheSize** superiore al numero di modelli generalmente utilizzati. Se **Templatecachesize** è minore rispetto al numero di modelli, le prestazioni diminuiscono in quanto il numero di modelli aumento. Il **TemplateCacheSize** può essere impostata su un massimo di 128.  
  
 Ogni volta che viene utilizzato un modello memorizzato nella cache, viene controllata l'ora di modifica del file modello per vedere se deve essere aggiornata. Ciò accade in quanto la copia su disco è più recente della copia della cache.  
  
> [!NOTE]  
>  I parametri di modello e le proprietà dei comandi non vengono memorizzati nella cache.  
  
## <a name="see-also"></a>Vedere anche  
 [La memorizzazione nella cache dello schema &#40;SQLXML 4.0&#41;](schema-caching-sqlxml-4-0.md)   
 [La memorizzazione nella cache XSL &#40;SQLXML 4.0&#41;](xsl-caching-sqlxml-4-0.md)  
  
  