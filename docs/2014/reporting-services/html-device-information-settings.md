---
title: Impostazioni relative alle informazioni sul dispositivo HTML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- HTML [Reporting Services], rendering
- device information settings [Reporting Services], HTML rendering
ms.assetid: f505f478-dd6d-444a-957c-34f7cfb98911
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a415a5f735e731efe3f3ae8b282f8ce2a1ad2eba
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48155843"
---
# <a name="html-device-information-settings"></a>Impostazioni relative alle informazioni sul dispositivo HTML
  Nella tabella seguente si elencano le impostazioni relative alle informazioni sul dispositivo per il rendering nel formato HTML.  
  
> [!IMPORTANT]  
>  Le impostazioni relative alle informazioni sui dispositivi elencate nella tabella di seguito con un **(\*)** sono deprecate, pertanto è consigliabile non usarle nelle nuove applicazioni. Per altre informazioni, vedere [Deprecated Features di SQL Server Reporting Services in SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md).  
  
|Impostazione|valore|  
|-------------|-----------|  
|`AccessibleTablix`|Indica se eseguire il rendering con i metadati di accessibilità aggiuntivi per l'utilizzo con le utilità per la lettura dello schermo. Questo parametro è applicabile solo ai report che contengono strutture di tabelle o matrici semplici con raggruppamento semplice. Il valore predefinito è `false`. I metadati di accessibilità aggiuntivi fanno in modo che il report visualizzabile sia conforme agli standard tecnici riportati di seguito definiti nella sezione 1194.22 relativa alle informazioni e alle applicazioni Intranet e Internet basate sul web nel documento Electronic and Information Technology Accessibility Standards (Sezione 508):<br /><br /> (g) Le intestazioni di riga e colonna devono essere identificate per le tabelle di dati.<br /><br /> (h) Il markup deve essere usato per associare celle di dati e celle di intestazione per le tabelle di dati che dispongono di due o più livelli logici di intestazioni di riga o colonna.<br /><br /> (i) I frame devono disporre di testo che ne faciliti l'identificazione e la navigazione.<br /><br /> Questo parametro è supportato in [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[SPS2010](../includes/sps2010-md.md)], ma non in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[SPS2007](../includes/sps2007-md.md)].|  
|**ActionScript(\*)**|Specifica il nome della funzione JavaScript da usare quando si verifica un evento relativo alla funzione, ad esempio la scelta di un segnalibro o un drill-through. Se viene specificato questo parametro, un evento relativo all'azione genererà la funzione JavaScript anziché un postback al server.|  
|**BookmarkID**|ID del segnalibro a cui passare nel report.|  
|**DocMap**|Indica se mostrare o nascondere la mappa documento del report. Il valore predefinito di questo parametro è `true`.|  
|`ExpandContent`|Indica se il report deve essere incluso in una struttura di tabella per limitarne la dimensione orizzontale.|  
|**FindString**|Testo da cercare nel report. Il valore predefinito di questo parametro è una stringa vuota.|  
|**GetImage (\*)**|Ottiene una determinata icona per l'interfaccia utente del visualizzatore HTML.|  
|`HTMLFragment`|Indica se viene creato un frammento HTML al posto di un documento HTML completo. In un frammento HTML il contenuto del report viene inserito in un elemento TABLE e gli elementi HTML e BODY vengono omessi. Il valore predefinito è `false`. Il rendering tramite SOAP con la `HTMLFragment` impostata su `true` creati URL contenenti informazioni sulla sessione che può essere utilizzati per richiedere correttamente le immagini. Le immagini devono essere risorse caricate nel database del server di report.|  
|`ImageConsolidation`|Indica se consolidare il grafico, la mappa, il misuratore e le immagini dell'indicatore di cui è stato eseguito il rendering in un'unica grande immagine. Il consolidamento di immagini consente di migliorare le prestazioni del report nel browser del client quando il report contiene molti elementi di visualizzazione dei dati. Il valore predefinito è `true` per i browser più moderni.|  
|**JavaScript**|Indica se JavaScript è supportato nel report visualizzabile. Il valore predefinito è `true`.|  
|`LinkTarget`|Destinazione dei collegamenti ipertestuali nel report. È possibile assegnare una finestra o frame fornendo il nome della finestra, ad esempio `LinkTarget` = *window_name*, o è possibile scegliere come destinazione una finestra nuova usando `LinkTarget`= blank. Altri nomi di destinazione validi includono _self, _parent e _top.|  
|**OnlyVisibleStyles(\*)**|Indica che vengono generati solo gli stili condivisi per la pagina di cui è stato attualmente eseguito il rendering.|  
|`OutlookCompat`|Indica se eseguire il rendering con metadati aggiuntivi che comportano una visualizzazione migliore del report in Outlook, Per altri utenti, il valore predefinito è `false`.|  
|**Parametri**|Indica se mostrare o nascondere l'area dei parametri della barra degli strumenti. Se si imposta questo parametro su un valore di `true`, viene visualizzata l'area dei parametri della barra degli strumenti. Il valore predefinito di questo parametro è `true`.|  
|`PrefixId`|Quando abbinata `HTMLFragment`, aggiunge il prefisso specificato a tutti `ID` attributi nel frammento HTML creato.|  
|**ReplacementRoot(\*)**|Stringa da anteporre a tutti i collegamenti di drill-through, attivazione/disattivazione e segnalibro nel report quando viene eseguito il rendering al di fuori del controllo ReportViewer. Ad esempio, viene usata per il reindirizzamento della selezione di un utente a una pagina personalizzata.|  
|**ResourceStreamRoot(\*)**|Stringa da anteporre all'URL per tutte le risorse dell'immagine, ad esempio le immagini per l'attivazione o la disattivazione oppure l'ordinamento.|  
|**Sezione**|Numero di pagina del report di cui eseguire il rendering. Un valore `0` indica che viene eseguito il rendering di tutte le sezioni del report. Il valore predefinito è `1`.|  
|**StreamRoot (\*)**|Percorso usato per anteporre un prefisso al valore dell'attributo **src** dell'elemento IMG nel report HTML restituito dal server di report. Per impostazione predefinita, il percorso viene fornito dal server di report. È possibile usare questa impostazione per specificare un percorso radice per le immagini in un report, ad esempio **http://\<nomeserver>/risorse/immaginiazienda**.|  
|**StyleStream**|Indica se stili e script vengono creati come flusso separato anziché nel documento. Il valore predefinito è `false`.|  
|`Toolbar`|Indica se mostrare o nascondere la barra degli strumenti. Il valore predefinito di questo parametro è `true`. Se il valore di questo parametro è `false`, tutte le opzioni rimanenti (ad eccezione della mappa documento) vengono ignorate. Se si omette questo parametro, la barra degli strumenti viene visualizzata automaticamente nei formati di rendering che la supportano.<br /><br /> Il rendering della barra degli strumenti del Visualizzatore report viene eseguito quando si usano l'accesso con URL per il rendering di un report, ma non quando si usano l'API SOAP. Tuttavia, il `Toolbar` le informazioni sul dispositivo impostazione influisce sulle modalità che il report viene visualizzato quando si utilizza SOAP `Render` (metodo). Se il valore di questo parametro è `true` quando si usano SOAP per eseguire il rendering in formato HTML, viene eseguito il rendering solo della prima sezione del report. Se il valore è `false`, viene eseguito il rendering dell'intero report HTML come singola pagina HTML.|  
|`UserAgent`|Il `user-agent` stringa del browser che effettua la richiesta, situata nella richiesta HTTP.|  
|**Zoom (\*)**|Valore di zoom del report come percentuale di un valore intero o come costante stringa. I valori stringa standard comprendono `Page Width` e `Whole Page`. Questo parametro viene ignorato dalle versioni di [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer precedenti a Internet Explorer 5.0 e da tutti i browser non [!INCLUDE[msCoName](../includes/msconame-md.md)]. Il valore predefinito di questo parametro è `100`.|  
|**DataVisualizationFitSizing**|Indica il comportamento di adattamento della visualizzazione dei dati all'interno di una tablix. Sono inclusi grafici, misuratori e mappe.<br /><br /> I valori possibili sono **Approssimato** ed **Esatto**.<br /><br /> Il valore predefinito è **Approssimato**. Se l'impostazione viene rimossa dal file **rsreportserver.config** il comportamento predefinito è **Esatto**.<br /><br /> L'abilitazione del ridimensionamento **Esatto** può avere impatto sulle prestazioni perché l'elaborazione per determinare la dimensione esatta potrebbe impiegare più molto tempo di un adattamento approssimativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Il passaggio di impostazioni informazioni dispositivo a estensioni per il Rendering](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personalizzare i parametri di estensione per il rendering in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Riferimento tecnico &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
