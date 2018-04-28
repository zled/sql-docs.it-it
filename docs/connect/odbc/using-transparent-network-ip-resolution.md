---
title: Utilizzando la risoluzione IP di rete Transparent | Documenti Microsoft
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
ms.topic: article
ms.assetid: d255208f-d486-4ad3-8080-61c6e0261825
caps.latest.revision: 2
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e7249d00dc4f3d71b7c3245e2939be7e541f5b39
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-transparent-network-ip-resolution"></a>Utilizzando la risoluzione IP di rete Transparent
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

TransparentNetworkIPResolution è una revisione della funzionalità MultiSubnetFailover esistente, in Microsoft ODBC Driver 13.1 for SQL Server, che influisce sulla sequenza di connessione del driver nel caso in cui il primo indirizzo IP risolto del nome host non disponibile rispondere e sono presenti più indirizzi IP associati al nome host. Interagisce con MultiSubnetFailover per fornire le sequenze di connessione seguenti:

* 0: uno IP viene tentata, seguito da tutti gli indirizzi IP in parallelo
* 1: tentare tutti gli indirizzi IP in parallelo
* 2: tutti gli indirizzi IP viene tentata una dopo l'altra

|TransparentNetworkIPResolution|MultiSubnetFailover|Comportamento|
|:-:|:-:|:-:|
|(predefinito)|(predefinito)|0|
|(predefinito)|Abilitata|1|
|(predefinito)|Disabilitata|0|
|Abilitata|(predefinito)|0|
|Abilitata|Abilitata|1|
|Abilitata|Disabilitata|0|
|Disabilitata|(predefinito)|2|
|Disabilitata|Abilitata|1|
|Disabilitata|Disabilitata|2|

Il `TransparentNetworkIPResolution` stringa di connessione e DSN (parola chiave) controlla questa impostazione a livello di stringa di connessione. Il valore predefinito è abilitato.

Parola chiave|Valori|Valore predefinito
-|-|-
`TransparentNetworkIPResolution`|`Yes`, `No`|`Yes`

Il `SQL_COPT_SS_TNIR` pre-connessione attributo consente a un'applicazione controllare questa impostazione a livello di codice:

Attributo di connessione|   Tipo di dimensione /|  Valore predefinito| Value| Description
-|-|-|-|-
`SQL_COPT_SS_TNIR` (1249)| `SQL_IS_INTEGER`o`SQL_IS_UINTEGER`| `SQL_IS_ON`(1), `SQL_IS_OFF`(0)|`SQL_IS_ON`|Abilita o disabilita TNIR.

<a name="for-more-information-about-multisubnetfailover-see-odbc-driver-on-linux-and-macos---high-availability-and-disaster-recoveryconnectodbclinux-macodbc-driver-on-linux-support-for-high-availability-disaster-recoverymd"></a>Per ulteriori informazioni su MultiSubnetFailover, vedere [Driver ODBC in Linux e macOS - disponibilità elevata e ripristino di emergenza](../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)
--------------------------------------------------
## <a name="see-also"></a>Vedere anche  
* [Microsoft ODBC Driver for SQL Server in Windows](../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
* [SQL Server Clustering su più Subnet (SQL Server)](https://msdn.microsoft.com/library/ff878716.aspx#RelatedContent)
