---
title: Installazione di SMO | Documenti Microsoft
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: sql
ms.prod_service: database-engine
ms.component: smo
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- installing SMO
- SMO [SQL Server], installing
- SQL Server Management Objects, installing
ms.assetid: 140e9971-4940-4866-89b9-5cec938e2a16
caps.latest.revision: "46"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 5d758997c68328cd984befcf808721336c18ece4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
#<a name="installing-smo"></a>Installazione di SMO (SQL Server Management Objects)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Questa pagina fornisce informazioni su come installare SMO per l'utilizzo da applicazioni e i requisiti di sistema per l'utilizzo di SMO.

## <a name="smo-nuget-package"></a>Pacchetto NuGet SMO

A partire da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2017 SMO viene distribuito come il [Microsoft.SqlServer.SqlManagementObjects](https://www.nuget.org/packages/Microsoft.SqlServer.SqlManagementObjects) pacchetto NuGet per consentire agli utenti di sviluppare applicazioni con SMO.

Si tratta di una sostituzione per SharedManagementObjects.msi, che in precedenza è stato rilasciato come parte del Feature Pack di SQL per ogni versione di SQL Server. Le applicazioni che utilizzano SMO devono essere aggiornate per utilizzare invece il pacchetto NuGet e saranno responsabile dell'applicazione che i file binari vengono installati con l'applicazione in fase di sviluppo.

>>[!Important]
>>Come accennato nel [file e i numeri di versione](files-and-version-numbers.md) pagina, evitare di installare gli assembly SMO nella GAC. In questo modo potrebbe verificarsi problemi con altre applicazioni che utilizzano tali versioni di SMO (ad esempio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio).

##<a name="installing-the-package"></a>L'installazione del pacchetto

Vedere [NuGet avvio rapido - utilizzo di un pacchetto](https://docs.microsoft.com/en-us/nuget/quickstart/use-a-package) per istruzioni ed esempi di installazione e utilizzo di un pacchetto NuGet. 
  
## <a name="system-requirements"></a>Requisiti di sistema
  
 SMO richiede [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.0 in esecuzione, pertanto le applicazioni che utilizzano necessario assicurarsi che i computer client dispone di tale versione o versione successiva.
  
