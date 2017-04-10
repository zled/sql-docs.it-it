---
title: "Visualizzazione delle voci di log nella finestra Registra eventi | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "log [Integration Services], visualizzazione"
  - "pacchetti di Integration Services, log"
  - "pacchetti [Integration Services], log"
ms.assetid: c02123c3-67fc-4370-ad14-91ed259f1873
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 21
---
# Visualizzazione delle voci di log nella finestra Registra eventi
  In questo argomento viene descritta la procedura per eseguire un pacchetto e visualizzare le voci di log scritte da tale pacchetto. È possibile visualizzare le voci di log in tempo reale. Le voci di log scritte nella finestra **Registra eventi** possono inoltre essere copiate e salvate per analisi ulteriori.  
  
 Per scrivere le voci di log nella finestra **Registra eventi** non è necessario scriverle in un log.  
  
### Per visualizzare voci di log  
  
1.  In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] aprire il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  Scegliere **Registra eventi** dal menu **SSIS**. Facoltativamente, è possibile visualizzare la finestra **Registra eventi** eseguendo il mapping tra il comando View.LogEvents e una combinazione di tasti scelta dall'utente nella pagina **Tastiera** della finestra di dialogo **Opzioni**.  
  
3.  Scegliere **Avvia debug** dal menu **Debug**.  
  
     Quando il runtime rileva i messaggi personalizzati e gli eventi per cui è attivata la registrazione, le voci di log per ogni evento o messaggio vengono scritte nella finestra **Registra eventi**.  
  
4.  Scegliere **Arresta debug** dal menu **Debug**.  
  
     Le voci di log rimangono disponibili nella finestra **Registra eventi** finché non si esegue nuovamente il pacchetto, non si esegue un pacchetto diverso o non si chiude [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
5.  Esaminare le voci di log nella finestra **Registra eventi**.  
  
6.  Facoltativamente, selezionare le voci di log da copiare, fare clic con il pulsante destro del mouse e quindi scegliere **Copia**.  
  
7.  Facoltativamente, fare doppio clic su una voce di log e, nella finestra di dialogo **Voce log**, esaminare i dettagli della singola voce di log selezionata.  
  
8.  Nella finestra di dialogo **Voce log** usare le frecce SU o GIÙ per visualizzare la voce di log precedente o successiva e quindi fare clic sull'icona Copia per copiare la voce di log selezionata.  
  
9. Aprire un editor di testo, incollare e quindi salvare la voce di log in un file di testo.  
  
## Vedere anche  
 [Registrazione di Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md)  
  
  