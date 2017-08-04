---
title: Compilazione, distribuzione e debug di oggetti personalizzati | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom objects [Integration Services]
ms.assetid: b03685bc-5398-4c3f-901a-1219c1098fbe
caps.latest.revision: 50
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 99fdd71403b12cee8ba9f207890268cde2e1d450
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="building-deploying-and-debugging-custom-objects"></a>Compilazione, distribuzione e debug di oggetti personalizzati
  Una volta scritto il codice per un oggetto personalizzato per [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], è necessario compilare l'assembly, distribuirlo e integrarlo in [!INCLUDE[ssIS](../../includes/ssis-md.md)] finestra di progettazione per renderla disponibile per l'utilizzo nei pacchetti e di test ed eseguirne il debug.  
  
##  <a name="top"></a>Passaggi di compilazione, distribuzione e il debug di un oggetto personalizzato per Integration Services  
 La funzionalità personalizzata per l'oggetto è già stata scritta. A questo punto, è necessario testarla e renderla disponibile per gli utenti. I passaggi sono molto simili per tutti i tipi di oggetti personalizzati che è possibile creare per [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Ecco i passaggi per compilare, distribuire e testarlo.  
  
1.  [Accesso](#signing) l'assembly deve essere generato con un nome sicuro.  
  
2.  [Compilare](#building) l'assembly.  
  
3.  [Distribuire](#deploying) l'assembly spostandolo o copiandolo appropriati [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] cartella.  
  
4.  [Installare](#installing) l'assembly nella global assembly cache (GAC).  
  
     L'oggetto viene automaticamente aggiunto alla Casella degli strumenti.  
  
5.  [Risoluzione dei problemi](#troubleshooting) la distribuzione, se necessario.  
  
6.  [Test](#testing) ed eseguire il debug del codice.  
  
 È ora possibile utilizzare Progettazione SSIS in SQL Server Data Tools (SSDT) per creare, gestire ed eseguire pacchetti destinati a versioni diverse di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ulteriori informazioni sull'impatto di questo miglioramento su estensioni personalizzate, vedere [ottenere estensioni SSIS personalizzate devono essere supportati dal supporto di più versioni di 2015 di SSDT per SQL Server 2016](https://blogs.msdn.microsoft.com/ssis/2016/04/19/getting-your-ssis-custom-extensions-to-be-supported-by-the-multi-version-support-of-ssdt-2015-for-sql-server-2016/)  
  
##  <a name="signing"></a>La firma dell'Assembly  
 Quando un assembly deve essere condiviso, è necessario installarlo nella Global Assembly Cache. Una volta aggiunto alla Global Assembly Cache, l'assembly può essere utilizzato da applicazioni come [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Un requisito della Global Assembly Cache è che l'assembly deve essere firmato con un nome sicuro che garantisca che sia globalmente univoco. Un assembly con nome sicuro dispone di un nome completo che include il nome, la lingua, la chiave pubblica e il numero di versione dell'assembly. Tali informazioni vengono utilizzate dal runtime per individuare l'assembly e distinguerlo da altri assembly aventi lo stesso nome.  
  
 Per firmare un assembly con un nome sicuro, è innanzitutto necessario avere o creare una coppia di chiavi pubblica/privata. Questa coppia di chiavi di crittografia, pubblica e privata, viene utilizzata durante la compilazione per creare un assembly con nome sicuro.  
  
 Per ulteriori informazioni sui nomi sicuri e sui passaggi che è necessario eseguire per firmare un assembly, vedere gli argomenti seguenti nella documentazione relativa a [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK:  
  
-   Assembly con nomi sicuri  
  
-   Creazione di una coppia di chiavi  
  
-   Firma di un assembly con un nome sicuro  
  
 È possibile firmare facilmente l'assembly con un nome sicuro in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] durante la compilazione. Nel **le proprietà del progetto** la finestra di dialogo, seleziona il **firma** scheda. Selezionare l'opzione per **firmare l'assembly** e quindi specificare il percorso del file di chiave (con estensione snk).  
  
##  <a name="building"></a>Compilazione dell'Assembly  
 Dopo la firma del progetto, è necessario compilare o ricompilare il progetto o soluzione utilizzando i comandi disponibili nel **compilare** dal menu di [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. La soluzione può contenere un progetto distinto per un'interfaccia utente personalizzata, che deve essere firmato con un nome sicuro e può essere compilato contemporaneamente.  
  
 Il metodo più semplice per eseguire i due passaggi successivi, ovvero la distribuzione dell'assembly e l'installazione nella Global Assembly Cache, consiste nel generare script per questi passaggi come evento di post-compilazione in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Sono disponibili gli eventi di compilazione di **compilare** pagina delle proprietà di progetto per un [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] progetto e dal **eventi di compilazione** pagina per un progetto c#. Il percorso completo è obbligatorio per le utilità della riga di comando, ad esempio **gacutil.exe**. È necessario racchiudere tra virgolette i percorsi che contengono spazi e le macro, ad esempio $(TargetPath), che si espandono in percorsi che contengono spazi.  
  
 Di seguito è riportato un esempio di una riga di comando per eventi di post-compilazione per un provider di log personalizzato:  
  
```  
"C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0A\bin\NETFX 4.0 Tools\gacutil.exe" -u $(TargetName)  
"C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0A\bin\NETFX 4.0 Tools\gacutil.exe" -i $(TargetFileName)  
copy $(TargetFileName) "C:\Program Files\Microsoft SQL Server\130\DTS\LogProviders "  
```  
  
##  <a name="deploying"></a>Distribuzione dell'Assembly  
 Il [!INCLUDE[ssIS](../../includes/ssis-md.md)] progettazione individua gli oggetti personalizzati disponibili per l'utilizzo nei pacchetti enumerando i file trovati in una serie di cartelle che vengono creati quando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] è installato. Quando il valore predefinito [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono utilizzate le impostazioni di installazione, questo set di cartelle si trova in **C:\Program Files\Microsoft SQL Server\130\DTS**. Se si crea un programma di installazione per l'oggetto personalizzato, è tuttavia necessario controllare il valore della **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\SSIS\Setup\DtsPath** chiave del Registro di sistema per verificare il percorso della cartella.  
  
> [!NOTE]  
>  Per informazioni su come distribuire i componenti personalizzati per l'uso con il supporto di più versioni di SQL Server Data Tools, vedere [ottenere estensioni SSIS personalizzate devono essere supportati dal supporto di più versioni di 2015 di SSDT per SQL Server 2016](https://blogs.msdn.microsoft.com/ssis/2016/04/19/getting-your-ssis-custom-extensions-to-be-supported-by-the-multi-version-support-of-ssdt-2015-for-sql-server-2016/).  
  
 È possibile inserire l'assembly nella cartella in due modi:  
  
-   Spostare o copiare l'assembly compilato nella cartella appropriata dopo averlo compilato. Per praticità, è possibile includere il comando di copia in un evento di post-compilazione.  
  
-   Compilare l'assembly direttamente nella cartella appropriata.  
  
 Le seguenti cartelle di distribuzione in **C:\Program Files\Microsoft SQL Server\130\DTS** vengono utilizzati per i vari tipi di oggetti personalizzati:  
  
|Oggetto personalizzato|Cartella di distribuzione|  
|-------------------|-----------------------|  
|Attività|Attività|  
|Gestione connessione|Connessioni|  
|Provider di log|LogProviders|  
|Componente del flusso di dati|PipelineComponents|  
  
> [!NOTE]  
>  Gli assembly vengono copiati in queste cartelle per supportare l'enumerazione degli oggetti personalizzati disponibili, quali attività, gestioni connessioni e così via. Pertanto, non è necessario distribuire in queste cartelle gli assembly che contengono solo l'interfaccia utente personalizzata per gli oggetti personalizzati.  
  
##  <a name="installing"></a>Installazione dell'Assembly nella Global Assembly Cache  
 Per installare l'assembly dell'attività nella global assembly cache (GAC), utilizzare lo strumento da riga di comando **gacutil.exe**, o trascinare gli assembly di `%system%\assembly` directory. Per praticità, è possibile includere anche la chiamata a **gacutil.exe** in un evento di post-compilazione.  
  
 Il comando seguente consente di installare un componente denominato *MyTask* nella GAC tramite **gacutil.exe**.  
  
 `gacutil /iF MyTask.dll`  
  
 Dopo l'installazione di una nuova versione dell'oggetto personalizzato, è necessario chiudere e riaprire Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Se sono state installate versioni precedenti dell'oggetto personalizzato nella Global Assembly Cache, è necessario rimuoverle prima di installare la nuova versione. Per disinstallare un assembly, eseguire **gacutil.exe** e specificare il nome dell'assembly con il `/u` opzione.  
  
 Per ulteriori informazioni sulla Global Assembly Cache, vedere lo strumento corrispondente (Gactutil.exe) in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Tools.  
  
##  <a name="troubleshooting"></a>Risoluzione dei problemi di distribuzione  
 Se l'oggetto personalizzato è presente il **della casella degli strumenti** o l'elenco di oggetti disponibili, ma non sono in grado di aggiungere a un pacchetto, provare le soluzioni seguenti:  
  
1.  Verificare se nella Global Assembly Cache sono disponibili più versioni del componente. In caso affermativo, è possibile che la finestra di progettazione non sia in grado di caricare il componente. Eliminare tutte le istanze dell'assembly dalla Global Assembly Cache, quindi aggiungere nuovamente l'assembly.  
  
2.  Verificare che nella cartella di distribuzione esista una singola istanza dell'assembly.  
  
3.  Aggiornare la casella degli strumenti.  
  
4.  Collegare [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a **devenv.exe** e impostare un punto di interruzione per esaminare il codice di inizializzazione per garantire che non si verificano eccezioni.  
  
##  <a name="testing"></a>Test e debug del codice  
 È l'approccio più semplice per i metodi della fase di esecuzione di un oggetto personalizzato di debug per avviare **dtexec.exe** da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dopo la creazione dell'oggetto personalizzato ed eseguire un pacchetto che utilizza il componente.  
  
 Se si desidera eseguire il debug, ad esempio i metodi del componente in fase di progettazione, il **convalida** (metodo), aprire un pacchetto che utilizza il componente in una seconda istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]e collegare il **devenv.exe** processo.  
  
 Se si desidera eseguire il debug di metodi di runtime del componente quando un pacchetto è aperto e in esecuzione in [!INCLUDE[ssIS](../../includes/ssis-md.md)] della finestra di progettazione, è necessario forzare una pausa nell'esecuzione del pacchetto in modo che è anche possibile collegare al **DtsDebugHost.exe** processo.  
  
#### <a name="to-debug-an-objects-run-time-methods-by-attaching-to-dtexecexe"></a>Per eseguire il debug dei metodi di runtime di un oggetto tramite connessione a dtexec.exe  
  
1.  Firmare e compilare il progetto nella configurazione di debug, distribuirlo e installarlo nella Global Assembly Cache come descritto in questo argomento.  
  
2.  Nel **Debug** scheda della **le proprietà del progetto**selezionare **Avvia programma esterno** come il **azione di avvio**e individuare **dtexec.exe**, cui è installato per impostazione predefinita in C:\Program Files\Microsoft SQL Server\130\DTS\Binn.  
  
3.  Nel **opzioni della riga di comando** nella casella di testo in **opzioni di avvio**, immettere gli argomenti della riga di comando necessari per eseguire un pacchetto che utilizza il componente. In genere l'argomento della riga di comando sarà costituito dall'opzione /F[ILE] seguita dal percorso e dal nome del file con estensione dtsx. Per altre informazioni, vedere [dtexec Utility](../../integration-services/packages/dtexec-utility.md).  
  
4.  Impostare i punti di interruzione nel codice sorgente, laddove appropriato, nei metodi di runtime del componente.  
  
5.  Eseguire il progetto.  
  
#### <a name="to-debug-a-custom-objects-design-time-methods-by-attaching-to-sql-server-data-tools"></a>Per eseguire il debug dei metodi della fase di progettazione di un oggetto personalizzato tramite connessione a SQL Server Data Tools  
  
1.  Firmare e compilare il progetto nella configurazione di debug, distribuirlo e installarlo nella Global Assembly Cache come descritto in questo argomento.  
  
2.  Impostare i punti di interruzione nel codice sorgente, laddove appropriato, nei metodi della fase di progettazione dell'oggetto personalizzato.  
  
3.  Aprire una seconda istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e caricare un progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenente un pacchetto in cui è utilizzato l'oggetto personalizzato.  
  
4.  La prima istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], collegare la seconda istanza di **devenv.exe** in cui viene caricato il pacchetto selezionando **Connetti a processo** dal **Debug** menu della prima istanza.  
  
5.  Eseguire il pacchetto dalla seconda istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
#### <a name="to-debug-a-custom-objects-run-time-methods-by-attaching-to-sql-server-data-tools"></a>Per eseguire il debug dei metodi di runtime di un oggetto personalizzato tramite connessione a SQL Server Data Tools  
  
1.  Dopo aver completato i passaggi elencati nella procedura precedente, forzare una pausa nell'esecuzione del pacchetto in modo che sia possibile connettersi a **DtsDebugHost.exe**. È possibile forzare questa pausa mediante l'aggiunta di un punto di interruzione di **OnPreExecute** evento, o tramite l'aggiunta di un'attività Script al progetto e passare allo script che visualizza una finestra di messaggio modale.  
  
2.  Eseguire il pacchetto. Quando si verifica la pausa, passare all'istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] in cui il progetto di codice è aperta e selezionare **Connetti a processo** dal **Debug** menu. Assicurarsi di connettersi all'istanza di **DtsDebugHost.exe** elencato come **gestito, x86** nel **tipo** colonna, non all'istanza indicata come **x86** solo.  
  
3.  Tornare al pacchetto in pausa e continuare oltre il punto di interruzione o fare clic su **OK** di chiudere la finestra di messaggio generata dall'attività Script e continuare l'esecuzione del pacchetto e il debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di oggetti personalizzati per Integration Services](../../integration-services/extending-packages-custom-objects/developing-custom-objects-for-integration-services.md)   
 [Persistenza degli oggetti personalizzati](../../integration-services/extending-packages-custom-objects/persisting-custom-objects.md)   
 [Risoluzione dei problemi relativi agli strumenti per lo sviluppo dei pacchetti](../../integration-services/troubleshooting/troubleshooting-tools-for-package-development.md)  
  
  
