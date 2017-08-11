---
title: Accesso con URL (SSRS) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- URL access [Reporting Services]
- links [Reporting Services], URL access
- URL access [Reporting Services], about URL access
- parameters [Reporting Services], URL access
- report servers [Reporting Services], URL access
- hyperlinks [Reporting Services]
ms.assetid: 52c3f2a3-3d6d-4fee-9c46-83f366919398
caps.latest.revision: 43
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f91b97d1877e365813f3aa2445fabea1a263ab2b
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="url-access-ssrs"></a>Accesso con URL (SSRS)
  L'accesso tramite URL al server di report in SQL Server Reporting Services (SSRS) consente di inviare comandi a un server di report tramite una richiesta URL. Ad esempio, è possibile personalizzare il rendering di un report in un server di report in modalità nativa o in una raccolta di SharePoint. È possibile che il report sia stato visualizzato utilizzando un set specifico di valori dei parametri del report o che sia stata visualizzata una particolare pagina di interesse nel report. È possibile incapsulare queste informazioni nell'URL utilizzando i parametri di accesso tramite URL predefiniti. È possibile personalizzare ulteriormente il modo in cui il server di report elabora il report incorporando parametri relativi ai formati di rendering o all'aspetto del visualizzatore di report. Si può, quindi, incollare direttamente questo URL in un messaggio di posta elettronica o in una pagina Web per permettere ad altri di accedere al report con le stesse modalità tramite il browser.  
  
 Le altre azioni che si possono eseguire attraverso l'accesso tramite URL sono:  
  
-   Inviare comandi al visualizzatore HTML, ad esempio per l'impostazione dell'aspetto  
  
-   Elencare gli elementi figlio di una cartella del catalogo  
  
-   Recuperare la definizione XML di un elemento del catalogo  
  
-   Eseguire il rendering di uno snapshot della cronologia di un report specifico  
  
-   Gestire le sessioni di report  
  
 Per l'elenco completo dei comandi e delle impostazioni disponibili attraverso l'accesso tramite URL, vedere [Riferimento ai parametri di accesso con URL](../reporting-services/url-access-parameter-reference.md).  
  
## <a name="url-access-concepts"></a>Concetti di base relativi all'accesso tramite URL  
 Le richieste URL al server di report contengono parametri elaborati dal server di report. Il modo in cui le richieste URL vengono gestite dal server di report dipende dai parametri, dai prefissi di parametro e dai tipi di elementi inclusi nell'URL. Gli URL del server di report sono conformi alle linee guida per la formattazione degli URL proposte dalla bozza di standard congiunta del World Wide Web Consortium W3C/IETF. La funzionalità URL di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] è compatibile con la maggior parte dei browser Internet o delle applicazioni che supportano il reindirizzamento URL standard.  
  
### <a name="url-access-syntax"></a>Sintassi per l'accesso con URL  
 Le richieste URL possono contenere più parametri elencati in qualsiasi ordine. I parametri sono separati da una e commerciale (&), mentre le coppie nome/valore sono separate da un segno di uguale (=).  
  
```  
  
rswebserviceurl  
?  
reportpath  
      [&prefix:param=value]...n]  
  
```  
  
### <a name="syntax-description"></a>Descrizione della sintassi  
 *rswebserviceurl*  
 URL del servizio Web del server di report. Per la modalità nativa, è l'URL del servizio Web dell'istanza del server di report configurata nella Gestione configurazione Reporting Services (vedere [Configurare gli URL del server di report &#40;Gestione configurazione SSRS&#41;](../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)). Esempio:  
  
```  
http://myrshost/reportserver  
https://machine.adventure-works.com/reportserver_MYNAMEDINSTANCE  
```  
  
 Per la modalità integrata SharePoint, è l'URL del proxy [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] a un sito di SharePoint integrato con [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Esempio:  
  
```  
http://myspsite/subsite/_vti_bin/reportserver  
```  
  
> [!TIP]  
>  È importante che nell'URL sia inclusa la sintassi proxy `_vti_bin` per indirizzare la richiesta tramite SharePoint e il proxy HTTP di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Tramite il proxy viene aggiunto del contesto alla richiesta HTTP. Questo contesto è necessario per garantire l'esecuzione corretta del report per i server di report in modalità SharePoint.  
  
 *pathinfo*  
 Il nome di percorso relativo dell'elemento nel database del server di report in modalità nativa o l'URL completo dell'elemento in un catalogo di SharePoint.  
  
 Il percorso dell'elemento del catalogo. Per la modalità nativa, si tratta del percorso relativo dell'elemento nel database del server di report, che inizia con una barra (**/**). Esempio:  
  
```  
/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2  
```  
  
 Per la modalità integrata SharePoint, si tratta dell'URL completo dell'elemento nella raccolta di SharePoint, inclusa l'estensione dell'elemento. Esempio:  
  
```  
http://myspsite/subsite/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2.rdl  
```  
  
 **&**  
 Carattere utilizzato per separare le coppie di nome e valore dei parametri di accesso tramite URL.  
  
 **prefix**  
 Facoltativa. Un prefisso per il parametro di accesso tramite URL (ad esempio, `rs:` o `rc:`) per l'accesso a un processo specifico in esecuzione nel server di report.  
  
> [!NOTE]  
>  Se per un parametro di accesso tramite URL non viene incluso un prefisso, il parametro viene elaborato dal server di report come parametro del report. Nei parametri del report non si utilizzano prefissi dei parametri e non esistono distinzioni tra maiuscole e minuscole.  
  
 **param**  
 Nome del parametro.  
  
 *Valore*  
 Testo dell'URL che corrisponde al valore del parametro utilizzato.  
  
 **Nota:** per un elenco dei parametri di accesso tramite URL disponibili, vedere [Riferimento ai parametri di accesso con URL](../reporting-services/url-access-parameter-reference.md). Per esempi di passaggi di parametri di report nell'URL, vedere [Passare un parametro del report in un URL](../reporting-services/pass-a-report-parameter-within-a-url.md).  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Descrizioni delle attività|Collegamenti|  
|-----------------------|-----------|  
|Accedere a elementi del server di report, quali report, origini dati condivise e risorse.|[Elementi di Server di Report di Access con accesso tramite URL](../reporting-services/access-report-server-items-using-url-access.md)|  
|Passare i parametri di report a un report.|[Passare un parametro di Report all'interno di un URL](../reporting-services/pass-a-report-parameter-within-a-url.md)|  
|Impostare le impostazioni locali dei parametri del report nella stringa dell'accesso tramite URL che definisce le interpretazioni delle impostazioni locali di date, valute e così via.|[Impostare la lingua per i parametri del Report in un URL](../reporting-services/set-the-language-for-report-parameters-in-a-url.md)|  
|Inviare le impostazioni specifiche dell'estensione di rendering che personalizzano l'esecuzione del rendering del report.|[Specificare impostazioni informazioni dispositivo in un URL](../reporting-services/specify-device-information-settings-in-a-url.md)|  
|Esportare un report direttamente in un formato di file senza visualizzarlo nel browser.|[Esportare un Report con accesso tramite URL](../reporting-services/export-a-report-using-url-access.md)|  
|Aprire un report e passare rapidamente alla posizione di una stringa.|[Ricerca di un Report con accesso tramite URL](../reporting-services/search-a-report-using-url-access.md)|  
|Eseguire il rendering di uno snapshot della cronologia di un report specifico.|[Eseguire il rendering di uno Snapshot della cronologia del Report con accesso tramite URL](../reporting-services/render-a-report-history-snapshot-using-url-access.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Passare un parametro di Report all'interno di un URL](../reporting-services/pass-a-report-parameter-within-a-url.md)   
 [Riferimento ai parametri URL accesso](../reporting-services/url-access-parameter-reference.md)   
 [Integrazione di Reporting Services con accesso tramite URL](../reporting-services/application-integration/integrating-reporting-services-using-url-access.md)   
 [La ricerca, visualizzazione e gestione di report &#40; Generatore report e SSRS &#41;](../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
