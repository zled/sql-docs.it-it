---
title: Mapping tra i database MySQL e gli schemi di SQL Server (MySQLToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Mapping, Modifying target database and schema
- Mapping, reverting to default database and schema
ms.assetid: 5c6fb445-92ae-4933-b77d-80230931c024
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 79cbcae3c7c272f871b18ff0fc9b5a5c1acce57f
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="mapping-mysql-databases-to-sql-server-schemas-mysqltosql"></a>Mapping tra i database MySQL e gli schemi di SQL Server (MySQLToSQL)
Per impostazione predefinita, SSMA per MySQL esegue la migrazione di tutti gli oggetti in uno schema di MySQL per un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o denominato per lo schema di database di SQL Azure. Tuttavia, è possibile personalizzare il mapping tra gli schemi di MySQL e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database di SQL Azure.  
  
## <a name="mysql-and-sql-server-or-sql-azure-schemas"></a>MySQL e SQL Server o SQL Azure schemi  
Il concetto di MySQL di uno schema viene eseguito il mapping al concetto di un database e uno dei relativi schemi di SQL Server. SSMA si intende la combinazione di SQL Server di database e lo schema come schema.  
  
Il concetto di MySQL di uno schema viene eseguito il mapping al concetto di un database e uno dei relativi schemi di SQL Server. Ad esempio, MySQL potrebbe essere uno schema denominato **HR**. Un'istanza di SQL Server potrebbe disporre di un database denominato **HR**, e all'interno del database sono gli schemi. È uno schema di **dbo** (o proprietario del database) dello schema. Per impostazione predefinita, gli schemi di MySQL **HR** verrà eseguito il mapping per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database e lo schema **HR.dbo**. SSMA si intende il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] combinazione di database e lo schema come schema.  
  
È possibile modificare il mapping tra MySQL e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o degli schemi di Azure.  
  
## <a name="modifying-the-target-database-and-schema"></a>Modifica il Database di destinazione e lo Schema  
In SSMA, è possibile mappare schemi di MySQL a eventuale [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o lo schema di SQL Azure.  
  
**Per modificare il database e lo schema**  
  
1.  Nel Visualizzatore metadati MySQL, selezionare **schemi**.  
  
    Il **dello Schema di Mapping** scheda è disponibile anche quando si seleziona singoli schemi. Nell'elenco di **dello Schema di Mapping** scheda personalizzata per l'oggetto selezionato.  
  
2.  Nel riquadro di destra, fare clic su di **dello Schema di Mapping** scheda.  
  
    Verrà visualizzato un elenco di tutti gli schemi di MySQL, seguito da un valore di destinazione. La destinazione è identificata in una notazione di due parti (*database.schema*) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure in cui gli oggetti e dati sarà possibile eseguire la migrazione.  
  
3.  Selezionare la riga che contiene il mapping che si desidera modificare e quindi fare clic su **modifica**.  
  
    Nel **scegliere lo Schema di destinazione** la finestra di dialogo, è esplorare per database di destinazione disponibili e dello schema o un tipo di database e lo schema nella casella di testo in una notazione di due parti (database.schema) e quindi fare clic su **OK**.  
  
4.  La destinazione viene modificato nel **dello Schema di Mapping** scheda.  
  
**Modalità di Mapping**  
  
-   Mapping a SQL Server  
  
È possibile mappare i database di origine a un database di destinazione. Per impostazione predefinita viene eseguito il mapping di database di origine alla destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database a cui si è connessi con SSMA. Se il database di destinazione viene eseguito il mapping è inesistente in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], quindi verrà visualizzato un messaggio **"il Database e/o schema non esiste nella destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] metadati. Viene creato durante la sincronizzazione. Si desidera continuare?"** Fare clic su Sì. Analogamente, è possibile eseguire il mapping di schema allo schema non esistente nella destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database che verrà creato durante la sincronizzazione.  
  
-   Mapping a SQL Azure  
  
È possibile eseguire il mapping del database di origine alla destinazione connessa [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database o per qualsiasi schema nel database di destinazione connesso [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database. Se si esegue il mapping dello Schema di origine per qualsiasi schema non esistente nel database di destinazione connesso, quindi verrà visualizzato un messaggio **"dello Schema non esiste nei metadati di destinazione. Viene creato durante la sincronizzazione. Si desidera continuare? "** Fare clic su Sì.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Ripristinando il Database predefinito e lo Schema  
Se si personalizza il mapping tra schemi di MySQL e uno schema di SQL Server, è possibile ripristinare il mapping i valori predefiniti.  
  
**Per ripristinare il database predefinito e lo schema**  
  
1.  Nella scheda mapping dello schema, selezionare una riga e fare clic su **Ripristina predefiniti** per ripristinare il database predefinito e lo schema.  
  
## <a name="next-steps"></a>Passaggi successivi  
Se si desidera analizzare la conversione di oggetti di MySQL in oggetti di SQL Server o SQL Azure, è possibile [creare un report di conversione](http://msdn.microsoft.com/en-us/2a56a003-3b0f-453a-963c-00c9e40933ec) in caso contrario, è possibile [convertire le definizioni degli oggetti di database MySQL](http://msdn.microsoft.com/en-us/ac21850b-fb32-4704-9985-5759b7c688c7) negli schemi di SQL Server o SQL Azure  
  
## <a name="see-also"></a>Vedere anche  
[Le impostazioni del progetto &#40;conversione&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md)  
[La connessione al database SQL di Azure &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
[Database MySQL la migrazione a SQL Server - SQL di Azure DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
[La connessione a SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
