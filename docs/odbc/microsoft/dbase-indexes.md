---
title: gli indici di dBASE | Documenti Microsoft
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
- DBase indexes [ODBC]
- DBase driver [ODBC], indexes
ms.assetid: fdfa56f5-e324-4ec2-9267-fdf95ab99373
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9f2725f312691d3cb644f9a096b5f469f1356c55
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="dbase-indexes"></a>Indici di dBASE
Il driver ODBC dBASE apre automaticamente e l'aggiornamento dei file di indice dBASE IV. È necessario utilizzare il **Seleziona indici** finestra di dialogo visualizzata tramite Amministrazione origine dati ODBC per associare i file di dBASE III ndx file dBASE.  
  
 Per la creazione di indici dBASE sono applicate le limitazioni seguenti:  
  
-   Tutti i nomi di colonna devono essere validi.  
  
-   Tutte le colonne devono essere in modo crescente o decrescente.  
  
-   La lunghezza di qualsiasi colonna di testo deve essere inferiore a 100 byte.  
  
-   Se esiste più di una colonna, tutte le colonne devono essere colonne di testo e la somma delle dimensioni di colonna deve essere inferiore a 100 byte.  
  
-   I campi di credito non possono essere indicizzati.  
  
-   Un indice non deve essere specificato per il set corrente di campi (ovvero, gli indici duplicati non consentiti).  
  
-   Il nome dell'indice deve corrispondere la convenzione di denominazione indice dBASE. file dBASE III richiede che ogni indice in un file separato, ognuno dei quali con un'estensione ndx. Nel file dBASE IV, gli indici vengono creati come nomi di tag che vengono archiviati in un singolo file MDX. Il file con estensione MDX è lo stesso nome di base del file di database (ad esempio, emp è il file di indice per il database emp).  
  
-   file dBASE definisce un indice univoco, come in un solo record da un set con gli stessi valori chiavi viene aggiunto all'indice.

