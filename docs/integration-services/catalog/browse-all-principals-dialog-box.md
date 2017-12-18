---
title: "Finestra di dialogo Sfoglia tutte le entità | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: service
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.ssis.ssms.browseprincipals.f1
ms.assetid: f11d2c5e-ee05-45f3-8dc2-0feb99b2f76f
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eb1af890ad8c92bd32e7250bde4210f78c419545
ms.sourcegitcommit: 6bbecec786b0900db86203a04afef490c8d7bfab
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2017
---
# <a name="browse-all-principals-dialog-box"></a>Finestra di dialogo Sfoglia tutte le entità
  Utilizzare la finestra di dialogo **Sfoglia tutte le entità** per selezionare un'entità di database per modificare le autorizzazioni dell'entità per il progetto selezionato o per tutti i progetti contenuti in una cartella selezionata.  
  
 **Per saperne di più**  
  
-   [Aprire la finestra di dialogo Sfoglia tutte le entità](#open_dialog)  
  
-   [Configurare le opzioni](#options)  
  
##  <a name="open_dialog"></a> Aprire la finestra di dialogo Sfoglia tutte le entità  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]connettersi al server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     Verrà eseguita la connessione all'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in cui è ospitato il catalogo SSISDB.  
  
2.  In Esplora oggetti espandere l'albero per visualizzare il nodo dei **cataloghi di Integration Services** .  
  
3.  Espandere il nodo **SSISDB** .  
  
4.  Per modificare le autorizzazioni dell'entità per tutti i progetti contenuti in una cartella selezionata, fare clic con il pulsante destro del mouse sulla cartella, quindi scegliere **Proprietà**.  
  
     Per modificare le autorizzazioni dell'entità per un progetto selezionato, espandere la cartella che contiene il progetto, fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **Proprietà**.  
  
5.  Selezionare la pagina **Autorizzazioni** , quindi fare clic su **Sfoglia**.  
  
##  <a name="options"></a> Configurare le opzioni  
 In questa pagina vengono visualizzate le entità della vista del catalogo sys.database_principals del database SSISDB.  
  
 Tramite la selezione le entità vengono aggiunte all'elenco **Account di accesso o ruoli** nella pagina **Autorizzazioni** della finestra di dialogo padre quando si fa clic su **OK** e si chiude la finestra di dialogo **Sfoglia tutte le entità** . Dopo aver aggiunto le entità all'elenco **Account di accesso o ruoli** , è possibile modificare le autorizzazioni per il progetto selezionato.  
  
 **Colonna Selezione**  
 Selezionare per aggiungere l'entità all'elenco **Account di accesso o ruoli** nella pagina **Autorizzazioni** della finestra di dialogo padre.  
  
 **Colonna Icona**  
 Icona che corrisponde al **Tipo** di entità.  
  
 **Nome**  
 Nome dell'entità.  
  
 **Tipo**  
 Tipo dell'entità. I tipi comuni sono:  
  
-   Utente SQL  
  
-   Utente di Windows  
  
-   Ruolo del database  
  
  
