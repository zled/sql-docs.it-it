---
title: 'Lezione 6: Utilizzo di parametri con il modello di distribuzione SSIS | Documenti Microsoft'
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
ms.assetid: 9216f18c-1762-4f2d-8c22-bd0ab7107555
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 547da852d6a52393be8e0adf53b4aa18955a6cad
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="lesson-6-using-parameters-with-the-project-deployment-model-in-ssis"></a>Lezione 6: Usare parametri con il modello di distribuzione del progetto in SSIS
In SQL Server 2012 è disponibile un nuovo modello di distribuzione in cui è possibile distribuire i progetti nel server Integration Services. Il server Integration Services consente di gestire ed eseguire pacchetti e di configurare i valori di runtime per i pacchetti.  
  
In questa lezione verrà modificato il pacchetto creato nella [Lezione 5: Aggiungere configurazioni di pacchetto SSIS per il modello di distribuzione dei pacchetti](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md) per usare il modello di distribuzione dei progetti. Sostituire il valore di configurazione con un parametro per specificare la posizione dei dati di esempio. È inoltre possibile copiare il pacchetto della lezione 5 completato incluso nell'esercitazione.  
  
Mediante la configurazione guidata progetti di Integration Services convertire il progetto nel modello di distribuzione del progetto e utilizzare un parametro anziché un valore di configurazione per impostare la proprietà Directory. In questa lezione vengono illustrati solo alcuni dei passaggi per convertire i pacchetti esistenti SSIS nel nuovo modello di distribuzione del progetto.  
  
Quando il pacchetto viene di nuovo eseguito, il servizio Integration Services usa il parametro per popolare il valore della variabile e la variabile a sua volta aggiorna la proprietà Directory. Di conseguenza, tramite il pacchetto viene eseguita un'iterazione della nuova cartella dei dati specificata dal valore del parametro anziché della cartella impostata nel file di configurazione del pacchetto.  
  
> [!IMPORTANT]  
> Per eseguire questa esercitazione, è necessario il database di esempio **AdventureWorksDW2012** . Per altre informazioni sull'installazione e sulla distribuzione di **AdventureWorksDW2012**, vedere [Considerazioni per l'installazione di esempi e di database di esempio di SQL Server](http://technet.microsoft.com/en-us/library/ms161556%28v=sql.105%29).  
  
## <a name="lesson-tasks"></a>Argomenti della lezione  
In questa lezione sono incluse le attività seguenti:  
  
1.  [Passaggio 1: Copia del pacchetto della lezione 5](../integration-services/lesson-6-1-copying-the-lesson-5-package.md)  
  
2.  [Passaggio 2: Conversione del progetto nel modello di distribuzione del progetto](../integration-services/lesson-6-2-converting-the-project-to-the-project-deployment-model.md)  
  
3.  [Passaggio 3: Test del pacchetto della lezione 6](../integration-services/lesson-6-3-testing-the-lesson-6-package.md)  
  
4.  [Passaggio 4: Distribuzione del pacchetto della lezione 6](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
## <a name="start-the-lesson"></a>Inizio della lezione  
[Passaggio 1: Copia del pacchetto della lezione 5](../integration-services/lesson-6-1-copying-the-lesson-5-package.md)  
  

