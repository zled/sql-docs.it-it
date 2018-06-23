---
title: Data-at-Execution e Text, ntext o Image Columns | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- data-at-execution
- ODBC data-at-execution
- image columns [ODBC]
ms.assetid: 67ffb1a6-f38d-4712-ba64-96bdd41ec2b2
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 90777c1f7f1ac50266eaf7fe473c5ca3b1c2f189
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158432"
---
# <a name="data-at-execution-and-text-ntext-or-image-columns"></a>Colonne data-at-execution di tipo text, ntext o image
  ODBC data-at-execution è una caratteristica che consente alle applicazioni di utilizzare quantità estremamente elevate di dati su colonne o parametri associati. Quando si recuperano grandi **testo**, **ntext**, o **immagine** le colonne, un'applicazione potrebbe non essere in grado di allocare un buffer di grandi dimensioni, associare la colonna nel buffer e il recupero semplicemente la riga. Durante l'aggiornamento di dimensioni molto grandi **testo**, **ntext**, o **immagine** colonne, l'applicazione potrebbe non essere in grado di allocare un buffer di grandi dimensioni, associarlo a un marcatore di parametro in un SQL semplicemente istruzione, quindi eseguire l'istruzione. In questi casi, l'applicazione deve utilizzare [SQLGetData](../native-client-odbc-api/sqlgetdata.md) oppure [SQLPutData](../native-client-odbc-api/sqlputdata.md) con le opzioni di data-at-execution.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di colonne di tipo text e image](managing-text-and-image-columns.md)  
  
  