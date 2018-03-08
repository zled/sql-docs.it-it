---
title: Troncamento dei dati (SSIS) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- truncating data
- data truncation [Integration Services]
- expressions [Integration Services], data truncation
- truncate options [Integration Services]
ms.assetid: 02461e15-49ca-445b-abb3-5c369c283ec2
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ef2edbec96d329db8f16a5046fa8c359052a0115
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="data-truncation-ssis"></a>Troncamento dei dati (SSIS)
  La conversione di valori da un tipo di dati in un altro può causare il troncamento dei valori.  
  
 Il troncamento può verificarsi nei casi seguenti:  
  
-   Durante la traduzione dei dati di tipo stringa da un tipo di dati *DT_WSTR* in un tipo di dati *DT_STR* con la stessa lunghezza se la stringa originale contiene caratteri a due byte.  
  
-   Durante il cast di un valore intero da un tipo di dati *DT_I4* a un tipo di dati *DT_I2* è possibile perdere cifre significative.  
  
-   Durante il cast di un valore intero senza segno a un valore intero con segno le cifre significative potrebbero essere perse.  
  
-   Durante il cast di un numero reale da un tipo di dati *DT_R8* a un tipo di dati *DT_R4* è possibile perdere cifre non significative.  
  
-   Durante il cast di un valore intero da un tipo di dati *DT_I4* a un tipo di dati *DT_R4* è possibile perdere cifre non significative.  
  
 L'analizzatore di espressioni identifica i cast espliciti che possono causare troncamenti e genera un avviso durante l'analisi dell'espressione. L'analizzatore di espressioni genera un avviso ad esempio quando viene eseguito il cast di una stringa di 30 caratteri in una stringa di 20 caratteri.  
  
 Tuttavia, il troncamento non viene verificato in fase di esecuzione. In fase di esecuzione i dati vengono troncati senza generare avvisi. La maggior parte degli adattatori e delle trasformazioni supporta output degli errori che riesce a gestire la disposizione delle righe con errori.  
  
 Per altre informazioni sulla gestione del troncamento dei dati, vedere [Gestione degli errori nei dati](../../integration-services/data-flow/error-handling-in-data.md)  
  
  
