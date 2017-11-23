---
title: Tipi di descrittori di | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: descriptors [ODBC], types
ms.assetid: ec20e446-e540-41ad-8559-d9c0a5b8358f
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7092b59719850ed514ce792c17eea32ae290b932
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="types-of-descriptors"></a>Tipi di descrittori di
Un descrittore utilizzato per descrivere uno dei valori seguenti:  
  
-   Un insieme di zero o più parametri. Un descrittore del parametro può essere utilizzato per descrivere:  
  
    -   Il *buffer del parametro dell'applicazione,* che contiene degli argomenti dinamici inpui come impostato dall'applicazione o degli argomenti dinamici output dopo l'esecuzione di un **CHIAMARE** istruzione SQL.  
  
    -   Il *buffer del parametro implementazione*. Per argomenti di input dinamici, contiene gli stessi argomenti il buffer del parametro dell'applicazione, dopo l'applicazione può specificare qualsiasi conversione di dati. Per argomenti dinamici di output, contiene gli argomenti restituiti, prima di qualsiasi conversione di dati che può specificare l'applicazione.  
  
     Per argomenti di input dinamici, l'applicazione deve essere utilizzata per una descrizione del parametro dell'applicazione prima di eseguire qualsiasi istruzione SQL che contiene gli indicatori di parametro dinamico. Per argomenti dinamici di input e di output, l'applicazione può specificare i tipi di dati diversi da quelli nel descrittore di parametri di implementazione per ottenere la conversione dei dati.  
  
-   Una singola riga di dati del database. Un descrittore della riga può essere utilizzato per descrivere:  
  
    -   Il *buffer di riga di implementazione,* che contiene la riga dal database. (Questi buffer concettualmente contengono dati come scrivere o leggere dal database. Tuttavia, i moduli archiviati dati del database non sono specificato. Un database potrebbe effettuare ulteriore conversione dei dati dal formato nel buffer di implementazione.)  
  
    -   Il *buffer di riga dell'applicazione,* che contiene la riga di dati come presentato all'applicazione, dopo qualsiasi conversione di dati che può specificare l'applicazione.  
  
     L'applicazione usa il descrittore della riga di applicazione in tutti i casi in cui i dati della colonna dal database devono essere visualizzato nelle variabili di applicazione. Per ottenere la conversione dei dati di dati della colonna, l'applicazione può specificare i tipi di dati diversi da quelli nel descrittore della riga di implementazione.  
  
 Nella tabella seguente sono riepilogati i tipi di descrittore.  
  
|Tipo di buffer|Righe|Parametri dinamici|  
|-----------------|----------|------------------------|  
|**Buffer dell'applicazione**|Descrittore della riga di applicazione (ARD)|Descrittore del parametro dell'applicazione (APD)|  
|**Buffer di implementazione**|Descrittore della riga di implementazione (IRD)|Descrizione del parametro di implementazione (IPD)|  
  
 Per il parametro o i buffer di riga, se l'applicazione specifica di tipi di dati diversi in record corrispondenti dei descrittori di implementazione e dell'applicazione, il driver esegue la conversione dei dati quando vengono utilizzati i descrittori. Ad esempio, può convertire valori numerici e data/ora in formato stringa di caratteri. (Per le conversioni valide, vedere [appendice d: i tipi di dati](../../../odbc/reference/appendixes/appendix-d-data-types.md).)  
  
 Un descrittore di eseguire diversi ruoli. Istruzioni diverse possono condividere un descrittore di allocate in modo esplicito dall'applicazione. Un descrittore della riga in un'unica istruzione può essere utilizzato come un descrittore del parametro in un'altra istruzione.  
  
 È sempre noto se un determinato descrittore è un descrittore di applicazione o un descrittore di implementazione, anche se il descrittore non è ancora stato utilizzato in un'operazione di database. Per i descrittori allocata in modo implicito l'implementazione, l'implementazione registra la riga predefinita relativo handle di istruzione. Qualsiasi descrittore che consente di allocare l'applicazione chiamando **SQLAllocHandle** è un descrittore di applicazione.
