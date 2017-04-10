---
title: "Passaggio 9: Test del pacchetto creato nella lezione 1 dell&#39;esercitazione | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 9aee7acf-797b-46f2-830d-80ab64a9f0b6
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# Passaggio 9: Test del pacchetto creato nella lezione 1 dell&#39;esercitazione
In questa lezione sono state eseguite le operazioni seguenti:  
  
-   Creazione di un nuovo progetto [!INCLUDE[ssIS](../includes/ssis-md.md)].  
  
-   Configurazione delle gestioni connessioni necessarie al pacchetto per connettersi ai dati di origine e di destinazione.  
  
-   Aggiunta di un flusso di dati che preleva i dati da un'origine file flat, esegue le necessarie trasformazioni Ricerca sui dati e configura i dati per la destinazione.  
  
Il pacchetto è ora completo. A questo punto, è necessario testarlo.  
  
## Verifica del layout del pacchetto  
Prima di testare il pacchetto è consigliabile verificare che il flusso di controllo e il flusso di dati nel pacchetto della lezione 1 contengano gli oggetti visualizzati nelle figure seguenti.  
  
**Flusso di controllo**  
  
![Control flow in package](../integration-services/media/task9lesson1control.gif "Control flow in package")  
  
**Flusso di dati**  
  
![Data flow in package](../integration-services/media/task9lesson1data.gif "Data flow in package")  
  
### Per eseguire il pacchetto creato nella lezione 1 dell'esercitazione  
  
1.  Scegliere **Avvia debug** dal menu **Debug**.  
  
    Il pacchetto verrà eseguito e verranno aggiunte 1097 righe alla tabella dei fatti **FactCurrency** in **AdventureWorksDW2012**.  
  
2.  Al termine dell'esecuzione del pacchetto, scegliere **Arresta debug** dal menu **Debug**.  
  
## Lezione successiva  
[Lezione 2: Aggiungere cicli con SSIS](../integration-services/lesson-2-adding-looping-with-ssis.md)  
  
## Vedere anche  
[Esecuzione di progetti e pacchetti](../Topic/Execution%20of%20Projects%20and%20Packages.md)  
  
  
  
