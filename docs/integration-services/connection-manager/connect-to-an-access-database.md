---
title: Connettersi a un database di Access | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Access [Integration Services]
- Access databases [Integration Services]
ms.assetid: 229fbd46-ef6a-4609-a4cc-d80d52c33cf1
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 44c04e7978ca425eb6fb625374f9404e3f286fde
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="connect-to-an-access-database"></a>Connessione a un database di Access
  Per connettere un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] a un'origine dati di Microsoft Office Access, è necessario disporre di una gestione connessione e di un provider di dati OLE DB. Il provider di dati usato dipende dalla versione di Access in cui è stata creata l'origine dati:  
  
-   Per Access 2003 e versioni precedenti, il pacchetto richiede il provider OLE DB [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet.  
  
-   Per Access 2007, il pacchetto richiede il provider OLE DB per il motore di database di Microsoft Office 12.0 Access.  
  
 È possibile creare una gestione connessione OLE DB e selezionare il provider di dati corrispondente dall'area Gestioni connessioni di Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o dall'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  In un computer a 64 bit è necessario eseguire i pacchetti che si connettono a origini dati di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Access in modalità a 32 bit. Il provider OLE DB [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet e il provider OLE DB per il motore di database di Microsoft Office 12.0 Access sono disponibili solo nelle versioni a 32 bit.  

## <a name="connectivity-components-for-microsoft-excel-and-access-files"></a>Componenti di connettività per i file di Microsoft Excel e Access
  
Se non sono già stati installati, potrebbe essere necessario scaricare i componenti di connettività per i file di Microsoft Office. Scaricare la versione più recente dei componenti di connettività per i file Excel e Access qui: [Microsoft Access Database Engine 2016 Redistributable](https://www.microsoft.com/download/details.aspx?id=54920).
  
La versione più recente dei componenti può aprire file creati da versioni precedenti di Access.

Se il computer ha una versione a 32 bit di Office, è necessario installare la versione a 32 bit dei componenti e verificare anche di eseguire il pacchetto in modalità a 32 bit.

Se si ha un abbonamento a Office 365, assicurarsi di scaricare Access Database Engine 2016 Redistributable e non Microsoft Access 2016 Runtime. Durante l'esecuzione del programma di installazione potrebbe essere visualizzato un messaggio di errore che indica non è possibile installare il download in modalità affiancata con i componenti di Office A portata di clic. Per ignorare questo messaggio di errore, eseguire l'installazione in modalità non interattiva aprendo una finestra del prompt dei comandi ed eseguendo il file con estensione EXE scaricato con l'opzione `/quiet`. Ad esempio

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`
  
## <a name="connecting-to-a-data-source-in-access-2003-or-earlier-format"></a>Connessione a un'origine dati in formato Access 2003 o precedente  
  
### <a name="to-create-an-access-connection-manager-from-the-connection-managers-area"></a>Per creare una gestione connessione Access dall'area Gestioni connessioni  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il pacchetto.  
  
2.  Fare clic con il pulsante destro del mouse in un punto qualsiasi dell'area **Gestioni connessioni** e quindi scegliere **Nuova connessione OLE DB**.  
  
3.  Nella finestra di dialogo **Configura gestione connessione OLE DB** fare clic su **Nuova**.  
  
     Per altre informazioni, vedere [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
4.  Nella finestra di dialogo **Gestione connessione** selezionare **Provider OLE DB di Microsoft Jet 4.0**per **Provider**e quindi configurare la gestione connessione in base alle proprie esigenze.  
  
### <a name="to-create-an-access-connection-from-the-sql-server-import-and-export-wizard"></a>Per creare una connessione ad Access dall'Importazione/Esportazione guidata SQL Server  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]avviare l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  Nella pagina **Scelta origine dati** selezionare **Microsoft Access**per **Origine dati**e quindi configurare la connessione ad Access.  
  
     Quando si seleziona **Microsoft Access** come **Origine dati**, la procedura guidata crea automaticamente la gestione connessione OLE DB necessaria con il provider di dati corretto. Per altre informazioni, vedere [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
## <a name="connecting-to-a-data-source-in-access-2007-format"></a>Connessione a un'origine dati in formato Access 2007  
 Per accedere a un'origine dati di Access 2007, la gestione connessione OLE DB richiede il provider OLE DB per il motore di database di Microsoft Office 12.0 Access. Questo provider viene installato automaticamente con [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office System 2007. Se Office System 2007 non è installato nel computer in cui è in esecuzione [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , è necessario installare il provider separatamente. Per installare il provider OLE DB per il motore di database di Microsoft Office 12.0 Access, scaricare e installare i componenti disponibili nella pagina Web [Driver di Office System 2007: Data Connectivity Components](http://go.microsoft.com/fwlink/?LinkId=98155).  
  
### <a name="to-create-an-ole-db-connection-manager-from-the-connection-managers-area"></a>Per creare una gestione connessione OLE DB dall'area Gestioni connessioni  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il pacchetto.  
  
2.  Fare clic con il pulsante destro del mouse in un punto qualsiasi dell'area **Gestioni connessioni** e quindi scegliere **Nuova connessione OLE DB**.  
  
3.  Nella finestra di dialogo **Configura gestione connessione OLE DB** fare clic su **Nuova**.  
  
     Per altre informazioni, vedere [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
4.  Nella finestra di dialogo **Gestione connessione** selezionare **Provider OLE DB per il motore di database di Microsoft Office 12.0 Access**per **Provider**e quindi configurare la gestione connessione in base alle proprie esigenze.  
  
    > [!NOTE]  
    >  Per stabilire una connessione a un'origine dati che usa Access 2007, non è possibile selezionare **Provider OLE DB di Microsoft Jet 4.0** come **Origine dati**.  
  
### <a name="to-create-an-ole-db-connection-from-the-sql-server-import-and-export-wizard"></a>Per creare una connessione OLE DB dall'Importazione/Esportazione guidata SQL Server  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]avviare l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  Nella pagina **Scelta origine dati** selezionare **Provider OLE DB per il motore di database di Microsoft Office 12.0 Access**per **Origine dati**e quindi configurare la connessione in base alle proprie esigenze.  
  
    > [!NOTE]  
    >  Per stabilire una connessione a un'origine dati che usa Access 2007, non è possibile selezionare **Provider OLE DB di Microsoft Jet 4.0** come **Origine dati**.  
  
     Quando si seleziona **Provider OLE DB per il motore di database di Microsoft Office 12.0 Access** come **Origine dati**, la procedura guidata crea automaticamente la gestione connessione OLE DB necessaria con il provider di dati corretto. Per altre informazioni, vedere [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione a una cartella di lavoro di Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md)  
  
  
