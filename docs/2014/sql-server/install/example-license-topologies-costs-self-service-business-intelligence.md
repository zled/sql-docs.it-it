---
title: Esempi di topologie di licenza e costi per SQL Server 2014 Self-Service di Business Intelligence | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 682b8711-407a-48d1-9807-415d4c24dad6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a7e08f483f1f56dcab49391190fd1c6edc11f6db
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2018
ms.locfileid: "49462057"
---
# <a name="example-license-topologies-and-costs--for-sql-server-2014-self-service-business-intelligence"></a>Esempi di topologie di licenza e dei costi di Business Intelligence in modalità self-service di SQL Server 2014
  In questo argomento vengono illustrate considerazioni dettagliate per la scelta di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Business Intelligence Edition o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Edition. Nell'argomento sono descritte diverse topologie locali di esempio di Microsoft Business Intelligence (BI) in modalità self-service. Gli esempi includono le versioni e le licenze che possono essere utilizzate per ottimizzare il bilanciamento tra costi e prestazioni. Le topologie, il numero di server e i costi di gestione delle licenze sono forniti **solo a livello esemplificativo**. Con Microsoft [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e Microsoft SharePoint 2013 sono state introdotte diverse modifiche nella gestione delle licenze che forniscono ulteriori opzioni per la gestione delle licenze di server, utenti e dispositivi. Le licenze di[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] supportano gli stessi scenari di Business Intelligence correlati.  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] è disponibile nella versione Business Intelligence e offre una gestione delle licenze per core per alcune versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   SharePoint 2013 ha semplificato la gestione delle licenze di SharePoint Server per gli scenari Extranet e Intranet e per le opzioni di SharePoint Online.  
  
 Prima di effettuare l'acquisto, visitare la sezione "Modalità di acquisto" per ogni prodotto e contattare il rivenditore locale o il rappresentante Microsoft per informazioni su specifici requisiti di licenza. Per informazioni sui piani e sui costi aggiornati della gestione delle licenze, vedere gli argomenti riportati di seguito:  
  
-   [Informazioni sulle licenze-SQL Server 2014](http://www.microsoft.com/licensing/about-licensing/sql2014.aspx)  
  
-   [Licenze di SharePoint 2013](http://office.microsoft.com/sharepoint/sharepoint-licensing-overview-collaboration-software-FX103789438.aspx).  
  
 **Contenuto dell'argomento:**  
  
-   [Componenti di SQL Server Business Intelligence](#bkmk_bi_components)  
  
-   [Riepilogo delle licenze di SQL Server 2014](#bkmk_sql_server_license)  
  
-   [Riepilogo delle licenze SharePoint 2013](#bkmk_sharepoint_license)  
  
-   [Topologia a 3 livelli con server PowerPivot separati](#bkmk_3tier_powerpivot)  
  
-   [Topologia a 3 livelli](#bkmk_3tier)  
  
-   [Topologia a 2 livelli](#bkmk_2tier)  
  
-   [Contenuto di riferimento e della community](#bkmk_reference)  
  
##  <a name="bkmk_bi_components"></a> Componenti di SQL Server Business Intelligence  
 In questo argomento vengono illustrate le tecnologie server di SharePoint e SQL Server. I costi e gli esempi non indicano in modo specifico i componenti di Microsoft Windows Server o Microsoft Office richiesti per una soluzione completa client e server. I componenti di SQL Server Business Intelligence riportati in questo argomento sono SQL Server Reporting Services in esecuzione in modalità SharePoint e PowerPivot per SharePoint. I componenti includono le seguenti funzionalità:  
  
-   Cartelle di lavoro interattive di PowerPivot nel browser.  
  
-   Report interattivi di [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] in SharePoint.  
  
-   Raccolta [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], pianificazione dell'aggiornamento dei dati, dashboard di gestione.  
  
-   Reporting Services in modalità SharePoint, incluso Avvisi dati.  
  
 Per altre informazioni, vedere la tabella delle funzionalità nella [installare le funzionalità di Business Intelligence di SQL Server con SharePoint &#40;PowerPivot e Reporting Services&#41;](../../../2014/sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md).  
  
## <a name="license-summary"></a>Riepilogo delle licenze  
 In questa sezione vengono riepilogati i requisiti per le licenze di SQL Server e SharePoint. Le informazioni costituiscono un riepilogo dettagliato e vengono considerati solo gli scenari utilizzati nei diagrammi di topologia e negli esempi di costi presenti in questo documento. Per ulteriori informazioni dettagliate sulle licenze, esaminare come indicato i collegamenti dei contenuti. I prezzi di esempio sono basati sui prezzi del programma Microsoft Open License (MOLP).  
  
 Una pratica comune è quella di utilizzare **Enterprise Edition** per i server che eseguono il motore di database di SQL Server e **Business Intelligence Edition** per i server che eseguono Reporting Services o PowerPivot per SharePoint. Tuttavia, il **numero di utenti** e il **numero di core server** della distribuzione influiscono sul costo e sulla decisione della versione da utilizzare.  
  
###  <a name="bkmk_sql_server_license"></a> Riepilogo delle licenze di SQL Server 2014  
  
-   SQL Server Enterprise Edition utilizza licenze basate su core. Le licenze basate su core vengono vendute in pacchetti a **due core** .  
  
-   SQL Server Business Intelligence Edition utilizza le licenze server e CAL (Client Access License).  
  
-   Le licenze CAL (Client Access License) sono basate su ogni utente o dispositivo connesso a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], indipendentemente dal numero di server a cui si connettono.  
  
-   La licenza core richiede che tutti i core nel server vengano coperti da una licenza. Per ogni processore fisico del server sono richieste almeno **quattro** licenze core.  
  
 Nella tabella seguente sono riepilogati i dettagli sulle licenze utilizzati per la stima dei costi di licenza e la progettazione della distribuzione. **NOTA:**  I prezzi indicati sono solo a scopo dimostrativo.  
  
|Edizioni di SQL Server|Licenza SQL Server + licenza CAL (Client Access License)|Licenza basata su core di SQL Server|  
|-------------------------|---------------------------------------------------------|-----------------------------------|  
|Enterprise|Non applicabile|**(Sì)** $6874 X (n. di core] X [core factor]|  
|Business Intelligence|**(Sì)** $8592 + $199 per CAL|Non applicabile|  
|Standard|**(Sì)**|**(Sì)**|  
  
 Per ulteriori informazioni sui prezzi di esempio delle licenze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vedere:  
  
-   [Gestione delle licenze per gli ambienti virtuali](http://www.microsoft.com/licensing/about-licensing/virtualization.aspx) (http://www.microsoft.com/licensing/about-licensing/virtualization.aspx).  
  
-   [SQL Server 2014 foglio dati delle licenze - Home Page di Microsoft](http://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf) (http://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf).  
  
-   [Edizioni di SQL server 2014 e licenze](http://www.microsoft.com/licensing/about-licensing/sql2014.aspx#tab=2)  
  
1.  **Presupposti per SQL Server e altre informazioni sulle licenze:**  
  
2.  Nei diagrammi riportati in questo argomento viene utilizzato SQL Server Enterprise Edition per i server di database in modo che sia disponibile il set completo delle funzionalità a disponibilità elevata, ad esempio i gruppi di disponibilità AlwaysOn. Per ulteriori informazioni, vedere [Features Supported by the Editions of SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
3.  I server in questo esempio sono tutti con 2 processori a 6 core Intel Xeon, pertanto è previsto un **core factor di SQL Server** di **1** per il calcolo dei costi delle licenze. Per altre informazioni sui core factor e sui costi delle licenze, vedere [tabella Core Factor di SQL Server](http://download.microsoft.com/download/9/B/F/9BF63163-D8F9-4339-90AA-EBC9AAFC49AD/SQL2012_CoreFactorTable_Mar2012.pdf) (http://download.microsoft.com/download/0/C/8/0C85665B-11EA-4FF5-B37C-8CC21CF95AC4/BizTalk%202013_CoreFactorTable_**3.19.2013**. v4.pdf).  
  
###  <a name="bkmk_sharepoint_license"></a> Riepilogo delle licenze SharePoint 2013  
 Nell'elenco seguente sono riepilogati i modelli di licenza utilizzati per la stima dei costi di licenza e la progettazione della distribuzione. I prezzi indicati sono solo a scopo dimostrativo.  
  
1.  Per ogni istanza di Microsoft SharePoint Server è necessaria una licenza SharePoint Server.  
  
2.  Per concedere in licenza SharePoint Enterprise, per ogni utente finale o dispositivo finale, acquistare una **licenza CAL Standard** di Microsoft SharePoint Server 2013 oltre a una **licenza CAL Enterprise**di Microsoft SharePoint Server 2013.  
  
3.  Le licenze CAL (Client Access License) di SharePoint vengono acquistate una per ogni utente o dispositivo che accede ai server SharePoint. Non è necessario acquistare le licenze CAL (Client Access License) per ogni server.  
  
 Ad esempio se l'ambiente fosse costituito da 2 istanze utilizzate da 100 utenti e i costi di quota fossero i seguenti:  
  
-   Licenza CAL Standard di Microsoft SharePoint Server 2013: **$107,99**  
  
-   Licenza CAL Enterprise di Microsoft SharePoint Server 2013: **$94,99**  
  
-   Licenza Microsoft SharePoint Server 2013: **$6.412,99**  
  
 Il costo sarebbe: **$33.123,98**  
  
-   Licenza CAL: ($107,99 +$94,99) X 100) =$20.298,00  
  
-   Licenza server: ($6.412,99 X 2) =$12.825,98  
  
 **Presupposti per SharePoint e ulteriori informazioni sulle licenze:**  
  
 Le distribuzioni di esempio sono costituite tutte da ambienti Intranet, quindi è richiesta la licenza CAL di SharePoint.  
  
-   [Elenco completo delle licenze SharePoint](http://technet.microsoft.com/library/jj819267.aspx#bkmk_FeaturesOnPremise) (http://technet.microsoft.com/library/jj819267.aspx#bkmk_FeaturesOnPremise).  
  
-   [Come acquistare SharePoint](http://sharepoint.microsoft.com/Pages/buy.aspx) (http://sharepoint.microsoft.com/Pages/buy.aspx).  
  
##  <a name="bkmk_3tier_powerpivot"></a> Topologia con separato a 3 livelli [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] server  
 In questo esempio viene illustrato che con un massimo di 800 utenti, è meno dispendioso utilizzare SQL Server Business Intelligence Edition per i server di applicazioni SharePoint e i server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint. Tuttavia, per 800 o più utenti, SQL Server Enterprise Edition è la soluzione meno costosa. La licenza core è indipendente dal numero di utenti e pertanto è previsto un punto di soglia dei costi quando si confrontano i costi delle licenze CAL (Client Access License) e core e il numero di utenti aumenta. Oltre il punto di soglia Enterprise Edition è la soluzione meno costosa. Per determinare la soglia dei costi, confrontare i costi in base al numero dei core da concedere in licenza con il numero di licenze CAL (Client Access License) dell'utente finale o del dispositivo finale da concedere in licenza.  
  
-   In questo esempio viene descritta una distribuzione Intranet e pertanto le licenze CAL (Client Access License) di SharePoint si applicano a SharePoint 2013.  
  
-   Il ruolo applicazione (2) include SQL Server Reporting Services installato in modalità SharePoint.  
  
     I database dell'applicazione del servizio SharePoint vengono eseguiti nei server del ruolo del database (4).  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint viene eseguito in server separati (3). [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint 2013 viene eseguito all'esterno della farm di SharePoint e può essere installato nei server che non includono un'installazione di SharePoint, migliorando le prestazioni.  
  
-   Il ruolo del database (4) utilizza SQL Server Enterprise in modo che la funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , i gruppi di disponibilità AlwaysOn, sia disponibile.  
  
 ![bi_license_3tiers_and_ASseparate](../../../2014/sql-server/install/media/bi-license-3tiers-and-asseparate.gif "bi_license_3tiers_and_ASseparate")  
  
 Con 100 utenti, SQL Server Business Intelligence Edition è la soluzione meno costosa.  
  
 ![bi_license_3tiers_and_ASseperate_calcs](../../../2014/sql-server/install/media/bi-license-3tiers-and-asseperate-calcs.gif "bi_license_3tiers_and_ASseperate_calcs")  
  
 Tuttavia con 300 utenti è meno costoso SQL Server Enterprise Edition.  
  
 ![bi_license_3tiers_and_ASseperate_calcs2](../../../2014/sql-server/install/media/bi-license-3tiers-and-asseperate-calcs2.gif "bi_license_3tiers_and_ASseperate_calcs2")  
  
##  <a name="bkmk_3tier"></a> Topologia a 3 livelli  
 In questo esempio viene illustrato che con un massimo 100, è meno costoso utilizzare SQL Server Business Intelligence Edition per i server che eseguono la funzionalità SQL Server Business Intelligence. Tuttavia se sono presenti 500 o più utenti, SQL Server Enterprise Edition è la soluzione meno costosa.  
  
-   In questo esempio viene descritta una distribuzione Intranet e pertanto le licenze CAL (Client Access License) di SharePoint si applicano a SharePoint 2013.  
  
-   Analysis Services in modalità PowerPivot (2) viene eseguito all'esterno della farm, mentre PowerPivot viene eseguito **negli stessi server fisici** nell'altro ruolo applicazione.  
  
-   Il ruolo del database (3) utilizza SQL Server Enterprise in modo che la funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , i gruppi di disponibilità AlwaysOn, sia disponibile.  
  
 ![bi_license_3tiers](../../../2014/sql-server/install/media/bi-license-3tiers.gif "bi_license_3tiers")  
  
 Con 100 utenti, SQL Server Business Intelligence Edition è la soluzione meno costosa.  
  
 ![bi_license_3tiers_calcs1](../../../2014/sql-server/install/media/bi-license-3tiers-calcs1.gif "bi_license_3tiers_calcs1")  
  
 Tuttavia con 500 utenti è meno costoso SQL Server Enterprise Edition.  
  
 ![bi_license_3tiers_calcs3](../../../2014/sql-server/install/media/bi-license-3tiers-calcs3.gif "bi_license_3tiers_calcs3")  
  
##  <a name="bkmk_2tier"></a> Topologia a 2 livelli  
 Con solo 2 livelli, SQL Server Enterprise Edition è utilizzato in modo che la funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dei gruppi di disponibilità AlwaysOn è disponibile per il motore di database di SQL Server. Di conseguenza non ci sono differenze di costi tra le due edizioni di SQL Server. L'unica variabile è il prezzo della licenza CAL di SharePoint basato sul numero di utenti.  
  
-   In questo esempio viene descritta una distribuzione Intranet e pertanto le licenze CAL (Client Access License) di SharePoint si applicano a SharePoint 2013.  
  
-   Analysis Services in modalità PowerPivot viene eseguito all'esterno della farm, mentre PowerPivot viene eseguito negli stessi server (2) fisici del motore di database di SQL Server.  
  
 ![bi_license_2tiers](../../../2014/sql-server/install/media/bi-license-2tiers.gif "bi_license_2tiers")  
  
 ![bi_license_2tiers_calcs1](../../../2014/sql-server/install/media/bi-license-2tiers-calcs1.gif "bi_license_2tiers_calcs1")  
  
##  <a name="bkmk_reference"></a> Contenuto di riferimento e della community  
  
### <a name="license-tools"></a>Strumenti per le licenze  
  
-   [Licenza Microsoft Advisor](http://mla.microsoft.com/default.aspx) (http://mla.microsoft.com/default.aspx).  
  
-   [Licenza di accesso client (CAL) dello strumento di decisione](http://www.microsoft.com/licensing/CalTool/) (http://www.microsoft.com/licensing/CalTool/).  
  
-   [Hub di Microsoft Business: Modalità di acquisto](http://www.microsoftbusinesshub.com/How_To_Buy#) (http://www.microsoftbusinesshub.com/How_To_Buy#).  
  
### <a name="microsoft-license-information"></a>Informazioni sulle licenze Microsoft  
  
-   [Informazioni sulle licenze: Licenze di accesso Client e le licenze di gestione](http://www.microsoft.com/licensing/about-licensing/client-access-license.aspx) (http://www.microsoft.com/licensing/about-licensing/client-access-license.aspx).  
  
-   [Informazioni sulle licenze: Il prodotto ricerca delle licenze](http://www.microsoftvolumelicensing.com/default.aspx) (http://www.microsoftvolumelicensing.com/default.aspx).  
  
-   [Contratti multilicenza: prezzi e modalità di acquisto](http://www.microsoft.com/licensing/how-to-buy/how-to-buy.aspx) (http://www.microsoft.com/licensing/how-to-buy/how-to-buy.aspx).  
  
### <a name="community-content"></a>Contenuto della community  
  
-   [Licenze di SQL Server 2014 Developer Edition](http://sqlmag.com/sql-server-2014/sql-server-2014-developer-edition-licensing).  
  
-   [Modifiche di gestione delle licenze di SQL Server 2014](http://www.brentozar.com/archive/2014/04/sql-server-2014-licensing-changes)(http://www.brentozar.com/archive/2014/04/sql-server-2014-licensing-changes).  
  
-   [Modifiche alle licenze per SQL Server 2014](https://www.directionsonmicrosoft.com/sites/default/files/PDFs/Licensing_Changes_for_SQL_Server_2014.pdf)(https://www.directionsonmicrosoft.com/sites/default/files/PDFs/Licensing_Changes_for_SQL_Server_2014.pdf).  
  
-   [Stima dei costi di licenza di SharePoint 2013](http://www.degdigital.com/blog/sharepoint-2013-licensing-for-dummies/) (http://www.degdigital.com/blog/sharepoint-2013-licensing-for-dummies/).  
  
-   [Community per clienti contratti multilicenza](http://www.microsoft.com/licensing/existing-customers/community.aspx) (http://www.microsoft.com/licensing/existing-customers/community.aspx).  
  
  
