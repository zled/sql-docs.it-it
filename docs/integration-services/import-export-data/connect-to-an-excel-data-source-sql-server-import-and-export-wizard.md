---
title: Connettersi a un'origine dati di Excel (SQL Server importazione / esportazione guidata) | Documenti Microsoft
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43fbaca0-36d8-4583-9056-af7010209b87
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: b4411fdd2337d93f15b149febf845fb7b0762c40
ms.contentlocale: it-it
ms.lasthandoff: 08/28/2017

---
# <a name="connect-to-an-excel-data-source-sql-server-import-and-export-wizard"></a>Connettersi a un'origine dati di Excel (SQL Server importazione / esportazione guidata)
In questo argomento viene illustrato come connettersi a un **Microsoft Excel** dell'origine dati dal **scegliere un'origine dati** o **scegliere una destinazione** pagina di SQL Server di importazione / esportazione guidata.

La schermata seguente mostra una connessione di esempio a una cartella di lavoro di Microsoft Excel.

![Connessione di Excel](../../integration-services/import-export-data/media/excel-connection.png) 

## <a name="options-to-specify"></a>Opzioni per specificare

> [!NOTE]
> Le opzioni di connessione per il provider di dati sono gli stessi se Excel è l'origine o destinazione. Ovvero le opzioni disponibili sono gli stessi in entrambi i **scegliere un'origine dati** e **scegliere una destinazione** pagine della procedura guidata.

**Percorso file di Excel**  
 Specificare il percorso e il nome del file di Excel. Esempio:
-   Per un file nel computer locale, **c:\\MyData.xlsx**.
-   Per un file in una condivisione di rete,  **\\ \\Sales\\Database\\Northwind.xlsx**.

In alternativa, fare clic su **Sfoglia**.  
  
 **Sfoglia**  
 Consente di individuare il foglio di calcolo tramite la finestra di dialogo **Apri**.  

> [!NOTE]
> La procedura guidata non può aprire un file di Excel protetto da password.

 **Versione di Excel**  
Selezionare la versione di Excel usata dalla cartella di lavoro di origine.

> [!IMPORTANT]
> È possibile scaricare e installare i file aggiuntivi per connettersi al file di Excel. Vedere [ottenere i file necessari per connettersi a Excel](#officeDownloads) in questa pagina per altre informazioni.

**Nomi di colonna nella prima riga**  
Indica se la prima riga dei dati contiene nomi di colonna.
-   Se i dati non contengono nomi di colonna, ma si abilita questa opzione, la procedura guidata considera la prima riga di dati di origine come i nomi di colonna.
-   Se i dati contengano nomi di colonna, ma si disabilita questa opzione, la riga di nomi di colonna verrà considerata come prima riga di dati.

Se si specifica che i dati non dispone di nomi di colonna, la procedura guidata utilizza F1, F2 e così via, come intestazioni di colonna.

## <a name="i-dont-see-excel-in-the-list-of-data-sources"></a>Excel non viene visualizzato nell'elenco delle origini dati
Se Excel non viene visualizzato nell'elenco delle origini dati, si esegue la procedura guidata a 64 bit? I provider per Excel e Access sono in genere a 32 bit e non sono visibili nella procedura guidata a 64 bit. Eseguire la procedura guidata a 32 bit.

> [!NOTE]
> Per utilizzare la versione a 64 bit di SQL Server di importazione / esportazione guidata, è necessario installare SQL Server. SQL Server Data Tools (SSDT) e SQL Server Management Studio (SSMS) sono applicazioni a 32 bit e installare solo i file a 32 bit, inclusa la versione a 32 bit della procedura guidata.

## <a name="officeDownloads"></a>Ottenere i file che necessari per connettersi a Excel  
È possibile scaricare i componenti di connettività per le origini dati di Microsoft Office, tra cui Excel e Access, se non è già non sono installati. Scaricare la versione più recente dei componenti di connettività per qui file di Excel e di accesso: [Microsoft Access Database Engine 2016 Redistributable](https://www.microsoft.com/download/details.aspx?id=54920).
  
La versione più recente dei componenti è possibile aprire i file creati con versioni precedenti di Excel.

Se il computer dispone di una versione a 32 bit di Office, quindi è necessario installare la versione a 32 bit dei componenti ed è inoltre necessario assicurarsi di eseguire il pacchetto in modalità a 32 bit.

Se si dispone di una sottoscrizione Office 365, assicurarsi di scaricare il pacchetto ridistribuibile di 2016 del motore di accesso Database e non Microsoft Access 2016 Runtime. Quando si esegue il programma di installazione, è possibile vedere un messaggio di errore che non è possibile installare il download side-by-side con componenti di Office a portata di clic. Per ignorare questo messaggio di errore, eseguire l'installazione in modalità non interattiva, aprendo una finestra del prompt dei comandi ed eseguire il. File EXE scaricato con il `/quiet` passare. Esempio:

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`

## <a name="see-also"></a>Vedere anche
[Scegliere un'origine dati](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Scegliere una destinazione](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


