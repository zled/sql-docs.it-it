---
title: EnvelopeCenter (tipo di dati geography) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EnvelopeCenter
- EnvelopeCenter_TSQL
dev_langs: TSQL
helpviewer_keywords: EnvelopeCenter method
ms.assetid: dee9d807-faad-45b8-b3f3-7e8aa7d07147
caps.latest.revision: "17"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 07b46f0d198fe2e90456252c9b1ad95669cfc478
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="envelopecenter-geography-data-type-"></a>EnvelopeCenter (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce un punto che può essere utilizzato come centro di un cerchio di delimitazione per il **geography** istanza.  
  
 Per determinare il cerchio di delimitazione, ogni punto nell'istanza viene descritto come un vettore dal centro della terra al punto sulla superficie della terra. Il punto centrale del cerchio di delimitazione viene calcolato come media di tutti i vettori. Per i cicli chiusi, in un **poligono** istanza o un **linestring** istanza, il primo e ultimo punto viene utilizzata una sola volta.  
  
 Questo **geography** metodo supportata dal tipo di dati **FullGlobe** istanze o le istanze spaziali con dimensioni maggiori di un emisfero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
EnvelopeCenter( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo restituisce un **punto**. Se usato con `EnvelopeAngle()`, `EnvelopeCenter()` restituisce un cerchio di delimitazione di un **geography** istanza.  
  
> [!NOTE]  
>  `EnvelopeCenter()`Restituisce un cerchio di delimitazione per un **geography** istanza, ma i risultati non sono garantiti per produrre il cerchio di delimitazione minimo. Al contrario, il **geometry** metodo con tipo di dati `STEnvelope()` è garantita per restituire il rettangolo di selezione minimo quando viene applicato a un **geometry** istanza.  
  
 In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e versioni successive, restituisce il centro del cerchio che rappresenta la busta di questa istanza è un **punto**. Per tutti gli oggetti di grandi dimensioni, come definito da `EnvelopeAngle()` = 180, `EnvelopeCenter()` restituirà (90,0).  
  
 Il metodo non è preciso.  
  
## <a name="examples"></a>Esempi  
  
```  
DECLARE @g geography = 'LINESTRING(-120 45, -120 0, -90 0)';  
SELECT @g.EnvelopeCenter().ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geografia](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [EnvelopeAngle &#40; tipo di dati geography &#41;](../../t-sql/spatial-geography/envelopeangle-geography-data-type.md)  
  
  
