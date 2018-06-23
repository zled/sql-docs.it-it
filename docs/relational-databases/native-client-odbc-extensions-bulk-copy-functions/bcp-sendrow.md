---
title: bcp_sendrow | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- bcp_sendrow
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_sendrow function
ms.assetid: ddbdb4bd-ad4e-4bf1-9a75-656aa26ce10a
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d78aceec83230cc8772186d5360b80b2ff656053
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35695742"
---
# <a name="bcpsendrow"></a>bcp_sendrow
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Invia una riga di dati dalle variabili di programma a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RETCODE bcp_sendrow (  
    HDBC hdbc);  
```  
  
## <a name="arguments"></a>Argomenti  
 *HDBC*  
 Handle di connessione ODBC abilitato per la copia bulk.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SUCCEED o FAIL.  
  
## <a name="remarks"></a>Remarks  
 Il **bcp_sendrow** funzione compila una riga dalle variabili di programma e lo invia a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Prima di chiamare **bcp_sendrow**, è necessario effettuare chiamate al [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) per specificare le variabili di programma che contiene dati di riga.  
  
 Se **bcp_bind** viene chiamato specificando un tipo di dati long a lunghezza variabile, ad esempio, un *eDataType* parametro di SQLTEXT e un valore non NULL *pData* parametro, **bcp_sendrow** invia l'intero valore dei dati, come avviene per qualsiasi altro tipo di dati. Se, tuttavia **bcp_bind** ha un valore NULL *pData* parametro **bcp_sendrow** restituisce il controllo all'applicazione subito dopo tutte le colonne con i dati specificati vengono inviate a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'applicazione può quindi chiamare [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) ripetutamente per inviare i dati long a lunghezza variabile a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un blocco alla volta. Per altre informazioni, vedere [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md).  
  
 Quando si **bcp_sendrow** consente di copia bulk di righe dalle variabili di programma in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabelle, delle righe viene eseguito solo quando l'utente chiama [bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) oppure [bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md) . L'utente può scegliere di chiamare **bcp_batch** una volta ogni *n* righe o quando c'è una pausa nei tra periodi di dati in arrivo. Se **bcp_batch** viene mai chiamato, le righe vengono eseguito il commit quando **bcp_done** viene chiamato.  
  
 Per informazioni sull'interruzione di una modifica di copia bulk a partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], vedere [l'esecuzione di operazioni di copia Bulk &#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di copia bulk](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
