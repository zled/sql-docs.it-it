---
title: Il mapping dei dati di parametro CLR | Documenti Microsoft
ms.custom: 
ms.date: 08/01/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SqlBinary data type
- SqlInt16 data type
- SqlMoney data type
- SqlString data type
- SqlSingle data type
- data types [CLR integration]
- SqlInt64 data type
- SqlDateTime data type
- SqlXml data type
- SqlBoolean data type
- SqlDecimal data type
- SqlBytes data type
- mapping data types [CLR integration]
- SqlChars data type
- SqlInt32 data type
ms.assetid: 89b43ee9-b9ad-4281-a4bf-c7c8d116daa2
caps.latest.revision: "71"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: bee49e277d3492dc93bcdf29b65c1c3007cebe50
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="mapping-clr-parameter-data"></a>Mapping dei dati dei parametri CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]La tabella seguente elenca [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipi di dati, i relativi equivalenti in common language runtime (CLR) per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel **System.Data.SqlTypes** dello spazio dei nomi e gli equivalenti CLR nativi nel [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET framework.  
  
||||  
|-|-|-|  
|**Tipo di dati di SQL Server**|Tipo (in System.Data.SqlTypes o Microsoft.SqlServer.Types)|**Tipo di dati CLR (.NET Framework)**|  
|**bigint**|**SqlInt64**|**Int64, Nullable\<Int64 >**|  
|**binary**|**SqlBytes, SqlBinary**|**Byte]**|  
|**bit**|**SqlBoolean**|**Ammette valori null, booleano\<booleano >**|  
|**char**|Nessuno|Nessuno|  
|**cursor**|Nessuno|Nessuno|  
|**data**|**SqlDateTime**|**Data/ora, Nullable\<DateTime >**|  
|**datetime**|**SqlDateTime**|**Data/ora, Nullable\<DateTime >**|  
|**datetime2**|Nessuno|**Data/ora, Nullable\<DateTime >**|  
|**DATETIMEOFFSET**|**Nessuno**|**DateTimeOffset, Nullable\<DateTimeOffset >**|  
|**decimal**|**SqlDecimal**|**Decimal, Nullable\<decimale >**|  
|**float**|**SqlDouble**|**Valore Double, ammette valori null\<Double >**|  
|**geography**|**SqlGeography**<br /><br /> **SqlGeography** è definito in Microsoft.SqlServer.Types.dll, che viene installato con SQL Server e può essere scaricato dal [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [feature pack di](https://www.microsoft.com/download/details.aspx?id=52676).|Nessuno|  
|**geometry**|**SqlGeometry**<br /><br /> **SqlGeometry** è definito in Microsoft.SqlServer.Types.dll, che viene installato con SQL Server e può essere scaricato dal [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [feature pack di](https://www.microsoft.com/download/details.aspx?id=52676).|Nessuno|  
|**hierarchyid**|**SqlHierarchyId**<br /><br /> **SqlHierarchyId** è definito in Microsoft.SqlServer.Types.dll, che viene installato con SQL Server e può essere scaricato dal [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [feature pack di](https://www.microsoft.com/download/details.aspx?id=52676).|Nessuno|  
|**image**|Nessuno|Nessuno|  
|**int**|**SqlInt32**|**Int32, Nullable\<Int32 >**|  
|**money**|**SqlMoney**|**Decimal, Nullable\<decimale >**|  
|**nchar**|**SqlChars, SqlString**|**Stringa, Char]**|  
|**ntext**|Nessuno|Nessuno|  
|**numeric**|**SqlDecimal**|**Decimal, Nullable\<decimale >**|  
|**nvarchar**|**SqlChars, SqlString**<br /><br /> **SQLChars** è una corrispondenza migliore per il trasferimento di dati e l'accesso, e **SQLString** è una corrispondenza migliore per l'esecuzione di operazioni di stringa.|**Stringa, Char]**|  
|**nvarchar(1), nchar (1)**|**SqlChars, SqlString**|**Char, String, Char [], Nullable\<char >**|  
|**real**|**SqlSingle** (l'intervallo di **SqlSingle**, tuttavia, è maggiore di **reale**)|**Singolo, ammette valori null\<singolo >**|  
|**rowversion**|Nessuno|**Byte]**|  
|**smallint**|**SqlInt16**|**Int16, Nullable\<Int16 >**|  
|**smallmoney**|**SqlMoney**|**Decimal, Nullable\<decimale >**|  
|**sql_variant**|Nessuno|**Oggetto**|  
|**table**|Nessuno|Nessuno|  
|**text**|Nessuno|Nessuno|  
|**time**|Nessuno|**Intervallo di tempo, Nullable\<TimeSpan >**|  
|**timestamp**|Nessuno|Nessuno|  
|**tinyint**|**SqlByte**|**Byte, che ammette valori null\<Byte >**|  
|**uniqueidentifier**|**SqlGuid**|**GUID, Nullable\<Guid >**|  
|**Type(UDT) definito dall'utente**|Nessuno|La stessa classe associata al tipo definito dall'utente (UDT) nello stesso assembly o un assembly dipendente.|  
|**varbinary**|**SqlBytes, SqlBinary**|**Byte]**|  
|**varbinary(1), binary(1)**|**SqlBytes, SqlBinary**|**byte, Byte [], Nullable\<byte >**|  
|**varchar**|Nessuno|Nessuno|  
|**xml**|**SqlXml**|Nessuno|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>Conversione automatica dei tipi di dati con parametri Out  
 Un metodo CLR può restituire informazioni per il codice o il programma chiamante contrassegnando un parametro di input con il **out** modificatore (Microsoft Visual c#) o  **\<out () > ByRef** (Microsoft Visual Basic) Se il parametro di input è un tipo di dati CLR nel **System.Data.SqlTypes** spazio dei nomi e il programma chiamante specifica equivalente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del tipo di dati come parametro di input, una conversione del tipo generato automaticamente Quando il metodo CLR restituisce il tipo di dati.  
  
 Ad esempio, la seguente stored procedure CLR è un parametro di input di **SqlInt32** tipo di dati CLR che è contrassegnato con **out** (c#) o  **\<out () > ByRef** ( Visual Basic):  
  
```csharp  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void PriceSum(out SqlInt32 value)  
{ … }  
```  
  
```vb  
\<Microsoft.SqlServer.Server.SqlProcedure> _  
Public Shared Sub PriceSum( \<Out()> ByRef value As SqlInt32)  
…  
End Sub  
```  
  
 Dopo che l'assembly compilato e creato nel database, la stored procedure viene creata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con Transact-SQL seguente, che consente di specificare un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati di **int** come parametro di OUTPUT:  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 Quando CLR stored procedure viene chiamata la **SqlInt32** tipo di dati viene convertito automaticamente in un **int** tipo di dati e restituito al programma chiamante.  
  
 Non tutti i tipi di dati CLR possono essere convertiti automaticamente nei tipi dei dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] equivalenti tramite un parametro out. Nella seguente tabella vengono descritte queste eccezioni.  
  
|||  
|-|-|  
|**Tipo di dati CLR (SQL Server)**|**Tipo di dati di SQL Server**|  
|**Decimale**|smallmoney|  
|**SqlMoney**|smallmoney|  
|**Decimale**|money|  
|**DateTime**|smalldatetime|  
|**SQLDateTime**|smalldatetime|  
  
## <a name="change-history"></a>Cronologia modifiche  
  
|Contenuto aggiornato|  
|---------------------|  
|Aggiunto **SqlGeography**, **SqlGeometry**, e **SqlHierarchyId** tipi alla tabella di mapping.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati di SQL Server in .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
