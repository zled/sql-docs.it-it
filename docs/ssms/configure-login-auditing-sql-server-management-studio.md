---
title: Configurare il controllo accessi (SQL Server Management Studio) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], logins
- logins [SQL Server], auditing
ms.assetid: 16961116-57ac-4eef-8037-791b26ade548
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: a4517e717ed4af66420855b357015c5cd5a74306
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="configure-login-auditing-sql-server-management-studio"></a>Configurazione del controllo accessi (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Questo argomento descrive come configurare il controllo di accesso in [!INCLUDE[ssCurrent](../includes/sscurrent_md.md)] per eseguire il monitoraggio dell'attività di accesso del [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)]. È possibile configurare il controllo accessi per scrivere nel log degli errori quando si verificano gli eventi riportati di seguito.  
  
-   Accessi non riusciti  
  
-   Accessi riusciti  
  
-   Accessi riusciti e non riusciti  
  
Per rendere effettiva questa opzione, è necessario riavviare [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] .  
  
## <a name="SSMSProcedure"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-configure-login-auditing"></a>Per configurare il controllo accessi  
  
1.  In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)]connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)] tramite Esplora oggetti.  
  
2.  In Esplora oggetti fare clic con il pulsante destro del mouse sul nome del server e quindi scegliere **Proprietà**.  
  
3.  Nella pagina **Sicurezza** selezionare l'opzione desiderata in **Controllo accessi** e chiudere la pagina **Proprietà server** .  
  
4.  In Esplora oggetti fare clic con il pulsante destro del mouse sul nome del server e scegliere **Riavvia**.  
  
