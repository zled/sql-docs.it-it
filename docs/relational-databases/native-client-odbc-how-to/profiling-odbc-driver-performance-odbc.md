---
title: Profilatura di ODBC Driver procedure relative alle prestazioni (ODBC) | Documenti di Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 0e6d7aed-28d2-419e-be6a-f60d3729bfd0
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0687d63e9662b94d47341f8f371f1328ec5da0e5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47820179"
---
# <a name="profiling-odbc-driver-performance-odbc"></a>Profilatura delle prestazioni del driver ODBC (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Sono disponibili due opzioni specifiche che possono essere utilizzate dal driver ODBC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per l'analisi delle prestazioni del driver.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC può registrare statistiche sulle prestazioni nei file. Il file di log delle statistiche è un file delimitato da tabulazioni che può essere analizzato in qualsiasi foglio di calcolo in grado di supportare i file delimitati da tabulazioni, come Microsoft Excel.  
  
 Il driver può registrare anche query con esecuzione prolungata (query che non ottengono una risposta dal server entro un periodo di tempo specificato). Tali query possono essere analizzate in un secondo momento da programmatori e amministratori del database.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Profiling dei dati sulle prestazioni del Driver &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/profiling-odbc-driver-performance-data.md)  
  
-   [Registrare query con esecuzione prolungata &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/profiling-odbc-driver-performance-data-log-long-running-queries.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure relative a ODBC](../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)  
  
  
