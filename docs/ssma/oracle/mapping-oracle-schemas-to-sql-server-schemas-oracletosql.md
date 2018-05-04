---
title: Oracle schemi di mapping per gli schemi di SQL Server (OracleToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0edeaa08-9c5d-4e3a-bc15-b9a1f0c8a9dc
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 91aa5097f4117c12a6d53af83f6a5e6a6ee68cd2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mapping-oracle-schemas-to-sql-server-schemas-oracletosql"></a>Oracle schemi di mapping per gli schemi di SQL Server (OracleToSQL)
In Oracle, ogni database dispone di uno o più schemi. Per impostazione predefinita, SSMA esegue la migrazione di tutti gli oggetti in uno schema Oracle per un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] denominato per lo schema di database. Tuttavia, è possibile personalizzare il mapping tra gli schemi di Oracle e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database.  
  
## <a name="oracle-and-sql-server-schemas"></a>Oracle e schemi SQL Server  
Un database Oracle contiene gli schemi. Un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] contiene più database, ognuno dei quali può disporre di più schemi.  
  
Il concetto di Oracle uno schema di mapping per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] concetto di un database e uno dei relativi schemi. Ad esempio Oracle potrebbe essere uno schema denominato **HR**. Un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] potrebbe disporre di un database denominato **HR**, e all'interno del database sono gli schemi. È uno schema di **dbo** (o proprietario del database) dello schema. Per impostazione predefinita, lo schema di Oracle **HR** verrà eseguito il mapping per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database e lo schema **HR.dbo**. SSMA si intende il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] combinazione di database e lo schema come schema.  
  
È possibile modificare il mapping tra Oracle e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] schemi.  
  
## <a name="modifying-the-target-database-and-schema"></a>Modifica il Database di destinazione e lo Schema  
In SSMA, è possibile mappare un schema Oracle a eventuale [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] dello schema.  
  
**Per modificare il database e lo schema**  
  
1.  Nel Visualizzatore metadati Oracle, selezionare **schemi**.  
  
    Il **Mapping dello Schema** scheda è disponibile anche quando si seleziona un singolo database, il **schemi** cartella o singoli schemi. Nell'elenco di **dello Schema di Mapping** scheda personalizzata per l'oggetto selezionato.  
  
2.  Nel riquadro di destra, fare clic su di **dello Schema di Mapping** scheda.  
  
    Verrà visualizzato un elenco di tutti gli schemi di Oracle, seguito da un valore di destinazione. La destinazione è identificata in una notazione di due parti (*database.schema*) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] in cui gli oggetti e dati sarà possibile eseguire la migrazione.  
  
3.  Selezionare la riga che contiene il mapping che si desidera modificare e quindi fare clic su **modifica**.  
  
    Nel **scegliere lo Schema di destinazione** la finestra di dialogo, è esplorare per database di destinazione disponibili e dello schema o un tipo di database e lo schema nella casella di testo in una notazione di due parti (database.schema) e quindi fare clic su **OK**.  
  
4.  La destinazione viene modificato nel **dello Schema di Mapping** scheda.  
  
**Modalità di Mapping**  
  
-   Mapping a SQL Server  
  
È possibile mappare i database di origine a un database di destinazione. Per impostazione predefinita viene eseguito il mapping di database di origine alla destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database a cui si è connessi con SSMA. Se il database di destinazione viene eseguito il mapping è inesistente in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], quindi verrà visualizzato un messaggio **"il Database e/o schema non esiste nella destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] metadati. Viene creato durante la sincronizzazione. Si desidera continuare?"** Fare clic su Sì. Analogamente, è possibile eseguire il mapping di schema allo schema non esistente nella destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database che verrà creato durante la sincronizzazione.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Ripristinando il Database predefinito e lo Schema  
Se si personalizza il mapping tra uno schema di Oracle e un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] dello schema, è possibile ripristinare il mapping i valori predefiniti.  
  
**Per ripristinare il database predefinito e lo schema**  
  
1.  Nella scheda mapping dello schema, selezionare una riga e fare clic su **Ripristina predefiniti** per ripristinare il database predefinito e lo schema.  
  
## <a name="next-steps"></a>Passaggi successivi  
Se si desidera analizzare la conversione degli oggetti Oracle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oggetti, è possibile [creare un report di conversione](http://msdn.microsoft.com/en-us/4de9bcf6-1346-4740-87f9-7f24a8226357). In caso contrario, è possibile [convertire le definizioni degli oggetti di database Oracle](http://msdn.microsoft.com/en-us/e021182d-31da-443d-b110-937f5db27272) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] definizioni di oggetti.  
  
## <a name="see-also"></a>Vedere anche  
[La connessione a SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md)  
[Migrazione di Oracle database a SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
