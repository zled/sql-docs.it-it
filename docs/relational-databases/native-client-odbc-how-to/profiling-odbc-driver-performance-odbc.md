---
title: Profilatura di ODBC Driver procedure relative alle prestazioni (ODBC) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0e6d7aed-28d2-419e-be6a-f60d3729bfd0
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 701f1ee9bc5f4c6544a3cbe56d87210c63e1f863
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35696672"
---
# <a name="profiling-odbc-driver-performance-odbc"></a>Profilatura delle prestazioni del Driver ODBC (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Sono disponibili due opzioni specifiche che possono essere utilizzate dal driver ODBC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per l'analisi delle prestazioni del driver.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC può registrare statistiche sulle prestazioni nei file. Il file di log delle statistiche è un file delimitato da tabulazioni che può essere analizzato in qualsiasi foglio di calcolo in grado di supportare i file delimitati da tabulazioni, come Microsoft Excel.  
  
 Il driver può registrare anche query con esecuzione prolungata (query che non ottengono una risposta dal server entro un periodo di tempo specificato). Tali query possono essere analizzate in un secondo momento da programmatori e amministratori del database.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [I dati sulle prestazioni del Driver del profilo &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/profiling-odbc-driver-performance-data.md)  
  
-   [Registrazione di query con esecuzione prolungata &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/profiling-odbc-driver-performance-data-log-long-running-queries.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure relative a ODBC](../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)  
  
  
