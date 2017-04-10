---
title: "Riferimento all&#39;interfaccia utente dell&#39;Installazione guidata pacchetti | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.deploymentwizard.welcome.f1"
  - "sql13.dts.deploymentwizard.confirminstallation.f1"
  - "sql13.dts.deploymentwizard.deploydtspackages.f1"
  - "sql13.dts.deploymentwizard.finish.f1"
  - "sql13.dts.deploymentwizard.configurepackages.f1"
  - "sql13.dts.deploymentwizard.selectinstfolder.f1"
  - "sql13.dts.deploymentwizard.packagevalidation.f1"
  - "sql13.dts.deploymentwizard.specifytargetsqlserver.f1"
helpviewer_keywords: 
  - "Installazione guidata pacchetti"
ms.assetid: 6fca44d9-5001-4644-bcf3-c2d10a674b97
caps.latest.revision: 24
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 24
---
# Riferimento all&#39;interfaccia utente dell&#39;Installazione guidata pacchetti
  Usare l'**Installazione guidata pacchetti** per distribuire un progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], inclusi i pacchetti, i file contenuti ed eventuali dipendenze dei pacchetti.  
  
 Prima di distribuire i pacchetti, è possibile creare configurazioni e distribuirle con i pacchetti. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] usa le configurazioni per aggiornare in modo dinamico le proprietà di pacchetti e oggetti relativi in fase di esecuzione. La stringa di connessione di una connessione OLE DB può essere ad esempio impostata dinamicamente in fase di esecuzione, specificando una configurazione che esegue il mapping di un valore alla proprietà contenente la stringa di connessione.  
  
 Non è possibile eseguire l'Installazione guidata pacchetti finché non si compila un progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e non si crea un'utilità di distribuzione. Per altre informazioni, vedere [Distribuzione dei pacchetti utilizzando l'utilità di distribuzione](../../integration-services/packages/deploy-packages-by-using-the-deployment-utility.md).  
  
 Nelle sezioni seguenti vengono descritte le pagine della procedura guidata.  
  
## Pagina dell'Installazione guidata pacchetti  
 L'**Installazione guidata pacchetti** consente di distribuire un progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per cui è stata compilata un'utilità di distribuzione dei pacchetti.  
  
 **Non visualizzare più questa pagina iniziale**  
 Selezionare questa opzione per ignorare la pagina iniziale quando si esegue nuovamente la procedura guidata.  
  
 **Avanti**  
 Consente di passare alla pagina successiva della procedura guidata.  
  
 **Fine**  
 Consente di passare alla pagina Completamento Installazione guidata pacchetti. Utilizzare questa opzione se sono state controllate le scelte effettuate nelle pagine precedenti della procedura guidata e si è certi di avere specificato tutte le opzioni necessarie.  
  
## Pagina Configurazione pacchetti  
 La pagina **Configurazione pacchetti** consente di modificare le configurazioni dei pacchetti.  
  
### Opzioni  
 **File di configurazione**  
 Consente di modificare il contenuto di un file di configurazione selezionando il file dall'elenco.  
  
 **Argomenti correlati:** [Creazione delle configurazioni dei pacchetti](../../integration-services/packages/create-package-configurations.md)  
  
 **Percorso**  
 Indica il percorso della proprietà da configurare.  
  
 **Tipo**  
 Indica il tipo di dati della proprietà.  
  
 **Value**  
 Consente di specificare il valore della configurazione.  
  
 **Avanti**  
 Consente di passare alla pagina successiva della procedura guidata.  
  
 **Fine**  
 Consente di passare alla pagina Completamento Installazione guidata pacchetti. Utilizzare questa opzione se sono state controllate le scelte effettuate nelle pagine precedenti della procedura guidata e si è certi di avere specificato tutte le opzioni necessarie.  
  
## Pagina Conferma installazione  
 La pagina **Conferma installazione** consente di avviare l'installazione dei pacchetti, visualizzare lo stato e visualizzare informazioni che verranno usate dalla procedura guidata per l'installazione dei file dal progetto specificato.  
  
 **Avanti**  
 Consente di installare i pacchetti e le relative dipendenze, quindi di passare alla pagina successiva della procedura al termine dell'installazione.  
  
 **Stato**  
 Mostra lo stato dell'installazione del pacchetto.  
  
 **Fine**  
 Consente di passare alla pagina Completamento Installazione guidata pacchetti. Utilizzare questa opzione se sono state controllate le scelte effettuate nelle pagine precedenti della procedura guidata e si è certi di avere specificato tutte le opzioni necessarie.  
  
## Pagina Distribuzione pacchetti SSIS  
 Usare la pagina **Distribuzione pacchetti SSIS** per specificare il percorso d'installazione dei pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e delle relative dipendenze.  
  
### Opzioni  
 **Distribuzione nel file system**  
 Consente di distribuire i pacchetti e le dipendenze in una cartella specificata del file system.  
  
 **Distribuzione in SQL Server**  
 Consente di distribuire i pacchetti e le dipendenze in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Usare questa opzione se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] condivide i pacchetti tra i server. Le eventuali dipendenze dei pacchetti vengono installate nella cartella specificata del file system.  
  
 **Convalida pacchetti dopo l'installazione**  
 Consente di specificare se convalidare i pacchetti dopo l'installazione.  
  
 **Avanti**  
 Consente di passare alla pagina successiva della procedura guidata.  
  
 **Fine**  
 Consente di passare alla pagina Completamento Installazione guidata pacchetti. Utilizzare questa opzione se sono state controllate le scelte effettuate nelle pagine precedenti della procedura guidata e si è certi di avere specificato tutte le opzioni necessarie.  
  
## Pagina Convalida pacchetti  
 Usare la pagina **Convalida pacchetti** per visualizzare lo stato e i risultati della convalida dei pacchetti.  
  
 **Avanti**  
 Consente di passare alla pagina successiva della procedura guidata.  
  
## Pagina Selezione cartella di destinazione  
 Usare la pagina **Selezione cartella di installazione** per specificare la cartella del file system in cui installare i pacchetti e le relative dipendenze.  
  
### Opzioni  
 **Cartella**  
 Consente di specificare il percorso e la cartella in cui copiare il pacchetto e le relative dipendenze.  
  
 **Sfoglia**  
 Consente di selezionare la cartella di destinazione utilizzando la finestra di dialogo **Sfoglia cartella**.  
  
 **Avanti**  
 Consente di passare alla pagina successiva della procedura guidata.  
  
 **Fine**  
 Consente di passare alla pagina Completamento Installazione guidata pacchetti. Utilizzare questa opzione se sono state controllate le scelte effettuate nelle pagine precedenti della procedura guidata e si è certi di aver specificato tutte le opzioni necessarie.  
  
## Pagina Impostazione istanza di SQL Server di destinazione  
 Usare la pagina **Impostazione istanza di SQL Server di destinazione** per specificare le opzioni per la distribuzione del pacchetto in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### Opzioni  
 **Nome server**  
 Consente di specificare il nome del server in cui distribuire i pacchetti.  
  
 **Usa autenticazione di Windows**  
 Consente di specificare se utilizzare l'autenticazione di Windows per l'accesso al server. Per una maggiore sicurezza è consigliabile utilizzare l'autenticazione di Windows.  
  
 **Usa autenticazione di SQL Server**  
 Consente di specificare se il pacchetto deve utilizzare l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per l'accesso al server. Se si usa l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , è necessario specificare un nome utente e una password.  
  
 **Nome utente**  
 Consente di specificare un nome utente.  
  
 **Password**  
 Consente di specificare una password.  
  
 **Percorso pacchetto**  
 Consente di specificare il nome della cartella logica o immettere "/" per la cartella predefinita.  
  
 Per selezionare la cartella nella finestra di dialogo **Pacchetto SSIS**, fare clic su Sfoglia (...). Tuttavia, la finestra di dialogo non consente di selezionare la cartella predefinita. Se si desidera utilizzare la cartella predefinita, è necessario immettere "/" nella casella di testo.  
  
> [!NOTE]  
>  Se non si immette un percorso del pacchetto valido, viene visualizzato il messaggio di errore seguente: "Uno o più argomenti non sono validi."  
  
 **Usa l'archiviazione su server per la crittografia**  
 Selezionare questa opzione per usare le funzionalità di sicurezza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] per proteggere i pacchetti.  
  
 **Avanti**  
 Consente di passare alla pagina successiva della procedura guidata.  
  
 **Fine**  
 Consente di passare alla pagina Completamento Installazione guidata pacchetti. Utilizzare questa opzione se sono state controllate le scelte effettuate nelle pagine precedenti della procedura guidata e si è certi di avere specificato tutte le opzioni necessarie.  
  
## Pagina Completamento Installazione guidata pacchetti  
 Usare la pagina **Completamento Installazione guidata pacchetti** per visualizzare un riepilogo dei risultati dell'installazione dei pacchetti. In questa pagina sono specificati dettagli quali il nome del progetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] distribuito, i pacchetti installati, i file di configurazione e il percorso di installazione.  
  
 **Fine**  
 Fare clic su **Fine** per uscire dalla procedura guidata.  
  
## Vedere anche  
 [Distribuzione del pacchetto legacy &#40;SSIS&#41;](../../integration-services/packages/legacy-package-deployment-ssis.md)  
  
  