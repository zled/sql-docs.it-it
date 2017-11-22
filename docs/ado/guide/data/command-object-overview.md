---
title: Comando oggetto Panoramica | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: command object [ADO]
ms.assetid: e84a14b1-3c2a-4f7d-a966-9e08a93948df
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8f1f01c7ca7a378faaaabf11099b97b0dfa0c7a2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="command-object-overview"></a>Panoramica dell'oggetto Command
Con un **comando** dell'oggetto, è possibile eseguire le operazioni seguenti:  
  
-   Definire il testo del comando (ad esempio, un'istruzione SQL o una stored procedure) eseguibile tramite la **CommandText** proprietà.  
  
-   Definire le query con parametri o argomenti di stored procedure utilizzando **parametro** oggetti e **parametri** insieme.  
  
-   Eseguire un comando e restituire un **Recordset** oggetto, se appropriato, utilizzando il **Execute** metodo.  
  
-   Specificare il tipo di comando utilizzando il **CommandType** proprietà prima dell'esecuzione per ottimizzare le prestazioni.  
  
-   Specificare le informazioni specifiche del testo del comando utilizzando il **sottolinguaggio** proprietà del **comando** oggetto.  
  
-   Controllare se il provider Salva una versione preparata (compilata o) del comando prima dell'esecuzione utilizzando il **Prepared** proprietà.  
  
-   Impostare il numero di secondi di attesa per un comando da eseguire utilizzando un provider di **CommandTimeout** proprietà.  
  
-   Associare una connessione aperta con un **comando** oggetto impostando il relativo **ActiveConnection** proprietà.  
  
-   Impostare il **nome** proprietà per identificare il **comando** oggetto come un metodo sull'oggetto associato **connessione** oggetto.  
  
-   Passare un **comando** dell'oggetto per il **origine** proprietà di un **Recordset** per ottenere i dati.  
  
-   Passare un **flusso** oggetto che contiene un comando (ad esempio, un comando XML) a un provider che lo supporta.
