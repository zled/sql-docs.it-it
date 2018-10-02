---
title: ReorientObject (tipo di dati geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ReorientObject
- ReorientObject_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ReorientObject method (geography)
ms.assetid: e2a1a4f1-211b-4e82-abed-03fc7140a83c
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0f14609b70d5984be8166e17a5388297fead4db0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47800084"
---
# <a name="reorientobject-geography-data-type"></a>ReorientObject (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Restituisce un'istanza **geography** con aree esterne e interne scambiate.  
  
 Questo metodo con tipo di dati **geography** supporta le istanze **FullGlobe** o le istanze spaziali con dimensioni maggiori di un emisfero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.ReorientObject (geography)  
```  
  
## <a name="arguments"></a>Argomenti  
 *geography*  
 Altra istanza **geography** su cui viene richiamato `ReorientObject()`.  
  
## <a name="return-value"></a>Valore restituito  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 Questo metodo modifica l'orientamento dell'anello di tutti gli oggetti **Polygon** in una **GeometryCollection** ma non rimuove né modifica alcun **Point** o **Linestring** nella raccolta specificata.  
  
 Se una **GeometryCollection** viene passata a questo metodo, ogni istanza della raccolta viene riorientata, ma non viene riorientata la raccolta nel suo complesso.  
  
## <a name="examples"></a>Esempi  
  
```  
DECLARE @R GEOGRAPHY = GEOGRAPHY::Parse('Polygon((-10 -10, -10 10, 10 10, 10 -10, -10 -10))');  
SELECT @R.ReorientObject().STAsText();  
--Result: POLYGON ((10 10, -10 10, -10 -10, 10 -10, 10 10))  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze geografiche](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
