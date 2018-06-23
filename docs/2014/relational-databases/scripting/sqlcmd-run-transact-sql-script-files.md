---
title: Eseguire file script Transact-SQL mediante sqlcmd | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transact sql scripts
ms.assetid: 90067eb8-ca3e-44e8-bb1a-bf7d1a359423
caps.latest.revision: 41
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ff18203f0120210f3443973ed7e44761b84ac8ea
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157449"
---
# <a name="run-transact-sql-script-files-using-sqlcmd"></a>Esecuzione di file script Transact-SQL mediante sqlcmd
  È possibile utilizzare `sqlcmd` per eseguire un file script [!INCLUDE[tsql](../../includes/tsql-md.md)]. Un [!INCLUDE[tsql](../../includes/tsql-md.md)] file di script è un file di testo che può contenere una combinazione di [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni, `sqlcmd` comandi e variabili di scripting.  
  
 Per creare un file script [!INCLUDE[tsql](../../includes/tsql-md.md)] semplice in Blocco note, eseguire la procedura seguente:  
  
1.  Fare clic su **Start**, scegliere **Tutti i programmi**, **Accessori**e quindi fare clic su **Blocco note**.  
  
2.  Copiare e incollare il codice seguente [!INCLUDE[tsql](../../includes/tsql-md.md)] codice nel blocco note:  
  
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
  
### <a name="to-run-the-script-file"></a>Per eseguire il file script  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Nella finestra del prompt dei comandi, digitare: `sqlcmd -S myServer\instanceName -i C:\myScript.sql`  
  
3.  Premere INVIO.  
  
 Nella finestra del prompt dei comandi verrà visualizzato un elenco di nomi e indirizzi di dipendenti di [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] .  
  
### <a name="to-save-this-output-to-a-text-file"></a>Per salvare l'output in un file di testo  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Nella finestra del prompt dei comandi, digitare: `sqlcmd -S myServer\instanceName -i C:\myScript.sql -o C:\EmpAdds.txt`  
  
3.  Premere INVIO.  
  
 Nella finestra del prompt dei comandi non verrà restituito alcun output. L'output verrà invece inviato al file EmpAdds.txt. È possibile verificare l'output aprendo il file EmpAdds.txt.  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio dell'utilità sqlcmd](sqlcmd-start-the-utility.md)   
 [Utilità sqlcmd](../../tools/sqlcmd-utility.md)  
  
  