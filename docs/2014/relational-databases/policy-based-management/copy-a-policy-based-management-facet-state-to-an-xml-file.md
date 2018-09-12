---
title: Copiare lo stato di un facet della gestione basata su criteri in un file XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, copy facet state to XML file
ms.assetid: 7d604ab1-6dd6-4f8e-a79c-eba99ab106fd
caps.latest.revision: 6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: adbb35cf7758c1802084b346d97775ffc6f5bcc8
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43820047"
---
# <a name="copy-a-policy-based-management-facet-state-to-an-xml-file"></a>Copiare lo stato di un facet della gestione basata su criteri in un file XML
  In questo argomento verrà descritto come copiare lo stato di un facet della gestione basata su criteri in un file XML in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per copiare lo stato di un facet in un file XML tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Le procedure descritte in questo argomento richiedono l'appartenenza al ruolo PolicyAdministratorRole nel database msdb.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-copy-a-facet-state-to-an-xml-file"></a>Per copiare lo stato di un facet in un file XML  
  
1.  In Esplora oggetti fare clic con il pulsante destro del mouse su un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], su un oggetto istanza, su un database o su un oggetto di database, quindi scegliere **Facet**.  
  
2.  Nella finestra di dialogo *Visualizza facet -***nome_oggetto* fare clic su **Esporta stato corrente come criteri**.  
  
3.  Nella finestra di dialogo **Esporta come criterio** digitare il percorso e il nome del file oppure usare il pulsante Sfoglia (**...**) per trovare il file, quindi digitare il nome del file XML. Per ulteriori informazioni sulle opzioni disponibili in questa finestra di dialogo, vedere [Export As Policy Dialog Box](export-as-policy-dialog-box.md).  
  
4.  Al termine, fare clic su **OK**.  
  
  
