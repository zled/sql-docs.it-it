---
title: Limitazioni di sicurezza per SQL Server in Linux | Microsoft Docs
description: Questo articolo descrive le restrizioni di Linux SQL Server.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/30/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.openlocfilehash: 9c58592568ca841df270190970fb76fefe43d96d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47711719"
---
# <a name="security-limitations-for-sql-server-on-linux"></a>Limitazioni di sicurezza per SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server in Linux è attualmente presenta le limitazioni seguenti:

* Viene fornito un criterio di password standard. MUST_CHANGE è l'unica opzione che è possibile configurare.  
* Extensible Key Management non è supportato. 
* Con chiavi archiviate in Azure Key Vault non è supportato.
* SQL Server genera il proprio certificato autofirmato per la crittografia delle connessioni. SQL Server può essere configurato per l'uso di un utente fornito certificato per TLS. 

Per altre informazioni sulle funzionalità di sicurezza disponibili in SQL Server, vedere la [Centro sicurezza per il motore di Database di SQL Server e Database SQL di Azure](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## <a name="next-steps"></a>Passaggi successivi

Per attività di sicurezza comuni, vedere [Introduzione alle funzionalità di sicurezza di SQL Server in Linux](sql-server-linux-security-get-started.md). Per uno script modificare il protocollo TCP numero di porta, le directory di SQL Server e configurare i flag di traccia o le regole di confronto, vedere [configurare SQL Server in Linux con mssql-conf](sql-server-linux-configure-mssql-conf.md).
