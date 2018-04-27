---
title: 'Lezione 5: Aggiungere configurazioni del pacchetto SSIS per il modello di distribuzione del pacchetto | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: tutorial
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 1c10dd54-67cb-4b63-9e4d-aa6ff0452ecb
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 9c855dded254a65e62812e6e9ffdec4e568d6cb9
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="lesson-5-add-ssis-package-configurations-for-the-package-deployment-model"></a>Lezione 5: Aggiungere configurazioni del pacchetto SSIS per il modello di distribuzione del pacchetto
Le configurazioni di pacchetto consentono di impostare variabili e proprietà di runtime all'esterno dell'ambiente di sviluppo. Le configurazioni consentono inoltre di sviluppare pacchetti flessibili e semplici da implementare e distribuire. [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sono disponibili i tipi di configurazione seguenti:  
  
-   File di configurazione XML  
  
-   Variabile di ambiente  
  
-   Voce del Registro di sistema  
  
-   Variabile pacchetto padre  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] table  
  
In questa lezione verrà modificato il semplice pacchetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] creato nella [Lezione 4: Aggiungere il reindirizzamento del flusso errato con SSIS](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md) per usare il modello di distribuzione del pacchetto e le configurazioni del pacchetto. È inoltre possibile copiare il pacchetto della lezione 4 completato incluso nell'esercitazione. La Configurazione guidata pacchetto consente di creare una configurazione XML che aggiorna la proprietà **Directory** del contenitore Foreach Loop tramite una variabile a livello di pacchetto associata alla proprietà Directory. Dopo aver creato il file di configurazione è possibile modificare il valore della variabile all'esterno dell'ambiente di sviluppo e puntare la proprietà modificata a una nuova cartella di dati di esempio. Quando il pacchetto viene eseguito nuovamente, il file di configurazione popola il valore della variabile che a sua volta aggiorna la proprietà **Directory**. Di conseguenza, il pacchetto esegue un'iterazione della nuova cartella dei dati anziché della cartella originale specificata a livello di codice nel pacchetto.  
  
> [!IMPORTANT]  
> Per eseguire questa esercitazione, è necessario il database di esempio **AdventureWorksDW2012** . Per altre informazioni sull'installazione e sulla distribuzione di **AdventureWorksDW2012**, vedere la pagina relativa agli [esempi del prodotto Reporting Services su CodePlex](http://go.microsoft.com/fwlink/p/?LinkID=526910).  
  
## <a name="lesson-tasks"></a>Argomenti della lezione  
In questa lezione sono incluse le attività seguenti:  
  
-   [Passaggio 1: Copia del pacchetto della lezione 4](../integration-services/lesson-5-1-copying-the-lesson-4-package.md)  
  
-   [Passaggio 2: Abilitazione e impostazione delle configurazioni dei pacchetti](../integration-services/lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
-   [Passaggio 3: Modifica del valore di configurazione della proprietà Directory](../integration-services/lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
-   [Passaggio 4: Test del pacchetto creato nell'esercitazione della lezione 5](../integration-services/lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Inizio della lezione  
  
-   [Passaggio 1: Copia del pacchetto della lezione 4](../integration-services/lesson-5-1-copying-the-lesson-4-package.md)  
  
  
  
