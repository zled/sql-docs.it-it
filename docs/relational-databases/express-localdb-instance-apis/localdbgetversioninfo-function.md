---
title: Funzione LocalDBGetVersionInfo | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: localdb
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- LocalDBGetVersionInfo
apilocation:
- sqluserinstance.dll
apitype: DLLExport
ms.assetid: d4aaea30-1d0d-4436-bcdc-5c101d27b1c1
caps.latest.revision: 
author: JennieHubbard
ms.author: jhubbard
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e3fb6ab670f626cb629a1ba301cab4b51c9a2c56
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2018
---
# <a name="localdbgetversioninfo-function"></a>Funzione LocalDBGetVersionInfo
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Vengono restituite le informazioni per la versione del database locale di SQL Server Express specificata, se esistente, e il numero completo della versione del database locale, ovvero con i numeri di compilazione e della versione inclusi.  
  
 Vengono restituite le informazioni sotto forma di un **struct** denominato **LocalDBVersionInfo**, che presenta la definizione seguente.  
  
```  
typedef struct _LocalDBVersionInfo  
{  
      // Contains the size of the LocalDBVersionInfo struct  
      DWORD  cbLocalDBVersionInfoSize;  
  
      // Holds the version name  
      TLocalDBVersionwszVersion;  
  
      // TRUE if the instance files exist on disk, FALSE otherwise  
      BOOL   bExists;  
  
      // Holds the LocalDB version for the instance in the format: major.minor.build.revision  
      DWORD  dwMajor;  
      DWORD  dwMinor;  
      DWORD  dwBuild;  
      DWORD  dwRevision;  
} LocalDBVersionInfo;  
  
```  
  
 **File di intestazione:** SQLNCLI. h  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT LocalDBGetVersionInfo(  
           PCWSTR wszVersionName,           PLocalDBVersionInfo pVersionInfo,           DWORD dwVersionInfoSize);  
```  
  
## <a name="parameters"></a>Parametri  
 *wszVersionName*  
 [Input] Nome della versione del database locale.  
  
 *pVersionInfo*  
 [Output] Buffer per archiviare le informazioni sulla versione del database locale.  
  
 *dwVersionInfoSize*  
 [Input] Include le dimensioni del *VersionInfo* buffer.  
  
## <a name="returns"></a>Valori di codice restituiti  
 S_OK  
 Funzione completata.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../../relational-databases/express-localdb-error-messages/localdb-error-not-installed.md)  
 Database locale di SQL Server Express non installato nel computer.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Uno o più parametri di input specificati non validi.  
  
 [LOCALDB_ERROR_UNKNOWN_VERSION](../../relational-databases/express-localdb-error-messages/localdb-error-unknown-version.md)  
 La versione del database locale specificata non esiste.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 Errore imprevisto. Per informazioni, vedere il registro eventi.  
  
## <a name="details"></a>Dettagli  
 La logica alla base dell'introduzione del **struct** argomento delle dimensioni (*lpVersionInfoSize*) consiste nell'abilitare l'API per versioni diverse di restituire il **LocalDBVersionInfostruct**, in modo efficace l'abilitazione di compatibilità con le versioni precedenti e successive.  
  
 Se il **struct** argomento delle dimensioni (*lpVersionInfoSize*) corrisponde alle dimensioni di una versione nota del **LocalDBVersionInfostruct**, tale versione di  **struct** viene restituito. In caso contrario, viene restituito LOCALDB_ERROR_INVALID_PARAMETER.  
  
 Un esempio tipico di **LocalDBGetVersionInfo** utilizzo delle API è simile al seguente:  
  
```  
LocalDBVersionInfo vi;  
LocalDBVersionInfo(L”11.0”, &vi, sizeof(LocalDBVersionInfo));  
  
```  
  
## <a name="remarks"></a>Osservazioni  
 Per un esempio di codice che usa l'API del database locale, vedere [riferimento di SQL Server Express LocalDB](../../relational-databases/sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sulla versione e intestazione di SQL Server Express LocalDB](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
