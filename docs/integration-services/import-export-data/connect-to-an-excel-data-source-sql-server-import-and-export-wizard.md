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
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d744e84aa2b4ae0462a5d5a1e4453a9e86abb890
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

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
> Per connettersi alla versione di Excel selezionata, può essere necessario scaricare e installare file aggiuntivi. Vedere [ottenere i file necessari per connettersi a Excel](#officeDownloads) in questa pagina per altre informazioni.

Se si dispone di un problema quando si specifica una versione, provare a specificare una versione diversa, anche una versione precedente. Ad esempio, potrebbe non essere in grado di installare i provider di dati di Office 2016, perché si dispone di una sottoscrizione di Microsoft Office 365. È possibile installare solo i provider di dati di Excel 2016 e accesso 2016 con una versione desktop di Microsoft Office. In questo caso, è possibile specificare Excel 2013 invece di Excel 2016. Le due versioni del provider sono funzionalmente equivalenti. Questa limitazione del runtime di Office 2016 è menzionata nella [questo post di blog](https://blogs.office.com/2015/12/16/access-2016-runtime-is-now-available-for-download/).

**Nomi di colonna nella prima riga**  
Indica se la prima riga dei dati contiene nomi di colonna.
-   Se i dati non contengono nomi di colonna, ma si abilita questa opzione, la procedura guidata considera la prima riga di dati di origine come i nomi di colonna.
-   Se i dati contengano nomi di colonna, ma si disabilita questa opzione, la riga di nomi di colonna verrà considerata come prima riga di dati.

Se si specifica che i dati non dispone di nomi di colonna, la procedura guidata utilizza F1, F2 e così via, come intestazioni di colonna.

## <a name="i-dont-see-excel-in-the-list-of-data-sources"></a>Excel non viene visualizzato nell'elenco delle origini dati
Se Excel non viene visualizzato nell'elenco delle origini dati, si esegue la procedura guidata a 64 bit? I provider per Excel e Access sono in genere a 32 bit e non sono visibili nella procedura guidata a 64 bit. Eseguire la procedura guidata a 32 bit.

## <a name="officeDownloads"></a>Ottenere i file che necessari per connettersi a Excel  
È possibile scaricare i componenti di connettività per le origini dati di Microsoft Office, tra cui Excel e Access, se non è già non sono installati.

Le versioni più recenti dei componenti possono aprire file creati da versioni precedenti dei programmi. In alcuni casi le versioni precedenti dei componenti possono aprire anche file creati dalle ultime versioni dei programmi. Ad esempio, se non è possibile installare i componenti di Office 2016, utilizzare invece i componenti di Office 2013. Le due versioni del provider sono funzionalmente equivalenti. Questa limitazione del runtime di Office 2016 è menzionata nella [questo post di blog](https://blogs.office.com/2015/12/16/access-2016-runtime-is-now-available-for-download/).

Se il computer dispone di una versione a 32 bit di Office, è tipico, anche nei computer a 64 bit, è necessario installare la versione a 32 bit dei componenti. È inoltre necessario assicurarsi di eseguire la procedura guidata a 32 bit, o eseguire il pacchetto di SQL Server Integration Services che consente di creare la procedura guidata in modalità a 32 bit. 
 
|Versione di Microsoft Office|Scarica|  
|------------------------------|--------------|  
|2016|[Microsoft Access 2016 Runtime](https://www.microsoft.com/download/details.aspx?id=50040)|
|2013|[Microsoft Access 2013 Runtime](http://www.microsoft.com/download/details.aspx?id=39358)|
|2010|[Microsoft Access 2010 Runtime](https://www.microsoft.com/download/details.aspx?id=10910)|  
|2007|[Driver di Office System 2007: Componenti di connettività dei dati](https://www.microsoft.com/download/details.aspx?id=23734)|  

## <a name="see-also"></a>Vedere anche
[Scegliere un'origine dati](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Scegliere una destinazione](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


