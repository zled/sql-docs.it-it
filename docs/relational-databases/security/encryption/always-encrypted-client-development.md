---
title: Crittografia Always Encrypted (sviluppo client) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: 9595eb66-284c-4474-828f-8961a05ce989
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5fc16ae7a4e051d7085cb4d6229da9b23824a761
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37272307"
---
# <a name="always-encrypted-client-development"></a>Crittografia sempre attiva (sviluppo client)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

[Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) è una tecnologia di crittografia lato client che assicura che i dati riservati e le chiavi di crittografia associate non vengano mai rivelati a SQL Server o al database SQL di Azure. Con Always Encrypted, un driver client crittografa in modo trasparente i dati sensibili prima di passarli al motore di database e decrittografa in modo trasparente i dati recuperati da colonne di database crittografate.

Per informazioni dettagliate sullo sviluppo di applicazioni che usano database protetti da Always Encrypted e sui driver client e sulle versioni dei driver che supportano Always Encrypted, vedere:

- [Using Always Encrypted with .NET Framework Data Provider for SQL Server (Uso di Always Encrypted con il provider di dati .NET Framework per SQL Server)](../../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)
- [Utilizzo di Always Encrypted con il JDBC Driver](../../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)
- [Uso di Always Encrypted con il driver ODBC Windows](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)



## <a name="see-also"></a>Vedere anche

[Always Encrypted (Motore di database)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)

