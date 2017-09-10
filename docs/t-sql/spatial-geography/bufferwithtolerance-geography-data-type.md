---
title: BufferWithTolerance (tipo di dati geography) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BufferWithTolerance_TSQL
- BufferWithTolerance
dev_langs:
- TSQL
helpviewer_keywords:
- BefferWithTolerance method
ms.assetid: f1783e6b-0f17-464f-b1c7-1c3f7d8aa042
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: feaa401cfd6e2077035d164412941392412011ae
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="bufferwithtolerance-geography-data-type"></a>BufferWithTolerance (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce i valori di un oggetto geometrico che rappresenta l'unione di tutti i punti la cui distanza da un **geography** istanza è minore o uguale a un valore specificato, consentendo una tolleranza specificata.  
  
 Metodo supportata dal tipo di dati geography **FullGlobe** istanze o le istanze spaziali con dimensioni maggiori di un emisfero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.BufferWithTolerance ( distance, tolerance, relative )  
```  
  
## <a name="arguments"></a>Argomenti  
 *distanza*  
 È un **float** espressione che specifica la distanza tra il **geography** istanza intorno alla quale calcolare il buffer.  
  
 La distanza massima del buffer non può superare 0,999 \* *π* * minorAxis \* minorAxis / majorAxis (~0.999 \* della circonferenza della terra di 1/2) o l'intero globo.  
  
 *tolleranza di errore*  
 È un **float** espressione che specifica la tolleranza della distanza del buffer.  
  
 Il *tolleranza* valore indica la variazione massima della distanza del buffer ideale per l'approssimazione lineare restituita.  
  
 La distanza ideale del buffer di un punto ad esempio è un cerchio, che però deve essere approssimato da un poligono. Minore è il valore della tolleranza, maggiore sarà il numero di punti del poligono. In questo caso aumenterà la complessità del risultato, ma diminuirà l'errore.  
  
 Il limite minimo è lo 0,1 percento della distanza e qualsiasi tolleranza inferiore verrà arrotondata al limite minimo.  
  
 *relativo*  
 È un **bit** che specifica se il *tolleranza* valore è relativo o assoluto. Se 'TRUE' o 1, tolleranza è relativa e viene calcolata come prodotto tra il *tolleranza* parametro e l'estensione angolare \* raggio equatoriale dell'ellissoide. Se 'FALSE' o 0, tolleranza è assoluta e *tolleranza* valore è la variazione massima assoluta nella distanza del buffer ideale per l'approssimazione lineare restituita.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo genererà un' **ArgumentException** se il *distanza* non è un numero (NAN) oppure se *distanza* è infinito positivo o negativo.  Questo metodo genererà inoltre un **ArgumentException** se *tolleranza* è zero (0), non un numero (NaN), infinito negativo o positivo o negativo.  
  
 `STBuffer()`verrà restituito un **FullGlobe** istanza in determinati casi; ad esempio, `STBuffer()` restituisce un **FullGlobe** istanza su due poli quando la distanza del buffer è maggiore della distanza dall'equatore a poli.  
  
 Questo metodo genererà un' **ArgumentException** in **FullGlobe** istanze in cui la distanza del buffer eccede il limite seguente:  
  
 0,999 \* *π* * minorAxis \* minorAxis / majorAxis (~0.999 \* della circonferenza della terra di 1/2)  
  
 L'errore tra il buffer calcolato e quello teorico è max (tolleranza, extent \* all'1. e-7) in cui tolleranza di errore è il valore della *tolleranza* parametro. Per ulteriori informazioni sulle estensioni, vedere [metodo riferimento al tipo di dati geography](http://msdn.microsoft.com/library/028e6137-7128-4c74-90a7-f7bdd2d79f5e).  
  
 Il metodo non è preciso.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `Point` e viene utilizzato `BufferWithTolerance()` per ottenere un buffer approssimato intorno all'istanza stessa.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.BufferWithTolerance(1, .5, 0).ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [STBuffer &#40; tipo di dati geography &#41;](../../t-sql/spatial-geography/stbuffer-geography-data-type.md)   
 [Metodi estesi sulle istanze di geografia](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
