---
title: Funzione LocalDBStopTracing | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- LocalDBStopTracing
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 1d50e040-8602-4ffa-be8f-b8633fdfa7ff
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 7aea3e8a28f8d272f513065c49e0e673997c747d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48076763"
---
# <a name="localdbstoptracing-function"></a>Funzione LocalDBStopTracing
  Viene disabilitata la traccia delle chiamate API per tutte le istanze del database locale SQL Server Express di proprietà dell'utente di Windows corrente.  
  
 **File di intestazione:** SQLNCLI. h  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT LocalDBStopTracing();  
```  
  
## <a name="returns"></a>Valori di codice restituiti  
 S_OK  
 Funzione completata.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../express-localdb-error-messages/localdb-error-internal-error.md)  
 Errore imprevisto. Per informazioni, vedere il registro eventi.  
  
## <a name="remarks"></a>Note  
 Per un esempio di codice che utilizza l'API LocalDB, vedere [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sulla versione e intestazione di SQL Server Express LocalDB](sql-server-express-localdb-header-and-version-information.md)  
  
  
