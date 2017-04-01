---
title: "Passaggio 4: Test del pacchetto creato nella lezione 2 dell&#39;esercitazione | Microsoft Docs"
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
ms.assetid: 0e8c0a25-8f79-41df-8ed2-f82a74b129cd
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# Passaggio 4: Test del pacchetto creato nella lezione 2 dell&#39;esercitazione
Dopo aver configurato il contenitore Ciclo Foreach e la gestione connessione file flat, il pacchetto creato nella lezione 2 consente di eseguire un'iterazione dell'insieme di 14 file flat contenuti nella cartella Sample Data. Ogni volta che viene trovato un nome di file corrispondente ai criteri specificati, il contenitore Ciclo Foreach popola la variabile definita dall'utente con il nome del file. Tale variabile aggiorna di conseguenza la proprietà ConnectionString della gestione connessione file flat e viene stabilita una connessione al nuovo file flat. Il contenitore Ciclo Foreach quindi esegue l'attività del flusso di dati non modificati sui dati del nuovo file flat prima di connettersi al file successivo contenuto nella cartella.  
  
Utilizzare la procedura seguente per verificare la funzionalità relativa ai cicli aggiunta al pacchetto.  
  
> [!NOTE]  
> Se si esegue il pacchetto della lezione 1, sarà necessario eliminare i record da dbo.FactCurrency in AdventureWorksDW2012 prima di eseguire il pacchetto da questa lezione. In caso contrario, il pacchetto non verrà eseguito correttamente e verranno generati errori indicanti una violazione del vincolo di chiave primaria. Verranno restituiti gli stessi errori se si esegue il pacchetto selezionando Debug/Avvia debug (o premendo F5) perché verranno eseguite entrambe le lezioni 1 e 2. Tramite la lezione 2 si tenterà di inserire record già inseriti nella lezione 1.  
  
## Verifica del layout del pacchetto  
Prima di testare il pacchetto, è consigliabile verificare che il flusso di controllo e il flusso di dati nel pacchetto della lezione 2 contengano gli oggetti visualizzati nei diagrammi seguenti. Il flusso di dati deve essere identico a quello nella lezione 1.  
  
**Flusso di controllo**  
  
![Control flow in package](../integration-services/media/task4lesson2control.gif "Control flow in package")  
  
**Flusso di dati**  
  
![Data flow in package](../integration-services/media/task9lesson1data.gif "Data flow in package")  
  
### Per testare il pacchetto creato nella lezione 2 dell'esercitazione  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Lesson 2.dtsx** e scegliere **Esegui pacchetto**.  
  
    Il pacchetto verrà eseguito. È possibile verificare lo stato di ogni ciclo nella finestra Output o facendo clic sulla scheda **Stato** . Ad esempio, viene evidenziato che sono state aggiunte 1097 righe alla tabella di destinazione dal file Currency_VEB.txt.  
  
2.  Al termine dell'esecuzione del pacchetto, scegliere **Arresta debug** dal menu **Debug**.  
  
## Lezione successiva  
[Lezione 5: Aggiungere configurazioni del pacchetto SSIS per il modello di distribuzione del pacchetto](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
  
## Vedere anche  
[Esecuzione di progetti e pacchetti](../Topic/Execution%20of%20Projects%20and%20Packages.md)  
  
  
  
