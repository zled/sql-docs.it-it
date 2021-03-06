---
title: Metodo modify() (tipo di dati xml) | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- modify() method
- modify method
ms.assetid: 52430735-51f4-46d1-a308-9aecf8648fda
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b0c9866d90a532314c75ed65db9fbb0f6e764029
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47708509"
---
# <a name="modify-method-xml-data-type"></a>Metodo modify() (tipo di dati xml)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Modifica il contenuto di un documento XML. Usare questo metodo per modificare il contenuto di una variabile o colonna di tipo **xml**. Il metodo richiede un'istruzione XML DML per inserire, aggiornare o eliminare i nodi dai dati XML. Il metodo **modify()** del tipo di dati **xml** può essere usato unicamente nella clausola SET di un'istruzione UPDATE.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
modify (XML_DML)  
```  
  
## <a name="arguments"></a>Argomenti  
 XML_DML  
 Stringa nel linguaggio di manipolazione dei dati (DML, Data Manipulation Language) XML. Il documento XML viene aggiornato in base a questa espressione.  
  
> [!NOTE]  
>  Se il metodo **modify()** viene chiamato su un valore Null oppure restituisce un valore Null, viene restituito un errore.  
  
## <a name="examples"></a>Esempi  
 Dato che il metodo **modify()** richiede una stringa nel linguaggio di manipolazione dei dati XML (DML, Data Manipulation Language), gli esempi per **modify()** sono contenuti negli argomenti che descrivono le istruzioni XML DML. Per questi esempi, vedere [insert &#40;XML DML&#41;](../../t-sql/xml/insert-xml-dml.md), [delete &#40;XML DML&#41;](../../t-sql/xml/delete-xml-dml.md) e [replace value of &#40;XML DML&#41;](../../t-sql/xml/replace-value-of-xml-dml.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creare istanze di dati XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [metodi con tipo di dati XML](../../t-sql/xml/xml-data-type-methods.md)   
 [Linguaggio XML di manipolazione dei dati &#40;XML DML&#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
