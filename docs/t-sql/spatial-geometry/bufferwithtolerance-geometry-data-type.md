---
title: BufferWithTolerance (tipo di dati geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- BufferWithTolerance_TSQL
- BufferWithTolerance
dev_langs:
- TSQL
helpviewer_keywords:
- BufferWithTolerance (geometry Data Type)
ms.assetid: 7049d37a-3e72-4e93-87a1-c96a6f0e2b99
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: dc1dd1617ff0bcdd30782b5c7890f60aa30258f1
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51700949"
---
# <a name="bufferwithtolerance-geometry-data-type"></a>BufferWithTolerance (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un oggetto geometrico che rappresenta l'unione dei valori di tutti i punti la cui distanza da un'istanza **geometry** è minore o uguale a un valore specificato, consentendo una tolleranza specificata.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.BufferWithTolerance ( distance, tolerance, relative )  
```  
  
## <a name="arguments"></a>Argomenti  
 *distance*  
 Espressione **float** che specifica la distanza dall'istanza **geometry** intorno alla quale calcolare il buffer.  
  
 *tolerance*  
 Espressione **float** che specifica la tolleranza della distanza del buffer.  
  
 Il termine *tolleranza* indica la variazione massima nella distanza ideale del buffer per l'approssimazione lineare restituita.  
  
 La distanza ideale del buffer di un punto ad esempio è un cerchio, che però deve essere approssimato da un poligono. Minore è il valore della tolleranza, maggiore sarà il numero di punti del poligono. In questo caso aumenterà la complessità del risultato, ma diminuirà l'errore.  
  
 *relative*  
 Valore **bit** che specifica se il valore *tolerance* è relativo o assoluto. Se il valore è TRUE o 1, la tolleranza è relativa e viene calcolata come prodotto tra il parametro *tolerance* e il diametro del rettangolo di contenimento dell'istanza. Se il valore è FALSE o 0, la tolleranza è assoluta e il valore *tolerance* è la variazione massima assoluta nella distanza ideale del buffer per l'approssimazione lineare restituita.  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
## <a name="exceptions"></a>Eccezioni  
 Il parametro *tolerance* deve essere maggiore di zero. Se *tolerance* <= 0 viene generata un'eccezione `System.ArgumentOutOfRangeException`.  
  
> [!NOTE]  
>  Poiché *tolerance* è di tipo **float**, è possibile che venga generata un'eccezione `System.Runtime.InteropServices.COMException` se il valore specificato per la tolleranza è estremamente ridotto. Ciò è dovuto a problemi di arrotondamento dei tipi a virgola mobile.  
  
## <a name="remarks"></a>Remarks  
 Se *distance* > 0 viene restituita un'istanza **Polygon** o **MultiPolygon**.  
  
> [!NOTE]  
>  Poiché distance è di tipo **float**, un valore estremamente ridotto può corrispondere a zero nei calcoli. Quando ciò si verifica, viene restituita una copia dell'istanza **geometry** chiamante. Vedere [float e real &#40;Transact-SQL&#41;](../../t-sql/data-types/float-and-real-transact-sql.md).  
  
 Quando *distance* = 0 viene restituita una copia dell'istanza **geometry** chiamante.  
  
 Quando *distance* < 0  
  
-   Viene restituita un'istanza **GeometryCollection** vuota se le dimensioni dell'istanza sono 0 o 1.  
  
-   Viene restituito un buffer negativo quando le dimensioni dell'istanza sono 2 o maggiori di 2.  
  
    > [!NOTE]  
    >  È possibile che un buffer negativo crei un'istanza **GeometryCollection** vuota.  
  
 Un buffer negativo rimuove tutti i punti all'interno della distanza specificata del limite dell'istanza **geometry**.  
  
 L'errore tra il buffer calcolato e quello teorico è max(tolerance, extents \* 1.E-7) dove tolerance è il valore del parametro *tolerance*. Per altre informazioni sulle estensioni, vedere la [Guida di riferimento ai metodi per il tipo di dati geometry](https://msdn.microsoft.com/library/d88e632b-6b2f-4466-a15f-9fbef1a347a7).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `Point` e viene utilizzato `BufferWithTolerance()` per ottenere un buffer approssimato intorno all'istanza stessa.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(3 3)', 0);  
SELECT @g.BufferWithTolerance(1, .5, 0).ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [STBuffer &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stbuffer-geometry-data-type.md)   
 [Metodi estesi sulle istanze di geometria](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

