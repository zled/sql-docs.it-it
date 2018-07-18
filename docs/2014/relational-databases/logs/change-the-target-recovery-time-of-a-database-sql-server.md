---
title: Modificare il tempo di recupero di riferimento di un database (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 10/13/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e466419a-d8a4-48f7-8d97-13a903ad6b15
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c23360f7a57e110c5cf50bb01406b51f166c5950
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37149322"
---
# <a name="change-the-target-recovery-time-of-a-database-sql-server"></a>Modificare il tempo di recupero di riferimento di un database (SQL Server)
  In questo argomento viene illustrato come impostare la modifica del tempo di recupero di riferimento di un database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Per impostazione predefinita, il tempo di recupero di riferimento è 0 e il database utilizza *checkpoint automatici* (controllati dall'opzione server **recovery interval** ). L'impostazione del tempo di recupero di riferimento su un valore maggiore di 0 fa sì che il database utilizzi i *checkpoint indiretti* e stabilisce un limite superiore per il tempo di recupero per il database.  
  
> [!NOTE]  
>  Il limite superiore specificato per un determinato database dall'impostazione del tempo di recupero di riferimento può essere superato se una transazione con esecuzione prolungata provoca tempi eccessivi di UNDO.  
  
-   **Prima di iniziare:**  [Limitazioni e restrizioni](#Restrictions), [Sicurezza](#Security)  
  
-   **Per modificare il tempo di recupero di riferimento usando:**  [SQL Server Management Studio](#SSMSProcedure) o [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a>  
  
> [!CAUTION]  
>  Un carico di lavoro transazionale online su un database configurato per i checkpoint indiretti potrebbe subire un calo delle prestazioni. I checkpoint indiretti assicurano che il numero di pagine dirty è inferiore a una determinata soglia, in modo che il recupero del database viene completato entro il tempo di recupero di riferimento. A differenza dei checkpoint indiretti che usano il numero di pagine dirty, l'opzione di configurazione recovery interval usa il numero di transazioni per determinare il tempo di recupero. Quando i checkpoint indiretti sono abilitati per un database che riceve un numero elevato di operazioni DML, il writer in background può iniziare a scaricare i buffer dirty su disco in modo intensivo per garantire che il tempo necessario per eseguire il recupero non superi il tempo di recupero di riferimento impostato per il database. Questo può causare in determinati sistemi ulteriore attività di I/O che può comportare un collo di bottiglia delle prestazioni se il sottosistema del disco opera al di sopra o in prossimità della soglia di I/O.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È richiesta l'autorizzazione ALTER per il database.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 **Per modificare il tempo di recupero di riferimento**  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], quindi espanderla.  
  
2.  Fare clic con il pulsante destro del mouse sul database che si desidera modificare e scegliere il comando **Proprietà** .  
  
3.  Nella finestra di dialogo **Proprietà database** fare clic sulla pagina **Opzioni** .  
  
4.  Nel campo **Tempo di recupero di riferimento (secondi)** del pannello **Recupero** specificare il numero di secondi desiderato come limite superiore nel tempo di recupero per il database.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
 **Per modificare il tempo di recupero di riferimento**  
  
1.  Connettersi all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in cui risiede il database.  
  
2.  Usare l'istruzione [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options), come indicato di seguito:  
  
     TARGET_RECOVERY_TIME **=***target_recovery_time* { SECONDS | MINUTES }  
  
     *target_recovery_time*  
     Quando è maggiore di 0 (valore predefinito), il valore specifica il limite superiore del tempo di recupero per il database specificato in caso di arresto anomalo del sistema.  
  
     SECONDS  
     Indica che *target_recovery_time* viene espresso come numero di secondi.  
  
     MINUTES  
     Indica che *target_recovery_time* viene espresso come numero di minuti.  
  
     Nell'esempio seguente viene impostato il tempo di recupero di riferimento del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] su `60` .  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET TARGET_RECOVERY_TIME = 60 SECONDS;  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Checkpoint di database &#40;SQL Server&#41;](database-checkpoints-sql-server.md)   
 [Opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
  
