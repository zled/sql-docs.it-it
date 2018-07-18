---
title: Connettersi a una cartella di lavoro di Excel | Microsoft Docs
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: connection-manager
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Excel [Integration Services]
ms.assetid: d9746318-3669-4ce2-bbb0-4a1bd471c9dd
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 62c9d7b4de0b764ff7208b0fa077ec12b58dec60
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="connect-to-an-excel-workbook"></a>Connessione a una cartella di lavoro di Excel
  Per connettere un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] a una cartella di lavoro di Microsoft Office Excel, è necessario disporre di una gestione connessione Excel.  
  
 È possibile creare queste gestioni connessioni dall'area Gestioni connessioni di Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o da Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
 
## <a name="connectivity-components-for-microsoft-excel-and-access-files"></a>Componenti di connettività per i file di Microsoft Excel e Access
  
Se non sono già stati installati, potrebbe essere necessario scaricare i componenti di connettività per i file di Microsoft Office. Scaricare la versione più recente dei componenti di connettività per i file di Excel e Access qui: [Microsoft Access Database Engine 2016 Redistributable](https://www.microsoft.com/download/details.aspx?id=54920).
  
La versione più recente dei componenti può aprire file creati da versioni precedenti di Excel.

Se il computer ha una versione a 32 bit di Office, è necessario installare la versione a 32 bit dei componenti e verificare anche di eseguire il pacchetto in modalità a 32 bit.

Se si ha un abbonamento a Office 365, assicurarsi di scaricare Access Database Engine 2016 Redistributable e non Microsoft Access 2016 Runtime. Durante l'esecuzione del programma di installazione potrebbe essere visualizzato un messaggio di errore che indica non è possibile installare il download in modalità affiancata con i componenti di Office A portata di clic. Per ignorare questo messaggio di errore e installare i componenti correttamente, eseguire l'installazione in modalità non interattiva aprendo una finestra del prompt dei comandi ed eseguendo il file EXE scaricato con l'opzione `/quiet`. Ad esempio

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`

## <a name="create-an-excel-connection-manager"></a>Creare una gestione connessione Excel

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
  
  
