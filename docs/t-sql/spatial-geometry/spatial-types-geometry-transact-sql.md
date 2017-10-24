---
title: Geometry (Transact-SQL) | Documenti Microsoft
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
- geometry
dev_langs:
- TSQL
helpviewer_keywords:
- spatial data types [SQL Server]
- geometry data type [SQL Server], Transact-SQL
ms.assetid: 3fefdf7b-f931-404c-821c-82c0375eaf51
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2ba0303292df8bb8610831594393f6ec3072b5f3
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="spatial-types---geometry-transact-sql"></a>Tipi spaziali - geometry (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Il tipo di dati spaziali planari **geometry**, viene implementato come un tipo di dati di common language runtime (CLR) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questo tipo rappresenta i dati in un sistema di coordinate euclideo (piano).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]supporta un set di metodi per il **geometry** tipo di dati spaziali. Questi metodi includono metodi sul **geometry** che sono definiti dallo standard Open Geospatial Consortium (OGC) e un set di [!INCLUDE[msCoName](../../includes/msconame-md.md)] estensioni a tale standard.  
 
 La tolleranza di errore per i metodi di geometria può essere di dimensioni pari a 1.0-7 * extent. La distanza massima approssimativa tra i punti di consultare gli extent di **geometry**oggetto.
  
## <a name="registering-the-geometry-type"></a>Registrazione del tipo geometry  
 Il tipo **geometry** è predefinito e disponibile in ogni database. È possibile creare colonne di tabella di tipo **geometry** e operare sui dati **geometry** nello stesso modo in cui si utilizzano gli altri tipi CLR. Questo tipo può essere utilizzato in colonne calcolate persistenti e non persistenti.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-showing-how-to-add-and-query-geometry-data"></a>A. Informazioni su come aggiungere ed eseguire una query su dati geometry  
 Nei due esempi seguenti viene illustrato come aggiungere ed eseguire query su dati di tipo geometry. Nel primo esempio viene creata una tabella con una colonna Identity e una colonna `geometry`, ovvero `GeomCol1`. Una terza colonna effettua il rendering della colonna `geometry` nella rappresentazione Well-Known Text (WKT) OGC (Open Geospatial Consortium) e utilizza il metodo `STAsText()` . Vengono quindi inserite due righe: in una riga è contenuta un'istanza `LineString` di `geometry`e in una seconda è contenuta un'istanza `Polygon` .  
  
```tsql 
IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
    DROP TABLE dbo.SpatialTable;  
GO  
  
CREATE TABLE SpatialTable   
    ( id int IDENTITY (1,1),  
    GeomCol1 geometry,   
    GeomCol2 AS GeomCol1.STAsText() );  
GO  
  
INSERT INTO SpatialTable (GeomCol1)  
VALUES (geometry::STGeomFromText('LINESTRING (100 100, 20 180, 180 180)', 0));  
  
INSERT INTO SpatialTable (GeomCol1)  
VALUES (geometry::STGeomFromText('POLYGON ((0 0, 150 0, 150 150, 0 150, 0 0))', 0));  
GO  
```  
  
### <a name="b-returning-the-intersection-of-two-geometry-instances"></a>B. Restituzione dell'intersezione di due istanze geometry  
 Nel secondo esempio viene utilizzato il metodo `STIntersection()` per restituire i punti in cui si intersecano le due istanze `geometry` inserite in precedenza.  
  
```tsql  
DECLARE @geom1 geometry;  
DECLARE @geom2 geometry;  
DECLARE @result geometry;  
  
SELECT @geom1 = GeomCol1 FROM SpatialTable WHERE id = 1;  
SELECT @geom2 = GeomCol1 FROM SpatialTable WHERE id = 2;  
SELECT @result = @geom1.STIntersection(@geom2);  
SELECT @result.STAsText();  
```  
  
### <a name="c-using-geometry-in-a-computed-column"></a>C. Utilizzo del tipo geometry in una colonna calcolata  
 Nell'esempio seguente viene creata una tabella con una colonna calcolata persistente utilizzando un **geometry** tipo.  
  
```tsql  
IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
    DROP TABLE dbo.SpatialTable;  
GO  
  
CREATE TABLE SpatialTable  
(  
    locationId int IDENTITY(1,1),  
    location geometry,  
    deliveryArea as location.STBuffer(10) persisted  
)  
```  
  
## <a name="see-also"></a>Vedere anche  
  [Dati spaziali &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  

