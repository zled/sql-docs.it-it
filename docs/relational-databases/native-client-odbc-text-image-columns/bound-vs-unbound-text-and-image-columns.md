---
title: Colonne di Annullare l'associazione di colonne Text e Image | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
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
- image columns [ODBC]
ms.assetid: ffd3442e-d880-46e9-b848-2365a09a2406
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8439982e197354dc786a82ea627500975d870f3c
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43091104"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Colonne di tipo text e image associate e non associate
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Quando si utilizzano i cursori server, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client è ottimizzato per non trasmettere i dati per annullare l'associazione **testo**, **ntext**, o **immagine** colonne di tempo **SQLFetch** viene eseguita. Il **testo**, **ntext**, o **immagine** dati non vengono effettivamente recuperati dal server finché i problemi dell'applicazione [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) per il colonna.  
  
 Molte applicazioni possono essere scritti in modo che nessun **testo**, **ntext**, o **immagine** dati vengono visualizzati anche se un utente viene semplicemente effettuato uno scorrimento verticale in un cursore. Quando un utente seleziona una riga per ottenere altri dettagli, l'applicazione può quindi chiamare **SQLGetData** per recuperare le **testo**, **ntext**, oppure **immagine** dati. Sarà in grado di trasmettere il **testo**, **ntext**, o **immagine** dati per tutte le righe, l'utente non seleziona e può pertanto impediscono la trasmissione di dimensioni molto grandi quantità di dati.  
  
## <a name="see-also"></a>Vedere anche  
 [La gestione di colonne Text e Image](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)   
 [Comportamenti del cursore](../../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)  
  
  
