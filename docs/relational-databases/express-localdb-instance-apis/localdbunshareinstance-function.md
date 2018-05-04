---
title: Funzione LocalDBUnshareInstance | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: localdb
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- LocalDBUnshareInstance
apilocation:
- sqluserinstance.dll
apitype: DLLExport
ms.assetid: 54012ccb-eded-43f7-8ea5-da5ce79224c6
caps.latest.revision: 9
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 61d415909a7df862fde0ece19d894a582960edaa
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="localdbunshareinstance-function"></a>Funzione LocalDBUnshareInstance
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Viene arrestata la condivisione dell'istanza del database locale di SQL Server Express specificata.  
  
 **File di intestazione:** SQLNCLI. h  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT LocalDBUnShareInstance(  
           PCWSTR pInstanceSharedName,   
           DWORD dwFlags   
);  
```  
  
## <a name="parameters"></a>Parametri  
 *pInstanceSharedName*  
 [Input] Nome condiviso dell'istanza di LocalDB di cui interrompere la condivisione.  
  
 *dwFlags*  
 [Input] Riservato per utilizzi futuri. Deve essere impostato attualmente su 0.  
  
## <a name="returns"></a>Valori di codice restituiti  
 S_OK  
 Funzione completata.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../../relational-databases/express-localdb-error-messages/localdb-error-not-installed.md)  
 Database locale di SQL Server Express non installato nel computer.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Uno o più parametri di input specificati non validi.  
  
 [LOCALDB_ERROR_INVALID_INSTANCE_NAME](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 Nome dell'stanza specificata non valido.  
  
 [LOCALDB_ERROR_UNKNOWN_INSTANCE](../../relational-databases/express-localdb-error-messages/localdb-error-unknown-instance.md)  
 Istanza specificata inesistente.  
  
 [LOCALDB_ERROR_ADMIN_RIGHTS_REQUIRED](../../relational-databases/express-localdb-error-messages/localdb-error-admin-rights-required.md)  
 Per eseguire questa operazione, è necessario disporre dei privilegi di amministratore.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 Errore imprevisto. Per informazioni, vedere il registro eventi.  
  
## <a name="remarks"></a>Osservazioni  
 Per un esempio di codice che usa l'API del database locale, vedere [riferimento di SQL Server Express LocalDB](../../relational-databases/sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sulla versione e intestazione di SQL Server Express LocalDB](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
