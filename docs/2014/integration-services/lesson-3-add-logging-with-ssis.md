---
title: 'Lezione 3: Aggiunta di registrazione | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c4ad03f67a8a386b3c42697d1060910c277580c3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37164878"
---
# <a name="lesson-3-adding-logging"></a>Lezione 3: Aggiunta delle funzionalità di registrazione
  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] include funzionalità di registrazione che consentono di risolvere i problemi e monitorare l'esecuzione dei pacchetti offrendo una traccia degli eventi generati dalle attività e dai contenitori. Le caratteristiche di registrazione sono flessibili ed è possibile attivarle a livello di pacchetto o a livello di singole attività o contenitori del pacchetto. È possibile selezionare gli eventi che si desidera registrare e creare più log per un singolo pacchetto.  
  
 La registrazione è garantita da un provider di log. Ogni provider di log è in grado di scrivere le informazioni di registrazione in diversi formati e tipi di destinazione. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] rende disponibili i provider di log seguenti:  
  
-   File di testo  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   Registro eventi di Windows  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   File XML  
  
 In questa lezione si creerà una copia del pacchetto creato nella [lezione 2: aggiungere cicli](lesson-2-adding-looping-with-ssis.md). Usando questo nuovo pacchetto, verranno aggiunte e configurate funzionalità di registrazione per monitorare eventi specifici durante l'esecuzione del pacchetto. Se non è stata completata nessuna delle lezioni precedenti, è possibile copiare il pacchetto della lezione 2 completato incluso nell'esercitazione.  
  
> [!IMPORTANT]  
>  Per eseguire questa esercitazione, è necessario il database di esempio **AdventureWorksDW2012** . Per altre informazioni su come installare e distribuire **AdventureWorksDW2012**, [Reporting Services Product Samples in CodePlex](http://go.microsoft.com/fwlink/p/?LinkID=52691).  
  
## <a name="lesson-tasks"></a>Argomenti della lezione  
 In questa lezione sono incluse le attività seguenti:  
  
-   [Passaggio 1: Copia del pacchetto della lezione 2](lesson-3-1-copying-the-lesson-2-package.md)  
  
-   [Passaggio 2: Aggiunta e configurazione di funzionalità di registrazione](lesson-3-2-adding-and-configuring-logging.md)  
  
-   [Passaggio 3: Test del pacchetto creato nella lezione 3 dell'esercitazione](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Inizio della lezione  
 [Passaggio 1: Copia del pacchetto della lezione 2](lesson-3-1-copying-the-lesson-2-package.md)  
  
  
