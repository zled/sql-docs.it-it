---
title: Sybase ASE schemi di mapping per gli schemi di SQL Server (SybaseToSQL) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Schema Mapping
ms.assetid: 2c927003-c49d-4fe1-8e3e-5b2899166268
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: c712831f4db10fd10f0d635fc43779c39b0f8953
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql"></a>Sybase ASE schemi di mapping per gli schemi di SQL Server (SybaseToSQL)
In Sybase Adaptive Server Enterprise (ASE), ogni database dispone di uno o più schemi. Per impostazione predefinita, SSMA esegue la migrazione di tutti gli oggetti all'interno di un database e lo schema nello stesso database e schema in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Tuttavia, è possibile personalizzare il mapping tra ASE e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database di SQL Azure e schemi.  
  
## <a name="ase-and-sql-server-or-sql-azure-schemas"></a>ASE e SQL Server o SQL Azure schemi  
ASE e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure sia specificare database e i relativi schemi utilizzando la notazione parte due come *database.schema*. Ad esempio, in un ASE **demo** del database, potrebbe esserci un **dbo** dello schema. Coppia di database e dello schema è specificata come **demo.dbo**. Se [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure è lo stesso database e dello schema, la coppia viene anche specificata come **demo.dbo**.  
  
## <a name="modifying-the-target-database-and-schema"></a>Modifica il Database di destinazione e lo Schema  
In SSMA, è possibile mappare un schema ASE a eventuale [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o lo schema di SQL Azure.  
  
**Per modificare il database e lo schema**  
  
1.  Nel Visualizzatore metadati Sybase, selezionare **database**.  
  
    Il **Mapping dello Schema** scheda è disponibile anche quando si seleziona un singolo database, il **schemi** cartella o singoli schemi. Nell'elenco di **dello Schema di Mapping** scheda personalizzata per l'oggetto selezionato.  
  
2.  Nel riquadro di destra, fare clic su di **dello Schema di Mapping** scheda.  
  
    Verrà visualizzato un elenco di tutti i database di base con i relativi schemi, seguiti da un valore di destinazione. La destinazione è identificata in una notazione di due parti (*database.schema*) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure in cui gli oggetti e dati sarà possibile eseguire la migrazione.  
  
3.  Selezionare la riga che contiene il mapping che si desidera modificare e quindi fare clic su **modifica**.  
  
4.  Nel **scegliere lo Schema di destinazione** la finestra di dialogo, è esplorare per database di destinazione disponibili e dello schema o un tipo di database e lo schema nella casella di testo in una notazione di due parti (database.schema) e quindi fare clic su **OK**.  
  
5.  La destinazione viene modificato nel **dello Schema di Mapping** scheda.  
  
**Modalità di Mapping**  
  
-   Mapping a SQL Server  
  
È possibile mappare i database di origine a un database di destinazione. Per impostazione predefinita viene eseguito il mapping di database di origine alla destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database a cui si è connessi con SSMA. Se il database di destinazione viene eseguito il mapping è inesistente in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], quindi verrà visualizzato un messaggio **"il Database e/o schema non esiste nella destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] metadati. Viene creato durante la sincronizzazione. Si desidera continuare?"** Fare clic su Sì. Analogamente, è possibile eseguire il mapping di schema allo schema non esistente nella destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database che verrà creato durante la sincronizzazione.  
  
-   Mapping a SQL Azure  
  
È possibile associare il database di origine al database di SQL Azure di destinazione connesso o ad alcuno schema nel database di SQL Azure di destinazione connesso. Se si esegue il mapping dello Schema di origine per qualsiasi schema non esistente nel database di destinazione connesso, quindi verrà visualizzato un messaggio **"dello Schema non esiste nei metadati di destinazione. Viene creato durante la sincronizzazione. Si desidera continuare? "** Fare clic su Sì.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Ripristinando il Database predefinito e lo Schema  
Se si personalizza il mapping tra uno schema di base e un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o schema di SQL Azure, è possibile ripristinare il mapping i valori predefiniti.  
  
**Per ripristinare il database predefinito e lo schema**  
  
1.  Nella scheda mapping dello schema, selezionare una riga e fare clic su **Ripristina predefiniti** per ripristinare il database predefinito e lo schema.  
  
## <a name="next-steps"></a>Passaggi successivi  
Se si desidera analizzare la conversione di oggetti di Sybase ASE in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o oggetti di SQL Azure, è possibile [creare un report di conversione](http://msdn.microsoft.com/en-us/eb996b7c-1eef-4f73-b5e6-2fa6faf7336c). In caso contrario, è possibile [convertire le definizioni degli oggetti di database ASE](http://msdn.microsoft.com/en-us/509cb65d-2f54-427a-83d7-37919cc4e3e3) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o le definizioni degli oggetti di SQL Azure.  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database Sybase ASE a SQL Server: SQL Azure database &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
