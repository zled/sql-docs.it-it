---
title: "Valutare i criteri della gestione basata su criteri da quei criteri | Microsoft Docs"
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
ms.assetid: 0b3214bd-d0ab-45ab-9281-3d95507abe54
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# Valutare i criteri della gestione basata su criteri da quei criteri
  In questo argomento verrà descritto come valutare i criteri utilizzandoli in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per valutare i criteri tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È necessaria l'appartenenza al ruolo PolicyAdministratorRole nel database msdb.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per valutare i criteri  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il server contenente i criteri da valutare.  
  
2.  Fare clic sul segno più per espandere la cartella **Gestione** .  
  
3.  Fare clic sul segno più per espandere la cartella **Gestione criteri**.  
  
4.  Fare clic sul segno più per espandere la cartella **Criteri** .  
  
5.  Fare clic con il pulsante destro del mouse sui criteri da valutare e scegliere **Valuta**.  
  
6.  Nella finestra di dialogo **Risultati valutazione**  verranno visualizzati i risultati della valutazione dei criteri. Per le destinazioni non conformi ai criteri e con proprietà che possono essere riconfigurate tramite gestione basata su criteri, è possibile applicare la conformità facendo clic su **Applica**. Per ulteriori informazioni sulle opzioni disponibili nella finestra di dialogo **Valuta criteri** , vedere [Evaluate Policies Dialog Box, Policy Selection Page](../../relational-databases/policy-based-management/evaluate-policies-dialog-box-policy-selection-page.md) e [Evaluate Policies Dialog Box, Evaluation Results Page](../../relational-databases/policy-based-management/evaluate-policies-dialog-box-evaluation-results-page.md).  
  
7.  Al termine, fare clic su **Chiudi**.  
  
  