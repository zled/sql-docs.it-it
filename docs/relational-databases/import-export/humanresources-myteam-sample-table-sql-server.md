---
title: Tabella di esempio HumanResources.myTeam (SQL Server) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-bulk-import-export
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- myTeam sample table [SQL Server]
- bulk importing [SQL Server], examples
- bulk exporting [SQL Server], examples
ms.assetid: 27da45a0-c1f4-4bf4-ab24-6196e80d3834
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8239a056d0fc646b3997e94c0d399a32543c28dc
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="humanresourcesmyteam-sample-table-sql-server"></a>Tabella di esempio HumanResources.myTeam (SQL Server)
  Molti degli esempi di codice inclusi nell'argomento relativo all' [importazione ed esportazione di dati bulk](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md) richiedono una tabella di prova speciale denominata **myTeam**. Prima che sia possibile eseguire gli esempi, è necessario creare la tabella **myTeam** nello schema **HumanResources** del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
> [!NOTE]  
>  [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] è uno dei database di esempio disponibili in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Nella tabella **myTeam** sono incluse le colonne seguenti.  
  
|Colonna|Tipo di dati|Supporto di valori Null|Descrizione|  
|------------|---------------|-----------------|-----------------|  
|**EmployeeID**|**smallint**|Non Null|Chiave primaria per le righe. ID dipendente di un membro del team.|  
|**Nome**|**nvarchar(50)**|Non Null|Nome di un membro del team.|  
|**Title**|**nvarchar(50)**|Ammette valori Null|Titolo professionale del dipendente nel team.|  
|**Background**|**nvarchar(50)**|Non Null|Data e ora dell'ultimo aggiornamento della riga. Valore predefinito.|  
  
**Per creare HumanResources.myTeam**  
  
-   Utilizzare le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] seguenti:  
  
    ```sql
    --Create HumanResources.MyTeam:   
    USE AdventureWorks;  
    GO  
    CREATE TABLE HumanResources.myTeam   
    (EmployeeID smallint NOT NULL,  
    Name nvarchar(50) NOT NULL,  
    Title nvarchar(50) NULL,  
    Background nvarchar(50) NOT NULL DEFAULT ''  
    );  
    GO  
    ```  
  
**Per popolare HumanResources.myTeam**  
  
-   Eseguire le istruzioni `INSERT` seguenti per popolare la tabella con due righe:  
  
    ```sql
    USE AdventureWorks;  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(77,'Mia Doppleganger','Administrative Assistant','Microsoft Office');  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(49,'Hirum Mollicat','I.T. Specialist','Report Writing and Data Mining');  
    GO  
    ```  
  
    > [!NOTE]  
    >  Queste istruzioni ignorano la quarta colonna, `Background`, che ha un valore predefinito. Ignorando la colonna, l'istruzione `INSERT` lascia la colonna vuota.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sull'importazione ed esportazione bulk di dati &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
