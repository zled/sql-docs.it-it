---
title: Descrittori | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC]
- descriptors [ODBC], about descriptors
- descriptor handles [ODBC]
- handles [ODBC], descriptor
ms.assetid: ef2cbb93-cd00-40f8-b1d2-5f5723a991aa
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 78f53c07a036719b669e3c14192eda5da3ead55e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="descriptors"></a>Descrittori
Un handle di descrittore fa riferimento a una struttura di dati che contiene informazioni su colonne o parametri dinamici.  
  
 Le funzioni ODBC che operano sui dati di parametro e colonna in modo implicito impostare e recupero i campi di descrizione. Ad esempio, quando **SQLBindCol** viene chiamato per associare i dati della colonna, imposta i campi di descrizione che descrivono completamente l'associazione. Quando **SQLColAttribute** viene chiamato per descrivere i dati della colonna, vengono restituiti i dati archiviati in campi di descrizione.  
  
 Un'applicazione che chiama le funzioni ODBC necessario non preoccuparsi dei descrittori. Nessuna operazione di database richiede che l'applicazione accesso diretto ai descrittori. Tuttavia, per alcune applicazioni, ottenere l'accesso diretto ai descrittori semplifica molte operazioni. Ad esempio, indirizzare l'accesso ai descrittori offre un modo per riassociare i dati della colonna, che possono essere più efficienti rispetto alla chiamata **SQLBindCol** nuovamente.  
  
> [!NOTE]  
>  Non è definita la rappresentazione fisica del descrittore. Applicazioni di ottengono l'accesso diretto a un descrittore solo modificando i relativi campi chiamando le funzioni ODBC con l'handle di descrittore.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Tipi di descrittori](../../../odbc/reference/develop-app/types-of-descriptors.md)  
  
-   [Campi del descrittore](../../../odbc/reference/develop-app/descriptor-fields.md)  
  
-   [Allocazione e liberazione di descrittori](../../../odbc/reference/develop-app/allocating-and-freeing-descriptors.md)  
  
-   [Recupero e configurazione dei campi del descrittore](../../../odbc/reference/develop-app/getting-and-setting-descriptor-fields.md)
