---
title: Installare pacchetti R aggiuntivi su SQL Server | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 11/08/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: 16
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: adc0e5fc229547632759c5702e98d87f4b71cbb3
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="install-additional-r-packages-on-sql-server"></a>Installare pacchetti R aggiuntivi su SQL Server
Questo argomento descrive come installare nuovi pacchetti R in un'istanza di [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] in un computer dotato di accesso a Internet.

## <a name="1-locate-the-windows-binaries-in-zip-file-format"></a>1. Individuare i file binari di Windows in formato di file ZIP

I pacchetti R sono supportati in molte piattaforme. È necessario assicurarsi che il pacchetto che si vuole installare abbia un formato binario per la piattaforma Windows. In caso contrario, il pacchetto scaricato non funzionerà.

Ad esempio, per ottenere il pacchetto [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) da Bioconductor:  
  
1.  Nell'elenco **Archivi dei pacchetti** , individuare la versione **binaria di Windows** .  
  
2.  Fare clic con il pulsante destro del mouse sul link al file ZIP, quindi selezionare  **Salva oggetto con nome**.  
  
3.  Passare alla cartella locale in cui vengono archiviati i pacchetti compressi, quindi fare clic su **Salva**.  
  
 Questo processo crea una copia locale del pacchetto. È quindi possibile installare il pacchetto oppure copiare il pacchetto compresso in un server privo di accesso a Internet.  
  
  
## <a name="2-open-the-default-r-package-library-for-sql-server-r-services"></a>2. Aprire la libreria di pacchetti R predefinita per SQL Server R Services 

Passare alla cartella del server in cui sono stati installati i pacchetti R associati a [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. È importante installare i pacchetti nella libreria predefinita associata all'istanza corrente. 

Per istruzioni su come individuare questa libreria, vedere [Installazione e gestione dei pacchetti R](../../advanced-analytics/r-services/installing-and-managing-r-packages.md).

   Per ogni istanza in cui si intende eseguire un pacchetto, è necessario installare una copia separata dei pacchetti. Attualmente i pacchetti non possono essere condivisi tra istanze.
     
  
## <a name="3-open-an-administrative-command-prompt"></a>3. Aprire un prompt dei comandi amministrativo 

Aprire R come amministratore.  A questo scopo, è possibile usare il prompt dei comandi di Windows o una delle utilità R.
  
### <a name="using-the-windows-command-prompt"></a>Uso del prompt dei comandi di Windows 

1. Aprire un prompt dei comandi di Windows come amministratore, quindi passare alla directory in cui si trova il file RTerm.Exe o RGui.exe.  
  
    In un'installazione predefinita, si tratta della directory **\bin** di R. Ad esempio, in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] gli strumenti R si trovano qui: 

    **Istanza predefinita**

     `C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin` 
 
     **Istanza denominata**
   
     `C:\Program files\MSSQL13.<instanceName>\R_SERVICES\bin\x64`  
  
2. Eseguire **R.exe**.  
  
### <a name="using-the-r-command-line-utilities"></a>Uso delle utilità della riga di comando di R 
  
1. Usare Esplora risorse per passare alla directory contenente gli strumenti di R.  
  
2. Fare clic con il pulsante destro del mouse su **RGui.exe** o **RTerm.exe** e quindi selezionare **Esegui come amministratore**.  
## <a name="4-install-the-package"></a>4. Installare il pacchetto

Il comando R per installare il pacchetto varia a seconda che il pacchetto venga ottenuto da Internet o da un file compresso locale.  
  
### <a name="install-package-from-internet"></a>Installare il pacchetto da Internet  
  
1.  In generale, è necessario usare il comando seguente per installare un nuovo pacchetto da CRAN o da uno dei siti mirror.  
  
    ```  
    install.packages("target_package_name")  
    ```
    
    Si noti che le virgolette doppie sono sempre obbligatorie per il nome del pacchetto.

2.  Per specificare la libreria in cui deve essere installato il pacchetto, usare un comando come questo per impostare il percorso della libreria:
    
    ```  
    lib.SQL <- "C:\\Program Files\\Microsoft SQL Server\\MSSQL13.MSSQLSERVER\\R_SERVICES\\library"    
    ```

    Per [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], è attualmente consentita una sola libreria di pacchetti. Non installare pacchetti in una libreria utente, perché in questo caso non sarà possibile eseguire il pacchetto da [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].   
     
3.  Dopo aver definito il percorso della libreria, l'istruzione seguente installa il diffuso pacchetto e1070 nella libreria di pacchetti usata da R Services.  
  
    ```  
    install.packages("e1071", lib = lib.SQL)  
    ```  
  
4.  Verrà richiesto un sito mirror da cui ottenere il pacchetto. Selezionare qualsiasi sito mirror utile per il percorso.  
  
    Per un elenco dei mirror CRAN correnti, vedere [questo sito](https://cran.r-project.org/mirrors.html).  
  
    > [!TIP]  
    >  Per evitare di selezionare un sito mirror ogni volta che si aggiunge un nuovo pacchetto, è possibile configurare l'ambiente di sviluppo di R in modo che usi sempre lo stesso repository.  
    >   
    >  Per eseguire questa operazione, modificare il file con estensione Rprofile delle impostazioni globali di R, quindi aggiungere la riga seguente:  
    >   
    >  `options(repos=structure(c(CRAN="<mirror site URL>")))`  
    >   
    >  Per informazioni dettagliate sulle preferenze e sugli altri file caricati all'avvio del runtime di R, eseguire questo comando in una console di R:  
    >   
    >  `?Startup`  
  
5.  Se il pacchetto di destinazione dipende da pacchetti aggiuntivi, il programma di installazione di R scaricherà automaticamente le dipendenze e le installerà.  
  
### <a name="manual-package-installation-or-installing-on-computer-with-no-internet-access"></a>Installazione manuale del pacchetto o installazione in un computer senza accesso a Internet 

1. Se il pacchetto che si intende installare ha dipendenze, ottenere in anticipo i pacchetti necessari e aggiungerli alla cartella con gli altri file di pacchetto compressi.

    > [!TIP]
    > 
    > È consigliabile configurare un repository locale con [miniCRAN](https://mran.revolutionanalytics.com/package/miniCRAN/) se è necessario supportare installazioni offline frequenti di pacchetti R.  
  
2.  Nel prompt dei comandi di R, digitare il comando seguente per specificare il percorso e il nome del pacchetto da installare:  
   
    ```  
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)  
    ``` 
     
    Questo comando consente di estrarre il pacchetto R dal file compresso locale, presupponendo che sia stata salvata una copia nella directory `C:\Temp\Downloaded packages`, quindi installa il pacchetto (con le relative dipendenze) nella libreria R sul computer locale.  
  
3.  Se in precedenza è stato modificato l'ambiente R nel computer, assicurarsi che la variabile di ambiente R `.libPath` usi solo un percorso, che deve puntare alla cartella R_SERVICES per l'istanza.  
  
> [!NOTE]
> Se è stato installato Microsoft R Server (Standalone) oltre a SQL Server R Services, il computer avrà un'installazione separata di R con tutti gli strumenti e le librerie R. I pacchetti installati nella libreria R_SERVER vengono usati solo da Microsoft R Server e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non può accedervi.  
> 
>  Assicurarsi di usare la libreria R_SERVICES quando si installano pacchetti da usare in SQL Server.

  
## <a name="see-also"></a>Vedere anche  
 [Configurare SQL Server R Services &#40;In-Database&#41;](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)  
  
  

