---
title: bcp_sendrow | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- bcp_sendrow
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_sendrow function
ms.assetid: ddbdb4bd-ad4e-4bf1-9a75-656aa26ce10a
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 97229063d5ce78ebae1293eb85b05ee8765fc4c6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062625"
---
# <a name="bcpsendrow"></a>bcp_sendrow
  Invia una riga di dati dalle variabili di programma a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RETCODE bcp_sendrow (  
    HDBC   
hdbc  
);  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *HDBC*  
 Handle di connessione ODBC abilitato per la copia bulk.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SUCCEED o FAIL.  
  
## <a name="remarks"></a>Remarks  
 Il **bcp_sendrow** funzione compila una riga dalle variabili di programma e lo invia a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Prima di chiamare **bcp_sendrow**, è necessario effettuare chiamate al [bcp_bind](bcp-bind.md) per specificare le variabili di programma che contiene dati di riga.  
  
 Se **bcp_bind** viene chiamato specificando un tipo di dati long a lunghezza variabile, ad esempio, un *eDataType* parametro di SQLTEXT e un valore diverso da null *pData* parametro, **bcp_sendrow** invia il valore entiredata come avviene per qualsiasi altro tipo di dati. Se, tuttavia **bcp_bind** ha un valore NULL *pData* parametro **bcp_sendrow** restituisce il controllo all'applicazione subito dopo tutte le colonne con i dati specificati vengono inviate a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'applicazione può quindi chiamare [bcp_moretext](bcp-moretext.md) ripetutamente per inviare i dati long a lunghezza variabile a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un blocco alla volta. Per altre informazioni, vedere [bcp_moretext](bcp-moretext.md).  
  
 Quando si **bcp_sendrow** consente di copia bulk di righe dalle variabili di programma in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabelle, delle righe viene eseguito solo quando l'utente chiama [bcp_batch](bcp-batch.md) oppure [bcp_done](bcp-done.md) . L'utente può scegliere di chiamare **bcp_batch** una volta ogni *n* righe o quando c'è una pausa nei tra periodi di dati in arrivo. Se **bcp_batch** viene mai chiamato, le righe vengono eseguito il commit quando **bcp_done** viene chiamato.  
  
 Per informazioni sull'interruzione di una modifica di copia bulk a partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], vedere [l'esecuzione di operazioni di copia Bulk &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di copia bulk](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  