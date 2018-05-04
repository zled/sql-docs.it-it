---
title: Impostazione delle opzioni progetto (SybaseToSQL) | Documenti Microsoft
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
- Project Options Setting
ms.assetid: 97b70fc8-1f68-4f15-8e22-db5b784ea4ec
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 7c7053d6a7acad85fe2094cca1bf8568a1a2f94a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="setting-project-options-sybasetosql"></a>Impostazione delle opzioni progetto (SybaseToSQL)
Per ogni progetto SSMA, è possibile impostare opzioni del livello di progetto. Queste opzioni specificano la conversione degli oggetti, il caricamento di oggetti, SQL azure, interfaccia utente e le impostazioni di migrazione di dati. Prima di convertire oggetti [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure o la migrazione dei dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, verificare che le opzioni di configurazione siano appropriate per il progetto.  
  
SSMA consente di configurare le opzioni predefinite per tutti i progetti. Queste opzioni vengono applicate a qualsiasi nuovo progetto creato. È quindi possibile personalizzare le opzioni per ogni progetto.  
  
## <a name="configuration-options-and-modes"></a>Modalità e le opzioni di configurazione  
SSMA con cinque set di impostazioni di progetto:  
  
1.  Informazioni sul progetto  
  
2.  Generale (conversione, migrazione e la raccolta dei dati)  
  
3.  Synchronization  
  
4.  GUI  
  
5.  Mapping dei tipi  
  
Include inoltre quattro modalità per la configurazione di queste impostazioni:  
  
1.  Valore predefinito  
  
2.  Optimistic  
  
3.  Completo  
  
4.  Custom  
  
La modalità predefinita è consigliata per la maggior parte degli utenti. La modalità ottimistica mantiene più la sintassi di Sybase Adaptive Server Enterprise (ASE) corrente e più facile la lettura. Tuttavia, mantenendo la sintassi corrente potrebbe non essere accurata. Se è necessario convertire la sintassi di base equivalente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o sintassi SQL Azure, la modalità completa esegue una conversione completa, ma il codice risulta potrebbe essere più difficile da leggere. In modalità personalizzata, impostare le opzioni.  
  
Le impostazioni sono descritte nella sezione dell'interfaccia utente di questa documentazione. Per ulteriori informazioni sulle impostazioni e come le impostazioni vengono applicate in ogni modalità, vedere gli argomenti seguenti:  
  
-   [Le impostazioni del progetto &#40;conversione&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md)  
  
-   [Le impostazioni del progetto &#40;migrazione&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-migration-sybasetosql.md)  
  
-   [Le impostazioni del progetto &#40;sincronizzazione&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-synchronization-sybasetosql.md)  
  
-   [Le impostazioni del progetto &#40;interfaccia utente grafica&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-gui-sybasetosql.md)  
  
-   [Le impostazioni del progetto &#40;Mapping dei tipi di&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md)  
  
-   [Le impostazioni del progetto &#40;database SQL di Azure &#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-azure-sql-db-sybasetosql.md)  
  
## <a name="setting-project-options"></a>Impostazione delle opzioni di progetto  
In SSMA, è possibile configurare le impostazioni predefinite per tutti i progetti. Queste impostazioni vengono salvate nel file di configurazione di SSMA e applicate a qualsiasi nuovo progetto creato.  
  
**Per impostare opzioni di progetto predefinite**  
  
1.  Nel **strumenti** dal menu **impostazioni di progetto predefinite**.  
  
2.  Nel **impostazioni di progetto predefinite** la finestra di dialogo, utilizzare una delle procedure seguenti:  
  
    -   Selezionare il tipo di progetto di migrazione per i quali impostazioni sono necessarie per essere visualizzati o modificati da **versione di destinazione della migrazione** drop verso il basso fare clic su Generale nella parte inferiore del riquadro a sinistra e quindi selezionare la conversione o la migrazione o SQL Azure.  
  
    -   Per selezionare una modalità predefinita, il **modalità** casella di riepilogo a discesa, selezionare **predefinito**, **Optimistic**, o **completo**.  
  
    -   Per specificare le impostazioni personalizzate, selezionare o immettere le nuove impostazioni o i valori.  
  
3.  Fare clic su **OK** per salvare le impostazioni.  
  
È anche possibile personalizzare le impostazioni per il progetto corrente. Queste impostazioni vengono salvate nel file di progetto corrente.  
  
**Per personalizzare le impostazioni per il progetto corrente**  
  
1.  Nel **strumenti** dal menu **impostazioni progetto**.  
  
2.  Nel **impostazioni progetto** la finestra di dialogo, utilizzare una delle procedure seguenti:  
  
    -   Per selezionare una modalità predefinita, il **modalità** casella di riepilogo a discesa, selezionare **predefinito**, **Optimistic**, o **completo**.  
  
    -   Per specificare una modalità personalizzata, nel **modalità** elenchi a discesa, selezionare **personalizzato**, selezionare un'opzione nel riquadro a sinistra, fare clic sull'impostazione o un valore nel riquadro di destra, quindi selezionare o immettere la nuova impostazione o un valore.  
  
3.  Fare clic su **OK** per salvare le impostazioni.  
  
## <a name="next-steps"></a>Passaggi successivi  
Il passaggio successivo della migrazione dipende dalle esigenze del progetto:  
  
-   Se si desidera personalizzato per il mapping dei tipi di dati di origine e di destinazione, vedere [Mapping Sybase ASE e tipi di dati di SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
-   In caso contrario, è possibile convertire le definizioni degli oggetti di database Sybase in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o le definizioni degli oggetti di SQL Azure. Per altre informazioni, vedere [convertire gli oggetti di Database di Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md).  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database Sybase ASE a SQL Server: SQL Azure database &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
