---
title: Configurare log degli errori di SQL Server | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.configurelogs.configureerrorlogs.f1
ms.assetid: 03f0d463-9b0b-4af9-a853-da936d75e5af
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d6815aac3852922ae49a4953abc501a2cf958a4c
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="scm-services---configure-sql-server-error-logs"></a>Gestione configurazione SQL Server - Configurare log degli errori di SQL Server
  In questo argomento viene descritto come visualizzare o modificare la modalità di riciclo dei log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a>Per aprire la finestra di dialogo Configura log degli errori di SQL Server  
  
1.  In Esplora oggetti espandere l'istanza di SQL Server, espandere **Gestione**, fare clic con il pulsante destro del mouse su **Log di SQL Server**e quindi scegliere **Configura**.  
  
2.  Nella finestra di dialogo **Configura log degli errori di SQL Server** , scegliere dalle opzioni seguenti.  
  
     **Limita il numero di file di log degli errori creati prima di essere riciclati**  
     Selezionare questa opzione per limitare il numero di log degli errori creati prima di essere riciclati. Ogni volta che viene avviata un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene creato un nuovo log degli errori. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mantiene backup dei sei log precedenti, a meno che non si selezioni questa opzione e non si specifichi un diverso numero massimo di log degli errori tramite l'opzione seguente.  
  
     **Numero massimo di file di log degli errori**  
     Consente di specificare il numero massimo di log degli errori creati prima di essere riciclati. Il valore predefinito è 6 che corrisponde al numero di log di backup precedenti mantenuti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prima che vengano riciclati.  
  
  
