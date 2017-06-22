---
title: Aprire un modello | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [Transact-SQL], opening
- opening templates
ms.assetid: 605b0f4c-5ba1-4249-ad1c-6341df77cd7a
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: fdf01f10ec6de0b63b1981f59cc6ba541b4de7c2
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

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
  
Se in seguito all'apertura di un modello viene aperta una nuova finestra dell'editor, la finestra verrà aperta con le credenziali della connessione attiva corrente. Ad esempio, se è attiva un'istanza del [!INCLUDE[ssDE](../../includes/ssde_md.md)] in Esplora oggetti quando si apre il modello CREATE DATABASE, verrà aperta una nuova finestra dell'editor utilizzando una connessione a tale istanza. In assenza di connessione attiva, in [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] verrà visualizzata una finestra di dialogo di accesso.  
  
## <a name="see-also"></a>Vedere anche  
[Visualizza](../../ssms/template/template-explorer.md)  
[Sostituisci parametri modello](../../ssms/template/replace-template-parameters.md)  
  

