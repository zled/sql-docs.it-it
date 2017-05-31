---
title: Usare l&quot;output FOR JSON in SQL Server e nelle app client (SQL Server) | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR JSON, using in client apps
- FOR JSON, using in SQL Server
ms.assetid: 302e5397-b499-4ea3-9a7f-c24ccad698eb
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5331ff00081a7b79756ef14e771ab4a22d3e35ac
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="use-for-json-output-in-sql-server-and-in-client-apps-sql-server"></a>Usare l'output FOR JSON in SQL Server e nelle app client (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Gli esempi seguenti illustrano alcuni modi per usare la clausola **FOR JSON** o il relativo output in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o nelle app client.  
  
## <a name="use-for-json-output-in-sql-server-variables"></a>Usare l'output FOR JSON nelle variabili di SQL Server  
 L'output della clausola JSON FOR è di tipo NVARCHAR(MAX), quindi può essere assegnato a qualsiasi variabile, come mostrato nell'esempio seguente.  
  
```tsql  
DECLARE @x NVARCHAR(MAX) = (SELECT TOP 10 * FROM Sales.SalesOrderHeader FOR JSON AUTO)  
```  
  
## <a name="use-for-json-output-in-sql-server-user-defined-functions"></a>Usare l'output FOR JSON nelle funzioni SQL Server definite dall'utente  
 È possibile creare funzioni definite dall'utente che formattano i set di risultati come JSON e restituiscono questo output JSON. Nell'esempio seguente viene creata una funzione definita dall'utente che recupera alcune righe di dettaglio di un ordine di vendita e le formatta come matrice JSON.  
  
```tsql  
CREATE FUNCTION GetSalesOrderDetails(@salesOrderId int)  
 RETURNS NVARCHAR(MAX)  
AS  
BEGIN  
   RETURN (SELECT UnitPrice, OrderQty  
           FROM Sales.SalesOrderDetail  
           WHERE SalesOrderID = @salesOrderId  
           FOR JSON AUTO)  
END
```  
  
 Questa funzione può essere usata in un batch o in una query, come mostrato nell'esempio seguente.  
  
```tsql  
DECLARE @x NVARCHAR(MAX)=dbo.GetSalesOrderDetails(43659)

PRINT dbo.GetSalesOrderDetails(43659)

SELECT TOP 10
  H.*,dbo.GetSalesOrderDetails(H.SalesOrderId) AS Details
FROM Sales.SalesOrderHeader H
```  
  
## <a name="merge-parent-and-child-data-into-a-single-table"></a>Unire dati padre e figlio in una singola tabella  
 Nell'esempio seguente ogni set di righe figlio è formattato come matrice JSON e diventa il valore della colonna Dettagli nella tabella padre.  
  
```tsql  
SELECT TOP 10 SalesOrderId, OrderDate,  
      (SELECT TOP 3 UnitPrice, OrderQty  
         FROM Sales.SalesOrderDetail D  
         WHERE H.SalesOrderId = D.SalesOrderID  
         FOR JSON AUTO) as Details  
INTO SalesOrder  
FROM Sales.SalesOrderHeader H  
```  
  
## <a name="update-the-data-in-json-columns"></a>Aggiornare i dati nelle colonne JSON  
 L'esempio seguente dimostra che è possibile aggiornare il valore delle colonne che contengono testo JSON.  
  
```tsql  
UPDATE SalesOrder  
SET Details =  
     (SELECT TOP 1 UnitPrice, OrderQty  
       FROM Sales.SalesOrderDetail D  
       WHERE D.SalesOrderId = SalesOrder.SalesOrderId  
      FOR JSON AUTO 
```  
  
## <a name="use-for-json-output-in-a-c-client-app"></a>Usare l'output FOR JSON in un'app client C#  
 L'esempio seguente mostra come recuperare l'output JSON di una query in un oggetto StringBuilder in un'app client C#. Si supponga che la variabile queryWithForJson contenga il testo di un'istruzione SELECT con una clausola FOR JSON.  
  
```csharp  
            var queryWithForJson = "SELECT ... FOR JSON";
            var conn = new SqlConnection("<connection string>");
            var cmd = new SqlCommand(queryWithForJson, conn);
            conn.Open();
            var jsonResult = new StringBuilder();
            var reader = cmd.ExecuteReader();
            if (!reader.HasRows)
            {
                jsonResult.Append("[]");
            }
            else
            {
                while (reader.Read())
                {
                    jsonResult.Append(reader.GetValue(0).ToString());
                }
            }
```  
  
## <a name="see-also"></a>Vedere anche  
 [Formattare i risultati delle query in formato JSON con FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  

