---
title: Gestione connessione Excel | Microsoft Docs
ms.date: 04/02/2018
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: connection-manager
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.dts.designer.excelconnection.f1
helpviewer_keywords:
- files [Integration Services], connections
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: 667419f2-74fb-4b50-b963-9197d1368cda
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e273a5c9c41162a130769cf685096b4176752825
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="excel-connection-manager"></a>Gestione connessione Excel
  Una gestione connessione Excel consente la connessione di un pacchetto a un file di cartella di lavoro di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel. L'origine e la destinazione Excel disponibili in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] usano la gestione connessione Excel.  
 
> [!IMPORTANT]
> Per informazioni dettagliate sulla connessione ai file di Excel e sulle limitazioni e i problemi noti per il caricamento di dati da o a file di Excel, vedere [Caricare i dati da o in Excel con SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md).

 Quando si aggiunge una gestione connessione Excel a un pacchetto, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crea una gestione connessione che in fase di esecuzione verrà risolta in una connessione Excel, imposta le proprietà della gestione connessione, quindi la aggiunge alla raccolta **Connessioni** del pacchetto.  
  
 La proprietà **ConnectionManagerType** della gestione connessione viene impostata su **EXCEL**.  
  
## <a name="configure-the-excel-connection-manager"></a>Configurare la gestione connessione Excel  
 Per configurare la gestione connessione Excel, procedere nel modo seguente:  
  
-   Specificare il percorso del file della cartella di lavoro di Excel.  
  
-   Specificare la versione di Excel utilizzata per creare il file.  
  
-   Indicare se la prima riga nei fogli di lavoro o negli intervalli selezionati contiene i nomi delle colonne.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , vedere [Editor gestione connessione Excel](../../integration-services/connection-manager/excel-connection-manager-editor.md).  
  
 Per informazioni sulla configurazione di una gestione connessione a livello di programmazione, vedere l'articolo relativo a <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> e [Aggiunta di connessioni a livello di programmazione](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="excel-connection-manager-editor"></a>Editor gestione connessione Excel
  Usare la finestra di dialogo **Editor gestione connessione Excel[!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]per aggiungere una connessione a un file di cartella di lavoro di**  nuovo o esistente.  
  
### <a name="options"></a>Opzioni  
 **Percorso file di Excel**  
 Consente di digitare il percorso e il nome del file di una cartella di lavoro di Excel nuova o esistente.  
   
 **Sfoglia**  
 Usare la finestra di dialogo **Apri** per passare alla cartella che contiene il file di Excel o in cui creare il nuovo file.  
  
 **Versione di Excel**  
 Consente di specificare la versione di Microsoft Excel utilizzata per creare il file.  
  
 **Nomi di colonna nella prima riga**  
 Consente di specificare se la prima riga di dati del foglio di lavoro selezionato contiene nomi di colonna. Il valore predefinito di questa opzione è **True**.  
  
## <a name="related-tasks"></a>Related Tasks  
[Caricare i dati da o in Excel con SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md)  
[Origine Excel](../data-flow/excel-source.md)  
[Destinazione Excel](../data-flow/excel-destination.md)
