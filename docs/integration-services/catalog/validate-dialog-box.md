---
title: Finestra di dialogo Convalida | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: service
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ssis.ssms.isprojectvalidate.f1
- sql13.ssis.ssms.ispackagevalidate.f1
ms.assetid: 134e14ce-4f8d-4a20-889a-918014c841d8
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5da747ddcee442987fd6b9cf4d961690b76108db
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="validate-dialog-box"></a>Finestra di dialogo Convalida
  Utilizzare la finestra di dialogo **Convalida** per verificare i problemi comuni in un progetto o pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Se si è verificato un problema, viene visualizzato un messaggio nella parte superiore della finestra di dialogo. In caso contrario, viene visualizzato il termine Pronto.  
  
 **Per saperne di più**  
  
-   [Aprire la finestra di dialogo Convalida](#open_dialog)  
  
-   [Impostare le opzioni nella pagina Generale](#general)  
  
##  <a name="open_dialog"></a> Aprire la finestra di dialogo Convalida  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]connettersi al server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     Verrà eseguita la connessione all'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in cui è ospitato il database SSISDB.  
  
2.  In Esplora oggetti espandere l'albero per visualizzare il nodo dei **cataloghi di Integration Services** .  
  
3.  Espandere il nodo **SSISDB** .  
  
4.  Espandere la cartella contenente il progetto o pacchetto che si desidera convalidare.  
  
5.  Fare clic con il pulsante destro del mouse sul pacchetto o sul progetto, quindi selezionare **Convalida**.  
  
##  <a name="general"></a> Impostare le opzioni nella pagina Generale  
 **Ambiente**  
 Selezionare l'ambiente da utilizzare per convalidare il progetto o pacchetto.  
  
 **Runtime a 32 bit**  
 Scegliere di utilizzare un runtime a 32 bit per eseguire un pacchetto.  
  
 Nella scheda **Parametri** sono elencati i valori dei parametri utilizzati per convalidare il progetto o pacchetto. Di seguito sono riportate le opzioni della scheda Parametri.  
  
 **Contenitore**  
 Viene elencato l'oggetto contenente il parametro.  
  
 **Parametro**  
 Viene elencato il nome dei parametri.  
  
 **Value**  
 Viene elencato il valore del parametro.  
  
 Nella scheda **Gestioni connessioni** sono elencati i valori delle proprietà delle gestioni connessioni utilizzati per convalidare il progetto o pacchetto.  
  
 Di seguito sono riportate le opzioni della scheda **Gestioni connessioni** .  
  
 **Contenitore**  
 Viene elencato l'oggetto contenente la gestione connessione.  
  
 **Nome**  
 Viene elencato il nome della gestione connessione.  
  
 **Nome proprietà**  
 Viene elencato il nome della proprietà della gestione connessione.  
  
 **Value**  
 Viene elencato il valore assegnato alla proprietà della gestione connessione.  
  
  
