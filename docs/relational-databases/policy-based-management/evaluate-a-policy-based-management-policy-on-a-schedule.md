---
title: "Valutare i criteri della gestione basata su criteri in una pianificazione | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "gestione basata su criteri, valutazione criteri"
ms.assetid: bea09522-ff47-4037-ab55-a98ea7c10099
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# Valutare i criteri della gestione basata su criteri in una pianificazione
  In questo argomento verrà descritto come valutare i criteri della gestione basata su criteri in una pianificazione in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per valutare i criteri in una pianificazione tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È necessaria l'appartenenza al ruolo PolicyAdministratorRole nel database msdb.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per valutare i criteri in una pianificazione  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il server contenente la pianificazione dei criteri da valutare.  
  
2.  Fare clic sul segno più per espandere la cartella **Gestione** .  
  
3.  Fare clic sul segno più per espandere la cartella **Gestione criteri**.  
  
4.  Fare clic sul segno più per espandere la cartella **Criteri** .  
  
5.  Fare clic con il pulsante destro del mouse sui criteri di cui si desidera valutare la pianificazione, quindi scegliere **Proprietà**.  
  
6.  Nella finestra di dialogo **Apri criteri –***nome_criterio*, nell'elenco **Modalità di valutazione**, selezionare **Su pianificazione**.  
  
7.  In **Pianificazione**fare clic su **Seleziona** per specificare una pianificazione esistente o su **Nuova** per creare una nuova pianificazione.  
  
8.  Al termine, fare clic su **OK**.  
  
  