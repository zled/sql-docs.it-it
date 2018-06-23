---
title: Opzioni (Editor di testo-Transact-SQL-IntelliSense) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.SQL.Advanced
dev_langs:
- TSQL
ms.assetid: 1855d916-5bf9-4d94-b0fb-9f9bb05ff950
caps.latest.revision: 15
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 67dc90ab7682d4882a3d64b78af1a69968fd2247
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170178"
---
# <a name="options-text-editor-transact-sql-intellisense"></a>Opzioni (Editor di testo-Transact-SQL-IntelliSense)
  La finestra di dialogo **Opzioni** consente di modificare le impostazioni IntelliSense per l'editor di query del [!INCLUDE[ssDE](../includes/ssde-md.md)]. Per visualizzare queste impostazioni, scegliere **Opzioni** dal menu **Strumenti**, espandere la cartella **Editor di testo**, espandere la cartella **Transact-SQL** e fare clic su **Avanzate**.  
  
## <a name="transact-sql-intellisense-settings"></a>Impostazioni IntelliSense per Transact-SQL  
 Specifica le opzioni IntelliSense per l'editor di query del [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
### <a name="enable-intellisense"></a>Abilitazione di IntelliSense  
 Abilita le caratteristiche IntelliSense. Quando questa casella non è selezionata, le opzioni IntelliSense non sono disponibili. Questa casella di controllo è selezionata per impostazione predefinita.  
  
 **Sottolinea errori**  
 Identifica errori semantici e di sintassi nelle istruzioni [!INCLUDE[tsql](../includes/tsql-md.md)] nella finestra Query. Tutti gli errori e gli avvisi sono visualizzati in rosso. Errori e avvisi sono supportati solo per le istruzioni [!INCLUDE[tsql](../includes/tsql-md.md)] per le quali è stato implementato IntelliSense. Questa casella di controllo è selezionata per impostazione predefinita.  
  
 **Struttura istruzioni**  
 Abilita la modalità struttura quando viene aperto un file in modo da creare blocchi comprimibili del codice [!INCLUDE[tsql](../includes/tsql-md.md)]. Questa casella di controllo è selezionata per impostazione predefinita.  
  
 **Dimensione massima script**  
 Specifica la dimensione in base alla quale la funzionalità IntelliSense viene disabilitata. Se uno script supera la dimensione specificata, viene visualizzato un messaggio di avviso e tutte le caratteristiche IntelliSense vengono disabilitate per quella finestra dell'editor, ad eccezione del codice a colori. IntelliSense è riabilitato quando si elimina del testo per ridurre la dimensione dello script entro il limite specificato. L'abilitazione di IntelliSense in caso di script di grandi dimensioni può ridurre le prestazioni di computer lenti. Le dimensioni consentite sono 100 KB, 500 KB, 1 MB, 2 MB e Illimitate. Il valore predefinito è 1 MB.  
  
 **Maiuscole/minuscole per nomi di funzioni predefinite**  
 Specifica se i nomi delle funzioni [!INCLUDE[tsql](../includes/tsql-md.md)] predefinite inclusi negli elenchi di completamento usano lettere maiuscole, ad esempio DATEADD, o lettere minuscole, ad esempio dateadd. Selezionare l'opzione corrispondente alle convenzioni di scrittura del codice [!INCLUDE[tsql](../includes/tsql-md.md)] in uso.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi di IntelliSense &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/troubleshooting-intellisense.md)  
  
  