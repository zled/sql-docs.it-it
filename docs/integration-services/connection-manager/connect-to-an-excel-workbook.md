---
title: Connettersi a una cartella di lavoro di Excel | Documenti Microsoft
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Excel [Integration Services]
ms.assetid: d9746318-3669-4ce2-bbb0-4a1bd471c9dd
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2800075091835b2d6f2b07ee34e9b897fe86634e
ms.openlocfilehash: f8fb1db80ac1b750950a3401516b54af5ee29686
ms.contentlocale: it-it
ms.lasthandoff: 08/17/2017

---
# <a name="connect-to-an-excel-workbook"></a>Connessione a una cartella di lavoro di Excel
  Per connettere un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] a una cartella di lavoro di Microsoft Office Excel, è necessario disporre di una gestione connessione Excel.  
  
 È possibile creare queste gestioni connessioni dall'area Gestioni connessioni di Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o da Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
 
## <a name="connectivity-components-for-microsoft-excel-and-access-files"></a>Componenti di connettività per i file di Microsoft Excel e Access
  
È possibile scaricare i componenti di connettività per i file di Microsoft Office, se non è già non sono installati. Scaricare la versione più recente dei componenti di connettività per qui file di Excel e di accesso: [Microsoft Access Database Engine 2016 Redistributable](https://www.microsoft.com/download/details.aspx?id=54920).
  
La versione più recente dei componenti è possibile aprire i file creati con versioni precedenti di Excel.

Se il computer dispone di una versione a 32 bit di Office, quindi è necessario installare la versione a 32 bit dei componenti ed è inoltre necessario assicurarsi di eseguire il pacchetto in modalità a 32 bit.

Se si dispone di una sottoscrizione Office 365, assicurarsi di scaricare il pacchetto ridistribuibile di 2016 del motore di accesso Database e non Microsoft Access 2016 Runtime. Quando si esegue il programma di installazione, è possibile vedere un messaggio di errore che non è possibile installare il download side-by-side con componenti di Office a portata di clic. Per ignorare questo messaggio di errore e installare i componenti correttamente, eseguire l'installazione in modalità non interattiva, aprendo una finestra del prompt dei comandi ed eseguire il. File EXE scaricato con il `/quiet` passare. Esempio:

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`

## <a name="create-an-excel-connection-manager"></a>Creare un Excel gestione connessione

### <a name="to-create-an-excel-connection-manager-from-the-connection-managers-area"></a>Per creare una gestione connessione Excel dall'area Gestioni connessioni  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il pacchetto.  
  
2.  Fare clic con il pulsante destro del mouse in un punto qualsiasi dell'area **Gestioni connessioni** , quindi scegliere **Nuova connessione**.  
  
3.  Nella finestra di dialogo **Aggiungi gestione connessione SSIS** selezionare **Excel**, quindi configurare la gestione connessione.  
  
     Per informazioni sulle opzioni di configurazione disponibili per questa gestione connessione, vedere [Editor gestione connessione Excel](../../integration-services/connection-manager/excel-connection-manager-editor.md).  
  
### <a name="to-create-an-excel-connection-from-the-sql-server-import-and-export-wizard"></a>Per creare una connessione Excel dall'Importazione/Esportazione guidata SQL Server  
  
1.  Avviare la versione a 32 bit di Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  Nella pagina **Scegliere un'origine dati** selezionare **Microsoft Excel**in **Origine dati**, quindi configurare la connessione Excel.  
  
     Per informazioni sulle opzioni di configurazione disponibili per questo tipo di connessione, vedere [Editor gestione connessione Excel](../../integration-services/connection-manager/excel-connection-manager-editor.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione a un database di Access](../../integration-services/connection-manager/connect-to-an-access-database.md)  
  
  

