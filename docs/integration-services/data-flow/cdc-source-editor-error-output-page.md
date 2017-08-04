---
title: CDC Source Editor (pagina Output degli errori) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ssis.designer.cdcsource.errorhandling.f1
ms.assetid: 8a4c2cb8-fd2f-4c45-824f-b93473a8981e
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 15818f42922d7fe21bdba64d0bf4c5e4a593eada
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="cdc-source-editor-error-output-page"></a>Editor origine CDC (pagina Output degli errori)
  Usare la pagina **Output degli errori** della finestra di dialogo **Editor origine CDC** per selezionare le opzioni di gestione degli errori.  
  
 Per ulteriori informazioni sull'origine CDC, vedere [CDC Source](../../integration-services/data-flow/cdc-source.md).  
  
## <a name="task-list"></a>Elenco attività  
 **Per aprire CDC Source Editor (pagina Output degli errori)**  
  
1.  In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], aprire il pacchetto [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] che contiene l'origine CDC.  
  
2.  Nella scheda **Flusso di dati** fare doppio clic sull'origine CDC.  
  
3.  In **Editor origine CDC**fare clic su **Output degli errori**.  
  
## <a name="options"></a>Opzioni  
 **Input/Output**  
 Consente di visualizzare il nome dell'origine dei dati.  
  
 **Colonna**  
 Consente di visualizzare le colonne esterne (di origine) selezionate nella pagina **Gestione connessione** della finestra di dialogo **Editor origine CDC** .  
  
 **Errore**  
 Consente di selezionare il modo in cui l'origine CDC deve gestire gli errori in un flusso: ignorare l'errore, reindirizzare la riga o interrompere il componente.  
  
 **Troncamento**  
 Consente di selezionare il modo in cui l'origine CDC deve gestire il troncamento in un flusso: ignorare l'errore, reindirizzare la riga o interrompere il componente.  
  
 **Description**  
 Non usato.  
  
 **Imposta questo valore nelle celle selezionate**  
 Consente di selezionare il modo in cui l'origine CDC gestisce tutte le celle selezionate in caso di errore o troncamento: ignorare l'errore, reindirizzare la riga o interrompere il componente.  
  
 **Applica**  
 Consente di applicare le opzioni di gestione degli errori alle celle selezionate.  
  
## <a name="error-handling-options"></a>Opzioni di gestione degli errori  
 Utilizzare le opzioni seguenti per configurare il modo in cui l'origine CDC gestisce errori e troncamenti.  
  
 **Interrompi componente**  
 Quando si verifica un errore o un troncamento l'attività Flusso di dati viene interrotta. Questo è il comportamento predefinito.  
  
 **Ignora errore**  
 L'errore o il troncamento viene ignorato e la riga di dati viene indirizzata all'output dell'origine CDC.  
  
 **Reindirizza flusso**  
 La riga di dati contenente l'errore o il troncamento viene indirizzata all'output degli errori dell'origine CDC. In questo caso, viene utilizzata la gestione degli errori dell'origine CDC. Per altre informazioni, vedere [Origine CDC](../../integration-services/data-flow/cdc-source.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Editor origine CDC &#40; Pagina Gestione connessione &#41;](../../integration-services/data-flow/cdc-source-editor-connection-manager-page.md)   
 [Editor origine CDC &#40; Pagina colonne &#41;](../../integration-services/data-flow/cdc-source-editor-columns-page.md)  
  
  
