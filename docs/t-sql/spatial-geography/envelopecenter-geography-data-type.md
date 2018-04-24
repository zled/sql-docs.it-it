---
title: EnvelopeCenter (tipo di dati geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- EnvelopeCenter
- EnvelopeCenter_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- EnvelopeCenter method
ms.assetid: dee9d807-faad-45b8-b3f3-7e8aa7d07147
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f72f27b98f97cfe15d853a961d194cfb7d1f25ad
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="envelopecenter-geography-data-type-"></a>EnvelopeCenter (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce un punto che può essere usato come centro di un cerchio di delimitazione per l'istanza **geography**.  
  
 Per determinare il cerchio di delimitazione, ogni punto nell'istanza viene descritto come un vettore dal centro della terra al punto sulla superficie della terra. Il punto centrale del cerchio di delimitazione viene calcolato come media di tutti i vettori. Per i cicli chiusi, in un'istanza **polygon** o **linestring** il primo e l'ultimo punto vengono usati solo una volta.  
  
 Questo metodo con tipo di dati **geography** supporta le istanze **FullGlobe** o le istanze spaziali con dimensioni maggiori di un emisfero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
EnvelopeCenter( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 Questo metodo restituisce un elemento **point**. Se usato con `EnvelopeAngle()`, `EnvelopeCenter()` restituisce un cerchio di delimitazione di un'istanza **geography**.  
  
> [!NOTE]  
>  `EnvelopeCenter()` restituisce un cerchio di delimitazione per un'istanza **geography**, ma i risultati non garantiscono l'ottenimento del cerchio di delimitazione minimo. Al contrario, il metodo `STEnvelope()` con tipo di dati **geometry** garantisce la restituzione del rettangolo di selezione minimo quando viene applicato a un'istanza **geometry**.  
  
 In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e versioni successive, restituisce il centro del cerchio che rappresenta la busta di questa istanza come **point**. Per tutti gli oggetti di grandi dimensioni, come definito da `EnvelopeAngle()` = 180, `EnvelopeCenter()` restituirà (90,0).  
  
 Il metodo non è preciso.  
  
## <a name="examples"></a>Esempi  
  
```  
DECLARE @g geography = 'LINESTRING(-120 45, -120 0, -90 0)';  
SELECT @g.EnvelopeCenter().ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geografia](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [EnvelopeAngle &#40;tipo di dati geography&#41;](../../t-sql/spatial-geography/envelopeangle-geography-data-type.md)  
  
  
