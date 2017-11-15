---
title: Eliminare tabelle (motore di database) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- table deletions [SQL Server]
- deleting tables
- removing tables
- dropping tables
ms.assetid: ca6aa3e9-9885-44c3-bafc-aec441fd97ec
caps.latest.revision: "19"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 966d1c9d35eb521deb4c5413850fc02065394da7
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="delete-tables-database-engine"></a>Elimina tabelle (motore di database)
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  È possibile eliminare una tabella dal database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!CAUTION]  
>  Prima di eliminare una tabella, valutare le possibili conseguenze. Se query, viste, funzioni definite dall'utente, stored procedure o programmi esistenti fanno riferimento a tale tabella, la modifica renderà non validi tali oggetti.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Sicurezza](#Security)  
  
-   **Per eliminare una tabella:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Non è possibile eliminare una tabella a cui fa riferimento un vincolo FOREIGN KEY. È prima necessario eliminare il vincolo FOREIGN KEY o la tabella di riferimento. Se con la stessa istruzione DROP TABLE si eliminano sia la tabella di riferimento che la tabella che contiene la chiave primaria, è necessario indicare la tabella di riferimento per prima nell'elenco.  
  
-   Con l'eliminazione di una tabella, le regole o i valori predefiniti della tabella vengono disassociati e i vincoli o trigger associati alla tabella vengono eliminati automaticamente. Se la tabella viene ricreata, è necessario associare nuovamente le regole e i valori predefiniti appropriati, ricreare eventuali trigger e aggiungere tutti i vincoli necessari.  
  
-   Se si elimina una tabella che contiene una colonna **varbinary (max)** con l'attributo FILESTREAM, non verrà rimosso alcun dato archiviato nel file system.  
  
-   DROP TABLE e CREATE TABLE non devono essere eseguiti nella stessa tabella nello stesso batch. In caso contrario, è possibile che si verifichi un errore imprevisto.  
  
-   Le viste o stored procedure che fanno riferimento alla tabella eliminata devono essere eliminate o modificate in modo esplicito per eliminare il riferimento alla tabella.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È richiesta l'autorizzazione ALTER per lo schema a cui appartiene la tabella, l'autorizzazione CONTROL per la tabella o l'appartenenza al ruolo predefinito del database **db_ddladmin** .  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-delete-a-table-from-the-database"></a>Per eliminare una tabella dal database  
  
1.  In Esplora oggetti selezionare la tabella che si desidera eliminare.  
  
2.  Fare clic con il pulsante destro del mouse sulla tabella, quindi scegliere **Elimina** dal menu di scelta rapida.  
  
3.  Verrà visualizzato un messaggio in cui viene chiesto di confermare l'eliminazione. Scegliere **Sì**.  
  
    > [!NOTE]  
    >  Eliminando una tabella verranno eliminate automaticamente anche tutte le corrispondenti relazioni.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### <a name="to-delete-a-table-in-query-editor"></a>Per eliminare una tabella in Editor di query  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    DROP TABLE dbo.PurchaseOrderDetail;  
  
    ```  
  
 Per altre informazioni, vedere [DROP TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-table-transact-sql.md)  
  
  
