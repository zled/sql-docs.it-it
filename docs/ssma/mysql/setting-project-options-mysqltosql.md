---
title: Impostazione delle opzioni progetto (MySQLToSQL) | Documenti Microsoft
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
- Setting project options,configuration options
ms.assetid: 08820d88-e157-4d49-9401-38580dd7ec2d
caps.latest.revision: 12
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0a39cb38cc8439ccb5eac559445b7836982b41ff
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="setting-project-options-mysqltosql"></a>Impostazione delle opzioni progetto (MySQLToSQL)
Per ogni progetto SSMA, è possibile impostare le opzioni a livello di progetto. Queste opzioni specificano la modalità di conversione, migrazione dei dati e modalità di mapping dei tipi di dati di origine ai tipi di dati di destinazione.  Prima di convertire gli oggetti in SQL Server o SQL Azure o la migrazione dei dati in SQL Server o SQL Azure, verificare che le opzioni di configurazione siano appropriate per il progetto.  
  
SSMA consente di configurare le opzioni predefinite per tutti i progetti. Queste opzioni vengono applicate a qualsiasi nuovo progetto creato. È quindi possibile personalizzare le opzioni per ogni progetto.  
  
## <a name="configuration-options-and-modes"></a>Modalità e le opzioni di configurazione  
SSMA con cinque set di impostazioni di progetto:  
  
-   Informazioni sul progetto  
  
-   Generale (conversione, migrazione e SQL Azure)  
  
-   Synchronization  
  
-   GUI  
  
-   Mapping dei tipi  
  
Le impostazioni di progetto possono essere configurate in quattro modi:  
  
-   Valore predefinito  
  
-   Optimistic  
  
-   Completo  
  
-   Custom  
  
La modalità predefinita è consigliata per la maggior parte degli utenti. La modalità ottimistica mantiene più la sintassi corrente di MySQL e più facile la lettura. Tuttavia, mantenendo la sintassi corrente potrebbe non essere accurata. Se la sintassi di MySQL deve essere convertita in sintassi equivalente di SQL Server o SQL Azure, la modalità completa esegue la conversione più completa. Il codice risultante, tuttavia, potrebbe essere più difficile da leggere. Nella modalità personalizzata, è possibile impostare le opzioni.  
  
Per ulteriori informazioni sulle impostazioni e come le impostazioni vengono applicate in ogni modalità, vedere gli argomenti seguenti:  
  
-   [Le impostazioni del progetto &#40;conversione&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md)  
  
-   [Le impostazioni del progetto &#40;migrazione&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-migration-mysqltosql.md)  
  
-   [Impostazioni del progetto (GUI) (SSMA comune)](http://msdn.microsoft.com/en-us/cf06baf1-8714-48a3-95dc-781f6ca53693)  
  
-   [Le impostazioni del progetto &#40;Mapping dei tipi di&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-type-mapping-mysqltosql.md)  
  
-   [Le impostazioni del progetto &#40;sincronizzazione&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-synchronization-mysqltosql.md)  
  
-   [Le impostazioni del progetto &#40;database SQL di Azure&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-azure-sql-db-mysqltosql.md)  
  
## <a name="setting-project-options"></a>Impostazione delle opzioni di progetto  
In SSMA, è possibile configurare le impostazioni predefinite per tutti i progetti. Queste impostazioni vengono salvate nel file di configurazione di SSMA e applicate a qualsiasi nuovo progetto creato.  
  
**Per impostare opzioni di progetto predefinite**  
  
1.  Nel **strumenti** menu, fare clic su **impostazioni di progetto predefinite**.  
  
2.  Nel **impostazioni di progetto predefinite** la finestra di dialogo, utilizzare una delle procedure seguenti:  
  
    1.  Selezionare il tipo di progetto di migrazione per i quali impostazioni sono necessarie per essere visualizzati o modificati da **versione di destinazione della migrazione** elenco a discesa, fare clic su **generale** nella parte inferiore del riquadro sinistro, quindi scegliere **conversione o la migrazione o SQL Azure** opzione.  
  
    2.  Per selezionare una modalità predefinita, selezionare **predefinito**, **Optimistic**, o **completo** dal **modalità** casella di riepilogo a discesa.  
  
    3.  Per specificare le impostazioni personalizzate, selezionare o immettere le nuove impostazioni o i valori.  
  
3.  Fare clic su **OK** per salvare le impostazioni.  
  
È anche possibile personalizzare le impostazioni per il progetto corrente. Le impostazioni vengono salvate nel file di progetto corrente.  
  
**Per personalizzare le impostazioni per il progetto corrente**  
  
1.  Nel **strumenti** menu, fare clic su **ProjectSettings**.  
  
2.  Nel **ProjectSettings** la finestra di dialogo, utilizzare una delle procedure seguenti:  
  
    1.  Per selezionare una modalità predefinita, selezionare **predefinito**, **Optimistic**, o **completo** dal **modalità** casella di riepilogo a discesa.  
  
    2.  Per specificare una modalità personalizzata, selezionare **personalizzato** dal **modalità** casella di riepilogo a discesa. E quindi selezionare le impostazioni di progetto appropriate.  
  
3.  Fare clic su **OK** per salvare le impostazioni.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo della migrazione dipende dalle esigenze del progetto:  
  
-   Per personalizzare il mapping dei tipi di dati di origine e di destinazione, vedere [tipi di dati di SQL Server e MySQL Mapping &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
-   In caso contrario, è possibile convertire le definizioni degli oggetti di database MySQL in SQL Server o le definizioni degli oggetti di SQL Azure. Per altre informazioni, vedere [conversione database MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Mapping di tipi di dati SQL Server e MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
