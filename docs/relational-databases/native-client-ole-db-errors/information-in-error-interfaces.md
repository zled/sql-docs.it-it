---
title: Le informazioni nelle interfacce di errore | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
ms.assetid: 4620f03f-1193-43e7-ba19-ad022737d300
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f6259d21a8b538742509b6f17efedc6530d5e60c
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35699132"
---
# <a name="information-in-error-interfaces"></a>Informazioni nelle interfacce di errore
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client segnala alcune informazioni di errore e di stato nelle interfacce di errore definite da OLE DB **IErrorInfo**, **IErrorRecords**, e **ISQLErrorInfo** .  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta **IErrorInfo** membro funziona nel modo seguente.  
  
|Funzione membro|Description|  
|---------------------|-----------------|  
|**GetDescription**|Stringa descrittiva del messaggio di errore.|  
|**GetGUID**|GUID dell'interfaccia che ha definito l'errore.|  
|**GetHelpContext**|Non supportato. Restituisce sempre zero.|  
|**GetHelpFile**|Non supportato. Viene restituito sempre NULL.|  
|**GetSource**|Stringa "Microsoft SQL Server Native Client".|  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta disponibili per il consumer **IErrorRecords** membro funziona nel modo seguente.  
  
|Funzione membro|Description|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|Inserisce in una struttura ERRORINFO le informazioni di base su un errore. Una struttura ERRORINFO contiene membri che identificano il valore restituito HRESULT per l'errore nonché il provider e l'interfaccia alle quali si applica l'errore.|  
|**GetCustomErrorObject**|Restituisce un riferimento nelle interfacce **ISQLErrorInfo** e [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1).|  
|**GetErrorInfo**|Restituisce un riferimento in un **IErrorInfo** interfaccia.|  
|**GetErrorParameters**|Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non restituisce parametri al consumer attraverso **GetErrorParameters**.|  
|**GetRecordCount**|Conteggio dei record di errore disponibili.|  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta **ISQLErrorInfo:: Getsqlinfo** parametri come indicato di seguito.  
  
|Parametro|Description|  
|---------------|-----------------|  
|*pbstrSQLState*|Restituisce un valore SQLSTATE per l'errore. I valori SQLSTATE vengono definiti nelle specifiche API, SQL-92, ODBC e ISO SQL. Né [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] né la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client definiti valori SQLSTATE specifici dell'implementazione.|  
|*plNativeError*|Restituisce il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] numero di errore **sysmessages** quando disponibile. Gli errori nativi sono disponibili dopo un tentativo riuscito di inizializzare una [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] origine dati del provider OLE DB Native Client. Prima del tentativo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce sempre zero.|  
  
## <a name="see-also"></a>Vedere anche  
 [errori](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
