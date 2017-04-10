---
title: "Installare Microsoft R Server dalla riga di comando | Microsoft Docs"
ms.custom: ""
ms.date: "01/19/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb4446ba-e9ce-4b93-9854-5e8a58507da0
caps.latest.revision: 4
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 3
---
# Installare Microsoft R Server dalla riga di comando
    
È possibile installare Microsoft R Server dalla riga di comando usando le funzionalità di scripting fornite con il programma di installazione di SQL Server. 

- Per un'installazione **automatica** è necessario specificare il percorso dell'utilità di installazione e usare gli argomenti per indicare le funzionalità da installare. 
- Per un'installazione **non interattiva**, specificare gli stessi argomenti e aggiungere l'opzione **/q**. In questo modo non vengono visualizzati messaggi di richiesta e non è necessaria alcuna interazione. Se tuttavia viene omesso uno qualsiasi degli argomenti obbligatori, l'installazione non riesce.

Per altre informazioni, vedere [Installare SQL Server 2016 dal prompt dei comandi](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).

## <a name="perform-a-command-line-install-of-microsoft-r-server-standalone"></a>Eseguire un'installazione da riga di comando di Microsoft R Server (Standalone)

 Gli esempi seguenti mostrano gli argomenti usati durante l'esecuzione di un'installazione da riga di comando di Microsoft R Server con il programma di installazione di SQL Server.


### <a name="example-of-unattended-installation-of-r-server-standalone"></a>Esempio di installazione automatica di R Server (Standalone)

Eseguire il comando seguente da un prompt dei comandi con privilegi elevati per installare solo Microsoft R Server (Standalone) e i relativi prerequisiti. 

```  
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR /IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS 
```  

Per visualizzare lo stato di avanzamento e i messaggi di richiesta, rimuovere l'argomento /q.

Si noti che tutti gli argomenti seguenti sono obbligatori:
  - **FEATURES = SQL_SHARED_MR** ottiene solo i componenti di Microsoft Server R, tra cui Microsoft R Open e i prerequisiti.
  - **IACCEPTROPENLICENSETERMS** indica che si sono accettate le condizioni di licenza per l'uso dei componenti R open source.
  - **IACCEPTSQLSERVERLICENSETERMS** è necessario per eseguire l'Installazione guidata.


### <a name="offline-installation"></a>Installazione offline

Se si installa Microsoft R Server (Standalone) in un computer che non ha accesso a Internet, è necessario scaricare prima i componenti R necessari e copiarli in una cartella locale. Per i collegamenti di download, vedere [Installazione dei componenti R senza accesso a Internet](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md).   


## <a name="advanced-installation-tips"></a>Suggerimenti per l'installazione avanzata

Al termine dell'installazione, è possibile esaminare il file di configurazione creato dal programma di installazione di SQL Server, insieme a un riepilogo delle azioni di installazione.

Per impostazione predefinita, tutti i riepiloghi e i log di installazione per SQL Server e le funzionalità correlate vengono creati in `C:\Program Files\Microsoft SQL Server\140\Setup Bootstrap\Log`.

Per ogni funzionalità installata viene creata una sottocartella separata. Per Microsoft R Server, cercare: 
- `RSetup.log`
- `Settings.xml`
- `Summmary<instance_GUID>.txt`

Per configurare un'altra istanza di Microsoft R Server con gli stessi parametri, è possibile anche riutilizzare il file di configurazione creato durante l'installazione. Per altre informazioni, vedere [Installare SQL Server tramite un file di configurazione](https://msdn.microsoft.com/library/dd239405.aspx).



### <a name="customizing-your-r-environment"></a>Personalizzazione dell'ambiente R

Dopo l'installazione, è possibile installare altri pacchetti R. Per altre informazioni, vedere [Installazione e gestione dei pacchetti R](../../advanced-analytics/r-services/installing-and-managing-r-packages.md).

> [!IMPORTANT]
> Se si intende eseguire il codice R in SQL Server, assicurarsi di installare gli stessi pacchetti sia nel computer client che esegue Microsoft R Server sia nell'istanza di SQL Server che esegue R Services. 



## <a name="see-also"></a>Vedere anche  

[Microsoft R Server](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)
  