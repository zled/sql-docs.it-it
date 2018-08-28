---
title: Aumentare le dimensioni di un database | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: databases
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], size
- increasing database size
- database size [SQL Server], increasing
- size [SQL Server], databases
ms.assetid: 14f4206d-3afa-4ba9-9849-23e81d63306d
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3c3c76a8a748d9387a9f936cf4094cdcd6d8971c
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43102378"
---
# <a name="increase-the-size-of-a-database"></a>Aumentare le dimensioni di un database
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  In questo argomento si descrive come aumentare le dimensioni di un database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Il database viene espanso aumentando le dimensioni di un file di dati o di log o esistente oppure aggiungendo un nuovo file al database.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Security](#Security)  
  
-   **Per aumentare le dimensioni di un database tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Non è possibile aggiungere o rimuovere un file durante l'esecuzione di un'istruzione BACKUP.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È richiesta l'autorizzazione ALTER per il database.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-increase-the-size-of-a-database"></a>Per aumentare le dimensioni di un database  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], quindi espandere questa istanza.  
  
2.  Espandere **Database**, fare clic con il pulsante destro del mouse sul database di cui si vuole aumentare le dimensioni e quindi scegliere **Proprietà**.  
  
3.  In **Proprietà database**selezionare la pagina **File** .  
  
4.  Per aumentare le dimensioni di un file esistente, aumentare il valore nella colonna **Dimensioni iniziali (MB)** per il file. È necessario aumentare le dimensioni del database almeno di un 1 megabyte.  
  
5.  Per aumentare le dimensioni del database aggiungendo un nuovo file, fare clic su **Aggiungi** , quindi immettere i valori per il nuovo file. Per altre informazioni, vedere [Aggiungere file di dati o file di log a un database](../../relational-databases/databases/add-data-or-log-files-to-a-database.md).  
  
6.  Fare clic su **OK**.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-increase-the-size-of-a-database"></a>Per aumentare le dimensioni di un database  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**. In questo esempio si aumentano le dimensioni del file `test1dat3`.  
  
 [!code-sql[DatabaseDDL#AlterDatabase5](../../relational-databases/databases/codesnippet/tsql/increase-the-size-of-a-d_1.sql)]  
  
 Per altri esempi, vedere [Opzioni per file e filegroup ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere file di dati o file di log a un database](../../relational-databases/databases/add-data-or-log-files-to-a-database.md)   
 [Compattare un database](../../relational-databases/databases/shrink-a-database.md)  
  
  
