---
title: Pagina di configurazione (Gestione configurazione Master Data Services) del database | Documenti Microsoft
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.mds.configmanager.dbpg.f1
ms.assetid: dd72220e-a599-465d-8b84-9bb6a7433216
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 212031f92de47da41ad2716b81740c6a42487e59
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="database-configuration-page-master-data-services-configuration-manager"></a>Pagina Configurazione database (Gestione configurazione Master Data Services)
  Utilizzare la pagina **Configurazione database** per modificare le impostazioni di sistema di un database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Le impostazioni di sistema hanno effetto su tutte le applicazioni Web e i servizi Web associati al database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] selezionato. Affinché le impostazioni di sistema vengano abilitate e rese disponibili per la configurazione, è innanzitutto necessario selezionare o creare un database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
## <a name="current-database"></a>Database corrente  
 Selezionare un database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] esistente o creare un nuovo database per il quale modificare le impostazioni di sistema. Il nuovo database verrà selezionato dopo averlo creato.  
  
|Nome del controllo|Description|  
|------------------|-----------------|  
|**Istanza di SQL Server**|Consente di visualizzare il nome dell'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] selezionata. Non viene visualizzato alcun nome fino a quando non ci si connette a un'istanza e quindi si seleziona o crea un database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**Database Master Data Services**|Consente di visualizzare il nome del database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] selezionato. Non viene visualizzato alcun nome fino a quando non ci si connette a un'istanza e quindi si seleziona o crea un database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**Versione del database Master Data Services**|La versione dello schema del database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**Crea database**|Consente di aprire la procedura guidata **Crea database** dalla quale è possibile connettersi un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e creare un database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] per quell'istanza.|  
|**Selezione database**|Consente di aprire la finestra di dialogo **Connetti al database** dalla quale è possibile connettersi a un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e selezionare un database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**Aggiorna database**|Consente di aprire una procedura guidata da cui è possibile aggiornare un database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] specificato. Questo pulsante viene abilitato solo quando il database specificato richiede un'aggiornamento.|  
|**Ripara database**|Fare clic su questo pulsante per assicurarsi il database MDS sia installato correttamente. Può essere utile se si esegue il backup e si ripristina un database MDS in un'istanza [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] che non ha mai ospitato un database MDS.|  
  
## <a name="system-settings"></a>Impostazioni sistema  
 Modificare le impostazioni di sistema per tutte le applicazioni e tutti i servizi Web associati al database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] selezionato.  
  
 Queste impostazioni sono disponibili in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] e vengono archiviate nella tabella Impostazioni sistema (mdm.tblSystemSetting) del database. Per un elenco di tutte le impostazioni, vedere [Impostazioni di sistema &#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md).  
  
## <a name="see-also"></a>Vedere anche  
[Installazione di master Data Services e la configurazione](../master-data-services/master-data-services-installation-and-configuration.md) [Database requisiti &#40; Master Data Services &#41;](../master-data-services/install-windows/database-requirements-master-data-services.md)  
  
  
