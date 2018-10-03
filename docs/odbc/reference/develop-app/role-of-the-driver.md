---
title: Ruolo del Driver | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver error checking [ODBC]
- diagnostic information [ODBC], driver error checking
ms.assetid: cac64c24-a27d-4884-96c0-ea7988351711
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2687e1a68789566fd7b660a8241d65ff4714a933
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47633569"
---
# <a name="role-of-the-driver"></a>Ruolo del driver
Il driver controlla tutti gli errori e avvisi non controllati da Gestione Driver e ordina i record di stato che genera. (Un ODBC 2. *x* driver non ordina i record di stato.) Quali errori e avvisi di troncamento dei dati, la conversione dei dati, sintassi e alcuni transizioni di stato. Il driver potrebbe anche controllare errori e avvisi controllo parzialmente selezionati da Gestione Driver. Ad esempio, anche se Gestione Driver controlla se il valore di *operazione* nel **SQLSetPos** è consentito, il driver deve controllare se è supportato.  
  
 Il driver esegue anche il mapping *gli errori nativi* , vale a dire, gli errori restituiti dall'origine dati, ovvero a SQLSTATE. Ad esempio, il driver può eseguire il mapping di un numero di errori nativi differenti per la sintassi non valida SQL a SQLSTATE 42000 (sintassi o violazione di accesso). Il driver restituisce il numero di errori nativi nel campo SQL_DIAG_NATIVE del record di stato. Documentazione del driver deve mostrare come errori e avvisi vengono mappati dall'origine dati e gli argomenti in **SQLGetDiagRec** e **SQLGetDiagField**.
