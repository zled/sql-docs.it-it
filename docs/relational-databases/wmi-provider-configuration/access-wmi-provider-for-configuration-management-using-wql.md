---
title: Provider WMI di accesso per la gestione della configurazione mediante WQL | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
ms.assetid: 26499530-d93b-452b-bbe4-217ef1d11e68
caps.latest.revision: 16
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: cece73ebb5402fe2f725fedbcdf7cdc833d08265
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33013178"
---
# <a name="access-wmi-provider-for-configuration-management-using-wql"></a>Accedere al provider WMI per la gestione della configurazione tramite WQL
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  In questa sezione viene illustrato come eseguire le istruzioni WQL ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Management Instrumentation Query Language) sul provider WMI per Gestione computer.  
  
 Nell'esempio viene utilizzato un editor WQL, WBEMtest.exe, per eseguire query WQL sul provider WMI per enumerare i servizi, i protocolli di rete e gli alias di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="querying-services-using-wbemtest"></a>Esecuzione di query sui servizi mediante WBEMtest  
  
1.  Dal **avviare** menu, fare clic su **eseguire**, quindi immettere **WBEMtest**.  
  
2.  Viene visualizzata la finestra di dialogo WBEMtest.exe. Fare clic su **Connetti**.  
  
3.  Nel primo campo di testo digitare lo spazio dei nomi del provider WMI per Gestione computer: root\Microsoft\SqlServer\ComputerManagement11. Fare clic su **Connetti**.  
  
4.  Fare clic su **Query**. Digitare una query che restituisca i servizi correnti in esecuzione nel computer locale: **selezionare \* da SqlService.** Fare clic su **Applica**.  
  
5.  Ridefinire ulteriormente la query aggiungendo **dove ServiceName = "MSSQLSERVER"**.  
  
  
