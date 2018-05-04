---
title: Diagnostica di gestione delle regole | Documenti Microsoft
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
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], diagnostic handling rules
- SQLGetDiagRec function [ODBC], diagnostic handling rules
- diagnostic information [ODBC], SqlGetDiagRec
ms.assetid: 74387c3a-d6b3-4c35-b209-b9612602b20a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9bea90a96cdfc7e879af64deeb287545d5637382
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="diagnostic-handling-rules"></a>Regole di gestione di diagnostica
Le regole seguenti determinano la gestione di diagnostica in **SQLGetDiagRec** e **SQLGetDiagField**.  
  
 Per tutti i componenti ODBC:  
  
-   È necessario non sostituire, modificare o mascherare gli errori o avvisi ricevuti da un altro componente ODBC.  
  
-   Può aggiungere un record di stato aggiuntivi quando ricevono un messaggio di diagnostica da un altro componente ODBC. Il record aggiunto è necessario aggiungere il valore reale informazioni al messaggio originale.  
  
 Per ODBC componente interfacce che direttamente un'origine dati:  
  
-   Necessario anteporre il relativo identificatore fornitore, il relativo identificatore del componente e identificatore dell'origine dati per il messaggio di diagnostica che riceve dall'origine dati.  
  
-   È necessario mantenere il codice di errore nativo dell'origine dati.  
  
-   È necessario mantenere messaggio di diagnostica dell'origine dati.  
  
 Per qualsiasi componente ODBC che genera un errore o avviso indipendentemente dal fatto che l'origine dati:  
  
-   Specificare il valore SQLSTATE corretto per l'errore o avviso.  
  
-   È necessario generare il testo del messaggio di diagnostica.  
  
-   È necessario anteporre il relativo identificatore fornitore e il relativo identificatore del componente per il messaggio di diagnostica.  
  
-   Deve restituire un codice di errore nativo, se disponibile e significativo.  
  
 Per il componente ODBC che si interfaccia con gestione Driver:  
  
-   È necessario inizializzare gli argomenti di output **SQLGetDiagRec** e **SQLGetDiagField**.  
  
-   È necessario formattare e restituire le informazioni di diagnostica come argomenti di output **SQLGetDiagRec** e **SQLGetDiagField** quando viene chiamata tale funzione.  
  
 Per un componente ODBC diverso da Gestione Driver:  
  
-   Impostare il valore SQLSTATE in base all'errore nativo. Per i driver basati su file e driver basati su DBMS che non utilizzano un gateway, il driver deve impostare il valore SQLSTATE. Per i driver basati su DBMS che usano un gateway, il driver o un gateway che supporti ODBC può impostare il valore SQLSTATE.
