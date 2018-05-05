---
title: Dati restituiti dalle funzioni di catalogo | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], result sets
- functions [ODBC], catalog functions
ms.assetid: 399e1a64-8766-4c44-81ff-445399b7a1de
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d27d395913ce64d263798205521a3d1136460105
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="data-returned-by-catalog-functions"></a>Dati restituiti dalle funzioni di catalogo
Ogni funzione di catalogo restituisce dati come set di risultati. Questo set di risultati non è diverso da qualsiasi altro set di risultati. In genere viene generato da un oggetto predefinito, con parametri **selezionare** istruzione che viene archiviato in una routine nell'origine dati o a livello di codice nel driver. Per informazioni su come recuperare dati da un set di risultati, vedere [è stato creato di impostare un risultato?](../../../odbc/reference/develop-app/was-a-result-set-created.md).  
  
 Set di risultati per ogni funzione di catalogo sono descritta nella voce di riferimento per tale funzione. Oltre alle colonne elencate, il set di risultati può contenere colonne specifiche del driver dopo l'ultima colonna predefinito. Queste colonne (se presenti) sono descritte nella documentazione del driver.  
  
 Le applicazioni devono essere associati a colonne specifiche del driver relativo alla fine del set di risultati. Vale a dire, si deve calcolare il numero di una colonna specifici del driver come il numero dell'ultima colonna, ovvero recuperati con **SQLNumResultCols** , meno il numero di colonne che si verificano dopo la colonna richiesta. Questo consente di salvare la necessità di modificare l'applicazione quando vengono aggiunte nuove colonne al risultato impostare nelle future versioni ODBC o il driver. Per questo schema utilizzare il driver necessario aggiungere nuove colonne specifiche del driver prima le colonne specifiche del driver precedente in modo da non modificano i numeri di colonna relativa alla fine del set di risultati.  
  
 Gli identificatori che vengono restituiti nel set di risultati non vengono inclusi, anche se contengono caratteri speciali. Si supponga ad esempio l'identificatore del tipo di virgolette (che è specifico del driver e viene restituita tramite **SQLGetInfo**) è un segno di virgolette doppie (") e la contabilità fornitori tabella contiene una colonna denominata Customer Name. Nella riga restituita da **SQLColumns** per questa colonna, il valore della colonna TABLE_NAME è fornitori, non "contabilità fornitori", e il valore della colonna COLUMN_NAME è cliente nome, non "Customer". Per recuperare i nomi dei clienti nella tabella contabilità fornitori, l'applicazione verrà offerta questi nomi:  
  
```  
SELECT "Customer Name" FROM "Accounts Payable"  
```  
  
 Per ulteriori informazioni, vedere [identificatori tra virgolette](../../../odbc/reference/develop-app/quoted-identifiers.md).  
  
 Le funzioni di catalogo sono basate su un modello di autorizzazione simile a SQL in cui viene stabilita una connessione in base a un nome utente e una password, e vengono restituiti solo i dati per cui l'utente dispone di un privilegio. Password di protezione di singoli file, che non rientrano in questo modello, è definito dal driver.  
  
 Set di risultati restituiti dalle funzioni di catalogo sono quasi mai aggiornabili e le applicazioni non dovrebbero essere in grado di modificare la struttura del database modificando i dati in questi set di risultati.
