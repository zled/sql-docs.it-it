---
title: 'Ibcpsession:: BCPColumns (OLE DB) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IBCPSession::BCPColumns (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPColumns method
ms.assetid: c338abe8-9e30-4853-a7c6-b1a6c00095e1
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a1fc6c8da0e46ac40bf6ddd2fbd821cdd6986dc8
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37426340"
---
# <a name="ibcpsessionbcpcolumns-ole-db"></a>IBCPSession::BCPColumns (OLE DB)
  Imposta il numero di campi da associare alle colonne di una tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT BCPColumns(   
DBCOUNTITEMnColumns);  
```  
  
## <a name="remarks"></a>Note  
 Chiama internamente [ibcpsession:: BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) per impostare i valori predefiniti per i dati di campo. Questi valori predefiniti vengono ottenuti dalle informazioni di colonna SQL Server che il provider recupera internamente quando il nome della tabella viene specificato tramite [ibcpsession:: BCPInit](ibcpsession-bcpinit-ole-db.md).  
  
> [!NOTE]  
>  Questo metodo può essere chiamato solo dopo aver **BCPInit** è stato chiamato con un nome file valido.  
  
 È consigliabile chiamare questo metodo solo se si intende utilizzare un formato di file utente diverso da quello predefinito. Per altre informazioni su una descrizione del formato di file utente predefinito, vedere la **BCPInit** (metodo).  
  
 Dopo la chiamata di **BCPColumns** metodo, è necessario chiamare il **BCPColFmt** metodo per ogni colonna nel file utente per definire completamente un formato di file personalizzato.  
  
## <a name="arguments"></a>Argomenti  
 *nColumns*[in]  
 Numero totale di campi nel file utente. Anche se ci si prepara a copia bulk di dati dal file utente a un Server SQL di tabella e non si intende copiare tutti i campi nel file utente, si dovrà comunque impostare la *nColumns* argomento per il numero totale di campi del file utente. I campi ignorati possono quindi essere specificati tramite **BCPColFmt**.  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 Il metodo è riuscito.  
  
 E_FAIL  
 Si è verificato un errore specifico del provider; Per informazioni dettagliate, usare il [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interfaccia.  
  
 E_UNEXPECTED  
 La chiamata al metodo non era prevista. Non è stato ad esempio chiamato il metodo **BCPInit** prima della chiamata a questo metodo. Si verifica inoltre quando questo metodo viene chiamato più volte per un'operazione di copia bulk.  
  
 E_OUTOFMEMORY  
 Errore di memoria insufficiente.  
  
## <a name="see-also"></a>Vedere anche  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [Esecuzione di operazioni di copia bulk](../native-client/features/performing-bulk-copy-operations.md)  
  
  
