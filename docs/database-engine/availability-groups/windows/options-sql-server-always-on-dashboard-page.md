---
title: "Opzioni (SQL Server AlwaysOn, pagina Dashboard) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Alwayson.Dashboard"
ms.assetid: 4369b588-e982-4b57-80a1-beb2e879ce0b
caps.latest.revision: 8
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 8
---
# Opzioni (SQL Server AlwaysOn, pagina Dashboard)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Usare la pagina del **dashboard AlwaysOn** della finestra di dialogo **Opzioni** di [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] per configurare il dashboard AlwaysOn.  
  
 **Per accedere alla pagina:**  
  
 Nel menu **Strumenti** fare clic su **Opzioni**, espandere la cartella **SQL Server AlwaysOn** e quindi fare clic su **Dashboard**.  
  
## In questa pagina  
 **Abilitare l'aggiornamento automatico.**  
 Fare clic per abilitare l'aggiornamento automatico. Le opzioni disponibili sono le seguenti:  
  
-   Il campo **Intervallo di aggiornamento (in secondi)** visualizza il numero di secondi trascorsi i quali il dashboard viene aggiornato. Il valore predefinito è 30. Quando l'aggiornamento automatico è abilitato, è possibile modificare il campo per modificare l'intervallo di aggiornamento.  
  
-   Nel campo **Numero di tentativi di connessione** viene visualizzato il numero di tentativi effettuati dal dashboard per connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che ospita una replica di disponibilità per un gruppo di disponibilità monitorato tramite il dashboard. Il valore predefinito è 65535. Quando l'aggiornamento automatico è abilitato, è possibile modificare il campo per cambiare il numero di tentativi di connessione.  
  
 **Abilita criteri AlwaysOn definiti dall'utente**  
 Se sono stati definiti criteri AlwaysOn, fare clic su questa opzione per abilitarli.  
  
## Vedere anche  
 [Utilizzare il Dashboard AlwaysOn &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  