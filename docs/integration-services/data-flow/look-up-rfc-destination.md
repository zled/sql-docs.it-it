---
title: Cerca destinazione RFC | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db9404d8-4c42-45e5-a100-c7a84b056109
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3c9db6a056a69d502b4a93b9575cb565da798adf
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="look-up-rfc-destination"></a>Cerca destinazione RFC
  Usare la finestra di dialogo **Cerca destinazione RFC** per cercare una destinazione RFC definita nel sistema SAP Netweaver BW. Quando viene visualizzato l'elenco delle destinazioni RFC disponibili, selezionare la destinazione desiderata e le opzioni associate verranno compilate con i valori richiesti dal componente.  
  
 Sia l'origine che la destinazione SAP BW usano la finestra di dialogo **Cerca destinazione RFC** . Per altre informazioni su questi componenti di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, vedere [Origine SAP BW](../../integration-services/data-flow/sap-bw-source.md) e [Destinazione SAP BW](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  La documentazione per Microsoft Connector 1.1 for SAP BW presuppone la conoscenza dell'ambiente SAP Netweaver BW. Per ulteriori informazioni su SAP Netweaver BW o per informazioni su come configurare oggetti e processi di SAP Netweaver BW, vedere la documentazione SAP.  
  
 **Per aprire la finestra di dialogo Cerca destinazione RFC**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il pacchetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene l'origine e la destinazione SAP BW.  
  
2.  Nella scheda **Flusso di dati** fare doppio clic sull'origine o sulla destinazione SAP BW.  
  
3.  Nell' **Editor origine SAP BW** o nell' **Editor destinazione SAP BW**fare clic su **Gestione connessione** per aprire la pagina **Gestione connessione** dell'editor.  
  
4.  Nella pagina **Gestione connessione** , nella casella di gruppo **Destinazione RFC** fare clic su **Ricerca** per visualizzare la finestra di dialogo **Cerca destinazione RFC** .  
  
     Nell' **Editor origine SAP BW**, la casella di gruppo **Destinazione RFC** viene visualizzata solo se il valore di **Modalità di esecuzione** è **P - Attivazione catena processi** o **W - Attesa notifica**.  
  
## <a name="options"></a>Opzioni  
 **Destinazione**  
 Visualizzare il nome della destinazione RFC definito nel sistema SAP Netweaver BW.  
  
 **Host gateway**  
 Visualizzare il nome del server o l'indirizzo IP dell'host gateway. In genere, il nome o l'indirizzo IP è uguale a quello del server applicazioni SAP.  
  
 **Servizio gateway**  
 Visualizzare il nome del servizio del gateway nel formato **sapgwNN**, dove **NN** è il numero del sistema.  
  
 **ID programma**  
 Visualizzare l'ID programma associato alla destinazione RFC.  
  
## <a name="see-also"></a>Vedere anche  
 [Editor origine SAP BW &#40; Pagina Gestione connessione &#41;](../../integration-services/data-flow/sap-bw-source-editor-connection-manager-page.md)   
 [Editor destinazione SAP BW &#40; Pagina Gestione connessione &#41;](../../integration-services/data-flow/sap-bw-destination-editor-connection-manager-page.md)   
 [Guida (F1) di Microsoft Connector for SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  
