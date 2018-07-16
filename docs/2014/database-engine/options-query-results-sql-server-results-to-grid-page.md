---
title: Opzioni (risultati SQL Server-risultati della Query in pagina della griglia) | Microsoft Docs
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
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLResultsToGrid
ms.assetid: f88a0f5c-e800-473b-ae23-c3943de5ed63
caps.latest.revision: 25
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 23e5634a67ff6daec4f6b0852905d8596b885c60
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37318901"
---
# <a name="options-query-results-sql-server-results-to-grid-page"></a>Opzioni (risultati SQL Server-risultati della Query in pagina della griglia)
  Utilizzare questa pagina per specificare le opzioni di visualizzazione di un set di risultati di query in formato griglia. Le modifiche apportate a queste opzioni vengono applicate solo alle nuove query di [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Per modificare le opzioni relative alle query correnti, scegliere **Opzioni query** dal menu **Query** oppure fare clic con il pulsante destro del mouse nella finestra Query di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e quindi scegliere **Opzioni query**. Nel riquadro sinistro della finestra di dialogo **Opzioni query** fare clic su **Griglia** in **Risultati**.  
  
## <a name="uielement-list"></a>Elenco degli elementi di interfaccia  
 **Includi la query del set di risultati**  
 Restituisce il testo della query all'interno dell'output della query.  
  
 **Includi intestazioni di colonna durante la copia o salvataggio dei risultati**  
 Selezionare questa casella di controllo per includere le intestazioni di colonna quando i risultati vengono copiati negli Appunti o salvati in un file. Deselezionare la casella se si desidera salvare o copiare i dati dei risultati senza le intestazioni di colonna.  
  
 **Elimina risultati dopo l'esecuzione**  
 Impedisce la visualizzazione dei risultati della query nel riquadro di revisione. I risultati vengono eliminati immediatamente dopo l'esecuzione. La specifica di questa opzione consente di risparmiare memoria.  
  
 **Visualizzare i risultati in una scheda separata**  
 Selezionare questa casella di controllo per visualizzare il set di risultati in una nuova scheda invece che nella parte inferiore della finestra del documento di query.  
  
 **Passare alla scheda risultati dopo l'esecuzione di query**  
 Selezionare questa casella di controllo per impostare automaticamente lo stato attivo sul riquadro dei risultati al termine della query.  
  
 **Dimensioni massime caratteri recuperati**  
 **Dati non XML**:  
  
 Consente di immettere un valore compreso tra 1 e 65535 per specificare il numero massimo di caratteri che sarà possibile visualizzare in ogni cella.  
  
> [!NOTE]  
>  Se si specifica un numero elevato di caratteri, i dati nel set di risultati potrebbero non essere visualizzati completamente. Il numero massimo di caratteri visualizzati in ogni cella dipende dalle dimensioni del carattere. Se si specifica un valore elevato in questa casella e vengono restituiti set di risultati di notevoli dimensioni, la memoria per [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] potrebbe risultare insufficiente con effetti negativi sulle prestazioni del sistema.  
  
 **Dati XML**:  
  
 Consente di selezionare i valori **1 MB**, **2 MB**o **5 MB**. Selezionare **Illimitate** per recuperare tutti i caratteri.  
  
 **Ripristina predefiniti**  
 Reimposta le impostazioni predefinite originali per tutti i valori nella pagina.  
  
  
