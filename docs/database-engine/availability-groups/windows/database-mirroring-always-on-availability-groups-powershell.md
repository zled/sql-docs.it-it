---
title: "Mirroring del database - Gruppi di disponibilità AlwaysOn - PowerShell | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], endpoint
ms.assetid: 6197bbe7-67d4-446d-ba5f-cabfa5df77f1
caps.latest.revision: "9"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7de2f3f143cd5bc800493034f2abf7aed925b7a3
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="database-mirroring---always-on-availability-groups--powershell"></a>Mirroring del database - Gruppi di disponibilità AlwaysOn - PowerShell
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  In questo argomento viene illustrato come creare un endpoint del mirroring del database che verrà utilizzato da [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite PowerShell.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  [Sicurezza](#Security)  
  
-   **Per creare un endpoint del mirroring del database tramite:**  [PowerShell](#PowerShellProcedure)  
  
## <a name="before-you-begin"></a>Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
> [!IMPORTANT]  
>  L'algoritmo RC4 è deprecato. [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)] È consigliabile utilizzare AES.  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È richiesta l'autorizzazione CREATE ENDPOINT o l'appartenenza al ruolo predefinito del server sysadmin. Per altre informazioni, vedere [GRANT - autorizzazioni per endpoint &#40;Transact-SQL&#41;](../../../t-sql/statements/grant-endpoint-permissions-transact-sql.md).  
  
##  <a name="PowerShellProcedure"></a> Utilizzo di PowerShell  
 **Per creare un endpoint del mirroring del database**  
  
1.  Spostarsi nella directory (**cd**) dell'istanza del server per cui si vuole creare l'endpoint del mirroring del database.  
  
2.  Usare il cmdlet **New-SqlHadrEndpoint** per creare l'endpoint e quindi usare **Set-SqlHadrEndpoint** per avviare l'endpoint.  
  
###  <a name="PShellExample"></a> Esempio (PowerShell)  
 I comandi di PowerShell seguenti creano un endpoint del mirroring del database in un'istanza di SQL Server (*Machine*\\*Instance*). L'endpoint utilizza la porta 5022.  
  
> [!IMPORTANT]  
>  Questo esempio funziona solo su un'istanza del server che attualmente non dispone di un endpoint del mirroring del database.  
  
```  
# Create the endpoint.  
$endpoint = New-SqlHadrEndpoint MyMirroringEndpoint -Port 5022 -Path SQLSERVER:\SQL\Machine\Instance  
  
# Start the endpoint  
Set-SqlHadrEndpoint -InputObject $endpoint -State "Started"  
  
```  
  
##  <a name="RelatedTasks"></a> Attività correlate  
 **Per configurare un endpoint del mirroring del database**  
  
-   [Creare un endpoint del mirroring del database per l'autenticazione Windows &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Utilizzare certificati per un endpoint del mirroring del database &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [Impostazione dell'endpoint del mirroring del database per l'utilizzo di certificati per le connessioni in uscita &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [Impostazione dell'endpoint del mirroring del database per l'utilizzo di certificati per le connessioni in ingresso &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [Specificare un indirizzo di rete del server &#40;Mirroring del database&#41;](../../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md)  
  
-   [Specificare l'URL dell'endpoint quando si aggiunge o si modifica una replica di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 **Per visualizzare informazioni sull'endpoint del mirroring del database**  
  
-   [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Creare un gruppo di disponibilità &#40;Transact-SQL&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)   
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
