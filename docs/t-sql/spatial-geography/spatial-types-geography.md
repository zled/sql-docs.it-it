---
title: Geography (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- geography
dev_langs:
- TSQL
helpviewer_keywords:
- geography data type [SQL Server], Transact-SQL
- spatial data types [SQL Server]
ms.assetid: d9e4952a-1841-4465-a64b-11e9288dba1d
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 2f9a5b86f49e2d5e9b07908cd3c866999ff2f646
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="spatial-types---geography"></a>Tipi di dati spaziali, geography
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Il tipo di dati spaziali geografici, **geography**, viene implementato come common language runtime (CLR) tipo di dati .NET nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questo tipo rappresenta i dati in un sistema di coordinate di tipo terra rotonda. Il tipo di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **geography** archivia dati ellissoidali (terra rotonda), ad esempio coordinate di latitudine e longitudine GPS.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]supporta un set di metodi per il **geography** tipo di dati spaziali. Inclusi metodi per **geography** che sono definiti dallo standard Open Geospatial Consortium (OGC) e un set di [!INCLUDE[msCoName](../../includes/msconame-md.md)] estensioni a tale standard.  
 
 La tolleranza di errore per il **geography** metodi possono essere di dimensioni pari a 1.0-7 * extent. La distanza massima approssimativa tra i punti di consultare gli extent di **geography**oggetto.
  

## <a name="registering-the-geography-type"></a>Registrazione di un tipo geography  
 Il tipo **geography** è predefinito e disponibile in ogni database. È possibile creare colonne di tabella di tipo **geography** e usare dati **geography** nello stesso modo in cui vengono usati gli altri tipi forniti dal sistema. Questo tipo può essere utilizzato in colonne calcolate persistenti e non persistenti.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-showing-how-to-add-and-query-geography-data"></a>A. Informazioni su come aggiungere ed eseguire una query su dati geography  
 Negli esempi seguenti viene illustrato come aggiungere ed eseguire query su dati geography. Nel primo esempio viene creata una tabella con una colonna Identity e una colonna `geography`, ovvero `GeogCol1`. Una terza colonna effettua il rendering della colonna `geography` nella rappresentazione Well-Known Text (WKT) OGC (Open Geospatial Consortium) e utilizza il metodo `STAsText()`. Vengono quindi inserite due righe: in una riga è contenuta un'istanza `LineString` di `geography`e in una seconda è contenuta un'istanza `Polygon` .  
  
```  
IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
    DROP TABLE dbo.SpatialTable;  
GO  
  
CREATE TABLE SpatialTable   
    ( id int IDENTITY (1,1),  
    GeogCol1 geography,   
    GeogCol2 AS GeogCol1.STAsText() );  
GO  
  
INSERT INTO SpatialTable (GeogCol1)  
VALUES (geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656 )', 4326));  
  
INSERT INTO SpatialTable (GeogCol1)  
VALUES (geography::STGeomFromText('POLYGON((-122.358 47.653 , -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326));  
GO  
```  
  
### <a name="b-returning-the-intersection-of-two-geography-instances"></a>B. Restituzione dell'intersezione di due istanze geografiche  
 Nell'esempio seguente viene utilizzato il metodo `STIntersection()` per restituire i punti in cui si intersecano le due istanze `geography` inserite in precedenza.  
  
```  
DECLARE @geog1 geography;  
DECLARE @geog2 geography;  
DECLARE @result geography;  
  
SELECT @geog1 = GeogCol1 FROM SpatialTable WHERE id = 1;  
SELECT @geog2 = GeogCol1 FROM SpatialTable WHERE id = 2;  
SELECT @result = @geog1.STIntersection(@geog2);  
SELECT @result.STAsText();  
```  
  
### <a name="c-using-geography-in-a-computed-column"></a>C. Utilizzo del tipo geography in una colonna calcolata  
 Nell'esempio seguente viene creata una tabella con una colonna calcolata persistente utilizzando un **geography** tipo.  
  
```  
IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
    DROP TABLE dbo.SpatialTable;  
GO  
  
CREATE TABLE SpatialTable  
(  
    locationId int IDENTITY(1,1),  
    location geography,  
    deliveryArea as location.STBuffer(10) persisted  
)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Dati spaziali &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)   

  
  
