---
title: Matrice di supporto di driver Microsoft per PHP per SQL Server | Documenti Microsoft
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
caps.latest.revision: ''
author: David-Engel
ms.author: v-daveng
manager: ''
ms.workload: On Demand
ms.openlocfilehash: 23159425e45fdc8974e0047859072654c5c77959
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="microsoft-php-drivers-for-sql-server-support-matrix"></a>Microsoft PHP driver per una matrice di supporto SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

  Questa pagina contiene la matrice e supporto di vita del supporto per i driver Microsoft PHP driver per SQL Server.

## <a name="microsoft-php-drivers-support-lifecycle-matrix-and-policy"></a>Matrice del ciclo di vita del supporto Microsoft PHP driver e i criteri
 I criteri relativi al ciclo di vita del supporto Microsoft (MSL) forniscono informazioni trasparenti e prevedibili riguardanti il ciclo di vita del supporto dei prodotti Microsoft. Versioni di driver PHP 3.x, 4.x e 5.x dispone di cinque anni di supporto "Mainstream" dalla data di rilascio del driver. Il supporto mainstream è definito nel [sito Web del ciclo di vita di supporto tecnico Microsoft](https://support.microsoft.com/lifecycle).

 Opzioni di supporto esteso e personalizzato non sono disponibili per i driver Microsoft PHP driver.

 Sono supportati i seguenti driver Microsoft PHP driver, fino alla data di fine del supporto indicata.

|Nome del driver|Versione del pacchetto driver|Fine del supporto Mainstream|
|-|-|-|
|Driver Microsoft PHP 5.2 per SQL Server|5.2|9 febbraio 2023|
|Microsoft PHP driver 4.3 per SQL Server|4.3|6 luglio 2022|
|Microsoft PHP driver 4.0 per SQL Server|4.0|11 luglio 2021|
|Microsoft PHP driver 3.2 per SQL Server|3.2|9 marzo 2020|
|Microsoft PHP driver 3.1 per SQL Server|3.1|12 dicembre 2019|

 Le seguenti driver Microsoft PHP driver non sono più supportate.

|Nome del driver|Versione del pacchetto driver|Fine del supporto Mainstream|
|-|-|-|
|Microsoft PHP driver 3.0 per SQL Server|3.0|6 marzo 2017|
|Microsoft PHP driver 2.0 per SQL Server|2.0|10 agosto 2015|
|Microsoft PHP driver 1.0 per SQL Server|1,0|28 aprile 2014|

## <a name="sql-server-version-certified-compatibility"></a>Compatibilità certificata versione di SQL Server
 La matrice seguente elenca le versioni di SQL Server che sono state testate e certificate come compatibili con la versione del driver corrispondenti. Si impegna a mantenere la compatibilità con le versioni precedenti del driver, ma solo la versione più recente driver supportato è testati e certificati con le nuove versioni di SQL Server come SQL Server viene rilasciato.

|PHP per la versione del driver SQL Server&#8594;<br />&#8595;Versione di SQL Server|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|3.0<br />&nbsp;|2.0<br />&nbsp;|
|---|---|---|---|---|---|---|---|
|Istanza gestita di SQL Azure<br/> (Extended anteprima privata)|S|S| | | | | |
|Azure SQL Data Warehouse|S|S| | | | | |
|SQL Server 2017   |S|S| | | | | |
|SQL Server 2016   |S|S|S| | | | |
|SQL Server 2014   |S|S|S|S|S| | |
|SQL Server 2012   |S|S|S|S|S|S| |
|SQL Server 2008 R2|S|S|S|S|S|S|S|
|SQL Server 2008   | | |S|S|S|S|S|

## <a name="php-version-support"></a>Supporto della versione PHP
 Con la versione di Microsoft PHP driver elencata sono supportate le seguenti versioni di PHP:

|PHP per la versione del driver SQL Server&#8594;<br />&#8595;Versione PHP|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|3.0<br />&nbsp;|2.0<br />&nbsp;|
|---|---|---|---|---|---|---|---|
|7.2|7.2.1+ in Windows<br/>7.2.0+ su altre piattaforme| | | | | | |
|7.1|7.1.0+ |7.1.0+ |       |        |        |        |        |
|7.0|7.0.0+ |7.0.0+ |7.0.0+ |        |        |        |        |
|5.6|       |       |       |5.6.4+  |        |        |        |
|5.5|       |       |       |5.5.16+ |5.5.16+ |        |        |
|5.4|       |       |       |5.4.32  |5.4.32  |5.4.32  |        |
|5.3|       |       |       |        |        |5.3.0   |5.3.0   |
|5.2|       |       |       |        |        |        |5.2.4<br />5.2.13|

## <a name="supported-operating-systems"></a>Sistemi operativi supportati
 Le versioni dei sistemi operativi Windows seguenti sono supportate con la versione di Microsoft PHP driver elencata:

|PHP per la versione del driver SQL Server&#8594;<br />&#8595;Sistema operativo|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|3.0<br />&nbsp;|2.0<br />&nbsp;|
|---|---|---|---|---|---|---|---|
|Windows Server 2016                 |S  |S  |   |   |   |   |   |
|Windows Server 2012 R2              |S  |S  |S  |S  |S  |   |   |
|Windows Server 2012                 |S  |S  |S  |S  |S  |   |   |
|Windows Server 2008 R2 SP1          |   |   |S  |S  |S  |S  |   |
|Windows Server 2008 R2              |   |   |   |   |   |   |S  |
|Windows Server 2008 SP2             |   |   |S  |S  |S  |S  |   |
|Windows Server 2008                 |   |   |   |   |   |   |S  |
|Windows Server 2003 SP1             |   |   |   |   |   |   |S  |
|Windows 10                          |S  |S  |S  |   |   |   |   |
|Windows 8.1                         |S  |S  |S  |S  |S  |   |   |
|Windows 8                           |   |S  |S  |S  |S  |   |   |
|Windows 7 SP1                       |   |   |S  |S  |S  |S  |   |
|Windows Vista SP2                   |   |   |S  |S  |S  |S  |S  |
|Windows XP SP3                      |   |   |   |   |   |   |S  |

 Con la versione dei driver Microsoft PHP elencata sono supportati Linux e Mac (solo 64-bit) versioni del sistema operativo seguenti:

|PHP per la versione del driver SQL Server&#8594;<br />&#8595;Sistema operativo|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|3.0<br />&nbsp;|2.0<br />&nbsp;|
|---|---|---|---|---|---|---|---|
|Ubuntu 17.10 (64 bit)               |S  |   |   |   |   |   |   |
|Ubuntu 16.04 (64 bit)               |S  |S  |S  |   |   |   |   |
|Ubuntu 15.10 (64 bit)               |   |S  |   |   |   |   |   |
|Ubuntu 15.04 (64 bit)               |   |   |S  |   |   |   |   |
|Debian 9 (64 bit)                   |S  |   |   |   |   |   |   |
|Debian 8 (64 bit)                   |S  |S  |   |   |   |   |   |
|Red Hat Enterprise Linux 7 (64 bit) |S  |S  |S  |   |   |   |   |
|Linux SUSE Enterprise 12 (64 bit)   |S  |   |   |   |   |   |   |
|macOS Sierra (64-bit)               |S  |S  |   |   |   |   |   |
|macOS El Capitan (64-bit)           |S  |S  |   |   |   |   |   |

## <a name="see-also"></a>Vedere anche  
[Note sulla versione](../../connect/php/release-notes-for-the-php-sql-driver.md)

[Risorse di supporto](../../connect/php/support-resources-for-the-php-sql-driver.md)

[System Requirements](../../connect/php/system-requirements-for-the-php-sql-driver.md)
