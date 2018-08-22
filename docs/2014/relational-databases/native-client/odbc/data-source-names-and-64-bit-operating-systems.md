---
title: Origine dati i nomi e i sistemi operativi a 64 Bit | Documenti di Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c2f86810-2775-4ddd-8df7-e8373785a7fc
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 323f2b89ac1af42038e1f6036ed5fea36edb8265
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2018
ms.locfileid: "40393431"
---
# <a name="data-source-names-and-64-bit-operating-systems"></a>Nomi di origine dati e sistemi operativi a 64 bit
  Per compilare ed eseguire un'applicazione come applicazione a 32 bit in un sistema operativo a 64 bit, è necessario creare l'origine dati ODBC con Amministratore ODBC in %windir%\SysWOW64\odbcad32.exe.  
  
## <a name="remarks"></a>Note  
 Un sistema operativo Windows a 64 bit include due file odbcad32.exe:  
  
-   %SystemRoot%\system32\odbcad32.exe viene utilizzato per creare e gestire nomi di origine dati per applicazioni a 64 bit.  
  
-   %SystemRoot%\SysWOW64\odbcad32.exe viene utilizzato per creare e gestire nomi di origine dati per applicazioni a 32 bit, incluse le applicazioni a 32 bit in esecuzione in sistemi operativi a 64 bit.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;ODBC&#41;](sql-server-native-client-odbc.md)  
  
  
