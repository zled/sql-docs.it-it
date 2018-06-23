---
title: Opzioni (Editor di testo - tutti i linguaggi-tabulazioni) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
ms.assetid: bd715d6b-f873-41d4-aa10-57b7098b61cc
caps.latest.revision: 21
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f3e0df6dced5c69f60cbb95abcb5ba8eee78879b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157793"
---
# <a name="options-text-editor---all-languages--tabs-page"></a>Opzioni (Editor di testo - tutti i linguaggi-tabulazioni)
  Utilizzare questa finestra di dialogo per impostare il comportamento di tabulazione in tutti e cinque gli editor di [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Per visualizzare le opzioni disponibili, scegliere **Opzioni** dal menu **Strumenti**. Selezionare la cartella **Editor di testo**, espandere la cartella **Tutti i linguaggi**, quindi fare clic su **Tabulazioni**.  
  
## <a name="tabbing-options-by-editor"></a>Opzioni di tabulazione in base all'editor  
 Per impostare le opzioni per gli editor DMX, MDX e SQL Server Compact è necessario usare le finestre di dialogo **Tutti i linguaggi**. Le opzioni impostate in queste finestre vengono applicate anche agli editor di testo normale, Transact-SQL e XML, tuttavia, per tali editor, è possibile impostare separatamente le opzioni espandendo le sottocartelle per questi linguaggi e selezionando le relative pagine di opzioni. Alcuni linguaggi non supportano tutte le opzioni di tabulazione.  
  
> [!CAUTION]  
>  Se si imposta un'opzione mediante questa finestra di dialogo, ma si desidera un'impostazione diversa per gli editor di testo normale, Transact-SQL o XML, le opzioni per questi editor devono essere impostate dopo l'applicazione delle selezioni nella finestra di dialogo **Tutti i linguaggi**.  
  
 Se si selezionano impostazioni diverse per editor particolari, viene visualizzato il messaggio "Le impostazioni dei rientri (o delle tabulazioni) per singoli formati di testo sono in conflitto". Ad esempio, questo promemoria viene visualizzato se è stata selezionata l'opzione **Blocco** per **Testo normale** e l'opzione **Nessuno** per **XML**.  
  
## <a name="indenting"></a>Stili rientri  
 **Nessuno**  
 Quando questa opzione è selezionata, la nuova riga creata in seguito alla pressione di INVIO non viene rientrata. Il cursore viene posizionato in corrispondenza della prima colonna della nuova riga.  
  
 **Blocco**  
 Quando questa opzione è selezionata, la nuova riga creata in seguito al pressione di INVIO viene automaticamente rientrata utilizzando la stessa distanza con cui è stata rientrata la riga precedente.  
  
 **Intelligente**  
 Quando questa opzione è selezionata, la nuova riga creata in seguito alla pressione di INVIO viene posizionata in base al contesto.  
  
## <a name="tabs"></a>Tabulazioni  
 **Dimensione tabulazione**  
 Consente di impostare la distanza in spazi tra le tabulazioni. Il valore predefinito è quattro spazi.  
  
 **Dimensione rientro**  
 Consente di impostare la dimensione in spazi di un rientro automatico. Il valore predefinito è quattro spazi. Per riempire la dimensione specificata verranno inseriti caratteri di tabulazione, caratteri spazio o entrambi i caratteri.  
  
 **Inserisci spazi**  
 Quando questa opzione è selezionata, durante le operazioni di rientro vengono inseriti solo caratteri spazio, non caratteri di tabulazione. Se, ad esempio, l'opzione **Dimensione rientro** è impostata su 5, vengono inseriti cinque caratteri spazio ogni volta che si preme il tasto TAB o si fa clic sul pulsante **Aumenta rientro** sulla barra degli strumenti della finestra principale di [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
 **Mantieni tabulazioni**  
 Quando questa opzione è selezionata, durante le operazioni di rientro viene inserito il numero massimo di caratteri di tabulazione possibile. Ogni carattere di tabulazione riempie il numero di spazi specificato in **Dimensione tabulazione**. Se il valore specificato per l'opzione **Dimensione rientro** non è un multiplo pari del valore specificato per l'opzione **Dimensione tabulazione**, per riempire la differenza vengono aggiunti caratteri spazio.  
  
  