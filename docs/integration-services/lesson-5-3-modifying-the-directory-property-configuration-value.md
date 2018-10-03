---
title: 'Passaggio 3: Modifica del valore di configurazione della proprietà Directory | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: ba2a091f-361c-4331-afe2-53b465164c36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a144bbde1537e167c82b63389be83c72f55a6346
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47742409"
---
# <a name="lesson-5-3---modifying-the-directory-property-configuration-value"></a>Lezione 5-3 - Modifica del valore di configurazione della proprietà Directory
In questa attività verrà modificata l'impostazione di configurazione archiviata nel file SSISTutorial.dtsConfig relativa alla proprietà Value della variabile a livello di pacchetto `User::varFolderName`. Tale variabile aggiorna la proprietà Directory del contenitore Ciclo Foreach. Il valore modificato punterà alla cartella **New Sample Data** creata nell'attività precedente. Dopo la modifica dell'impostazione di configurazione e l'esecuzione del pacchetto, la proprietà Directory viene aggiornata dalla variabile, usando il valore popolato dal file di configurazione anziché il valore della directory configurato in origine nel pacchetto.  
  
### <a name="to-modify-the-configuration-setting-of-the-directory-property"></a>Per modificare l'impostazione di configurazione della proprietà Directory  
  
1.  In Blocco note o in un altro editor di testo, individuare ed aprire il file di configurazione SSISTutorial.dtsConfig creato nell'attività precedente utilizzando Configurazione guidata pacchetto.  
  
2.  Modificare il valore dell'elemento **ConfiguredValue** in modo che corrisponda al percorso della cartella **New Sample Data** creata nell'attività precedente. Non racchiudere il percorso tra virgolette. Se la cartella **New Sample Data** si trova al livello radice dell'unità (ad esempio, C:\\), il codice XML aggiornato deve essere simile a quello dell'esempio seguente:  
  
    `<?xml version="1.0"?><DTSConfiguration><DTSConfigurationHeading><DTSConfigurationFileInfo GeneratedBy="DOMAIN\UserName" GeneratedFromPackageName="Lesson 5" GeneratedFromPackageID="{F4475E73-59E3-478F-8EB2-B10AFA61D3FA}" GeneratedDate="6/10/2012 8:16:50 AM"/></DTSConfigurationHeading><Configuration ConfiguredType="Property" Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType="String"><ConfiguredValue></ConfiguredValue></Configuration></DTSConfiguration>`  
  
    Le informazioni di intestazione, ovvero **GeneratedBy**, **GeneratedFromPackageID**e **GeneratedDate** , risulteranno ovviamente diverse nel file dell'utente. L'elemento da esaminare è **Configuration** . La proprietà **Value** della variabile `User::varFolderName`contiene ora C:\New Sample Data.  
  
3.  Salvare le modifiche e chiudere l'editor di testo.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Passaggio 4: Test del pacchetto creato nell'esercitazione della lezione 5](../integration-services/lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
  
  
