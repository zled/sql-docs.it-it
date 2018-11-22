---
title: "Passaggio 9: Test del pacchetto creato nella lezione 1 dell'esercitazione | Microsoft Docs"
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 9aee7acf-797b-46f2-830d-80ab64a9f0b6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0b140ea28397ace096c5b37db26a661fd7194647
ms.sourcegitcommit: 7e828cd92749899f4e1e45ef858ceb9a88ba4b6a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/14/2018
ms.locfileid: "51629544"
---
# <a name="lesson-1-9---testing-the-lesson-1-tutorial-package"></a>Lezione 1-9 - Test del pacchetto creato nella lezione 1 dell'esercitazione
In questa lezione sono state eseguite le operazioni seguenti:  
  
-   Creazione di un nuovo progetto [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
-   Configurazione delle gestioni connessioni necessarie al pacchetto per connettersi ai dati di origine e di destinazione.  
  
-   Aggiunta di un flusso di dati che preleva i dati da un'origine file flat, esegue le necessarie trasformazioni Ricerca sui dati e configura i dati per la destinazione.  
  
Il pacchetto è ora completo. A questo punto, è necessario testarlo.  
  
## <a name="checking-the-package-layout"></a>Verifica del layout del pacchetto  
Prima di testare il pacchetto è consigliabile verificare che il flusso di controllo e il flusso di dati nel pacchetto della lezione 1 contengano gli oggetti visualizzati nelle figure seguenti.  
  
**Flusso di controllo**  
  
![Flusso di controllo nel pacchetto](../integration-services/media/task9lesson1control.gif "Flusso di controllo nel pacchetto")  
  
**Flusso di dati**  
  
![Flusso di dati nel pacchetto](../integration-services/media/task9lesson1data.gif "Flusso di dati nel pacchetto")  
  
### <a name="to-run-the-lesson-1-tutorial-package"></a>Per eseguire il pacchetto creato nella lezione 1 dell'esercitazione  
  
1.  Scegliere **Avvia debug** dal menu **Debug**.  
  
    Il pacchetto verrà eseguito e verranno aggiunte 1097 righe alla tabella dei fatti **NewFactCurrencyRate** in **AdventureWorksDW2012**.  
  
2.  Al termine dell'esecuzione del pacchetto, scegliere **Arresta debug** dal menu **Debug**.  
  
## <a name="next-lesson"></a>Lezione successiva  
[Lezione 2: Aggiungere cicli con SSIS](../integration-services/lesson-2-adding-looping-with-ssis.md)  
  
## <a name="see-also"></a>Vedere anche  
[Esecuzione di progetti e pacchetti](packages/run-integration-services-ssis-packages.md) 
  
  
  
