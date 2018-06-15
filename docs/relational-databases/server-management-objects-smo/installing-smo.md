---
title: Installazione di SMO | Documenti Microsoft
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.prod_service: database-engine
ms.component: smo
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- installing SMO
- SMO [SQL Server], installing
- SQL Server Management Objects, installing
ms.assetid: 140e9971-4940-4866-89b9-5cec938e2a16
caps.latest.revision: 46
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 125712a02b362a49902c9f1e2422414f059864ef
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32965936"
---
#<a name="installing-smo"></a>Installazione di SMO (SQL Server Management Objects)

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

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
  
