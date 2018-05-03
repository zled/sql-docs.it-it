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
ms.topic: conceptual
ms.assetid: 36025ec0-3c72-4e68-8083-58b38e42d03b
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33b218598871e570fa99d212d565c834718de1d9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>JDBC 4.3 conformità per il Driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

    
> [!NOTE]  
>  Versioni precedenti a Microsoft JDBC Driver 6.4 per SQL Server sono conformi per le specifiche Java Database Connectivity API 4.2. In questa sezione non è applicabile per le versioni precedenti la versione 6.4.  
  
 Attualmente, Microsoft JDBC Driver 6.4 per SQL Server è Java 9 compatibili, ma non è completamente conforme per le specifiche Java Database Connectivity API 4.3. Per appena introdotta l'API di JDBC 4.3, se non è supportata dal driver, il driver genererà un SQLFeatureNotSupportedException.