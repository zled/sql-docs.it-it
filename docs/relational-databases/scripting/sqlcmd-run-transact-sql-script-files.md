---
title: Eseguire file script Transact-SQL mediante sqlcmd | Microsoft Docs
ms.custom: ''
ms.date: 07/15/2016
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-scripting
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transact sql scripts
ms.assetid: 90067eb8-ca3e-44e8-bb1a-bf7d1a359423
caps.latest.revision: 42
author: mightypen
ms.author: genemi
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e08af3e61b2fad2f30f0969e0f61f72cb1e25e2d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlcmd---run-transact-sql-script-files"></a>sqlcmd - Eseguire file script Transact-SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
 Usare **sqlcmd** per eseguire un file di script Transact-SQL. Un file script Transact-SQL è un file di testo che può contenere una combinazione di istruzioni Transact-SQL, comandi **sqlcmd** e variabili di scripting.  

## <a name="create-a-script-file"></a>Creare un file script  
 Per creare un file script Transact-SQL semplice in Blocco note, seguire questa procedura:  
  
1.  Fare clic su **Start**, scegliere **Tutti i programmi**, **Accessori**e quindi fare clic su **Blocco note**.  
  
2.  Copiare e incollare il codice Transact-SQL seguente in Blocco note:  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT p.FirstName + ' ' + p.LastName AS 'Employee Name',  
    a.AddressLine1, a.AddressLine2 , a.City, a.PostalCode   
    FROM Person.Person AS p   
       INNER JOIN HumanResources.Employee AS e   
            ON p.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.BusinessEntityAddress bea   
            ON bea.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.Address AS a   
            ON a.AddressID = bea.AddressID;  
    GO  
    ```  
  
3.  Salvare il file con il nome **myScript.sql** nell'unità C.  
  
## <a name="run-the-script-file"></a>Eseguire il file di script  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Nella finestra del prompt dei comandi digitare **sqlcmd -S myServer\instanceName -i C:\myScript.sql**  
  
3.  Premere INVIO.  
  
 Nella finestra del prompt dei comandi verrà visualizzato un elenco di nomi e indirizzi di dipendenti di [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] .  

## <a name="save-the-output-to-a-text-file"></a>Salvare l'output in un file di testo
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Nella finestra del prompt dei comandi digitare **sqlcmd -S myServer\instanceName -i C:\myScript.sql -o C:\EmpAdds.txt**  
  
3.  Premere INVIO.  
  
 Nella finestra del prompt dei comandi non verrà restituito alcun output. L'output verrà invece inviato al file EmpAdds.txt. È possibile verificare l'output aprendo il file EmpAdds.txt.  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio dell'utilità sqlcmd](../../relational-databases/scripting/sqlcmd-start-the-utility.md)   
 [Utilità sqlcmd](../../tools/sqlcmd-utility.md)  
  
  
