---
title: Espressioni aritmetiche (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- expressions [XQuery], arithmetic
- arithmetic expressions
ms.assetid: 90d675bf-56da-459a-9771-8cd13920a9fc
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3d970209b71a842aa1c78b2f7dd0db980e0ce73e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47642649"
---
# <a name="arithmetic-expressions-xquery"></a>Espressioni aritmetiche (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Sono supportati tutti gli operatori aritmetici, ad eccezione di **idiv**. Negli esempi seguenti viene illustrato l'utilizzo di base degli operatori aritmetici:  
  
```  
DECLARE @x xml  
SET @x=''  
SELECT @x.query('2 div 2')  
SELECT @x.query('2 * 2')  
```  
  
 In quanto **idiv** non è supportati, una soluzione consiste nell'utilizzare il **xs:integer()** costruttore:  
  
```  
DECLARE @x xml  
SET @x=''  
-- Following will not work  
-- SELECT @x.query('2 idiv 2')  
-- Workaround   
SELECT @x.query('xs:integer(2 div 3)')  
```  
  
 Il tipo risultante da un operatore aritmetico dipende dai tipi dei valori di input. Se gli operandi sono di tipo diverso, all'occorrenza verrà eseguito il cast di uno o entrambi gli operandi a un tipo di base primitivo comune, in base alla gerarchia dei tipi. Per informazioni sulla gerarchia dei tipi, vedere [regole di cast di tipi in XQuery](../xquery/type-casting-rules-in-xquery.md).  
  
 È possibile che i tipi numeric vengano promossi se ai due operandi sono associati tipi di base numerici diversi. Ad esempio, aggiungendo un **xs: decimal** a un **xs: double** innanzitutto modificare il valore decimale in un valore double. Viene quindi eseguita l'addizione, il cui risultato sarà un valore double.  
  
 Vengono eseguito il cast al tipo di base numerico di altro operando o di valori atomici non tipizzati **xs: double** se anche l'altro operando non è tipizzato.  
  
## <a name="implementation-limitations"></a>Limitazioni di implementazione  
 Limitazioni:  
  
-   Gli argomenti per gli operatori aritmetici devono essere di tipo numerico o **untypedAtomic**.  
  
-   Operazioni sui **xs: integer** i valori restituiscono un valore di tipo **xs: decimal** anziché **xs: integer**.  
  
  
