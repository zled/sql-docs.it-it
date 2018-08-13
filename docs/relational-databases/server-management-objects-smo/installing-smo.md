---
title: Installazione di SMO | Microsoft Docs
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
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 6fa46b32b884637e998a20037f510f37d3546fc9
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39553131"
---
#<a name="installing-smo"></a>Installazione di SMO (SQL Server Management Objects)

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

Questa pagina fornisce informazioni su come installare SMO per l'utilizzo da applicazioni e i requisiti di sistema per l'utilizzo di SMO.

## <a name="smo-nuget-package"></a>Pacchetto NuGet SMO

A partire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2017 SMO viene distribuito come i [Microsoft.SqlServer.SqlManagementObjects](https://www.nuget.org/packages/Microsoft.SqlServer.SqlManagementObjects) pacchetto NuGet per consentire agli utenti di sviluppare applicazioni con SMO.

Si tratta di una sostituzione per sharedmanagementobjects. msi, che in precedenza è stato rilasciato come parte del Feature Pack di SQL per ogni versione di SQL Server. Le applicazioni che utilizzano SMO devono essere aggiornate per usare invece il pacchetto NuGet e saranno responsabile di garantire che i file binari vengono installati con l'applicazione in fase di sviluppo.

>>[!Important]
>>Come accennato nel [file e i numeri di versione](files-and-version-numbers.md) pagina, non è necessario installare gli assembly SMO nella GAC. Ciò potrebbe causare problemi con altre applicazioni che usano tali versioni di SMO (ad esempio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio).

##<a name="installing-the-package"></a>Installazione del pacchetto

Visualizzare [NuGet introduttiva - usare un pacchetto](https://docs.microsoft.com/nuget/quickstart/use-a-package) per istruzioni ed esempi di installazione e uso di un pacchetto NuGet. 
  
## <a name="system-requirements"></a>Requisiti di sistema
  
 SMO richiede [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.0 in esecuzione, pertanto qualsiasi applicazione che usa, è necessario assicurarsi che i computer client utilizzano la stessa versione o versioni successive.
  
