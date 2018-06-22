---
title: Aprire un modello | Microsoft Docs
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
- templates [Transact-SQL], opening
- opening templates
ms.assetid: 605b0f4c-5ba1-4249-ad1c-6341df77cd7a
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2249e09cb2f8eb932a9a5d1d98ffa4b4205a13dd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063503"
---
# <a name="open-a-template"></a>Aprire un modello
  È possibile aprire un modello da Esplora modelli.  
  
## <a name="to-open-a-template-from-template-explorer"></a>Per aprire un modello da Esplora modelli  
 È possibile aprire modelli da Esplora modelli.  
  
1.  Per aprire Esplora modelli scegliere **Esplora modelli** dal menu **Visualizza**.  
  
2.  Nell'elenco delle categorie di modello espandere la categoria che contiene il modello che si desidera aprire.  
  
3.  Sono disponibili tre modi per aprire il modello:  
  
    1.  Fare doppio clic sul modello per aprirlo nella finestra dell'editor di codice.  
  
    2.  Fare clic con il pulsante destro del mouse sul modello e selezionare **Apri** nella finestra dell'editor di codice.  
  
    3.  Trascinare il modello nella finestra dell'editor di codice per aggiungere il relativo codice al contenuto della finestra dell'editor.  
  
 Dopo avere aperto il modello, usare la finestra di dialogo **Sostituisci parametri modello** per sostituire i parametri del modello con i valori appropriati.  
  
 Se in seguito all'apertura di un modello viene aperta una nuova finestra dell'editor, la finestra verrà aperta con le credenziali della connessione attiva corrente. Ad esempio, se è attiva un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] in Esplora oggetti quando si apre il modello CREATE DATABASE, verrà aperta una nuova finestra dell'editor utilizzando una connessione a tale istanza. In assenza di connessione attiva, in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] verrà visualizzata una finestra di dialogo di accesso.  
  
## <a name="see-also"></a>Vedere anche  
 [Esplora modelli](template-explorer.md)   
 [Sostituire i parametri del modello](replace-template-parameters.md)  
  
  