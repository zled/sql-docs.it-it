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
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b36b92c9beb840f6a2ea66250a5a025aa587acef
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-an-excel-workbook"></a>Connessione a una cartella di lavoro di Excel
  Per connettere un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] a una cartella di lavoro di Microsoft Office Excel, è necessario disporre di una gestione connessione Excel.  
  
 È possibile creare queste gestioni connessioni dall'area Gestioni connessioni di Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o da Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Provider e driver per i file di Microsoft Excel e Access**  
  
 Potrebbe essere necessario scaricare i provider OLE DB e i driver per i file di Microsoft Office, se non sono già installati. Le versioni successive del provider possono aprire i file creati con versioni precedenti di Excel.  
  
 Se il computer ha una versione a 32 bit di Office, è necessario installare la versione a 32 bit dei driver e verificare anche di eseguire la procedura guidata o il pacchetto di Integration Services creato in modalità a 32 bit.  
  
|Versione di Microsoft Office|Scarica|  
|------------------------------|--------------|  
|2007|[Driver di Office System 2007: Componenti di connettività dei dati](https://www.microsoft.com/en-us/download/details.aspx?id=23734)|  
|2010|[Microsoft Access 2010 Runtime](https://www.microsoft.com/en-us/download/details.aspx?id=10910)|  
|2013|[Microsoft Access 2013 Runtime](http://www.microsoft.com/en-us/download/details.aspx?id=39358)|  
  
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
  
  
