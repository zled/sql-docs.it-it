---
title: Gestione di parametri LOB (Large Object) in CLR | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- large data, CLR integration
- LOB data [SQL Server], CLR integration
- SqlBytes data type
- SqlChars data type
ms.assetid: d07956f6-9543-4476-9426-536f95991150
caps.latest.revision: "20"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a2fa2bb9022d5bc53ecf8424211b1a9bb6a8fe00
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a>Gestione di parametri di tipo LOB (Large Object) in CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Utilizzare **SqlBytes** e **SqlChars** passare LOB (large object) di tipo binario (**varbinary (max)**) e LOB di tipo carattere (**nvarchar (max)**) parametri, rispettivamente. Questi tipi consentono di eseguire il flusso dei valori LOB dal database alla routine CLR (Common Language Runtime) anziché copiare l'intero valore nello spazio gestito. **SqlBinary** e **SqlString** deve essere utilizzato solo per i binari di piccole dimensioni e i valori di stringa di caratteri.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati di SQL Server in .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
