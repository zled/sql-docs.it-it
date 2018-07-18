---
title: Dettagli relativi agli errori SQL Server | Microsoft Docs
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
- errors [OLE DB], error details
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error details
- ISQLServerErrorInfo interface
ms.assetid: 51500ee3-3d78-47ec-b90f-ebfc55642e06
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2b937fda454ae08549917cdf3682ef20c76373a6
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408990"
---
# <a name="sql-server-error-detail"></a>Dettagli relativi agli errori SQL Server
  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client definisce l'interfaccia di errore specifico del provider [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md). L'interfaccia restituisce maggiori dettagli relativi agli errori [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e risulta molto utile quando operazioni di esecuzione di comandi o del set di righe non riescono.  
  
 Esistono due modi per ottenere l'accesso al **ISQLServerErrorInfo** interfaccia.  
  
 Il consumer può chiamare **IErrorRecords:: Getcustomererrorobject** per ottenere un **ISQLServerErrorInfo** puntatore, come illustrato nell'esempio di codice seguente. (Non è necessario ottenere **ISQLErrorInfo.**) Entrambe **ISQLErrorInfo** e **ISQLServerErrorInfo** sono oggetti errore OLE DB personalizzati, con **ISQLServerErrorInfo** rappresenta l'interfaccia da utilizzare per ottenere informazioni di errori del server, inclusi dettagli quali i numeri di riga e il nome procedura as.  
  
```  
// Get the SQL Server custom error object.  
if(FAILED(hr=pIErrorRecords->GetCustomErrorObject(  
   nRec, IID_ISQLServerErrorInfo,  
   (IUnknown**)&pISQLServerErrorErrorInfo)))  
```  
  
 Un altro modo per ottenere un **ISQLServerErrorInfo** puntatore consiste nel chiamare il **QueryInterface** metodo su un già ottenuto **ISQLErrorInfo** puntatore. Si noti che, poiché **ISQLServerErrorInfo** contiene un superset delle informazioni disponibili da **ISQLErrorInfo**, è opportuno passare direttamente alla **ISQLServerErrorInfo**attraverso **GetCustomerErrorObject**.  
  
 Il **ISQLServerErrorInfo** interfaccia espone una funzione membro [ISQLServerErrorInfo:: GetErrorInfo](../native-client-ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md). La funzione restituisce un puntatore a una struttura SSERRORINFO e un puntatore a un buffer di stringhe. Entrambi i puntatori fanno riferimento a memoria, il consumer deve deallocare utilizzando il **IMalloc:: Free** (metodo).  
  
 I membri di struttura SSERRORINFO vengono interpretati dal consumer come segue.  
  
|Membro|Description|  
|------------|-----------------|  
|*pwszMessage*|Messaggio di errore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Identica alla stringa restituita nel **IErrorInfo:: GetDescription**.|  
|*pwszServer*|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per la sessione.|  
|*pwszProcedure*|Se appropriato, restituisce il nome della stored procedure in cui ha avuto origine l'errore. In caso contrario, una stringa vuota.|  
|*lNative*|Numero di errore nativo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Identico al valore restituito nel *plNativeError* del parametro **ISQLErrorInfo:: Getsqlinfo**.|  
|*bState*|Stato di un messaggio di errore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*bClass*|Gravità di un messaggio di errore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*wLineNumber*|Quando è applicabile, restituisce il numero di riga di una stored procedure in cui si è verificato l'errore.|  
  
## <a name="see-also"></a>Vedere anche  
 [Errori](errors.md)   
 [RAISERROR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
