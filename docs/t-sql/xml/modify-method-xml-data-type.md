---
title: Modify () (metodo) (tipo di dati xml) | Documenti Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- modify() method
- modify method
ms.assetid: 52430735-51f4-46d1-a308-9aecf8648fda
caps.latest.revision: "35"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 429797447e56ecb57f0dc257bfd13bea59ea1f40
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="modify-method-xml-data-type"></a>Metodo modify() (tipo di dati xml)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Modifica il contenuto di un documento XML. Utilizzare questo metodo per modificare il contenuto di un **xml** variabile di tipo o di colonna. Il metodo richiede un'istruzione XML DML per inserire, aggiornare o eliminare i nodi dai dati XML. Il **Modify ()** metodo il **xml** il tipo di dati può essere utilizzato solo nella clausola SET di un'istruzione UPDATE.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
modify (XML_DML)  
```  
  
## <a name="arguments"></a>Argomenti  
 XML_DML  
 Stringa nel linguaggio di manipolazione dei dati (DML, Data Manipulation Language) XML. Il documento XML viene aggiornato in base a questa espressione.  
  
> [!NOTE]  
>  Viene restituito un errore se il **Modify ()** metodo viene chiamato su un valore null o restituisce un valore null.  
  
## <a name="examples"></a>Esempi  
 Poiché il **Modify ()** metodo richiede una stringa nel XML Data Manipulation Language (DML), gli esempi per **Modify ()** sono contenute negli argomenti che descrivono le istruzioni XML DML. Per questi esempi, vedere [insert &#40; Linguaggio XML DML &#41; ](../../t-sql/xml/insert-xml-dml.md), [Elimina &#40; Linguaggio XML DML &#41; ](../../t-sql/xml/delete-xml-dml.md) e [sostituire valore &#40; Linguaggio XML DML &#41; ](../../t-sql/xml/replace-value-of-xml-dml.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creare istanze di dati XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [metodi con tipo di dati XML](../../t-sql/xml/xml-data-type-methods.md)   
 [Linguaggio di manipolazione dei dati XML &#40; Linguaggio XML DML &#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
