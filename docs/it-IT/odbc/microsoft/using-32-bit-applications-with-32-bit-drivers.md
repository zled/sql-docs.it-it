---
title: Utilizzo di applicazioni a 32 Bit con driver a 32 Bit | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], 32-bit applications
- 32-bit applications with 32-bit drivers [ODBC]
ms.assetid: 0cdd5788-5642-4280-8d53-b4ec461aafa1
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cfffd8474f11c0e10fe521e9ea222c72127a6d63
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-32-bit-applications-with-32-bit-drivers"></a>Utilizzo di applicazioni a 32 Bit con driver a 32 Bit
È possibile eseguire applicazioni a 32 bit con driver a 32 bit. Le applicazioni a 32 bit e il driver a 32 bit è possibile utilizzare l'API Win32®.  
  
## <a name="architecture"></a>Architecture  
 La figura seguente mostra le applicazioni a 32 bit di comunicare con driver a 32 bit. L'applicazione chiama il gestore di Driver a 32 bit, che a sua volta chiama driver a 32 bit.  
  
 ![Modalità 32&#45;comunicazione delle applicazioni di bit con 32&#45;bit driver](../../odbc/microsoft/media/sdka6.gif "sdka6")  
  
> [!IMPORTANT]  
>  Non utilizzare l'installazione a 32 bit thunk DLL su Windows NT o Windows 2000. Anche se presenta lo stesso nome di file del programma di installazione a 32 bit DLL, è un'altra DLL.  
  
## <a name="administration"></a>Amministrazione  
 È possibile gestire le origini dati per i driver a 32 bit tramite Amministrazione origine dati ODBC. Per aprire l'amministratore ODBC in computer che eseguono Windows 2000, aprire il pannello di controllo di Windows, fare doppio clic su **strumenti di amministrazione**, quindi fare doppio clic su **origini dati (ODBC)**. Nei computer che eseguono versioni precedenti di Microsoft Windows, l'icona è denominata **ODBC a 32 bit** o semplicemente **ODBC**.  
  
## <a name="components"></a>Components  
 Il componente ODBC include i seguenti file per l'esecuzione di applicazioni a 32 bit con driver a 32 bit. Questi componenti si trovano nella directory \Redist.  
  
|Nome file|Description|  
|---------------|-----------------|  
|ODBC32.dll|Gestione Driver a 32 bit|  
|Odbccp32|Installazione a 32 bit DLL|  
|Odbcad32.exe|programma Amministratore ODBC a 32 bit|  
|Odbcinst|File di programma di installazione della Guida|  
|Msvcrt40.dll|Libreria di runtime C|
