---
title: Gestione connessione Excel | Documenti Microsoft
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- files [Integration Services], connections
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: 667419f2-74fb-4b50-b963-9197d1368cda
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c817f552e527f0d01ec7638eb5f605da572cf9c0
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="excel-connection-manager"></a>Gestione connessione Excel
  Una gestione connessione Excel consente la connessione di un pacchetto a un file di cartella di lavoro di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel esistente. L'origine e la destinazione Excel disponibili in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] usano la gestione connessione Excel.  
  
 Quando si aggiunge una gestione connessione Excel a un pacchetto, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crea una gestione connessione che in fase di esecuzione verrà risolta in una connessione Excel, imposta le proprietà della gestione connessione, quindi la aggiunge alla raccolta **Connessioni** del pacchetto.  
  
 La proprietà **ConnectionManagerType** della gestione connessione viene impostata su **EXCEL**.  
  
## <a name="configuration-of-the-excel-connection-manager"></a>Configurazione della gestione connessione Excel  
 Per configurare la gestione connessione Excel, procedere nel modo seguente:  
  
-   Specificare il percorso del file della cartella di lavoro di Excel.  
  
    > [!NOTE]  
    >  Non è possibile connettersi a un file di Excel protetto da password.  
  
-   Specificare la versione di Excel utilizzata per creare il file.  
  
-   Indicare se la prima riga di dati a cui si accede nei fogli di lavoro o negli intervalli selezionati contiene i nomi delle colonne.  
  
 Se la gestione connessione Excel viene utilizzata da un'origine Excel, i nomi delle colonne saranno inclusi nei dati estratti. Se viene utilizzata da una destinazione Excel, i nomi delle colonne saranno inclusi nei dati scritti.  
  
 Per altre informazioni sul comportamento delle origini e delle destinazioni Excel, vedere [Origine Excel](../../integration-services/data-flow/excel-source.md) e [Destinazione Excel](../../integration-services/data-flow/excel-destination.md).  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , vedere [Editor gestione connessione Excel](../../integration-services/connection-manager/excel-connection-manager-editor.md).  
  
 Per informazioni sulla configurazione di una gestione connessione a livello di programmazione, vedere l'articolo relativo a <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> e [Aggiunta di connessioni a livello di programmazione](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
 Per informazioni sul ciclo tramite un gruppo di file Excel, vedere [Esecuzione di un ciclo su file e tabelle di Excel utilizzando un contenitore Ciclo Foreach](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md).  
  
## <a name="related-tasks"></a>Attività correlate  
  
-   [Esecuzione di un ciclo su file e tabelle di Excel utilizzando un contenitore Ciclo Foreach](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
-   [Connessione a una cartella di lavoro di Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md)  
  
  
