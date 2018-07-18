---
title: Supporto di FOR XML per i tipi di dati definiti dall'utente (UDT) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- UDTs [SQL Server], XML
- user-defined types [SQL Server], XML
ms.assetid: 354e2150-fa2a-4583-b1aa-6b78ae4378b6
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 713b1bbf215f9f0748de647264697ca30e0d99da
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37242331"
---
# <a name="for-xml-support-for-the-user-defined-data-types-udt"></a>Supporto di FOR XML per i tipi di dati definiti dall'utente (UDT)
  FOR XML non supporta tipi di dati definiti dall'utente Common Language Runtime (CLR).  
  
 Per utilizzare FOR XML con tipi di dati definiti dall'utente CLR, assicurarsi che il tipo di dati abbia una serializzazione XML e utilizzare un cast esplicito per XML nella clausola scelta FOR XML.  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto di FOR XML per vari tipi di dati di SQL Server](for-xml-support-for-various-sql-server-data-types.md)  
  
  
