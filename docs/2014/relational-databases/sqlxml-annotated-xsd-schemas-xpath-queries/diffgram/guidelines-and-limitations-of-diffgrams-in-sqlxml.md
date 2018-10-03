---
title: Linee guida e le limitazioni di DiffGram SQLXML | Documenti di Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: cf8689c4-2a63-4d05-b202-21b5ff187d7f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2adbd116b818086e13adacd5e88d3923b53f81ee
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48074974"
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>Linee guida e limitazioni per i Diffgram in SQLXML
  Quando si utilizzano Diffgram con SQLXML 4.0, tenere presenti le considerazioni seguenti:  
  
-   I tipi di oggetto binario di grandi dimensioni (BLOB), ad esempio i tipi `text/ntext` e le immagini, non devono essere utilizzati nel blocco `<diffgr:before>` quando si utilizzano Diffgram, perché in questo caso verranno inclusi per l'utilizzo nel controllo della concorrenza. Ciò può provocare problemi con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a causa delle limitazioni applicate al confronto per i tipi BLOB. La parola chiave LIKE, ad esempio, viene utilizzata nella clausola WHERE per il confronto tra colonne del tipo di dati `text`. I confronti, tuttavia, hanno esito negativo in presenza di tipi BLOB in cui le dimensioni dei dati sono maggiori di 8K.  
  
-   La presenza di caratteri speciali nei dati `ntext` può provocare problemi con SQLXML 4.0 a causa delle limitazioni applicate al confronto per i tipi BLOB. L'utilizzo, ad esempio, di "[Serializable]" nel blocco `<diffgr:before>` di un Diffgram se utilizzato nel confronto della concorrenza di una colonna di tipo `ntext` avrà esito negativo con la descrizione di errore SQLOLEDB seguente:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
