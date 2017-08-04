---
title: Editor gestione connessione Excel | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 03/02/2017
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
- Excel Connection Manager Editor
ms.assetid: 7ff097e4-cafb-4885-a898-05b2a46628c1
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3c4060736f824becd05fecceba0b162b45f0fed4
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="excel-connection-manager-editor"></a>Editor gestione connessione Excel
  Usare la finestra di dialogo **Editor gestione connessione Excel[!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]per aggiungere una connessione a un file di cartella di lavoro di**  nuovo o esistente.  
  
 Per altre informazioni sulla gestione connessioni Excel, vedere [Gestione connessione Excel](../../integration-services/connection-manager/excel-connection-manager.md).  
  
## <a name="options"></a>Opzioni  
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
  
## <a name="providers-and-drivers-for-microsoft-excel-and-access-file"></a>Provider e driver per i file di Microsoft Excel e Access  
 Potrebbe essere necessario scaricare i provider OLE DB e i driver per i file di Microsoft Office, se non sono già installati. Le versioni successive del provider possono aprire i file creati con versioni precedenti di Excel.  
  
 Se il computer ha una versione a 32 bit di Office, è necessario installare la versione a 32 bit dei driver e verificare anche di eseguire la procedura guidata o il pacchetto di Integration Services creato in modalità a 32 bit.  
  
|Versione di Microsoft Office|Scarica|  
|------------------------------|--------------|  
|2007|[Driver di Office System 2007: Componenti di connettività dei dati](https://www.microsoft.com/download/details.aspx?id=23734)|  
|2010|[Microsoft Access 2010 Runtime](https://www.microsoft.com/download/details.aspx?id=10910)|  
|2013|[Microsoft Access 2013 Runtime](http://www.microsoft.com/download/details.aspx?id=39358)|  
|2016|[Microsoft Access 2016 Runtime](https://www.microsoft.com/download/details.aspx?id=50040)|
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Ciclo tramite Excel, file e tabelle con un contenitore ciclo Foreach](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
  
