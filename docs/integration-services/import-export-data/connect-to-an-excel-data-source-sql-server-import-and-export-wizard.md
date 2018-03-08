---
title: Connettersi a un'origine dati Excel (Importazione/Esportazione guidata SQL Server) | Microsoft Docs
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43fbaca0-36d8-4583-9056-af7010209b87
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 16ace15a73d9ef727612c59f8c9329a4d4437312
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="connect-to-an-excel-data-source-sql-server-import-and-export-wizard"></a>Connettersi a un'origine dati Excel (Importazione/Esportazione guidata SQL Server)
Questo argomento illustra come connettersi a un'origine dati **Microsoft Excel** dalla pagina **Scelta origine dati** o **Scelta destinazione** dell'Importazione/Esportazione guidata SQL Server.

La schermata seguente mostra una connessione di esempio a una cartella di lavoro di Microsoft Excel.

![Connessione di Excel](../../integration-services/import-export-data/media/excel-connection.png) 

## <a name="options-to-specify"></a>Opzioni da specificare

> [!NOTE]
> Le opzioni di connessione per il provider di dati sono le stesse sia nel caso in cui Excel rappresenti l'origine sia nel caso in cui rappresenti la destinazione. Ovvero, le opzioni visualizzate sono le stesse in entrambe le pagine **Scelta origine dati** e **Scelta destinazione** della procedura guidata.

**Percorso file di Excel**  
 Specificare il percorso e il nome del file Excel. Ad esempio
-   Per un file nel computer locale, **C:\\MyData.xlsx**.
-   Per un file in una condivisione di rete, **\\\\Sales\\Database\\Northwind.xlsx**.

In alternativa, fare clic su **Sfoglia**.  
  
 **Sfoglia**  
 Consente di individuare il foglio di calcolo tramite la finestra di dialogo **Apri**.  

> [!NOTE]
> La procedura guidata non può aprire un file di Excel protetto da password.

 **Versione di Excel**  
Selezionare la versione di Excel usata dalla cartella di lavoro di origine.

> [!IMPORTANT]
> Per connettersi ai file Excel, può essere necessario scaricare e installare file aggiuntivi. Per altre informazioni, vedere [Ottenere i file necessari per connettersi a Excel](#officeDownloads) in questa pagina.

**Nomi di colonna nella prima riga**  
Specificare se la prima riga di dati contiene nomi di colonna.
-   Se i dati non contengono nomi di colonna e si abilita questa opzione, la procedura guidata considera la prima riga dei dati di origine come nomi di colonna.
-   Se i dati contengono nomi di colonna e si disabilita questa opzione, la procedura guidata considera la riga dei nomi di colonna come prima riga di dati.

Se si specifica che i dati non contengono nomi di colonna, la procedura guidata usa F1, F2 e così via come intestazioni di colonna.

## <a name="i-dont-see-excel-in-the-list-of-data-sources"></a>Excel non è incluso nell'elenco delle origini dati
Se Excel non è incluso nell'elenco delle origini dati, controllare se è in esecuzione la procedura guidata a 64 bit. I provider per Excel e Access sono in genere a 32 bit e non sono visibili nella procedura guidata a 64 bit. Eseguire la procedura guidata a 32 bit.

> [!NOTE]
> Per usare la versione a 64 bit dell'Importazione/Esportazione guidata SQL Server, è necessario installare SQL Server. SQL Server Data Tools (SSDT) e SQL Server Management Studio (SSMS) sono applicazioni a 32 bit e installano solo i file a 32 bit, inclusa la versione a 32 bit della procedura guidata.

## <a name="officeDownloads"></a>Ottenere i file necessari per connettersi a Excel  
Se non sono già stati installati, potrebbe essere necessario scaricare i componenti di connettività per le origini dati Microsoft Office, incluse le origini dati Excel e Access. Scaricare la versione più recente dei componenti di connettività per i file di Excel e Access qui: [Microsoft Access Database Engine 2016 Redistributable](https://www.microsoft.com/download/details.aspx?id=54920).
  
La versione più recente dei componenti può aprire file creati da versioni precedenti di Excel.

Se il computer ha una versione a 32 bit di Office, è necessario installare la versione a 32 bit dei componenti e verificare anche di eseguire il pacchetto in modalità a 32 bit.

Se si ha un abbonamento a Office 365, assicurarsi di scaricare Access Database Engine 2016 Redistributable e non Microsoft Access 2016 Runtime. Durante l'esecuzione del programma di installazione potrebbe essere visualizzato un messaggio di errore che indica non è possibile installare il download in modalità affiancata con i componenti di Office A portata di clic. Per ignorare questo messaggio di errore, eseguire l'installazione in modalità non interattiva aprendo una finestra del prompt dei comandi ed eseguendo il file con estensione EXE scaricato con l'opzione `/quiet`. Ad esempio

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`

## <a name="see-also"></a>Vedere anche
[Scelta origine dati](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Scelta destinazione](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)

