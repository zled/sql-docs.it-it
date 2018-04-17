---
title: Programma di amministrazione | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- administration program [ODBC]
- ODBC administrator [ODBC]
ms.assetid: a6c8248a-7a01-42e7-aaed-99dc94d50028
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2f4cd3ae3fd57dad914c8404e8fe9096e072771f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="administration-program"></a>Programma di amministrazione
> [!NOTE]  
>  A partire da Windows XP e Windows Server 2003, ODBC è incluso nel sistema operativo Windows. Solo in modo esplicito, è necessario installare ODBC nelle versioni precedenti di Windows.  
  
 Un programma di amministrazione, l'amministratore ODBC, è incluso in Windows SDK o MDAC SDK. Questo programma e può essere ridistribuito dagli utenti del SDK. Inoltre, gli sviluppatori possono scrivere i propri programmi di amministrazione. In genere, gli sviluppatori di scrivono i propri programmi di amministrazione solo se desiderano mantenere il controllo completo sulla configurazione dell'origine dati o se si configurano le origini dati direttamente da un'applicazione che funge da un programma di amministrazione. Ad esempio, un foglio di calcolo potrebbe consentire agli utenti di aggiungere e quindi utilizzare origini dati in fase di esecuzione.  
  
 Il programma di amministrazione carica innanzitutto il programma di installazione DLL. Chiama quindi le funzioni nel programma di installazione DLL per eseguire le attività seguenti:  
  
-   **Aggiungere, modificare o eliminare le origini dati in modo interattivo.** Il programma di amministrazione è possibile chiamare **SQLManageDataSources**, **SQLCreateDataSource**, o **SQLConfigDataSource**.  
  
     **SQLManageDataSources** Visualizza una finestra di dialogo con cui l'utente può aggiungere, modificare, o eliminare le origini dati e specificare le opzioni di traccia; questa funzione viene chiamata quando viene richiamato il programma di installazione DLL direttamente dal Pannello di controllo. **SQLCreateDataSource** Visualizza una finestra di dialogo in cui l'utente è possibile aggiungere solo origini dati. **SQLConfigDataSource** passa la chiamata direttamente per la DLL di installazione del driver.  
  
     In tutti i casi, il programma di installazione DLL chiama **ConfigDSN** nella DLL per aggiungere effettivamente l'installazione del driver, modificare o eliminare l'origine dati. Il programma di installazione di driver DLL potrebbe richiedere all'utente informazioni aggiuntive.  
  
-   **Aggiungere, modificare o eliminare le origini dati invisibile all'utente.** Il programma di amministrazione chiama **SQLConfigDataSource** nel programma di installazione DLL e passa è una null handle di finestra, il nome di un'origine dati per aggiungere, modificare o eliminare e un elenco di valori del Registro di sistema. Le chiamate DLL del programma di installazione **ConfigDSN** nella DLL per aggiungere effettivamente l'installazione del driver, modificare o eliminare l'origine dati.  
  
-   **Aggiungere, modificare o eliminare un'origine dati predefinita.** L'origine dati predefinita è lo stesso come qualsiasi altra origine dati, ad eccezione del fatto che il nome predefinito. Viene aggiunto, modificato o eliminato in modo identico a qualsiasi altra origine dati.
