---
title: Opzioni (Editor di testo - Transact-SQL - tabulazioni) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.SQL.Tabs
dev_langs:
- TSQL
ms.assetid: a4499784-67f7-46ef-9f7c-2d0fdd117a52
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 9c97c95ec2dff4d96f37eb274ee6ec98af117f89
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37152642"
---
# <a name="options-text-editor---transact-sql---tabs-page"></a>Opzioni (pagina Editor di testo - Transact-SQL - tabulazioni)
  Utilizzare questa finestra di dialogo per cambiare il comportamento di tabulazione dell'editor di query del [!INCLUDE[ssDE](../includes/ssde-md.md)] utilizzato per programmare gli script [!INCLUDE[tsql](../includes/tsql-md.md)]. Per visualizzare queste impostazioni, scegliere **Opzioni** dal menu **Strumenti**, espandere la cartella **Editor di testo**, espandere la sottocartella **Transact-SQL** e quindi fare clic su **Schede**.  
  
## <a name="setting-options-in-multiple-locations"></a>Opzioni di impostazione in più posizioni  
 Le opzioni per l'editor di query del [!INCLUDE[ssDE](../includes/ssde-md.md)] possono essere impostate anche nella finestra di dialogo **Tutti i linguaggi - Schede**. Se si utilizza la finestra di dialogo **Tutti i linguaggi** per impostare opzioni diverse per gli altri editor di [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , ad esempio DMX o MDX, è necessario reimpostare le opzioni dell'editor di query del [!INCLUDE[ssDE](../includes/ssde-md.md)] tramite questa finestra di dialogo.  
  
## <a name="indenting"></a>Stili rientri  
 **Nessuno**  
 Quando questa opzione è selezionata, la nuova riga creata in seguito alla pressione di INVIO non viene rientrata. Il cursore viene posizionato in corrispondenza della prima colonna della nuova riga.  
  
 **Blocco**  
 Quando è selezionata questa opzione la nuova riga creata premendo INVIO viene rientrata automaticamente della stessa distanza della riga precedente.  
  
 **Smart**  
 Questa opzione non è disponibile.  
  
## <a name="tabs"></a>Tabulazioni  
 **Dimensione tabulazione**  
 Consente di impostare la distanza in spazi tra le tabulazioni. Il valore predefinito è quattro spazi.  
  
 **Dimensione del rientro**  
 Consente di impostare la dimensione in spazi di un rientro automatico. Il valore predefinito è quattro spazi. Per riempire il rientro specificato verranno inseriti caratteri di tabulazione, caratteri di spazio o entrambi.  
  
 **Inserisci gli spazi**  
 Quando questa opzione è selezionata, durante le operazioni di rientro vengono inseriti solo caratteri spazio, non caratteri di tabulazione. Se la **Dimensione rientro** è impostata su 5, ad esempio, verranno inseriti cinque caratteri di spazio ogni volta che viene premuto TAB o si fa clic sul pulsante **Aumenta rientro** sulla barra degli strumenti della finestra principale di [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] .  
  
 **Mantieni tabulazioni**  
 Quando questa opzione è selezionata, durante le operazioni di rientro viene inserito il numero massimo di caratteri di tabulazione possibile. Ogni carattere di tabulazione riempie il numero di spazi specificato in **Dimensione tabulazione**. Se il valore specificato per l'opzione **Dimensione rientro** non è un multiplo pari del valore specificato per l'opzione **Dimensione tabulazione**, per riempire la differenza vengono aggiunti caratteri spazio.  
  
  
