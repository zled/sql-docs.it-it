---
title: "Passaggio 5: Aggiunta e configurazione dell'origine file flat | Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5c95ce51-e0fe-4fc5-95eb-2945929f2b13
caps.latest.revision: 20
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a48d451248e28f8c9e0fd623c96022f558b80ca8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068968"
---
# <a name="step-5-adding-and-configuring-the-flat-file-source"></a>Passaggio 5: Aggiunta e configurazione dell'origine file flat
  In questa attività verrà aggiunta e configurata l'origine file flat al pacchetto. Un'origine file flat è un componente del flusso di dati che utilizza i metadati definiti dalla gestione connessione file flat per specificare il formato e la struttura dei dati da estrarre dal file flat tramite un processo di trasformazione. È possibile configurare l'origine file flat per estrarre dati da un singolo file flat utilizzando la definizione del formato del file specificata dalla gestione connessione file flat.  
  
 Per questa esercitazione, si configurerà l'origine File Flat da utilizzare il `Sample Flat File Source Data` gestione connessione creata in precedenza.  
  
### <a name="to-add-a-flat-file-source-component"></a>Per aggiungere un componente origine file flat  
  
1.  Aprire il **flusso di dati** finestra di progettazione facendo doppio clic sui `Extract Sample Currency Data` attività flusso di dati o fare clic sul **scheda flusso di dati**.  
  
2.  Nella **Casella degli strumenti SSIS**espandere **OtherSources**, quindi trascinare un' **Origine file flat** sull'area di progettazione della scheda **Flusso di dati** .  
  
3.  Nel **flusso di dati** area di progettazione, fare doppio clic su appena aggiunta **origine File Flat**, fare clic su **rinominare**e modificare il nome in `Extract Sample Currency Data`.  
  
4.  Fare doppio clic sull'origine file flat per aprire la finestra di dialogo Editor origine file flat.  
  
5.  Nel **gestione connessione file Flat** , quindi selezionare `Sample Flat File Source Data`.  
  
6.  Fare clic su **Colonne** e verificare che i nomi delle colonne siano corretti.  
  
7.  Fare clic su **OK**.  
  
8.  Fare clic con il pulsante destro del mouse sull'origine file flat e scegliere **Proprietà**.  
  
9. Nella finestra Proprietà verificare che il `LocaleID` è impostata su **inglese (Stati Uniti)**.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Passaggio 6: Aggiunta e configurazione delle trasformazioni ricerca](lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Origine File flat](data-flow/flat-file-source.md)   
 [Editor gestione connessione file flat &#40;pagina Generale&#41;](general-page-of-integration-services-designers-options.md)  
  
  