---
title: DLL di installazione del driver | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing ODBC components [ODBC], driver setup DLL
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: 49bab021-81fa-402e-b7a4-a5214f1fadc4
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d75a8985feff2ddfe26d3e19e8bafd91f228d30e
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="driver-setup-dll"></a>DLL di installazione del driver
> [!NOTE]  
>  A partire da Windows XP e Windows Server 2003, ODBC è incluso nel sistema operativo Windows. Solo in modo esplicito, è necessario installare ODBC nelle versioni precedenti di Windows.  
  
 Il programma di installazione di driver DLL contiene il **ConfigDriver** e **ConfigDSN** funzioni. **ConfigDriver** esegue attività di installazione specifici del driver, quali l'immissione di informazioni specifiche del driver nel Registro di sistema. **ConfigDSN** gestisce le informazioni specifiche del driver su origini dati nel Registro di sistema. Per una descrizione completa di queste funzioni, vedere [riferimento API per l'installazione DLL](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 **ConfigDSN** chiama le funzioni seguenti nel programma di installazione DLL di mantenere le informazioni sull'origine dati nel Registro di sistema:  
  
-   **SQLWriteDSNToIni**. Aggiungere un'origine dati.  
  
-   **SQLRemoveDSNFromIni**. Eliminare un'origine dati.  
  
-   **SQLWritePrivateProfileString**. Scrivere un valore specifico del driver nella sottochiave specifica origine dati.  
  
-   **SQLGetPrivateProfileString**. Leggere un valore specifico del driver da una sottochiave specifica di origine dati.  
  
-   **SQLGetTranslator**. Richiedere all'utente un nome di funzione di conversione e l'opzione. Questa funzione chiama **ConfigTranslator del** nel convertitore DLL di installazione.  
  
 Il programma di installazione di driver DLL è scritta dallo sviluppatore del driver. Può essere parte del driver della DLL o una DLL separata.

