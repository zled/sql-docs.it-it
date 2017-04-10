---
title: "Controllo dell&#39;accesso per dati sensibili nei pacchetti | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "password [Integration Services]"
  - "pacchetti [Integration Services], sicurezza"
  - "livelli di protezione dei pacchetti [Integration Services]"
  - "file di configurazione [Integration Services]"
  - "crittografia [Integration Services]"
  - "crittografia [Integration Services]"
  - "sicurezza [Integration Services], livelli di protezione"
ms.assetid: d4b073c4-4238-41fc-a258-4e114216e185
caps.latest.revision: 44
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 44
---
# Controllo dell&#39;accesso per dati sensibili nei pacchetti
  Per proteggere i dati in un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], è possibile impostare un livello di protezione in modo da proteggere i dati sensibili o tutti i dati all'interno del pacchetto. Inoltre, è possibile crittografare questi dati con una password o una chiave utente o utilizzare il sistema di crittografia del database. Inoltre, il livello di protezione che si utilizza per un pacchetto non è necessariamente statico, ma cambia durante tutto il ciclo di vita del pacchetto. Spesso si imposta un livello di protezione durante lo sviluppo e un altro appena si distribuisce il pacchetto.  
  
> [!NOTE]  
>  Oltre ai livelli di protezione descritti in questo argomento, è possibile usare i ruoli predefiniti a livello di database per proteggere i pacchetti salvati nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## Definizione di informazioni riservate  
 In un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] le informazioni seguenti sono definite *riservate*:  
  
-   La password di una stringa di connessione. Se, tuttavia, si seleziona un'opzione che implica la crittografia dell'intero pacchetto, viene considerata riservata l'intera stringa di connessione.  
  
-   I nodi XML generati dall'attività contrassegnati come riservati. L'aggiunta di tag ai nodi XML viene controllata da [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e non può essere modificata dagli utenti.  
  
-   Qualsiasi variabile contrassegnata come riservata. Le variabili vengono contrassegnate come riservate da [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] una proprietà viene considerata riservata a seconda se lo sviluppatore del componente di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , ad esempio una gestione connessione o un'attività, abbia definito la proprietà come riservata. Gli utenti non possono aggiungere proprietà all'elenco di proprietà considerate riservate, né possono rimuoverle.  
  
## Crittografia  
 La crittografia applicata con i livelli di protezione dei pacchetti viene eseguita tramite l'API [!INCLUDE[msCoName](../../includes/msconame-md.md)] Data Protection (DPAPI), che fa parte dell'API Cryptography (CryptoAPI).  
  
 Con i livelli di protezione dei pacchetti che implicano la crittografia con password anche l'utente autorizzato a modificare l'origine deve specificare una password. Se tale utente sostituisce un livello di protezione che non richiede la password con un livello che la richiede, verrà richiesto di specificare una password.  
  
 Inoltre, per i livelli di protezione che prevedono una password, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] usa l'algoritmo di crittografia Triple DES con lunghezza di chiave di 192 bit, disponibile nella libreria di classi [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] (FCL).  
  
## Livelli di protezione  
 Nella tabella seguente vengono descritti i livelli di protezione disponibili in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. I valori tra parentesi derivano dall'enumerazione <xref:Microsoft.SqlServer.Dts.Runtime.DTSProtectionLevel>. e sono visualizzati nella finestra Proprietà utilizzata per la configurazione delle proprietà del pacchetto quando si utilizzano i pacchetti in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
|Livello di protezione|Descrizione|  
|----------------------|-----------------|  
|Non salva i dati sensibili (**DontSaveSensitive**)|Quando si salva il pacchetto, i valori delle proprietà riservate vengono eliminati. Con questo livello di protezione i dati non vengono crittografati, ma le proprietà contrassegnate come riservate non vengono salvate insieme al pacchetto. Di conseguenza i dati riservati non sono disponibili ad altri utenti, i quali dovranno specificarli quando aprono il pacchetto.<br /><br /> Se usato con l'utilità **dtutil** (dtutil.exe), questo livello di protezione corrisponde al valore 0.|  
|Crittografa tutti i dati con una password (**EncryptAllWithPassword**)|Viene utilizzata una password per crittografare l'intero pacchetto. Il pacchetto viene crittografato con una password specificata dall'utente in fase di creazione o di esportazione del pacchetto. Per aprire il pacchetto in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o per eseguirlo con l'utilità del prompt dei comandi **dtexec**, l'utente deve specificare la password del pacchetto. Se non specifica la password corretta, l'utente non può né aprire né eseguire il pacchetto.<br /><br /> Se usato con l'utilità **dtutil**, questo livello di protezione corrisponde al valore 3.|  
|Crittografa tutti i dati con una chiave utente (**EncryptAllWithUserKey**)|Viene utilizzata una chiave basata sul profilo utente corrente per crittografare l'intero pacchetto. Il pacchetto può essere aperto in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o eseguito con l'utilità del prompt dei comandi **dtexec** solo dall'utente che lo ha creato o esportato.<br /><br /> Se usato con l'utilità **dtutil**, questo livello di protezione corrisponde al valore 4.<br /><br /> Nota: per i livelli di protezione che prevedono una chiave utente, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] usa gli standard DPAPI. Per altre informazioni su DPAPI, vedere il sito MSDN Library all'indirizzo [http://msdn.microsoft.com/library](http://go.microsoft.com/fwlink/?LinkId=15408).|  
|Crittografa tutti i dati sensibili con una password (**EncryptSensitiveWithPassword**)|Viene utilizzata una password per crittografare solo i valori delle proprietà riservate nel pacchetto. Per la crittografia viene utilizzato DPAPI. I dati riservati vengono salvati come parte del pacchetto, ma crittografati tramite una password specificata dall'utente corrente in fase di creazione o di esportazione del pacchetto. Per poter aprire il pacchetto in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)], l'utente deve specificare la password. Se non specifica la password, il pacchetto viene aperto senza i dati riservati e l'utente corrente deve specificare nuovi valori per questi dati. I tentativi di esecuzione del pacchetto senza specificare la password hanno esito negativo. Per altre informazioni sulle password e sull'esecuzione dell'utilità della riga di comando, vedere [Utilità dtexec](../../integration-services/packages/dtexec-utility.md).<br /><br /> Se usato con l'utilità **dtutil**, questo livello di protezione corrisponde al valore 2.|  
|Crittografa tutti i dati sensibili con una chiave utente (**EncryptSensitiveWithPassword**)|Viene utilizzata una chiave basata sul profilo utente corrente per crittografare solo i valori delle proprietà riservate nel pacchetto. Il pacchetto può essere caricato solo da uno stesso utente in base allo stesso profilo. Gli altri utenti che aprono il pacchetto dovranno immettere le informazioni riservate. I tentativi di esecuzione del pacchetto hanno esito negativo. Per la crittografia viene utilizzato DPAPI.<br /><br /> Se usato con l'utilità **dtutil**, questo livello di protezione corrisponde al valore 1.<br /><br /> Nota: per i livelli di protezione che prevedono una chiave utente, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] usa gli standard DPAPI. Per altre informazioni su DPAPI, vedere il sito MSDN Library all'indirizzo [http://msdn.microsoft.com/library](http://go.microsoft.com/fwlink/?LinkId=15408).|  
|Usa l'archiviazione su server per la crittografia (**ServerStorage**)|Protegge l'intero pacchetto tramite ruoli del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa opzione è supportata quando i pacchetti vengono salvati nel database msdb di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Anche il catalogo SSISDB usa il livello di protezione **ServerStorage**.<br /><br /> Questa opzione non è supportata quando un pacchetto viene salvato nel file system da [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].|  
  
## Impostazione del livello di protezione e catalogo SSISDB  
 Il catalogo SSISDB usano il livello di protezione **ServerStorage** . Quando si distribuisce un progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], il catalogo crittografa automaticamente i dati e i valori sensibili del pacchetto. Il catalogo inoltre decrittografa automaticamente i dati quando viene recuperato.  
  
 Se si esporta il progetto (file con estensione ispac) dal server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] al file system, il sistema modifica automaticamente il livello di protezione in **EncryptSensitiveWithUserKey**. Se si importa il progetto usando **Importazione guidata progetto di Integration Services** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], la proprietà **ProtectionLevel** nella finestra **Proprietà** mostra il valore **EncryptSensitiveWithUserKey**.  
  
## Impostazione del livello di protezione sulla base del ciclo di vita del pacchetto  
 Il livello di protezione di un pacchetto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] viene impostato quando il pacchetto viene sviluppato per la prima volta in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. È possibile aggiornarlo successivamente quando il pacchetto viene distribuito, importato o esportato da [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] a [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oppure copiato da [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], nell'archivio pacchetti [!INCLUDE[ssIS](../../includes/ssis-md.md)] o nel file system. Si supponga, ad esempio, che nei computer in uso vengano creati e salvati pacchetti in base a una delle opzioni di livello di protezione con chiave utente. Se successivamente i pacchetti vengono distribuiti ad altri utenti, sarà necessario modificarne il livello di protezione in modo che possano essere aperti dagli altri utenti.  
  
 In genere, il livello di protezione viene modificato come spiegato nei passaggi seguenti:  
  
1.  Durante lo sviluppo, lasciare il livello di protezione dei pacchetti impostato sul valore predefinito **EncryptSensitiveWithUserKey**. Con questa impostazione si avrà la certezza che solo lo sviluppatore veda i valori riservati nel pacchetto. In alternativa, è possibile provare a usare **EncryptAllWithUserKey** o **DontSaveSensitive**.  
  
2.  Al momento di distribuire i pacchetti, è necessario impostare un livello di protezione che non dipenda dalla chiave utente dello sviluppatore. Di conseguenza, in genere è necessario selezionare **EncryptSensitiveWithPassword** o **EncryptAllWithPassword**. Crittografare i pacchetti assegnando una password complessa temporanea che è nota anche dal team di gestione nell'ambiente di produzione.  
  
3.  Dopo che i pacchetti sono stati distribuiti all'ambiente di produzione, il team di gestione può crittografare nuovamente i pacchetti distribuiti assegnando una password complessa nota solo dal team stesso. In alternativa, può crittografare i pacchetti distribuiti selezionando **EncryptSensitiveWithUserKey** o **EncryptAllWithUserKey** e usando le credenziali locali dell'account per l'esecuzione dei pacchetti.  
  
## Attività correlate  
  
-   [Impostazione o modifica del livello di protezione dei pacchetti](../../integration-services/packages/set-or-change-the-protection-level-of-packages.md)  
  
## Vedere anche  
 [Importare ed esportare pacchetti &#40;servizio SSIS&#41;](../../integration-services/service/import-and-export-packages-ssis-service.md)   
 [Pacchetti di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-packages.md)   
 [Panoramica della sicurezza &#40;Integration Services&#41;](../../integration-services/security/security-overview-integration-services.md)  
  
  