---
title: Configurare il controllo accessi (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], logins
- logins [SQL Server], auditing
ms.assetid: 16961116-57ac-4eef-8037-791b26ade548
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 2b48696d9304363214224e157eda65593edaf2dd
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="configure-login-auditing-sql-server-management-studio"></a>Configurazione del controllo accessi (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
In questo argomento viene descritto come configurare controllo di accesso in [!INCLUDE[ssCurrent](../includes/sscurrent_md.md)] per eseguire il monitoraggio dell'attività di accesso del [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)]. È possibile configurare il controllo accessi per scrivere nel log degli errori quando si verificano gli eventi riportati di seguito.  
  
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
  
