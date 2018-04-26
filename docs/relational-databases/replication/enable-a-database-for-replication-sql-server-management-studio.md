---
title: Abilitare un database per la replica (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- databases [SQL Server replication]
ms.assetid: 8092faa3-9cff-4f81-926c-6a0070d1ce2c
caps.latest.revision: 33
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 77c0bf56b3853dbee5c1c313a11b3e7eeb41ec3a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="enable-a-database-for-replication-sql-server-management-studio"></a>Abilitazione di un database per la replica (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Un database viene implicitamente abilitato per la replica quando un membro del ruolo predefinito del server **sysadmin** crea una pubblicazione mediante la Creazione guidata nuova pubblicazione. Il membro del ruolo predefinito del server **sysadmin** può inoltre abilitare esplicitamente un database per la replica, in modo che un membro del ruolo predefinito del database **db_owner** possa creare una o più pubblicazioni in tale database. A tale scopo, usare la pagina **Database di pubblicazione** della finestra di dialogo **Proprietà server di pubblicazione - \<ServerPubblicazione>**. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
### <a name="to-enable-a-database-for-replication"></a>Per abilitare un database per la replica  
  
1.  Nella pagina **Database di pubblicazione** della finestra di dialogo **Proprietà server di pubblicazione - \<ServerPubblicazione>** selezionare la casella di controllo **Transazionale** e/o **Merge** per ogni database da replicare. Selezionare **Transazionale** per abilitare il database per la replica snapshot.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
