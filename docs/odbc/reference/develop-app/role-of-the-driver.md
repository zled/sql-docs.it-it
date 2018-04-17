---
title: Ruolo del Driver | Documenti Microsoft
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
- driver error checking [ODBC]
- diagnostic information [ODBC], driver error checking
ms.assetid: cac64c24-a27d-4884-96c0-ea7988351711
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d05f69bd03e904745f4b4d3d81179472a7ff1375
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="role-of-the-driver"></a>Ruolo del Driver
Il driver verifica la presenza di tutti gli errori e avvisi da Gestione Driver non è selezionati e ordina i record di stato che viene generata. (Un database ODBC 2. *x* driver non sono ordinati i record di stato.) Errori e avvisi sono inclusi il troncamento dei dati, la conversione dei dati, sintassi e alcuni transizioni di stato. Il driver può verificare anche errori e avvisi parzialmente controllati da Gestione Driver. Ad esempio, anche se la gestione Driver controlla se il valore di *operazione* in **SQLSetPos** è valido, il driver deve controllare se è supportato.  
  
 Il driver esegue il mapping *errori nativi* , vale a dire, gli errori restituiti dall'origine dati, a SQLSTATE. Ad esempio, il driver potrebbe eseguire il mapping di un numero di errori nativi diversi per la sintassi non valida SQL a SQLSTATE 42000 (sintassi o violazione di accesso). Il driver restituisce il numero di errore nativo nel campo SQL_DIAG_NATIVE del record di stato. Documentazione del driver deve mostrare come errori e avvisi vengono eseguito il mapping dell'origine dati per gli argomenti in **SQLGetDiagRec** e **SQLGetDiagField**.
