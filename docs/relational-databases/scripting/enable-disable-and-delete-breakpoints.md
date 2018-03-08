---
title: Abilitare, disabilitare ed eliminare punti di interruzione | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 357b5874-273f-43a9-8e30-83872bdea5dc
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2c78a83bbf85641580f05d08af7272bce554bff2
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="enable-disable-and-delete-breakpoints"></a>Abilitazione, disabilitazione ed eliminazione di punti di interruzione
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Per visualizzare e gestire tutti i punti di interruzione impostati, è possibile usare la finestra **Punti di interruzione**. Utilizzare questa finestra per visualizzare informazioni sui punti di interruzione e per effettuare azioni quali l'eliminazione, la disabilitazione o l'abilitazione di punti di interruzione.  
  
## <a name="the-breakpoints-window"></a>Finestra Punti di interruzione  
 Nella finestra **Punti di interruzione** vengono elencate informazioni quali la riga di codice sulla quale è impostato il punto di interruzione. Nella finestra **Punti di interruzione** è inoltre possibile eliminare, disabilitare e abilitare punti di interruzione. Per ulteriori informazioni sulla finestra **Punti di interruzione** , vedere [Punti di interruzione Window](../../relational-databases/scripting/transact-sql-debugger-breakpoints-window.md).  
  
 La disabilitazione di un punto di interruzione previene la sospensione dell'esecuzione, tuttavia il punto di interruzione rimane presente qualora si desideri riattivarlo in un secondo momento. L'eliminazione di un punto di interruzione ne comporta la rimozione permanente. È necessario attivare o disattivare un nuovo punto di interruzione per mettere in pausa esecuzione sull'istruzione.  
  
## <a name="to-open-the-breakpoints-window"></a>Per aprire la finestra Punti di interruzione  
 **To open the Breakpoints window**  
  
 È possibile aprire la finestra **Punti di interruzione** in uno dei modi seguenti:  
  
-   Scegliere **Finestre** dal menu **Debug**, quindi fare clic su **Punti di interruzione**.  
  
-   Nella barra degli strumenti **Debug** fare clic sul pulsante **Punti di interruzione** .  
  
-   Premere CTRL+ALT+B.  
  
## <a name="to-disable-a-single-breakpoint"></a>Per disabilitare un solo punto di interruzione  
 **To disable a single breakpoint**  
  
 È possibile disabilitare un singolo punto di interruzione in uno dei modi seguenti:  
  
-   Nella finestra dell'editor di query, fare clic con il pulsante destro del mouse sul punto di interruzione, quindi fare clic su **Disabilita punto di interruzione**.  
  
-   Nella finestra Punti di interruzione, deselezionare la casella di controllo a sinistra del punto di interruzione.  
  
## <a name="to-disable-all-breakpoints"></a>Per disabilitare tutti i punti di interruzione  
 **To disable all breakpoints**  
  
 È possibile disabilitare tutti i punti di interruzione in uno dei modi seguenti:  
  
-   Scegliere **Disabilita tutti i punti di interruzione** dal menu **Debug**.  
  
-   Nella barra degli strumenti della finestra **Punti di interruzione** , fare clic sul pulsante **Disabilita tutti i punti di interruzione** .  
  
## <a name="to-enable-a-single-breakpoint"></a>Per abilitare un solo punto di interruzione  
 **To enable a single breakpoint**  
  
 È possibile abilitare un singolo punto di interruzione in uno dei modi seguenti:  
  
-   Nella finestra dell'editor di query, fare clic con il pulsante destro del mouse sul punto di interruzione, quindi fare clic su **Abilita punto di interruzione**.  
  
-   Nella finestra Punti di interruzione, selezionare la casella di controllo a sinistra del punto di interruzione.  
  
## <a name="to-enable-all-breakpoints"></a>Per abilitare tutti i punti di interruzione  
 **To enable all breakpoints**  
  
 È possibile abilitare tutti i punti di interruzione in uno dei modi seguenti:  
  
-   Scegliere **Abilita tutti i punti di interruzione** dal menu **Debug**.  
  
-   Nella barra degli strumenti della finestra **Punti di interruzione** , fare clic sul pulsante **Abilita tutti i punti di interruzione** .  
  
## <a name="to-delete-a-single-breakpoint"></a>Per eliminare un solo punto di interruzione  
 **To delete a single breakpoint**  
  
 È possibile eliminare un singolo punto di interruzione in uno dei modi seguenti:  
  
-   Nella finestra dell'editor di query, fare clic con il pulsante destro del mouse sul punto di interruzione, quindi fare clic su **Elimina punto di interruzione**.  
  
-   Nella finestra Punti di interruzione fare clic con il pulsante destro del mouse su un punto di interruzione e scegliere **Elimina** dal menu di scelta rapida.  
  
-   Nella finestra Punti di interruzione, selezionare il punto di interruzione, quindi premere CANC.  
  
## <a name="to-delete-all-breakpoints"></a>Per eliminare tutti i punti di interruzione  
 **To delete all breakpoints**  
  
 È possibile eliminare tutti i punti di interruzione in uno dei modi seguenti:  
  
-   Scegliere **Elimina tutti i punti di interruzione** dal menu **Debug**.  
  
-   Sulla barra degli strumenti della finestra **Punti di interruzione** fare clic sul pulsante **Elimina tutti i punti di interruzione** .  
  
## <a name="see-also"></a>Vedere anche  
 [Attivare/disattivare un punto di interruzione](../../relational-databases/scripting/toggle-a-breakpoint.md)  
  
  
