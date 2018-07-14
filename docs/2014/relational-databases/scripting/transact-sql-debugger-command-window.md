---
title: Finestra di comando | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.CommandWindow
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7b69735b5c2a2750ab34bc34d5a7f3c3e46bba16
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37253793"
---
# <a name="command-window"></a>Finestra di comando
  Usare la funzionalità **Finestra di comando** per eseguire comandi, ad esempio i comandi debug o di modifica, sul codice incluso nella finestra dell'editor di query del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] di cui è in corso il debug. Per usare la funzionalità **Finestra di comando**, è necessario usare la modalità di debug. Il debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] supporta molti dei comandi supportati anche in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Command** window. Per altre informazioni, vedere [Visual Studio Command Window](http://go.microsoft.com/fwlink/?LinkId=112007)(Finestra di comando di Visual Studio).  
  
## <a name="task-list"></a>Elenco attività  
 **Per accedere alla funzionalità Finestra di comando**  
  
-   Scegliere **Avvia debug** dal menu **Debug**.  
  
 **Per stampare il valore di una variabile**  
  
-   In **Finestra di comando** digitare **Debug.Print \<NomeVariabile>**, quindi premere INVIO.  
  
 **Per elencare le informazioni sul thread corrente**  
  
-   Nel **finestra di comando**, tipo `Debug.ListThread`, quindi premere INVIO.  
  
 **Per aggiungere una variabile alla finestra Controllo immediato**  
  
-   In **Finestra di comando** digitare **Debug.QuickWatch \<NomeVariabile>**, quindi premere INVIO.  
  
## <a name="see-also"></a>Vedere anche  
 [Debugger Transact-SQL](transact-sql-debugger.md)  
  
  
