---
title: Funzione SQLAsyncNotificationCallback | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c56aedc9-f7f7-4641-b605-f0f98ed4400c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c785f8547730817c0b1723da38f7ee021aa4f00
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32916976"
---
# <a name="sqlasyncnotificationcallback-function"></a>SQLAsyncNotificationCallback (funzione)
**Conformità**  
 Introdotta: versione ODBC 3.8  
  
 Conformità agli standard: nessuno  
  
 **Riepilogo**  
 **SQLAsyncNotificationCallback** consente al driver per la richiamata al Driver Manager quando si verifica alcuni lo stato di avanzamento dell'operazione asincrona corrente dopo che il driver restituisce SQL_STILL_EXECUTING. **SQLAsyncNotificationCallback** può essere solo chiamato dal driver.  
  
 I driver non chiamano **SQLAsyncNotificationCallback** con nome di funzione **SQLAsyncNotificationCallback**. Al contrario, gestione Driver passa un puntatore a funzione a un driver come il valore dell'attributo SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK o SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK per l'handle di connessione corrispondente o l'handle di istruzione, rispettivamente. È possibile assegnare gli handle di diversi valori del puntatore funzione diversa. Il tipo del puntatore a funzione è definito come SQL_ASYNC_NOTIFICATION_CALLBACK.  
  
 **SQLAsyncNotificationCallback** è thread-safe. Un driver è possibile scegliere di utilizzare più thread che chiamano **SQLAsyncNotificationCallback** su diversi gestisce contemporaneamente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef SQLRETURN (SQL_API *SQL_ASYNC_NOTIFICATION_CALLBACK)(  
   SQLPOINTER pContex,   
   BOOL fLast);  
```  
  
## <a name="arguments"></a>Argomenti  
 *pContex*  
 Puntatore a una struttura di dati definita da Gestione Driver. Il valore viene passato per il driver tramite SQLSetConnectAttr(SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT) o SQLSetStmtAttr(SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT).  Il driver non ha accesso al valore.  
  
 *fLast*  
 Utilizzato da un driver per indica che questa chiamata di funzione di callback è l'ultimo per l'operazione asincrona corrente. Quando Gestione Driver chiama la funzione nuovamente, il driver restituirà un codice restituito diverso da SQL_STILL_EXECUTING. Gestione Driver può utilizzare queste informazioni, ad esempio, per informare in anticipo l'applicazione che verrà completata l'operazione asincrona.  
  
 Se *gestire* non è un handle valido del tipo specificato da *HandleType*, **SQLCancelHandle** restituisca SQL_INVALID_HANDLE.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS o SQL_ERROR.  
  
## <a name="diagnostics"></a>Diagnostica  
 **SQLAsyncNotificationCallback** restituisce SQL_ERROR per due situazioni seguenti (queste informazioni indicano un problema di implementazione nel driver o di gestione Driver.  
  
|Errore|Description|  
|-----------|-----------------|  
|Connessione o l'istruzione non ha richiesto la notifica.||  
|Non valido *gestire*|Il driver passato un handle non valido, non superati i test di convalida interna di gestione Driver.|  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione asincrona (metodo di polling)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
