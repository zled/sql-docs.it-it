---
title: Esportare i criteri della gestione basata su criteri | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Policy-Based Management, export policy
ms.assetid: f0001b33-9078-4432-8460-496736fb325a
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 77c2911f2d4cefd96c01ac928bb944cb3e945795
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156675"
---
# <a name="export-a-policy-based-management-policy"></a>Esportare i criteri della gestione basata su criteri
  In questo argomento verrà descritto come esportare i criteri della gestione basata su criteri in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per esportare i criteri tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È necessaria l'appartenenza al ruolo PolicyAdministratorRole nel database msdb.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-export-a-policy"></a>Per esportare i criteri  
  
1.  In Esplora oggetti fare clic sul segno più per espandere il server contenente i criteri della gestione basata su criteri da esportare.  
  
2.  Fare clic sul segno più per espandere la cartella **Gestione** .  
  
3.  Fare clic sul segno più per espandere la cartella **Gestione criteri**.  
  
4.  Fare clic sul segno più per espandere la cartella **Criteri** .  
  
5.  Fare clic con il pulsante destro del mouse sui criteri che si vuole esportare e scegliere **Esporta criteri**.  
  
6.  Nella finestra di dialogo **Esporta criteri** digitare il percorso e il nome del file nella barra degli indirizzi. In alternativa, individuare un percorso appropriato per il file nel pannello di navigazione della finestra di dialogo, quindi digitare il nome del file XML nella casella **Nome file** .  
  
7.  Al termine, fare clic su **Salva**.  
  
  