---
title: Le informazioni nelle interfacce di errore | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
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
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a121dc2e94c67637e867398bfa40c7fe230cd411
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37419020"
---
# <a name="information-in-error-interfaces"></a>Informazioni nelle interfacce di errore
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
|**GetCustomErrorObject**|Restituisce un riferimento nelle interfacce **ISQLErrorInfo** e [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md).|  
|**GetErrorInfo**|Restituisce un riferimento in un **IErrorInfo** interfaccia.|  
|**GetErrorParameters**|Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non restituisce parametri al consumer attraverso **GetErrorParameters**.|  
|**GetRecordCount**|Conteggio dei record di errore disponibili.|  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta **ISQLErrorInfo:: Getsqlinfo** parametri come indicato di seguito.  
  
|Parametro|Description|  
|---------------|-----------------|  
|*pbstrSQLState*|Restituisce un valore SQLSTATE per l'errore. I valori SQLSTATE vengono definiti nelle specifiche API, SQL-92, ODBC e ISO SQL. Né [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] né il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client definiti valori SQLSTATE specifici dell'implementazione.|  
|*plNativeError*|Restituisce il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] numero di errore **master.dbo.sysmessages** quando disponibile. Gli errori nativi sono disponibili dopo un tentativo riuscito di inizializzare una [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] origine dati del provider OLE DB Native Client. Prima del tentativo, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce sempre zero.|  
  
## <a name="see-also"></a>Vedere anche  
 [errori](errors.md)  
  
  
