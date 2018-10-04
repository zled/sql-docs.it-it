---
title: Funzione LocalDBGetVersions | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- LocalDBGetVersions
apilocation:
- sqluserinstance.dll
apitype: DLLExport
ms.assetid: 033a9c6b-0d7f-4f8a-ab60-33cd6fee0d33
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: b78298326fdac24ec64155ab86b4e0eddc854d7c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47831789"
---
# <a name="localdbgetversions-function"></a>Funzione LocalDBGetVersions
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Vengono restituite tutte le versioni del database locale di SQL Server Express disponibili nel computer.  
  
 **File di intestazione:** SQLNCLI. h  
  
## <a name="syntax"></a>Sintassi  
  
```  
#define MAX_LOCALDB_VERSION_LENGTH 43typedef WCHAR TLocalDBVersion[MAX_LOCALDB_VERSION_LENGTH + 1];typedef TLocalDBVersion* PTLocalDBVersion;HRESULT LocalDBGetVersions(           PTLocalDBVersion pVersion,           LPDWORD lpdwNumberOfVersions);  
```  
  
## <a name="parameters"></a>Parametri  
 *pVersionNames*  
 [Output] Sono contenuti i nomi delle versioni del database locale disponibili nella workstation dell'utente.  
  
 *lpdwNumberOfVersions*  
 [Input/Output] Per l'input contiene il numero di slot per le versioni nel *pVersionNames* buffer.   
In fase di output, è contenuto il numero di versioni del database locale esistenti.  
  
## <a name="returns"></a>Valori di codice restituiti  
 S_OK  
 Funzione completata.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../../relational-databases/express-localdb-error-messages/localdb-error-not-installed.md)  
 Database locale di SQL Server Express non installato nel computer.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Uno o più parametri di input specificati non validi.  
  
 [LOCALDB_ERROR_INSUFFICIENT_BUFFER](../../relational-databases/express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 Buffer di input troppo corto. Troncamento non necessario.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 Errore imprevisto. Per informazioni, vedere il registro eventi.  
  
## <a name="remarks"></a>Note  
 Per un esempio di codice che utilizza l'API LocalDB, vedere [SQL Server Express LocalDB Reference](../../relational-databases/sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sulla versione e intestazione di SQL Server Express LocalDB](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
