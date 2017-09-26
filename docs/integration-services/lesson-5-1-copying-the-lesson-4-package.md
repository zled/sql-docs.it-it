---
title: 'Passaggio 1: Copia del pacchetto della lezione 4 | Documenti Microsoft'
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 8aa7d690-4649-4c0a-ac6f-9504637ee426
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 54328f5769560ca6710ed7df6ebe8de9509b8316
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="lesson-5-1---copying-the-lesson-4-package"></a>Lezione 5-1-copia del pacchetto della lezione 4
In questa attività si procederà alla creazione di una copia del pacchetto creato nella lezione 4, denominato Lesson 4.dtsx. In alternativa, è possibile aggiungere al progetto il pacchetto completo della lezione 4 incluso nell'esercitazione e, successivamente, copiarlo. Questa nuova copia verrà usata per tutto il seguito della lezione 5.  
  
### <a name="to-copy-the-lesson-4-package"></a>Per copiare il pacchetto della lezione 4  
  
1.  Se [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools non è già aperto, fare clic su **Start**, scegliere **Tutti i programmi**, **Microsoft SQL Server 2012**, quindi selezionare **SQL Server Data Tools**.  
  
2.  Scegliere **Apri** dal menu **File**, fare clic su **Progetto/Soluzione**, selezionare **SSIS Tutorial** e fare clic su **Apri**, quindi fare doppio clic su **SSIS Tutorial.sln**.  
  
3.  In Esplora soluzioni fare clic con il pulsante destro del mouse su **Lesson 4.dtsx**e quindi scegliere **Copia**.  
  
4.  In Esplora soluzioni fare clic con il pulsante destro del mouse su **Pacchetti SSIS**e quindi scegliere **Incolla**.  
  
    Per impostazione predefinita, il pacchetto copiato viene denominato Lesson 5.dtsx.  
  
5.  In Esplora soluzioni fare doppio clic su **Lesson 5.dtsx** per aprire il pacchetto.  
  
6.  Fare clic con il pulsante destro del mouse in un punto qualsiasi dello sfondo della scheda **Flusso di controllo** e scegliere **Proprietà**.  
  
7.  Nella finestra Proprietà aggiornare la proprietà **Name** impostandola su **Lesson 5**.  
  
8.  Fare clic sulla casella relativa alla proprietà **ID** , fare clic sulla freccia a discesa, quindi scegliere **<Generate New ID>**.  
  
### <a name="to-add-the-completed-lesson-4-package"></a>Per aggiungere il pacchetto della lezione 4 completato  
  
1.  Aprire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools e il progetto SSIS Tutorial.  
  
2.  In Esplora soluzioni fare clic con il pulsante destro del mouse su **Pacchetti SSIS**e scegliere **Aggiungi pacchetto esistente**.  
  
3.  Nella finestra di dialogo **Aggiungi copia del pacchetto esistente** , in **Posizione pacchetto**, selezionare **File system**.  
  
4.  Fare clic sul pulsante sfoglia **(…)** , passare a **Lesson 4.dtsx** nel computer, quindi fare clic su **Apri**.  
  
    Per scaricare tutti i pacchetti di lezioni di questa esercitazione, effettuare le operazioni seguenti.  
  
    1.  Passare alla pagina relativa agli [esempi di prodotti di Integration Services](http://go.microsoft.com/fwlink/?LinkId=275027)  
  
    2.  Fare clic sulla scheda **DOWNLOADS** .  
  
    3.  Fare clic sul file SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip.  
  
5.  Copiare e incollare il pacchetto della lezione 4, come illustrato nei passaggi 3-8 della procedura precedente.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Passaggio 2: Abilitazione e impostazione delle configurazioni dei pacchetti](../integration-services/lesson-5-2-enabling-and-configuring-package-configurations.md)  
  

