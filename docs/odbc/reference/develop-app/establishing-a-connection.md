---
title: Stabilire una connessione | Documenti Microsoft
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
- data sources [ODBC], connection functions
- SQLBrowseConnect function [ODBC], establising a connection
- functions [ODBC], data source or driver connections
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- SQLConnect function [ODBC], establising a connection
- SQLDriverConnect function [ODBC], making a connection
- ODBC drivers [ODBC], connection functions
ms.assetid: 8e3c717e-35e3-47ef-b5d3-3a96eeb7b869
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 43e7ab9f883df271f47b0ad55a931ce1a2d2c220
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="establishing-a-connection"></a>Stabilire una connessione
Dopo l'allocazione di handle di ambiente e di connessione e impostare gli attributi di connessione, l'applicazione è pronta per la connessione all'origine dati o driver. Sono disponibili tre diverse funzioni che l'applicazione può utilizzare per eseguire questa operazione: **SQLConnect** (il livello di conformità di interfaccia di base), **SQLDriverConnect** (Core), e **SQLBrowseConnect**(Livello 1). Ognuno dei tre è progettato per essere utilizzato in uno scenario diverso. Prima della connessione, l'applicazione può determinare quali di queste funzioni è supportata con il **ConnectFunctions** parola chiave restituita dal **SQLDrivers**.  
  
> [!NOTE]  
>  Alcuni driver limitare il numero di connessioni attive che supportano. Un'applicazione chiama **SQLGetInfo** con l'opzione SQL_MAX_DRIVER_CONNECTIONS per determinare il numero di connessioni attivo supporta un driver specifico.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Origine dati predefinita](../../../odbc/reference/develop-app/default-data-source.md)  
  
-   [Connessione con SQLConnect](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md)  
  
-   [Stringhe di connessione](../../../odbc/reference/develop-app/connection-strings.md)  
  
-   [Connessione con SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md)  
  
-   [Connessione con SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md)

