---
title: Espressioni aritmetiche (XQuery) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- expressions [XQuery], arithmetic
- arithmetic expressions
ms.assetid: 90d675bf-56da-459a-9771-8cd13920a9fc
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0736594cec09f9deb31340ab4d4e3c1fa052496b
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="arithmetic-expressions-xquery"></a>Espressioni aritmetiche (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Sono supportati tutti gli operatori aritmetici, ad eccezione di **idiv**. Negli esempi seguenti viene illustrato l'utilizzo di base degli operatori aritmetici:  
  
```  
DECLARE @x xml  
SET @x=''  
SELECT @x.query('2 div 2')  
SELECT @x.query('2 * 2')  
```  
  
 Poiché **idiv** non è supportato, una soluzione consiste nell'utilizzare il **xs:integer()** costruttore:  
  
```  
DECLARE @x xml  
SET @x=''  
-- Following will not work  
-- SELECT @x.query('2 idiv 2')  
-- Workaround   
SELECT @x.query('xs:integer(2 div 3)')  
```  
  
 Il tipo risultante da un operatore aritmetico dipende dai tipi dei valori di input. Se gli operandi sono di tipo diverso, all'occorrenza verrà eseguito il cast di uno o entrambi gli operandi a un tipo di base primitivo comune, in base alla gerarchia dei tipi. Per informazioni sulla gerarchia dei tipi, vedere [le regole di cast di tipo in XQuery](../xquery/type-casting-rules-in-xquery.md).  
  
 È possibile che i tipi numeric vengano promossi se ai due operandi sono associati tipi di base numerici diversi. Ad esempio, aggiungendo un **xs: decimal** per un **xs: double** innanzitutto modificare il valore decimale in un valore double. Viene quindi eseguita l'addizione, il cui risultato sarà un valore double.  
  
 Vengono eseguito il cast al tipo di base numerico di altro operando o di valori atomici non tipizzati **xs: double** se anche l'altro operando non è tipizzato.  
  
## <a name="implementation-limitations"></a>Limitazioni di implementazione  
 Limitazioni:  
  
-   Gli argomenti per gli operatori aritmetici devono essere di tipo numerico o **untypedAtomic**.  
  
-   Operazioni su **xs: integer** valori restituiscono un valore di tipo **xs: decimal** anziché **xs: integer**.  
  
  
