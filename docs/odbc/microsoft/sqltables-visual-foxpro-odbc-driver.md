---
title: SQLTables (Driver ODBC di Visual FoxPro) | Documenti Microsoft
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
- SQLTables function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 69e2a038-5def-423f-91aa-8756e069dd2a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fd3e59437eae02a94353a6205e567fde208f4b97
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqltables-visual-foxpro-odbc-driver"></a>SQLTables (Driver ODBC di Visual FoxPro)
> [!NOTE]  
>  In questo argomento contiene informazioni specifiche del Driver ODBC Visual FoxPro. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Supporto: completo  
  
 Conformità di API ODBC: Livello 1  
  
 Restituisce l'elenco dei nomi di tabella specificato dal parametro di **SQLTables** istruzione. Se viene specificato alcun parametro, restituisce i nomi delle tabelle archiviate nell'origine dati corrente. Il driver restituisce le informazioni come set di risultati.  
  
 Chiamate di tipo di enumerazione non riceveranno una voce del set di risultati per visualizzazioni remote o locale con parametri. Tuttavia, una chiamata a **SQLTables** con una tabella univoca identificatore di nome verrà trovata una corrispondenza per una visualizzazione di questo tipo se è presente con lo stesso nome; in questo modo l'API da utilizzare per verificare la presenza di conflitti di nomi prima creazione di una nuova tabella.  
  
> [!NOTE]  
>  Il driver ODBC Visual FoxPro riconosce la differenza tra [tabelle di database](../../odbc/microsoft/visual-foxpro-terminology.md) e [libero tabelle](../../odbc/microsoft/visual-foxpro-terminology.md), anche se entrambi i tipi di tabelle vengono archiviati nella stessa directory del sistema. Se l'origine dati è una directory di tabelle disponibile, il Driver ODBC di Visual FoxPro non catalogo o non restituire i nomi di tutte le tabelle che sono associati a un database.  
  
 Per ulteriori informazioni, vedere [SQLTables](../../odbc/reference/syntax/sqltables-function.md) nel *riferimento per programmatori ODBC*.
