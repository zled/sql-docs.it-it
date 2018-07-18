---
title: Oggetto SqlDataRecord | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SqlDataRecord object
- custom result sets [CLR integration]
ms.assetid: 2ed667fb-749c-4280-a8fb-650643683c8f
caps.latest.revision: 25
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: eed4ff836262fdf9a2a0cbb4d48e7b9fc7c4b94a
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37359923"
---
# <a name="sqldatarecord-object"></a>Oggetto SqlDataRecord
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Il **SqlDataRecord** oggetto rappresenta una singola riga di dati, insieme ai relativi metadati.  
  
 Le stored procedure gestite possono inviare al client set di risultati che non provengono da un **SqlDataReader**. Il **SqlDataRecord** classe, insieme con **SendResultsStart**, **SendResultsRow**, e **SendResultsEnd** metodi del **SqlPipe** oggetto, consente alle stored procedure per l'invio di set di risultati personalizzati al client.  
  
 Per altre informazioni, vedere la **Microsoft.SqlServer.Server.SqlDataRecord** classe documentazione di riferimento nella documentazione di .NET Framework SDK.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene creato un nuovo record relativo a un dipendente, che viene successivamente restituito al chiamante.  
  
 C#  
  
```  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void CreateNewRecordProc()  
{  
    // Variables.         
    SqlDataRecord record;  
  
    // Create a new record with the column metadata.  The constructor   
    // is able to accept a variable number of parameters.  
    record = new SqlDataRecord(new SqlMetaData("EmployeeID", SqlDbType.Int),  
                               new SqlMetaData("Surname", SqlDbType.NVarChar, 20),  
                               new SqlMetaData("GivenName", SqlDbType.NVarChar, 20),  
                               new SqlMetaData("StartDate", SqlDbType.DateTime) );  
  
    // Set the record fields.  
    record.SetInt32(0, 0042);  
    record.SetString(1, "Funk");  
    record.SetString(2, "Don");  
    record.SetDateTime(3, new DateTime(2005, 7, 17));  
  
    // Send the record to the calling program.  
    SqlContext.Pipe.Send(record);  
  
}  
```  
  
 Visual Basic  
  
```  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub  CreateNewRecordVBProc ()  
    ' Variables.  
    Dim record As SqlDataRecord  
  
    ' Create a new record with the column metadata. The constructor is   
    ' able to accept a variable number of parameters  
  
    record = New SqlDataRecord(New SqlMetaData("EmployeeID", SqlDbType.Int), _  
                           New SqlMetaData("Surname", SqlDbType.NVarChar, 20), _  
                           New SqlMetaData("GivenName", SqlDbType.NVarChar, 20), _  
                           New SqlMetaData("StartDate", SqlDbType.DateTime))  
  
    ' Set the record fields.  
    record.SetInt32(0, 42)  
    record.SetString(1, "Funk")  
    record.SetString(2, "Don")  
    record.SetDateTime(3, New DateTime(2005, 7, 17))  
  
    ' Send the record to the calling program.  
    SqlContext.Pipe.Send(record)  
  
End Sub  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto SqlPipe](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md)  
  
  
