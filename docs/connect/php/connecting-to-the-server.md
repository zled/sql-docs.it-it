---
title: Connessione al Server | Documenti Microsoft
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
ms.assetid: c251a239-e0bd-4f45-9207-b76651072dd0
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 818a71b8e0bc60168602e7fc0228c21319d08a21
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="connecting-to-the-server"></a>Connessione al server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Negli argomenti di questa sezione sono descritte le opzioni e le procedure per la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] con i [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  

I [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] possono connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] usando l'autenticazione di Windows o l'autenticazione di SQL Server. Per impostazione predefinita, i [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] tentano di connettersi al server usando l'autenticazione di Windows.  

## <a name="in-this-section"></a>Contenuto della sezione  

|Argomento|Description|  
|---------|---------------|  
|[Procedura: Connessione con l'autenticazione di Windows](../../connect/php/how-to-connect-using-windows-authentication.md)|Descrive come stabilire una connessione usando l'autenticazione di Windows.|  
|[Procedura: Connessione con l'autenticazione di SQL Server](../../connect/php/how-to-connect-using-sql-server-authentication.md)|Descrive come stabilire una connessione usando l'autenticazione di SQL Server.|  
|[Procedura: Connessione con l'autenticazione di Azure Active Directory](../../connect/php/azure-active-directory.md)|Viene descritto come impostare la modalità di autenticazione e connettersi usando l'identità di Azure Active Directory.|  
|[Procedura: Connessione a una porta specifica](../../connect/php/how-to-connect-on-a-specified-port.md)|Descrive come connettersi al server su una porta specifica.|  
|[Pool di connessioni](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md)|Fornisce informazioni sui pool di connessioni nel driver.|  
|[Procedura: Disabilitare più set di risultati attivi (MARS)](../../connect/php/how-to-disable-multiple-active-resultsets-mars.md)|Descrive come disabilitare la funzionalità MARS (Multiple Active Resultsets) quando si stabilisce una connessione.|  
|[Opzioni di connessione](../../connect/php/connection-options.md)|Elenca le opzioni che sono consentite nella matrice associativa contenente gli attributi di connessione.|  
|[Supporto per LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md)|Descrive il supporto dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] della funzione LocalDB aggiunta in [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)].|  
|[Supporto per il ripristino di emergenza a disponibilità elevato](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)|Viene descritta la modalità di configurazione l'applicazione per sfruttare il ripristino di emergenza a disponibilità elevata, le funzionalità aggiunte in [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)].|  
|[Connessione al database SQL di Microsoft Azure](../../connect/php/connecting-to-microsoft-azure-sql-database.md)|Viene illustrato come connettersi a un Database di SQL Azure.|  
|[Resilienza della connessione](../../connect/php/connection-resiliency.md)|Descrive la funzionalità di resilienza di connessione che consentano di ristabilire le connessioni interrotte.|  

## <a name="see-also"></a>Vedere anche  
[Guida di programmazione per i driver Microsoft per PHP per SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Applicazione di esempio &#40;Driver SQLSRV&#41;](../../connect/php/example-application-sqlsrv-driver.md)  
