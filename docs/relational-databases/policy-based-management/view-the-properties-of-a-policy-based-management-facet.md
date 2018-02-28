---
title: "Visualizzare le proprietà di un facet della gestione basata su criteri | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Policy-Based Management, view facet properties
ms.assetid: 022a244c-c2e7-4467-b9a2-c7a27859be22
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0ef0cb61dbfbf8e026b64db3ce97c24a3806be5b
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="view-the-properties-of-a-policy-based-management-facet"></a>Visualizzare le proprietà di un facet della gestione basata su criteri
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
In questo argomento verrà descritto come visualizzare le proprietà di un facet della gestione basata su criteri in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per visualizzare le proprietà di un facet tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È necessaria l'appartenenza al ruolo PolicyAdministratorRole nel database msdb.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-view-the-properties-of-a-facet"></a>Per visualizzare le proprietà di un facet  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il server contenente il facet di cui si desidera visualizzare le proprietà.  
  
2.  Fare clic sul segno più per espandere la cartella **Gestione** .  
  
3.  Fare clic sul segno più per espandere la cartella **Gestione criteri**.  
  
4.  Fare clic sul segno più per espandere la cartella **Facet** .  
  
5.  Fare clic con il pulsante destro del mouse sul facet di cui si vogliono visualizzare le proprietà e scegliere **Proprietà**. Per altre informazioni sulle opzioni disponibili nella finestra di dialogo **Proprietà facet -***nome_facet*, vedere [Finestra di dialogo Proprietà facet, pagina Generale](../../relational-databases/policy-based-management/facet-properties-dialog-box-general-page.md), [Finestra di dialogo Proprietà facet, pagina Criteri dipendenti](../../relational-databases/policy-based-management/facet-properties-dialog-box-dependent-policies-page.md), e [Finestra di dialogo Proprietà facet, pagina Condizioni dipendenti](../../relational-databases/policy-based-management/facet-properties-dialog-box-dependent-conditions-page.md).  
  
6.  Al termine, fare clic su **Chiudi**.  
  
  
