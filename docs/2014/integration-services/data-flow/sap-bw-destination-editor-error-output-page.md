---
title: Editor destinazione SAP BW (pagina Output degli errori) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: a543d811-0bd2-4890-a0d3-f5fdcd4524b8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fad8a8e38db162a12b0d3c39afb44800c4851524
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48191711"
---
# <a name="sap-bw-destination-editor-error-output-page"></a>Editor destinazione SAP BW (pagina Output degli errori)
  Usare la pagina **Output degli errori** dell'**Editor destinazione SAP BW** per specificare le opzioni di gestione degli errori.  
  
 Per altre informazioni sulla destinazione SAP BW di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, vedere [Destinazione SAP BW](sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  La documentazione per Microsoft Connector 1.1 for SAP BW presuppone la conoscenza dell'ambiente SAP Netweaver BW. Per ulteriori informazioni su SAP Netweaver BW o per informazioni su come configurare oggetti e processi di SAP Netweaver BW, vedere la documentazione SAP.  
  
 **Per aprire la pagina Output errori**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il pacchetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene la destinazione SAP BW.  
  
2.  Nella scheda **Flusso dati** fare doppio clic sulla destinazione SAP BW.  
  
3.  Nell' **Editor destinazione SAP BW**fare clic su **Output degli errori** per aprire la pagina **Output degli errori** dell'editor.  
  
## <a name="options"></a>Opzioni  
  
> [!NOTE]  
>  Se non si conoscono tutti i valori richiesti per configurare la destinazione, può essere necessario consultare l'amministratore SAP.  
  
 **Input o output**  
 Consente di visualizzare il nome dell'input.  
  
 **Colonna**  
 Questa opzione non viene utilizzata.  
  
 **Errore**  
 Specificare quale azione dovrà essere eseguita dalla destinazione in caso di errore: ignorare l'errore, reindirizzare la riga o interrompere il componente.  
  
 **Troncamento**  
 Questa opzione non viene utilizzata.  
  
 **Descrizione**  
 Consente di visualizzare la descrizione dell'operazione.  
  
 **Imposta questo valore nelle celle selezionate**  
 Specificare l'azione che dovrà essere eseguita dalla destinazione su tutte le celle selezionate in caso di errore o troncamento: ignorare l'errore, reindirizzare la riga o interrompere il componente.  
  
 **Applica**  
 Consente di applicare l'opzione di gestione degli errori alle celle selezionate.  
  
## <a name="see-also"></a>Vedere anche  
 [Editor destinazione SAP BW &#40;pagina Gestione connessione&#41;](sap-bw-destination-editor-connection-manager-page.md)   
 [Editor destinazione SAP BW &#40;pagina mapping&#41;](sap-bw-destination-editor-mappings-page.md)   
 [Editor destinazione SAP BW &#40;pagina Avanzate&#41;](sap-bw-destination-editor-advanced-page.md)   
 [Guida (F1) di Microsoft Connector 1.1 for SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
