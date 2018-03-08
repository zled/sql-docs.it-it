---
title: Mapping di database di origine e destinazione (AccessToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-access
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- database schemas
- mapping, databases
- schemas, mapping to
- schemas, SQL Azure
- schemas, SQL Server
- source database
- target database
ms.assetid: 69bee937-7b2c-49ee-8866-7518c683fad4
caps.latest.revision: "17"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 48e87d2b6c84db3534a3c52ee6176e29fd34257f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="mapping-source-and-target-databases-accesstosql"></a>Mapping di database di origine e destinazione (AccessToSQL)
Quando si connette a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, è necessario specificare un database di destinazione per la migrazione. Se si dispone di più database di Access è possibile eseguirne il mapping a più [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database (o gli schemi) o a più schemi del database di SQL Azure connesso.  
  
## <a name="sql-server-or-sql-azure-database-schemas"></a>SQL Server o SQL Azure Database schemi  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]database utilizzano il concetto di schemi per separare gli oggetti all'interno di un database in gruppi logici. Ad esempio, un database di libreria può utilizzare tre schemi denominati **documentazione**, **audio**, e **video** per separare gli oggetti di audio e video di libro, da altro. Per impostazione predefinita, il database di access viene eseguito il mapping a **master** database e **dbo** schema [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e al database connesso e **dbo** dello schema in SQL Azure.  
  
A meno che non si personalizza il mapping tra ogni database di Access e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database e dello schema, verrà eseguita la migrazione di SSMA tutti gli schemi e dati associati al database di accesso al database predefinito mappato.  
  
## <a name="modifying-the-target-database-and-schema"></a>Modifica il Database di destinazione e lo Schema  
SSMA consente di eseguire il mapping di ogni database di Access in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database di SQL Azure e lo schema. La procedura seguente viene descritto come personalizzare il mapping per ogni database.  
  
**Per modificare il database di destinazione e lo schema**  
  
1.  Nel riquadro Visualizzatore metadati di accesso, selezionare **accedere ai metadati**.  
  
    Mapping dello schema è disponibile anche quando si seleziona il **database** nodo o un qualsiasi nodo del database. L'elenco di mapping dello schema personalizzato per l'oggetto selezionato.  
  
2.  Nel riquadro di destra, fare clic su di **dello Schema di Mapping** scheda.  
  
    Verrà visualizzata una tabella contenente accesso dello schema di Sql Azure e il relativo ssNoVersion corrispondente o nomi di database. Lo schema di destinazione è identificato in una notazione di due parti (database.schema).  
  
3.  Selezionare la riga che contiene il mapping a cui si desidera personalizzare e quindi fare clic su **modifica**.  
  
4.  Nel **scegliere lo Schema di destinazione** la finestra di dialogo, è esplorare per database di destinazione disponibili e dello schema o un tipo di database e lo schema nella casella di testo in una notazione di due parti (database.schema) e quindi fare clic su **OK**.  
  
**Modalità di Mapping**  
  
-   Mapping a SQL Server  
  
È possibile mappare i database di origine a un database di destinazione. Per impostazione predefinita viene eseguito il mapping di database di origine alla destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database a cui si è connessi con SSMA. Se il database di destinazione viene eseguito il mapping non esiste in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], quindi verrà visualizzato un messaggio **"il Database e/o schema non esiste nella destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] metadati. Viene creato durante la sincronizzazione. Si desidera continuare?"** Fare clic su Sì. Analogamente, è possibile eseguire il mapping di schema allo schema non esistente nella destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database che verrà creato durante la sincronizzazione.  
  
-   Mapping a SQL Azure  
  
È possibile eseguire il mapping del database di origine alla destinazione connessa [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database o per qualsiasi schema nel database di destinazione connesso [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database. Se si esegue il mapping dello Schema di origine per qualsiasi schema non esistente nel database di destinazione connesso, quindi verrà visualizzato un messaggio **"dello Schema non esiste nei metadati di destinazione. Viene creato durante la sincronizzazione. Si desidera continuare? "** Fare clic su Sì.  
  
## <a name="reverting-to-your-initial-database-and-schema"></a>Ripristinando il Database iniziale e dello Schema  
Se si personalizza il mapping tra un database di Access e un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database di SQL Azure e dello schema, è possibile ripristinare il mapping al database specificato quando connesso a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.  
  
**Per reimpostare lo schema e di database predefinito**  
  
1.  Nella scheda mapping dello schema, selezionare una riga e fare clic su **Ripristina predefiniti** per ripristinare il database predefinito e lo schema.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo del processo di migrazione è [la conversione di oggetti di database](http://msdn.microsoft.com/en-us/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database di Access a SQL Server](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
