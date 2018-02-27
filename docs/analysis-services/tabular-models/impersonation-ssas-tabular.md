---
title: Rappresentazione nei modelli tabulari di Analysis Services | Documenti Microsoft
ms.custom: 
ms.date: 10/16/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fcc79e96-182a-45e9-8ae2-aeb440e9bedd
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 24d32bd54651eb173ca6de920d9e457c6331c8ca
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="impersonation"></a>Rappresentazione 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
Questo articolo fornisce agli autori di modelli tabulari una conoscenza di come credenziali di accesso vengono utilizzate da Analysis Services quando ci si connette a un'origine dati per importare ed elaborare (aggiornare) i dati.  

##  <a name="bkmk_conf_imp_info"></a> Configurazione della rappresentazione  
 La posizione e il contesto di un modello esistente determina la configurazione di rappresentazione. Quando si crea un nuovo progetto di modello, la rappresentazione è configurata in SQL Server Data Tools (SSDT) quando ci si connette a un'origine dati per importare i dati. Dopo aver distribuito un modello, la rappresentazione può configurata nella proprietà di stringa di connessione di database modello tramite SQL Server Management Studio (SSMS). Per i modelli tabulari in Azure Analysis Services, è possibile utilizzare SQL Server Management Studio o **visualizzare come: Script** modalità nella finestra di progettazione basata su browser per modificare il file Model.bim in JSON.
  
##  <a name="bkmk_how_imper"></a> Utilizzo della rappresentazione  
 La*rappresentazione* è la capacità di un'applicazione server, ad esempio Analysis Services, di assumere l'identità di un'applicazione client. Analysis Services viene eseguito utilizzando un account del servizio, tuttavia, quando il server viene stabilita una connessione a un'origine dati, viene utilizzata la rappresentazione in modo che i controlli di accesso per l'elaborazione e l'importazione dei dati può essere eseguita.  
  
 Credenziali utilizzate per la rappresentazione sono diverse da quelle che attualmente è connessi con. Credenziali vengono utilizzate per particolari operazioni lato client durante la creazione di un modello utente connesso.  
  
 È importante comprendere come le credenziali di rappresentazione vengono specificate e protetti, nonché la differenza tra i contesti in cui sia quello usato in vengono utilizzate le credenziali dell'utente e quando vengono utilizzate altre credenziali di rappresentazione.  
  
 **Informazioni sulle credenziali lato server**  
 
Quando i dati vengono importati o elaborati, le credenziali di rappresentazione vengono utilizzate per connettersi all'origine dati e recuperare i dati. Si tratta di un *sul lato server* operazione in esecuzione nel contesto di un'applicazione client, perché il server di Analysis Services che ospita il database dell'area di lavoro si connette all'origine dati e recupera i dati.  
  
 Quando si distribuisce un modello in un server Analysis Services, se il database dell'area di lavoro è in memoria durante la distribuzione del modello, le credenziali vengono passate al server Analysis Services in cui viene distribuito il modello. In nessuna circostanza si stratta di credenziali utente archiviate su disco.  
  
 Quando un modello distribuito vengono elaborati i dati da un'origine dati, le credenziali di rappresentazione, persistente nel database in memoria, vengono utilizzate per connettersi all'origine dati e recuperare i dati. Poiché questo processo viene gestito dal server di Analysis Services, gestione del database modello, si tratta nuovamente di un'operazione lato server.  
  
 **Informazioni sulle credenziali lato client**  
  
 Quando un nuovo modello di creazione o l'aggiunta di un'origine dati a un modello esistente, connettersi a un'origine dati e selezionare le tabelle e viste da importare nel modello. Nelle funzionalità di anteprima e filtro importazione guidata tabella o ottenere Data\Query finestra di progettazione, viene visualizzato un campione di dati importate. Inoltre, è possibile specificare filtri per escludere dati che non devono essere inclusi nel modello.  
  
 Analogamente, per i modelli esistenti che sono già stati creati, utilizzare il **proprietà tabella** finestra di dialogo Anteprima e filtrare i dati importati in una tabella.  
  
 Le funzionalità di anteprima e filtro **proprietà tabella**, e **gestione partizioni** finestre di dialogo sono un in-process *sul lato client* operazione, ovvero quella che viene effettuata durante l'esecuzione operazione sono diverse dalle modalità di connessione per l'origine dati e vengono recuperati dall'origine dati; un'operazione lato server. Le credenziali utilizzate per l'anteprima e il filtro dei dati sono quelle dell'utente attualmente connesso. In concreto, le credenziali. 
  
 La separazione di credenziali utilizzato sul lato server e operazioni lato client possono causare una mancata corrispondenza tra ciò che viene visualizzato e quali dati vengono recuperati durante un'importazione o di un processo (un'operazione lato server). Se le credenziali attualmente connessi con le credenziali di rappresentazione specificate sono diverse, i dati presenti le funzionalità di anteprima e filtro o **proprietà tabella** finestra di dialogo e i dati recuperati durante un'importazione o processo può essere diverso, a seconda delle credenziali richieste dall'origine dati.  
  
> [!IMPORTANT]  
>  Quando si crea un modello, verificare che le credenziali che si è connessi con e le credenziali specificate per la rappresentazione dispongano di diritti sufficienti per recuperare i dati dall'origine dati.  
  
##  <a name="bkmk_imp_info_options"></a> Opzioni  
 Quando si configura la rappresentazione o si modificano proprietà per una connessione all'origine dati esistente, specificare una delle opzioni seguenti:  
  
**Modelli tabulari 1400 e versioni successive**
 
|Opzione|Description|  
|------------|-----------------|  
|**Rappresenta l'Account**|Specifica il modello viene utilizzato un account utente di Windows per importare o elaborare dati dall'origine dati. Il dominio e il nome dell'account utente nel formato seguente:**\<nome di dominio >\\< nome dell'account utente\>**.|  
|**Rappresentare l'utente corrente**|Specifica che devono accedere ai dati dall'origine dati utilizzando l'identità dell'utente che ha inviato la richiesta. Questa modalità si applica solo in modalità DirectQuery.|  
|**Rappresentare l'identità**|Specifica un nome utente per accedere a origine dati, ma non è necessario specificare la password dell'account. Questa modalità si applica solo quando la delega Kerberos è abilitata e specifica che l'autenticazione S4U deve essere utilizzato.|  
|**Rappresenta l'Account del servizio**|Specifica l'utilizzo di modello le credenziali di sicurezza associate all'istanza del servizio Analysis Services che gestisce il modello.|  
|**Rappresentare l'Account automatico**|Specifica che il motore Analysis Services deve utilizzare un account automatico preconfigurati per accedere ai dati.|  


**Modelli tabulari 1200**
 
|Opzione|Description|  
|------------|-----------------|  
|**Specifica nome utente di Windows e password**|Questa opzione specifica il modello viene utilizzato un account utente di Windows per importare o elaborare dati dall'origine dati. Il dominio e il nome dell'account utente nel formato seguente:**\<nome di dominio >\\< nome dell'account utente\>**. Si tratta dell'opzione predefinita per la creazione di un nuovo modello tramite l'Importazione guidata tabella.|  
|**Account servizio**|Questa opzione consente di specificare che nel modello vengono utilizzate le credenziali di sicurezza associate all'istanza del servizio Analysis Services tramite cui viene gestito il modello.|  
  
##  <a name="bkmk_impers_sec"></a> Sicurezza  
 Le credenziali utilizzate con la rappresentazione sono persistenti in memoria dal motore di VertiPaq™. Credenziali non vengono mai scritti su disco. Se il database dell'area di lavoro non è in memoria quando il modello viene distribuito, l'utente viene richiesto di immettere le credenziali utilizzate per connettersi ai dati di origine dati e di recupero.  
  
> [!NOTE]  
>  Si consiglia di specificare un account utente di Windows e una password per le credenziali di rappresentazione. Un account utente di Windows può essere configurato per utilizzare privilegi minimi necessari per connettersi e leggere i dati dall'origine dati.  
  

  
## <a name="see-also"></a>Vedere anche  
 [Modalità DirectQuery](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Origini dati](../../analysis-services/tabular-models/data-sources-ssas-tabular.md)   
 [Distribuzione di una soluzione del modello tabulare](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)  
  
  
