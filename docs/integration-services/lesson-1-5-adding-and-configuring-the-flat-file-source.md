---
title: 'Passaggio 5: Aggiunta e configurazione di Flat File origine | Documenti Microsoft'
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 5c95ce51-e0fe-4fc5-95eb-2945929f2b13
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 2c56b634f36e69e06e03e0206cd70d841f4682ea
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="lesson-1-5---adding-and-configuring-the-flat-file-source"></a>Lezione 1-5-aggiunta e configurazione dell'origine File Flat
In questa attività verrà aggiunta e configurata l'origine file flat al pacchetto. Un'origine file flat è un componente del flusso di dati che utilizza i metadati definiti dalla gestione connessione file flat per specificare il formato e la struttura dei dati da estrarre dal file flat tramite un processo di trasformazione. È possibile configurare l'origine file flat per estrarre dati da un singolo file flat utilizzando la definizione del formato del file specificata dalla gestione connessione file flat.  
  
In questa esercitazione verrà configurata l'origine file flat in modo da utilizzare la gestione connessione **Sample Flat File Source Data** creata in precedenza.  
  
### <a name="to-add-a-flat-file-source-component"></a>Per aggiungere un componente origine file flat  
  
1.  Aprire la finestra di progettazione **Flusso di dati** facendo doppio clic sull'attività del flusso di dati **Extract Sample Currency Data** o selezionando la scheda **Flusso di dati**.  
  
2.  Nella **Casella degli strumenti SSIS**espandere **OtherSources**, quindi trascinare un' **Origine file flat** sull'area di progettazione della scheda **Flusso di dati** .  
  
3.  Nell'area di progettazione **Flusso di dati** fare clic con il pulsante destro del mouse sulla nuova **origine file flat**, scegliere **Rinomina**e cambiare il nome in **Extract Sample Currency Data**.  
  
4.  Fare doppio clic sull'origine file flat per aprire la finestra di dialogo Editor origine file flat.  
  
5.  Nella casella **Gestione connessione file flat** selezionare **Sample Flat File Source Data**.  
  
6.  Fare clic su **Colonne** e verificare che i nomi delle colonne siano corretti.  
  
7.  Scegliere **OK**.  
  
8.  Fare clic con il pulsante destro del mouse sull'origine file flat e scegliere **Proprietà**.  
  
9. Nella finestra Proprietà verificare che la proprietà **LocaleID** sia impostata su **Inglese (Stati Uniti)**.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Passaggio 6: Aggiunta e configurazione delle trasformazioni Ricerca](../integration-services/lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
## <a name="see-also"></a>Vedere anche  
[Origine file flat](../integration-services/data-flow/flat-file-source.md)  
[Editor gestione connessione file flat &#40;pagina Generale&#41;](../integration-services/connection-manager/flat-file-connection-manager-editor-general-page.md)  
  
  
  

