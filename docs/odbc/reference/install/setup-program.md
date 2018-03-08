---
title: Programma di installazione | Documenti Microsoft
ms.custom: 
ms.date: 08/31/2016
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: installing ODBC components [ODBC], setup program
ms.assetid: 9cc5d75d-b293-41e5-927c-10f4af2e7af1
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 615f3151212c362ad0a813ee1af9718f83398270
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="setup-program"></a>Programma di installazione
> **Nota:** a partire da Windows XP e Windows Server 2003, **ODBC è incluso nel sistema operativo Windows**. Solo in modo esplicito, è necessario installare ODBC nelle versioni precedenti di Windows.  
  
 L'utente esegue il programma di installazione per avviare il processo di installazione. Il programma di installazione viene scritto dallo sviluppatore dell'applicazione o driver. Oltre a installare i componenti ODBC, è possibile installare il software. Ad esempio, gli sviluppatori di applicazioni potrebbero utilizzare lo stesso programma di installazione per installare i componenti ODBC e per installare le applicazioni.  
  
 Gli sviluppatori possono scrivere il programma di installazione da zero, usando l'utilità di installazione di Microsoft® Windows® SDK o il software di installazione di altri fornitori. In questo modo gli sviluppatori di controllo completo sulla aspetto del programma di installazione. Il programma di installazione può essere scritti per installare software aggiuntivo, ad esempio un'applicazione ODBC. Per ulteriori informazioni sull'utilità di installazione di Windows SDK, vedere la documentazione di Windows SDK.  
  
 La quantità dell'installazione viene effettivamente eseguita dal programma di installazione dipende da quali funzioni chiamate nel programma di installazione DLL. Il programma di installazione DLL contiene funzioni per installare i singoli componenti ODBC. Il programma di installazione consente di chiamare semplicemente **SQLInstallDriverManager**, **SQLInstallDriverEx**, o **SQLInstallTranslatorEx** del DLL per recuperare il percorso del programma di installazione di Directory in cui il componente sia installato e di aggiungere informazioni sul componente al Registro di sistema. Queste funzioni non copiare effettivamente i file; il programma di installazione avviene mediante le informazioni negli argomenti di queste funzioni.  
  
 Il programma di installazione DLL contiene anche le funzioni per rimuovere i componenti ODBC. Il programma di installazione chiama **SQLRemoveDriverManager**, **SQLRemoveDriver**, o **SQLRemoveTranslator** nel programma di installazione di conteggio DLL per diminuire l'utilizzo di un componente di Registro di sistema e, se il conteggio di utilizzo della nuova del componente scende a 0, rimuovere tutte le informazioni sul componente dal Registro di sistema. Queste funzioni non rimuovono effettivamente i file per il componente. il programma di installazione avviene se il conteggio di utilizzo della nuova scende a 0.
