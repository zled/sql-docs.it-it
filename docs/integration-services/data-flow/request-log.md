---
title: Log richieste | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 165d3833-0493-490c-9f63-8a134a7fafb8
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 754f96b5e43b26d59bb1e42be6dd2af008c28dd2
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="request-log"></a>Log richieste
  Usare la finestra di dialogo **Log richieste** per visualizzare gli eventi registrati durante la richiesta fatta al sistema SAP Netweaver BW per i dati di esempio. Queste informazioni possono essere utili se è necessario risolvere i problemi relativi alla configurazione dell'origine SAP BW.  
  
 Per altre informazioni sul componente di origine SAP BW di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, vedere [Origine SAP BW](../../integration-services/data-flow/sap-bw-source.md).  
  
> [!IMPORTANT]  
>  La documentazione per Microsoft Connector 1.1 for SAP BW presuppone la conoscenza dell'ambiente SAP Netweaver BW. Per ulteriori informazioni su SAP Netweaver BW o per informazioni su come configurare oggetti e processi di SAP Netweaver BW, vedere la documentazione SAP.  
  
> [!IMPORTANT]  
>  L'estrazione di dati da SAP Netweaver BW richiede licenze SAP aggiuntive. Contattare SAP per verificare questi requisiti.  
  
 **Per aprire la finestra di dialogo Log richieste**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il pacchetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene l'origine SAP BW.  
  
2.  Nella scheda **Flusso di dati** fare doppio clic sull'origine SAP BW.  
  
3.  Nell' **Editor origine SAP BW**fare clic su **Gestione connessione** per aprire la pagina **Gestione connessione** dell'editor.  
  
4.  Dopo aver configurato l'origine SAP BW, fare clic su **Anteprima** per visualizzare gli eventi in anteprima nella finestra di dialogo **Log richieste** .  
  
    > [!NOTE]  
    >  Quando si fa clic su **Anteprima** , inoltre, viene aperta la finestra di dialogo **Anteprima** . Per altre informazioni su questa finestra di dialogo, vedere [Anteprima](../../integration-services/data-flow/preview.md).  
  
## <a name="options"></a>Opzioni  
 **Time**  
 Visualizza l'ora di registrazione dell'evento.  
  
 **Tipo**  
 Visualizza il tipo dell'evento registrato. Nella tabella seguente sono elencati i tipi di eventi possibili.  
  
|Valore|Description|  
|-----------|-----------------|  
|S|Messaggio di operazione completata.|  
|E|Messaggio di errore|  
|W|Messaggio di avviso.|  
|I|Messaggio informativo.|  
|A|L'operazione è stata interrotta.|  
  
 **Message**  
 Visualizza il testo del messaggio associato all'evento registrato.  
  
## <a name="see-also"></a>Vedere anche  
 [Editor origine SAP BW &#40;pagina Gestione connessione&#41;](../../integration-services/data-flow/sap-bw-source-editor-connection-manager-page.md)   
 [Guida (F1) di Microsoft Connector for SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  

