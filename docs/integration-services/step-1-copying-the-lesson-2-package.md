---
title: "Passaggio 1: Copia del pacchetto della lezione 2 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 4bd91402-4e37-41de-ab78-8ca5a1948a37
caps.latest.revision: 29
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# Passaggio 1: Copia del pacchetto della lezione 2
In questa attività si procederà alla creazione di una copia del pacchetto della lezione 2, denominato Lesson 2.dtsx. In alternativa è possibile aggiungere al progetto il pacchetto completo della lezione 2 incluso nell'esercitazione e successivamente copiarlo. Questa nuova copia verrà usata per il resto della lezione 3.  
  
### Per creare il pacchetto della lezione 3  
  
1.  Se [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools non è già aperto fare clic su **Start**, scegliere **Tutti i programmi**, **Microsoft SQL Server 2012** e quindi fare clic su **SQL Server Data Tools**.  
  
2.  Scegliere **Apri** dal menu **File**, fare clic su **Progetto/Soluzione**, selezionare **SSIS Tutorial**, fare clic su **Apri** e quindi fare doppio clic su **SSIS Tutorial.sln**.  
  
3.  In Esplora soluzioni fare clic con il pulsante destro del mouse su **Lesson 2.dtsx** e fare clic su **Copia**.  
  
4.  In Esplora soluzioni fare clic con il pulsante destro del mouse su **Pacchetti SSIS** e fare clic su **Incolla**.  
  
    Per impostazione predefinita, il pacchetto copiato viene denominato Lesson 3.dtsx.  
  
5.  In Esplora soluzioni fare doppio clic su **Lesson 3.dtsx** per aprire il pacchetto.  
  
6.  Fare clic con il pulsante destro del mouse in un punto qualsiasi dello sfondo della scheda **Flusso di controllo** e scegliere **Proprietà**.  
  
7.  Nella finestra Proprietà aggiornare la proprietà **Name** impostandola su **Lesson 3**.  
  
8.  Fare clic sulla casella relativa alla proprietà **ID** e quindi fare clic su **<Generate New ID>** nell'elenco.  
  
### Per aggiungere il pacchetto della lezione 2 completato  
  
1.  Aprire [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] e aprire il progetto SSIS Tutorial.  
  
2.  In Esplora soluzioni fare clic con il pulsante destro del mouse su **Pacchetti SSIS** e quindi fare clic su **Aggiungi pacchetto esistente**.  
  
3.  Nella finestra di dialogo **Aggiungi copia del pacchetto esistente**, in **Posizione pacchetto** selezionare **File system**.  
  
4.  Fare clic sul pulsante Sfoglia **(…)**, passare a **Lesson 2.dtsx** nel computer e fare clic su **Apri**.  
  
    Per scaricare tutti i pacchetti di lezioni di questa esercitazione, effettuare le operazioni seguenti.  
  
    1.  Passare alla pagina degli [esempi di prodotti Integration Services](http://go.microsoft.com/fwlink/?LinkId=275027).  
  
    2.  Fare clic sulla scheda **DOWNLOADS** .  
  
    3.  Fare clic sul file SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip.  
  
5.  Copiare e incollare il pacchetto della Lezione 3, come illustrato nei passaggi 3-8 della procedura precedente.  
  
## Attività successiva della lezione  
[Passaggio 2: Aggiunta e configurazione di funzionalità di registrazione](../integration-services/step-2-adding-and-configuring-logging.md)  
  
