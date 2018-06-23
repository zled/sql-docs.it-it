---
title: SQLParamData | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLParamData function
ms.assetid: 92349482-ea22-4a6a-8484-e9c6566794fa
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bd3fefeaa05f806650b58d1778658fda0ed63fa2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069391"
---
# <a name="sqlparamdata"></a>SQLParamData
  Quando viene restituito SQLParamData il *ValuePtrPtr* associato a un parametro con valori di tabella, l'applicazione deve chiamare SQLPutData con *StrLen_Or_Ind*. Se *StrLen_Or_Ind* ha un valore maggiore di 0, significa che l'applicazione è pronta per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client raccolga dati dei parametri per la riga di parametro con valori di tabella successiva. Se *StrLen_Or_Ind* ha un valore pari a 0, significa che non sono presenti altre righe di dati per il parametro con valori di tabella. Per altre informazioni, vedere [associazione e Data Transfer of Table-Valued parametri e valori di colonna](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Per ulteriori informazioni sui parametri con valori di tabella, vedere [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [SQLParamData](http://go.microsoft.com/fwlink/?LinkId=80706)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  