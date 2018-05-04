---
title: Utilizzo di applicazioni a 16 Bit con driver a 32 Bit | Documenti Microsoft
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
- ODBC drivers [ODBC], 16-bit applications
- 16-bit applications with 32-bit drivers [ODBC]
ms.assetid: 68feb3b7-c01a-4f42-8df9-f9c182d89325
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2241eaf4693bf7bdb1fe5d7fbbf809047090dfbc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-16-bit-applications-with-32-bit-drivers"></a>Utilizzo di applicazioni a 16 Bit con driver a 32 Bit
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Utilizzare invece Gestione driver a 32 bit o 64 bit.  
  
 È possibile eseguire applicazioni a 16 bit con driver a 32 bit sul sistema basato su Windows, purché il driver a 32 bit non chiama in modo esplicito le funzioni API Win32 che creano thread. Il sottosistema Windows on Windows (WOW) le applicazioni vengono eseguite in modalità a 16 bit e risolve le chiamate a 16 bit per il sistema operativo. ODBC thunk delle chiamate a 16 bit DLL resolve dall'applicazione al driver a 32 bit. Le applicazioni a 16 bit utilizzano l'API di Windows e driver a 32 bit dell'API Win32.  
  
## <a name="architecture"></a>Architecture  
 La figura seguente mostra le applicazioni a 16 bit di comunicare con driver a 32 bit. Tra il gestore di Driver a 16 bit e il driver a 32 bit sono generiche thunk DLL che convertono le chiamate a 16 bit ODBC alle chiamate ODBC a 32 bit.  
  
 ![16 come&#45;comunicazione delle applicazioni di bit con 32&#45;bit driver](../../odbc/microsoft/media/sdka2.gif "sdka2")  
  
> [!NOTE]  
>  Ogni volta che un'applicazione a 16 bit interagisce con un driver a 32 bit, 32 bit con Driver Manager restituisce sempre "2.0" della versione di ODBC supportati dal driver.  
  
## <a name="administration"></a>Amministrazione  
 È possibile gestire le origini dati per i driver a 32 bit tramite Amministrazione origine dati ODBC. Per aprire l'amministratore ODBC in computer che eseguono Microsoft® Windows® 2000, aprire il pannello di controllo di Windows, fare doppio clic su **strumenti di amministrazione**, quindi fare doppio clic su **origini dati (ODBC)**. Nei computer che eseguono versioni precedenti di Microsoft Windows, l'icona è denominata **ODBC a 32 bit** o semplicemente **ODBC**.  
  
 Nella figura seguente viene illustrato come un'applicazione a 16 bit chiama una DLL di installazione di driver a 32 bit. Tra il programma di installazione a 16 bit DLL e il driver a 32 bit DLL di installazione è una DLL di thunk generica che converte le chiamate DLL programma di installazione a 16 bit in chiamate DLL di installazione a 32 bit.  
  
 ![Come un 16&#45;bit app chiama un 32&#45;bit di installazione del driver DLL](../../odbc/microsoft/media/sdka3.gif "sdka3")  
  
 In Windows on Windows (thunk di 16 bit a 32 bit), una DLL thunk aggiuntiva denominata Ds32gt converte i valori di argomento a 16 bit passati tramite un programma di installazione a 32 bit DLL eseguire il backup a 16 bit.  
  
## <a name="components"></a>Components  
 Il componente ODBC di MDAC 2.8 SP1 SDK include i seguenti file per l'esecuzione di applicazioni a 16 bit con driver a 32 bit. Questi componenti si trovano nella directory \Redist.  
  
|Nome file|Description|  
|---------------|-----------------|  
|Odbc16gt|DLL thunk generico ODBC a 16 bit|  
|Odbc32gt|DLL thunk generico ODBC a 32 bit|  
|Odbccp32|installazione a 32 bit DLL|  
|Odbcad32.exe|programma di amministrazione di 32 bit|  
|Odbcinst|File di programma di installazione della Guida|  
|Ds16gt. dll|installazione di driver a 16 bit generico thunk DLL|  
|CTL3D32|raccolta di stili di finestra tridimensionale a 32 bit|  
  
 Inoltre, i file seguenti con la gestione di ODBC 2.10 Driver a 16 bit, che non fanno parte di ODBC 3.51, sono necessari per e devono essere installati con l'applicazione a 16 bit.  
  
|Nome file|Description|  
|---------------|-----------------|  
|Mentre|Gestione Driver a 16 bit|  
|Odbcinst.dll|programma di installazione a 16 bit DLL|  
|Odbcadm.exe|programma di amministrazione di ODBC a 16 bit|
