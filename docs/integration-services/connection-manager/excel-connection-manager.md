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
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2800075091835b2d6f2b07ee34e9b897fe86634e
ms.openlocfilehash: a5ce75f3c1715870113626642150028e31a0d58b
ms.contentlocale: it-it
ms.lasthandoff: 08/17/2017

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
  
## <a name="excel-connection-manager-editor"></a>Editor gestione connessione Excel
  Usare la finestra di dialogo **Editor gestione connessione Excel[!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]per aggiungere una connessione a un file di cartella di lavoro di**  nuovo o esistente.  
  
 Per altre informazioni sulla gestione connessioni Excel, vedere [Gestione connessione Excel](../../integration-services/connection-manager/excel-connection-manager.md).  
  
### <a name="options"></a>Opzioni  
 **Percorso file di Excel**  
 Consente di digitare il percorso e il nome del file di una cartella di lavoro di Excel (xls) nuova o esistente.  
  
> [!NOTE]  
>  Non è possibile connettersi a un file di Excel protetto da password.  
  
> [!WARNING]  
>  **Editor destinazione Excel** crea automaticamente il file di Excel quando si seleziona una **Connessione Excel** che fa riferimento a un file nuovo o non esistente e si fa clic su **Nuovo** per **Nome del foglio di Excel**.  
  
 **Sfoglia**  
 Usare la finestra di dialogo **Apri** per passare alla cartella che contiene il file di Excel o in cui creare il nuovo file.  
  
 **Versione di Excel**  
 Consente di specificare la versione di Microsoft Excel utilizzata per creare il file.  
  
 **Nomi di colonna nella prima riga**  
 Consente di specificare se la prima riga di dati del foglio di lavoro selezionato contiene nomi di colonna. Il valore predefinito di questa opzione è **True**.  
  
## <a name="connectivity-components-for-microsoft-excel-and-access-files"></a>Componenti di connettività per i file di Microsoft Excel e Access
  
È possibile scaricare i componenti di connettività per i file di Microsoft Office, se non è già non sono installati. Scaricare la versione più recente dei componenti di connettività per qui file di Excel e di accesso: [Microsoft Access Database Engine 2016 Redistributable](https://www.microsoft.com/download/details.aspx?id=54920).
  
La versione più recente dei componenti è possibile aprire i file creati con versioni precedenti di Excel.

Se il computer dispone di una versione a 32 bit di Office, quindi è necessario installare la versione a 32 bit dei componenti ed è inoltre necessario assicurarsi di eseguire il pacchetto in modalità a 32 bit.

Se si dispone di una sottoscrizione Office 365, assicurarsi di scaricare il pacchetto ridistribuibile di 2016 del motore di accesso Database e non Microsoft Access 2016 Runtime. Quando si esegue il programma di installazione, è possibile vedere un messaggio di errore che non è possibile installare il download side-by-side con componenti di Office a portata di clic. Per ignorare questo messaggio di errore, eseguire l'installazione in modalità non interattiva, aprendo una finestra del prompt dei comandi ed eseguire il. File EXE scaricato con il `/quiet` passare. Esempio:

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`
  
## <a name="related-tasks"></a>Attività correlate  
  
-   [Esecuzione di un ciclo su file e tabelle di Excel utilizzando un contenitore Ciclo Foreach](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
-   [Connessione a una cartella di lavoro di Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md)  
  
  

