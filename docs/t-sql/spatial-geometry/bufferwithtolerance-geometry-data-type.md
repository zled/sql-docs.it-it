---
title: BufferWithTolerance (tipo di dati geometry) | Documenti Microsoft
ms.custom: 
ms.date: 08/03/2017
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
- BufferWithTolerance (geometry Data Type)
ms.assetid: 7049d37a-3e72-4e93-87a1-c96a6f0e2b99
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ffa8a350cb4531f9d4a6d1439a4dad0682189266
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="bufferwithtolerance-geometry-data-type"></a>BufferWithTolerance (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce i valori di un oggetto geometrico che rappresenta l'unione di tutti i punti la cui distanza da un **geometry** istanza è minore o uguale a un valore specificato, consentendo una tolleranza specificata.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.BufferWithTolerance ( distance, tolerance, relative )  
```  
  
## <a name="arguments"></a>Argomenti  
 *distanza*  
 È un **float** espressione che specifica la distanza tra il **geometry** istanza intorno alla quale calcolare il buffer.  
  
 *tolleranza di errore*  
 È un **float** espressione che specifica la tolleranza della distanza del buffer.  
  
 *Tolleranza* indica la variazione massima della distanza del buffer ideale per l'approssimazione lineare restituita.  
  
 La distanza ideale del buffer di un punto ad esempio è un cerchio, che però deve essere approssimato da un poligono. Minore è il valore della tolleranza, maggiore sarà il numero di punti del poligono. In questo caso aumenterà la complessità del risultato, ma diminuirà l'errore.  
  
 *relativo*  
 È un **bit** che specifica se il *tolleranza* valore è relativo o assoluto. Se 'TRUE' o 1, quindi tolleranza è relativa e viene calcolata come prodotto tra il *tolleranza* parametro e il diametro del rettangolo di selezione dell'istanza. Se 'FALSE' o 0, tolleranza è assoluta e *tolleranza* valore è la variazione massima assoluta nella distanza del buffer ideale per l'approssimazione lineare restituita.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
## <a name="exceptions"></a>Eccezioni  
 Il *tolleranza* parametro deve essere maggiore di zero. Se *tolleranza* < = 0, quindi un `System.ArgumentOutOfRangeException` viene generata un'eccezione.  
  
> [!NOTE]  
>  Poiché *tolleranza* è un **float** tipo, un `System.Runtime.InteropServices.COMException` può essere generata se il valore specificato per la tolleranza è minimo a causa di problemi di arrotondamento con tipi a virgola mobile.  
  
## <a name="remarks"></a>Osservazioni  
 Quando *distanza* > 0, un **poligono** o **MultiPolygon** istanza viene restituita.  
  
> [!NOTE]  
>  Poiché la distanza è un **float**, un valore estremamente ridotto può corrispondere a zero nei calcoli. Quando ciò si verifica, una copia del chiamante **geometry** istanza viene restituita. Vedere [float e real &#40; Transact-SQL &#41; ](../../t-sql/data-types/float-and-real-transact-sql.md).  
  
 Quando *distanza* = 0, una copia del chiamante **geometry** istanza viene restituita.  
  
 Quando *distanza* < 0,  
  
-   un oggetto vuoto **GeometryCollection** istanza viene restituita quando le dimensioni dell'istanza sono 0 o 1.  
  
-   Viene restituito un buffer negativo quando le dimensioni dell'istanza sono 2 o maggiori di 2.  
  
    > [!NOTE]  
    >  Un buffer negativo può inoltre creare un oggetto vuoto **GeometryCollection** istanza.  
  
 Un buffer negativo rimuove tutti i punti all'interno della distanza specificata del limite del **geometry** istanza.  
  
 L'errore tra il buffer calcolato e quello teorico è max (tolleranza, extent \* all'1. e-7) in cui tolleranza di errore è il valore della *tolleranza* parametro. Per ulteriori informazioni sulle estensioni, vedere [metodo riferimento al tipo di dati geometry](http://msdn.microsoft.com/library/d88e632b-6b2f-4466-a15f-9fbef1a347a7).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `Point` e viene utilizzato `BufferWithTolerance()` per ottenere un buffer approssimato intorno all'istanza stessa.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(3 3)', 0);  
SELECT @g.BufferWithTolerance(1, .5, 0).ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [STBuffer &#40; tipo di dati geometry &#41;](../../t-sql/spatial-geometry/stbuffer-geometry-data-type.md)   
 [Metodi estesi sulle istanze di geometria](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  


