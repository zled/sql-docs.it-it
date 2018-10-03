---
title: Configurare il controllo accessi (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], logins
- logins [SQL Server], auditing
ms.assetid: 16961116-57ac-4eef-8037-791b26ade548
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ada9972994841e4ed0360bbfcca5cf392c5884e5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48169884"
---
# <a name="configure-login-auditing-sql-server-management-studio"></a>Configurazione del controllo accessi (SQL Server Management Studio)
  In questo argomento viene descritto come configurare controllo di accesso in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] per eseguire il monitoraggio dell'attività di accesso del [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]. È possibile configurare il controllo accessi per scrivere nel log degli errori quando si verificano gli eventi riportati di seguito.  
  
-   Accessi non riusciti  
  
-   Accessi riusciti  
  
-   Accessi riusciti e non riusciti  
  
 Per rendere effettiva questa opzione, è necessario riavviare [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-configure-login-auditing"></a>Per configurare il controllo accessi  
  
1.  In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] tramite Esplora oggetti.  
  
2.  In Esplora oggetti fare clic con il pulsante destro del mouse sul nome del server e quindi scegliere **Proprietà**.  
  
3.  Nella pagina **Sicurezza** selezionare l'opzione desiderata in **Controllo accessi** e chiudere la pagina **Proprietà server** .  
  
4.  In Esplora oggetti fare clic con il pulsante destro del mouse sul nome del server e scegliere **Riavvia**.  
  
  
