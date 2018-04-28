---
title: JDBC 4.3 conformità per il Driver JDBC | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 36025ec0-3c72-4e68-8083-58b38e42d03b
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3a943388e1a1a44eb377e9eaa6268733e31c4ef9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>JDBC 4.3 conformità per il Driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

    
> [!NOTE]  
>  Versioni precedenti a Microsoft JDBC Driver 6.4 per SQL Server sono conformi per le specifiche Java Database Connectivity API 4.2. In questa sezione non è applicabile per le versioni precedenti la versione 6.4.  
  
 Attualmente, Microsoft JDBC Driver 6.4 per SQL Server è Java 9 compatibili, ma non è completamente conforme per le specifiche Java Database Connectivity API 4.3. Per appena introdotta l'API di JDBC 4.3, se non è supportata dal driver, il driver genererà un SQLFeatureNotSupportedException.