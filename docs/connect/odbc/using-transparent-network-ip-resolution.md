---
title: Uso di risoluzione dell'IP di rete trasparente | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d255208f-d486-4ad3-8080-61c6e0261825
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 767e3e17b67a36bca93bd8a85704d50338fdfd58
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47610744"
---
# <a name="using-transparent-network-ip-resolution"></a>Uso della risoluzione dell'IP di rete trasparente
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

TransparentNetworkIPResolution è una revisione della funzionalità MultiSubnetFailover esistente, disponibile in Microsoft ODBC Driver 13.1 for SQL Server, che influisce sulla sequenza di connessione del driver nel caso in cui l'indirizzo IP risolto prima del nome host non esiste rispondere e sono presenti più indirizzi IP associati al nome host. Interagisce con MultiSubnetFailover per fornire le sequenze di tre connessione seguenti:

* 0: un tentativo di IP, seguito da tutti gli indirizzi IP in parallelo
* 1: tutti gli indirizzi IP vengono eseguiti in parallelo
* 2: tutti gli indirizzi IP vengono eseguiti uno dopo l'altro

|transparentNetworkIPResolution|MultiSubnetFailover|Comportamento|
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

Il `TransparentNetworkIPResolution` stringa di connessione e DSN (parola chiave) consente di controllare questa impostazione a livello di stringa di connessione. Il valore predefinito è abilitato.

Parola chiave|Valori|Default
-|-|-
`TransparentNetworkIPResolution`|`Yes`, `No`|`Yes`

Il `SQL_COPT_SS_TNIR` attributo pre-connessione consente a un'applicazione controllare questa impostazione a livello di codice:

Attributo di connessione|   Dimensioni/tipo|  Default| valore| Descrizione
-|-|-|-|-
`SQL_COPT_SS_TNIR` (1249)| `SQL_IS_INTEGER` o `SQL_IS_UINTEGER`| `SQL_IS_ON`(1), `SQL_IS_OFF`(0)|`SQL_IS_ON`|Abilita o disabilita TNIR.

<a name="for-more-information-about-multisubnetfailover-see-odbc-driver-on-linux-and-macos---high-availability-and-disaster-recoveryconnectodbclinux-macodbc-driver-on-linux-support-for-high-availability-disaster-recoverymd"></a>Per altre informazioni sulle MultiSubnetFailover, vedere [Driver ODBC in Linux e macOS - disponibilità elevata e ripristino di emergenza](../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)
--------------------------------------------------
## <a name="see-also"></a>Vedere anche  
* [Microsoft ODBC Driver for SQL Server in Windows](../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
* [Clustering su più subnet di SQL Server (SQL Server)](https://msdn.microsoft.com/library/ff878716.aspx#RelatedContent)
