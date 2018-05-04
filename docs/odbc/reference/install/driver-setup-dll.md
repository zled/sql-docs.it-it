---
title: DLL di installazione del driver | Documenti Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC], driver setup DLL
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: 49bab021-81fa-402e-b7a4-a5214f1fadc4
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 58d236da053585b4aced435697100e0f6c87379c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="driver-setup-dll"></a>DLL di installazione del driver
> [!NOTE]  
>  A partire da Windows XP e Windows Server 2003, ODBC è incluso nel sistema operativo Windows. Solo nelle versioni precedenti di Windows è necessario installare ODBC in modo esplicito.  
  
 Il programma di installazione di driver DLL contiene il **ConfigDriver** e **ConfigDSN** funzioni. **ConfigDriver** esegue le attività di installazione specifiche del driver, quali l'immissione di informazioni specifiche del driver nel Registro di sistema. **ConfigDSN** gestisce le informazioni specifiche del driver sulle origini dati nel Registro di sistema. Per una descrizione completa di queste funzioni, vedere [riferimento API per l'installazione DLL](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 **ConfigDSN** chiama le funzioni seguenti nel programma di installazione DLL per gestire le informazioni di origine dati nel Registro di sistema:  
  
-   **SQLWriteDSNToIni**. Aggiungere un'origine dati.  
  
-   **SQLRemoveDSNFromIni**. Eliminare un'origine dati.  
  
-   **SQLWritePrivateProfileString**. Scrivere un valore specifico del driver nella sottochiave specifica origine dati.  
  
-   **SQLGetPrivateProfileString**. Leggere un valore specifico del driver da una sottochiave specifica di origine dati.  
  
-   **SQLGetTranslator**. Richiedere all'utente un nome di funzione di conversione e l'opzione. Questa funzione chiama **ConfigTranslator del** nel convertitore DLL di installazione.  
  
 Il programma di installazione di driver DLL è scritta dallo sviluppatore del driver. Può essere parte del driver della DLL o una DLL separata.
