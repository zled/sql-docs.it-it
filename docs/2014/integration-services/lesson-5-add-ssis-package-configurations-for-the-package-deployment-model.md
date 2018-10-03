---
title: 'Lezione 5: Aggiunta delle configurazioni di pacchetto per il modello di distribuzione di pacchetto | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 1c10dd54-67cb-4b63-9e4d-aa6ff0452ecb
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4bcd47c7f2f045b3e2da43481daba549c503d9e3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48122771"
---
# <a name="lesson-5-adding-package-configurations-for-the-package-deployment-model"></a>Lezione 5: Aggiunta di configurazioni del pacchetto per il modello di distribuzione del pacchetto
  Le configurazioni di pacchetto consentono di impostare variabili e proprietà di runtime all'esterno dell'ambiente di sviluppo. Le configurazioni consentono inoltre di sviluppare pacchetti flessibili e semplici da implementare e distribuire. [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sono disponibili i tipi di configurazione seguenti:  
  
-   File di configurazione XML  
  
-   Variabile di ambiente  
  
-   Voce del Registro di sistema  
  
-   Variabile pacchetto padre  
  
-   Tabella [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
 In questa lezione verrà modificato il pacchetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] semplice creato nella [Lesson 4: Adding Error Flow Redirection](lesson-4-add-error-flow-redirection-with-ssis.md) per usare il modello di distribuzione del pacchetto e le configurazioni del pacchetto. È inoltre possibile copiare il pacchetto della lezione 4 completato incluso nell'esercitazione. Configurazione guidata pacchetto consente di creare una configurazione XML che aggiorna la proprietà `Directory` del contenitore Ciclo Foreach tramite una variabile a livello di pacchetto associata alla proprietà Directory. Dopo aver creato il file di configurazione è possibile modificare il valore della variabile all'esterno dell'ambiente di sviluppo e puntare la proprietà modificata a una nuova cartella di dati di esempio. Quando si esegue nuovamente il pacchetto, il file di configurazione popola il valore della variabile e la variabile a sua volta Aggiorna la `Directory` proprietà. Di conseguenza, il pacchetto esegue un'iterazione della nuova cartella dei dati anziché della cartella originale specificata a livello di codice nel pacchetto.  
  
> [!IMPORTANT]  
>  Per eseguire questa esercitazione, è necessario il database di esempio **AdventureWorksDW2012** . Per altre informazioni sull'installazione e sulla distribuzione di **AdventureWorksDW2012**, vedere [Esempi di Reporting Services su CodePlex](http://go.microsoft.com/fwlink/?LinkID=526910).  
  
## <a name="lesson-tasks"></a>Argomenti della lezione  
 In questa lezione sono incluse le attività seguenti:  
  
-   [Passaggio 1: Copia del pacchetto della lezione 4](lesson-5-1-copying-the-lesson-4-package.md)  
  
-   [Passaggio 2: Abilitazione e impostazione delle configurazioni dei pacchetti](lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
-   [Passaggio 3: Modifica del valore di configurazione della proprietà Directory](lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
-   [Passaggio 4: Test del pacchetto creato nell'esercitazione della lezione 5](lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Inizio della lezione  
  
-   [Passaggio 1: Copia del pacchetto della lezione 4](lesson-5-1-copying-the-lesson-4-package.md)  
  
  
