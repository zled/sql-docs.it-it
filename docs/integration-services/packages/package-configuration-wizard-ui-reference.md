---
title: "Riferimento all&#39;interfaccia utente della Configurazione guidata pacchetti | Microsoft Docs"
ms.custom: ""
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.configwizard.finishdtsconfiguration.f1"
  - "sql13.dts.configwizard.selectobjects.f1"
  - "sql13.dts.configwizard.selecconfigtype.f1"
  - "sql13.dts.configwizard.welcome.f1"
ms.assetid: adca6938-6d5a-40ec-950e-dceb79d044fe
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# Riferimento all&#39;interfaccia utente della Configurazione guidata pacchetti
  Usare la **Configurazione guidata pacchetto** per creare configurazioni tramite cui è possibile aggiornare le proprietà di un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e i relativi oggetti in fase di esecuzione. Questa procedura guidata viene eseguita quando si aggiunge una nuova configurazione o se ne modifica una esistente nella finestra di dialogo **Libreria configurazioni pacchetto**. Per aprire la finestra di dialogo **Libreria configurazioni pacchetto**, selezionare **Configurazioni pacchetto** nel menu **SSIS** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Per altre informazioni, vedere [Creazione di configurazioni dei pacchetti](../../integration-services/packages/create-package-configurations.md).  
  
> **NOTA:** le configurazioni sono disponibili per il modello di distribuzione del pacchetto. I parametri vengono utilizzati al posto delle configurazioni per il modello di distribuzione del progetto. Con il modello di distribuzione del progetto è possibile distribuire i progetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] al server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Per altre informazioni sui modelli di distribuzione, vedere [Distribuzione di progetti e pacchetti](https://msdn.microsoft.com/library/hh213290.aspx).  
  
 Nelle sezioni seguenti vengono descritte le pagine della procedura guidata.  
  
## Pagina della Configurazione guidata pacchetto  
 Usare la **Configurazione guidata SSIS** per creare configurazioni in grado di aggiornare le proprietà di un pacchetto e i relativi oggetti in fase di esecuzione.  
  
### Opzioni  
 **Non visualizzare più questa pagina**  
 Consente di evitare la visualizzazione della pagina di benvenuto alla successiva apertura della procedura guidata.  
  
 **Avanti**  
 Consente di passare alla pagina successiva della procedura guidata.  
  
## Pagina Selezione tipo di configurazione  
 Usare la pagina **Selezione tipo di configurazione** per specificare il tipo di configurazione da creare.  
  
 Per altre informazioni sulla selezione del tipo di configurazione da usare, vedere [Configurazioni di pacchetto](../../integration-services/packages/package-configurations.md).  
  
### Opzioni statiche  
 **Tipo configurazione**  
 Selezionare una delle opzioni seguenti per impostare il tipo di origine in cui archiviare la configurazione:  
  
|Valore|Description|  
|-----------|-----------------|  
|**File di configurazione XML**|Consente di archiviare la configurazione come file in formato XML. Tramite la selezione di questo valore le opzioni dinamiche vengono visualizzate nella sezione **Tipo configurazione**.|  
|**Variabile di ambiente**|Consente di archiviare la configurazione in una delle variabili di ambiente. Tramite la selezione di questo valore le opzioni dinamiche vengono visualizzate nella sezione **Tipo configurazione**.|  
|**Voce del Registro di sistema**|Consente di archiviare la configurazione nel Registro di sistema. Tramite la selezione di questo valore le opzioni dinamiche vengono visualizzate nella sezione **Tipo configurazione**.|  
|**Variabile pacchetto padre**|Consente di archiviare la configurazione come variabile nel pacchetto contenente l'attività.  Tramite la selezione di questo valore le opzioni dinamiche vengono visualizzate nella sezione **Tipo configurazione**.|  
|**SQL Server**|Consente di archiviare la configurazione in una tabella in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Tramite la selezione di questo valore le opzioni dinamiche vengono visualizzate nella sezione **Tipo configurazione**.|  
  
 **Avanti**  
 Consente di visualizzare la pagina successiva della procedura guidata.  
  
### Opzioni dinamiche  
  
#### Opzione tipo di configurazione = File di configurazione XML  
 **Usa le impostazioni di configurazione specificate di seguito**  
 Consente di specificare le impostazioni da utilizzare.  
  
|Valore|Description|  
|-----------|-----------------|  
|**Nome file di configurazione**|Consente di digitare il percorso del file di configurazione generato dalla procedura guidata.|  
|**Sfoglia**|Usare la finestra di dialogo **Selezionare il percorso del file di configurazione** per impostare il percorso del file di configurazione generato dalla procedura guidata. Se il file non esiste, verrà creato durante la procedura guidata.|  
  
 **Percorso della configurazione memorizzato in una variabile di ambiente**  
 Consente di specificare la variabile di ambiente in cui memorizzare la configurazione.  
  
|Valore|Description|  
|-----------|-----------------|  
|**Variabile di ambiente**|Consente di selezionare una variabile di ambiente nell'elenco.|  
  
#### Opzione tipo di configurazione = Variabile di ambiente  
 **Variabile di ambiente**  
 Consente di selezionare la variabile di ambiente contenente le informazioni di configurazione.  
  
#### Opzione tipo di configurazione = Voce del Registro di sistema  
 **Usa le impostazioni di configurazione specificate di seguito**  
 Consente di specificare le impostazioni da utilizzare.  
  
|Valore|Description|  
|-----------|-----------------|  
|**Voce del Registro di sistema**|Digitare la chiave del Registro di sistema contenente le informazioni di configurazione Il formato è \<chiave del Registro di sistema>.<br /><br /> È necessario che la chiave del Registro di sistema esista già in HKEY_CURRENT_USER e che il suo valore sia denominato Value. Il valore può essere un DWORD o una stringa.<br /><br /> Se si desidera usare una chiave del Registro di sistema che non si trova nella radice HKEY_CURRENT_USER, per identificare la chiave usare il formato \<chiave Registro di sistema\chiave Registro di sistema\\...>.|  
  
 **Percorso della configurazione memorizzato in una variabile di ambiente**  
 Consente di specificare la variabile di ambiente in cui memorizzare la configurazione.  
  
|Valore|Description|  
|-----------|-----------------|  
|**Variabile di ambiente**|Consente di selezionare una variabile di ambiente nell'elenco.|  
  
#### Opzione tipo di configurazione = Variabile pacchetto padre  
 **Usa le impostazioni di configurazione specificate di seguito**  
 Consente di specificare le impostazioni da utilizzare.  
  
|Valore|Description|  
|-----------|-----------------|  
|**Variabile padre**|Consente di specificare la variabile inclusa nel pacchetto padre contenente le informazioni di configurazione.|  
  
 **Percorso della configurazione memorizzato in una variabile di ambiente**  
 Consente di specificare la variabile di ambiente in cui viene memorizzata la configurazione.  
  
|Valore|Description|  
|-----------|-----------------|  
|**Variabile di ambiente**|Consente di selezionare una variabile di ambiente nell'elenco.|  
  
#### Opzione tipo di configurazione = SQL Server  
 **Usa le impostazioni di configurazione specificate di seguito**  
 Consente di specificare le impostazioni da utilizzare.  
  
|Valore|Description|  
|-----------|-----------------|  
|**Connessione**|Consente di selezionare una connessione nell'elenco o di creare una nuova connessione facendo clic su **Nuova**.|  
|**Tabella configurazione**|Consente di selezionare una tabella esistente o di creare una nuova tabella facendo clic su **Nuova** per scrivere un'apposita istruzione SQL.|  
|**Filtro configurazione**|Consente di selezionare un nome esistente o di digitarne uno nuovo per la configurazione.<br /><br /> È possibile memorizzare nella stessa tabella molteplici configurazioni di SQL Server, ciascuna delle quali può includere più elementi di configurazione.<br /><br /> Questo valore definito dall'utente è memorizzato nella tabella per identificare gli elementi della configurazione appartenenti a una configurazione specifica.|  
  
 **Percorso della configurazione memorizzato in una variabile di ambiente**  
 Consente di specificare la variabile di ambiente in cui è memorizzata la configurazione.  
  
|Valore|Description|  
|-----------|-----------------|  
|**Variabile di ambiente**|Consente di selezionare una variabile di ambiente nell'elenco.|  
  
## Pagina Selezione oggetti da esportare  
 Usare la pagina **Selezione proprietà di destinazione o Selezione proprietà da esportare** per specificare le proprietà degli oggetti incluse nella configurazione. La possibilità di selezionare più impostazioni è disponibile solo se si seleziona il tipo di configurazione XML.  
  
### Opzioni  
 **Oggetti**  
 Consente di espandere la gerarchia del pacchetto e di selezionare le proprietà da esportare.  
  
 **Attributi proprietà**  
 Consente di visualizzare gli attributi di una proprietà.  
  
 **Avanti**  
 Consente di passare alla pagina successiva della procedura guidata.  
  
## Pagina Completamento procedura guidata  
 La pagina **Completamento procedura guidata** consente di assegnare un nome per le impostazioni di configurazione e visualizzazione usate dalla procedura guidata per creare la configurazione. Dopo il completamento della procedura guidata, verrà visualizzato **Libreria configurazioni pacchetto** in cui sono elencate tutte le configurazioni per il pacchetto.  
  
### Opzioni  
 **Nome configurazione**  
 Consente di digitare il nome della configurazione.  
  
 **Anteprima**  
 Consente di visualizzare le impostazioni utilizzate dalla procedura guidata per creare la configurazione.  
  
 **Fine**  
 Consente di creare la configurazione e uscire dalla **Configurazione guidata pacchetto**.  
  
## Vedere anche  
 [Creazione di configurazioni dei pacchetti](../../integration-services/packages/create-package-configurations.md)  
  
  