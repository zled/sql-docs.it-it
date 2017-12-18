---
title: Configurare log degli errori di SQL Server | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.configurelogs.configureerrorlogs.f1
ms.assetid: 03f0d463-9b0b-4af9-a853-da936d75e5af
caps.latest.revision: "18"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 5251f3437e4cb31290c01596e736ed394e05bafa
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="scm-services---configure-sql-server-error-logs"></a>Gestione configurazione SQL Server - Configurare log degli errori di SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Questo argomento illustra come visualizzare o modificare la modalità di riciclo dei log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a>Per aprire la finestra di dialogo Configura log degli errori di SQL Server  
  
1.  In Esplora oggetti espandere l'istanza di SQL Server, espandere **Gestione**, fare clic con il pulsante destro del mouse su **Log di SQL Server**e quindi scegliere **Configura**.  
  
2.  Nella finestra di dialogo **Configura log degli errori di SQL Server** , scegliere dalle opzioni seguenti.  
  
     **Limita il numero di file di log degli errori creati prima di essere riciclati**  
     Selezionare questa opzione per limitare il numero di log degli errori creati prima di essere riciclati. Ogni volta che viene avviata un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene creato un nuovo log degli errori. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mantiene backup dei sei log precedenti, a meno che non si selezioni questa opzione e non si specifichi un diverso numero massimo di log degli errori tramite l'opzione seguente.  
  
     **Numero massimo di file di log degli errori**  
     Consente di specificare il numero massimo di log degli errori creati prima di essere riciclati. Il valore predefinito è 6 che corrisponde al numero di log di backup precedenti mantenuti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prima che vengano riciclati.  
  
  
