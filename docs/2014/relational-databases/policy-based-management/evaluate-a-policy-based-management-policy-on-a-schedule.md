---
title: Valutare i criteri della gestione basata su criteri in una pianificazione | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: bea09522-ff47-4037-ab55-a98ea7c10099
caps.latest.revision: 6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f641af8b8901e094b4ee02131f1cb6dd4f5c43cc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37315671"
---
# <a name="evaluate-a-policy-based-management-policy-on-a-schedule"></a>Valutare i criteri della gestione basata su criteri in una pianificazione
  In questo argomento verrà descritto come valutare i criteri della gestione basata su criteri in una pianificazione in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per valutare i criteri in una pianificazione tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È necessaria l'appartenenza al ruolo PolicyAdministratorRole nel database msdb.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-evaluate-a-policy-on-a-schedule"></a>Per valutare i criteri in una pianificazione  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il server contenente la pianificazione dei criteri da valutare.  
  
2.  Fare clic sul segno più per espandere la cartella **Gestione** .  
  
3.  Fare clic sul segno più per espandere la cartella **Gestione criteri**.  
  
4.  Fare clic sul segno più per espandere la cartella **Criteri** .  
  
5.  Fare clic con il pulsante destro del mouse sui criteri di cui si desidera valutare la pianificazione, quindi scegliere **Proprietà**.  
  
6.  Nella finestra di dialogo **Apri criteri –***nome_criterio*, nell'elenco **Modalità di valutazione** selezionare **Su pianificazione**.  
  
7.  In **Pianificazione**fare clic su **Seleziona** per specificare una pianificazione esistente o su **Nuova** per creare una nuova pianificazione.  
  
8.  Al termine, fare clic su **OK**.  
  
  
