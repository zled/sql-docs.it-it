---
title: Il cmdlet Set-PowerPivotServiceApplication | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a0951f53451141ead27cc3d7aa5f1346dbb47694
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="set-powerpivotserviceapplication-cmdlet"></a>Cmdlet Set-PowerPivotServiceApplication
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Imposta le proprietà di un'applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  

>[!NOTE] 
>In questo articolo può contenere esempi e informazioni non aggiornate. Usare il cmdlet Get-Help per la versione più recente.
  
 **Applicabile a:** SharePoint 2010 e SharePoint 2013.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Set-PowerPivotServiceApplication [-Identity] <SPGeminiServiceApplicationPipeBind> [-AdministrationConnectionPoolSize <int>] [-AllowCustomWindowsCredentials] [-BusinessHoursEndTime <string>] [-BusinessHoursStartTime <string>] [-CachedDatabaseholdLimit <int>] [-Confirm <switch>] [-ConnectionPoolSize <int>] [-ConnectionPoolTimeout <int>] [-DataLoadTimeout <int>] [-DataRefreshFailureThreshold <int>] [-DataRefreshInactiveWorkbooksThreshold <int>] [-DataRefreshMaxHistory <int>] [-HealthBasedAllocation <switch>] [-LoadsToConnectionsRatioCollectionInterval <int>] [-LoadsToConnectionsRatioLimit <int>] [-MemoryDatabaseHoldLimit <int>] [-QueryReportingInterval <int>] [-RoundRobinAllocation <switch>] [-UnattendedAccount <string>] [-UsageDataRetentionPeriod <int>] [-UsageExpectedResponseUpperLimit <int>] [-UsageLongResponseUpperLimit <int>] [-UsageQuickResponseUpperLimit <int>] [-UsageTrivialResponseUpperLimit <int>] [-UsageUpdateDayLimit <int>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 Il cmdlet Set-PowerPivotServiceApplication aggiorna le proprietà di un'applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nella farm. Il parametro Identity è obbligatorio. È necessario fornire il GUID dell'applicazione di servizio per la quale si stanno aggiornando le proprietà.  
  
 Per verificare le modifiche, eseguire il cmdlet seguente: Get-PowerPivotServiceApplication-Identity \<GUID > | formato elenco.  
  
## <a name="parameters"></a>Parametri  
  
### <a name="-identity-spgeminiserviceapplicationpipebind"></a>-Identity \<SPGeminiServiceApplicationPipeBind >  
 Specifica l'applicazione di servizio da aggiornare. Il tipo deve essere un GUID valido o un'istanza di un oggetto applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] valido. È possibile utilizzare Get-PowerPivotServiceApplication per restituire un'istanza dell'oggetto.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|true|  
|Accettare caratteri jolly?|false|  
  
### <a name="-administrationconnectionpoolsize-int"></a>-AdministrationConnectionPoolSize \<int >  
 Specifica il numero di connessioni aperte in un pool di connessioni creato per una connessione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ad Analysis Services. In ogni istanza del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] viene aperta una connessione amministrativa separata all'istanza di Analysis Services sullo stesso computer. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] consente di creare un pool separato per riutilizzare le connessioni amministrative allo scopo di verificare la presenza di connessioni inattive e monitorare l'integrità del server. Il valore predefinito è 200 connessioni. I valori validi sono -1 (senza limiti), 0 (pool di connessioni amministrative disabilitati) oppure un valore compreso tra 1 e 10000. Se si seleziona 0, ogni connessione verrà creata da zero.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|200|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-allowcustomwindowscredentials-switchparameter"></a>-AllowCustomWindowsCredentials [\<SwitchParameter >]  
 Specifica se i proprietari della pianificazione possono immettere credenziali di Windows arbitrarie per eseguire una pianificazione dell'aggiornamento dati. Se si seleziona questa casella di controllo, l'applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] creerà e gestirà un'applicazione di destinazione per ciascun set di credenziali archiviate. L'impostazione predefinita è true. Per disabilitare questa funzionalità, impostare AllowCustomWindowsCredentials:$false.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-businesshoursendtime-string"></a>-BusinessHoursEndTime \<string>  
 Specifica il punto finale in un intervallo di ore che definisce un giorno lavorativo. Le pianificazioni dell'aggiornamento dati possono essere eseguite al termine di un giorno lavorativo per selezionare i dati transazionali generati durante il normale orario di ufficio. L'impostazione predefinita è 8:00 p.m.  I valori validi vengono specificati tra virgolette, con l'indicazione a.m. o p.m., ad esempio, "08:00PM". Le ore devono essere comprese nell'intervallo da 1 a 12. I minuti devono essere compresi nell'intervallo da 1 a 59.  
  
 Per specificare l'intervallo completo di ore per un giorno lavorativo, è necessario impostare sia BusinessHoursStartTime che BusinessHoursEndTime. Con i due parametri è possibile definire l'intervallo di ore che costituisce un giorno lavorativo.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|8 PM|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-businesshoursstarttime-string"></a>-BusinessHoursStartTime \<string>  
 Specifica il punto iniziale in un intervallo di ore che definisce un giorno lavorativo. Le pianificazioni dell'aggiornamento dati possono essere eseguite al termine di un giorno lavorativo per selezionare i dati transazionali generati durante il normale orario di ufficio. L'impostazione predefinita è 4:00 a.m.  I valori validi vengono specificati tra virgolette, con l'indicazione a.m. o p.m., ad esempio, "04:00AM". Le ore devono essere comprese nell'intervallo da 1 a 12. I minuti devono essere compresi nell'intervallo da 1 a 59.  
  
 Per specificare l'intervallo completo di ore per un giorno lavorativo, è necessario impostare sia BusinessHoursStartTime che BusinessHoursEndTime. Con i due parametri è possibile definire l'intervallo di ore che costituisce un giorno lavorativo.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|4 AM|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-cacheddatabaseholdlimit-int"></a>-CachedDatabaseholdLimit \<int>  
 Specifica il numero di ore di permanenza di un database inattivo nel file system dopo essere stato scaricato dalla memoria. L'impostazione predefinita è 120 ore. Questa impostazione viene utilizzata dal processo di pulizia per determinare i file da eliminare. Tutti i database [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] che sono inattivi per 168 ore (48 ore in memoria e 120 nella cache) vengono eliminati dal disco dal processo di pulizia.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|120|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-confirm-switch"></a>-Confirm \<passare >  
 Richiede la conferma dell'utente prima dell'esecuzione del comando. Questo valore è abilitato per impostazione predefinita. Per ignorare la risposta di conferma in un comando, specificare Confirm:$false nel comando.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-connectionpoolsize-int"></a>-ConnectionPoolSize \<int >  
 Specifica il numero massimo di connessioni inattive create dal servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nei singoli pool di connessioni per ogni combinazione di versione, set di dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] e utente di SharePoint. Il valore predefinito è 1000 connessioni inattive. I valori validi sono -1 (senza limiti), 0 (pool di connessioni utente disabilitati) oppure un valore compreso tra 1 e 10000. Questi pool di connessioni consentono al servizio di supportare in modo più efficiente connessioni in corso agli stessi dati in sola lettura da parte dello stesso utente. Se si disabilita pool di connessioni, ogni connessione sarà creata di nuovo. La modifica del limite sulle dimensioni dei pool di connessioni, anche se impostata a 0, non causa l'interruzione delle connessioni. I pool di connessioni hanno la funzione di ridurre i tempi di attesa durante la connessione ai dati. Il servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] non negherà mai una connessione in base alle impostazioni del pool di connessioni.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|1000|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-connectionpooltimeout-int"></a>-ConnectionPoolTimeout \<int >  
 Specifica per quanti minuti rimane aperta una connessione dati inattiva. Il valore predefinito è 1800 secondi (o 30 minuti). Durante questo periodo, l'applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] riutilizzerà una connessione dati inattiva per le richieste di sola lettura provenienti dallo stesso utente di SharePoint per gli stessi dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Se non vengono ricevute ulteriori richieste di dati durante il periodo specificato, la connessione viene rimossa dal pool. I valori validi sono compresi tra 1 e 3600 secondi.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|1800|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-dataloadtimeout-int"></a>-DataLoadTimeout \<int >  
 Specifica il tempo di attesa da parte dell'applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per una risposta dall'istanza di SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) a cui è stata inoltrata una richiesta di caricamento dati. Poiché lo spostamento di set di dati di dimensioni molto elevate richiede tempo, è necessario consentire un tempo sufficiente all'istanza del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per recuperare la cartella di lavoro di Excel e spostare i dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in un'istanza di Analysis Services per l'elaborazione delle query. Il valore predefinito è 1800 secondi (o 30 minuti). I valori validi sono compresi tra 1 e 3600 secondi.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|1800|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-datarefreshfailurethreshold-int"></a>-DataRefreshFailureThreshold \<int >  
 Specifica il numero di errori consecutivi dopo cui viene disabilitata una pianificazione. Il valore predefinito è 10. È possibile anche immettere 0 per non disabilitare mai una pianificazione a causa di errori di aggiornamento.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|10|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-datarefreshinactiveworkbooksthreshold-int"></a>-DataRefreshInactiveWorkbooksThreshold \<int >  
 Specifica il numero di cicli di aggiornamento dati dopo cui una pianificazione viene disabilitata oppure immettere 0 per non disabilitare mai una pianificazione a causa dell'inattività. Il valore predefinito è 10 cicli.  
  
 L'inattività della cartella di lavoro viene misurata come assenza di eventi di connessione in più cicli di aggiornamento dati. Un ciclo di aggiornamento dati viene contato ogni volta che viene attivata un'operazione di aggiornamento dati (dalla pianificazione o da un'operazione Esegui ora), indipendentemente dall'esito positivo o negativo dell'operazione. Se un certo numero di cicli (10 per impostazione predefinita) passa senza alcuna richiesta di connessione per la cartella di lavoro, la pianificazione di aggiornamento dati viene disabilitata a causa dell'inattività.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|10|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-datarefreshmaxhistory-int"></a>-DataRefreshMaxHistory \<int >  
 Specifica per quanto tempo mantenere un record cronologico di elaborazione dell'aggiornamento dati. Queste informazioni vengono visualizzate nelle pagine della cronologia dell'aggiornamento dati mantenute per ogni cartella di lavoro per cui viene utilizzato l'aggiornamento dati. Sono visualizzate anche nel dashboard di gestione [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Il valore predefinito è 365 giorni.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|365|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-healthbasedallocation-switch"></a>-HealthBasedAllocation \<passare >  
 Specifica l'algoritmo di allocazione basato sull'integrità che inoltra le richieste di connessione al server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint in cui sono disponibili maggiori risorse di memoria e CPU. Si tratta dell'algoritmo di allocazione predefinito. HealthBasedAllocation e RoundRobinBasedAllocation si escludono a vicenda. È necessario specificare uno o l'altro. Se si impostano entrambi su false, viene utilizzato HealthBasedAllocation, in quanto corrisponde al valore predefinito. Se si impostano entrambi su true, viene generato un errore di convalida. La sintassi per questi parametri prevede l'immissione solo del nome del parametro oppure parameter:$true o parameter:$false.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-loadstoconnectionsratiocollectioninterval-int"></a>-LoadsToConnectionsRatioCollectionInterval \<int >  
 Specifica l'intervallo (in ore) per il conteggio di eventi di caricamento e di connessione al fine di calcolare il rapporto carico/connessioni. Per impostazione predefinita, nel sistema viene calcolato un nuovo rapporto ogni 4 ore. I valori validi sono compresi tra 1 e 24.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|4|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-loadstoconnectionsratiolimit-int"></a>-LoadsToConnectionsRatioLimit \<int >  
 Specifica il rapporto tra eventi di caricamento ed eventi di connessione, utilizzato come indicatore dell'integrità del server. Il valore predefinito corrisponde al 20%.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|20|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-memorydatabaseholdlimit-int"></a>-MemoryDatabaseHoldLimit \<int>  
 Specifica il numero di ore di permanenza in memoria di un database inattivo per soddisfare nuove richieste per tali dati. Un database attivo viene mantenuto sempre in memoria purché vengano eseguite query su di esso. Una volta inattivo, tuttavia, viene mantenuto in memoria per un ulteriore periodo di tempo, in caso vi siano ulteriori richieste per tali dati. L'impostazione predefinita è 48 ore.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|48|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-queryreportinginterval-int"></a>-QueryReportingInterval \<int >  
 Specifica il numero di secondi per la raccolta delle statistiche relative alle risposte alle query prima che le statistiche vengano incluse in un report come evento di utilizzo. Il valore predefinito è 300 secondi.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|300|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-roundrobinallocation-switch"></a>-RoundRobinAllocation \<passare >  
 Specifica l'algoritmo di allocazione round robin che inoltra le richieste di connessione al server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint successivo, alternando le richieste in modo equivalente tra i server disponibili, indipendentemente dal carico del server. HealthBasedAllocation e RoundRobinBasedAllocation si escludono a vicenda. È necessario specificare uno o l'altro. Se si impostano entrambi su false, viene utilizzato HealthBasedAllocation, in quanto corrisponde al valore predefinito. Se si impostano entrambi su true, viene generato un errore di convalida. La sintassi per questi parametri prevede l'immissione solo del nome del parametro oppure parameter:$true o parameter:$false.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-unattendedaccount-string"></a>-UnattendedAccount \<stringa >  
 Specifica il nome dell'applicazione di destinazione di un'applicazione del servizio di archiviazione sicura che archivia un account predefinito per l'esecuzione dei processi di aggiornamento dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-usagedataretentionperiod-int"></a>-UsageDataRetentionPeriod \<int >  
 Specifica il numero di giorni per la conservazione di una cronologia di dati di utilizzo e delle statistiche di integrità del server. Il valore predefinito è 365 giorni. Se si imposta questo valore su 0, tutta la cronologia viene conservata per un tempo illimitato.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|365|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-usageexpectedresponseupperlimit-int"></a>-UsageExpectedResponseUpperLimit \<int >  
 Imposta un limite massimo che definisce uno scambio richiesta-risposta previsto. Il valore predefinito è 3000 millisecondi. Qualsiasi richiesta completata entro un intervallo di tempo compreso tra 1000 e 3000 millisecondi viene considerata una risposta prevista ai fini del report.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|3000|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-usagelongresponseupperlimit-int"></a>-UsageLongResponseUpperLimit \<int >  
 Imposta un limite massimo che definisce uno scambio richiesta-risposta con esecuzione prolungata.  Il limite massimo è 10000 millisecondi. Tutte le richieste che superano questo limite massimo rientrano nella categoria Superato, che non prevede una soglia massima.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|10000|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-usagequickresponseupperlimit-int"></a>-UsageQuickResponseUpperLimit \<int >  
 Imposta un limite massimo che definisce uno scambio richiesta-risposta rapido. Il valore predefinito è 1000 millisecondi. Qualsiasi richiesta completata entro un intervallo di tempo compreso tra 500 e 1000 millisecondi viene considerata una risposta rapida ai fini del report.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|1000|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-usagetrivialresponseupperlimit-int"></a>-UsageTrivialResponseUpperLimit \<int >  
 Specifica una categoria di tempi di risposta che sono troppo piccoli per essere considerati rilevanti ai fini della raccolta dati. La maggior parte delle risposte che rientrano in questa categoria è costituita da comunicazioni tra server. Il valore predefinito è 500 millisecondi. Qualsiasi richiesta completata entro un intervallo di tempo compreso tra 0 e 500 millisecondi viene considerata una richiesta semplice e ignorata ai fini del report.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|500|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-usageupdatedaylimit-int"></a>-UsageUpdateDayLimit \<int>  
 Specifica la soglia (in giorni) per l'attivazione di un avviso relativo a un errore di aggiornamento del file di dati usato dai report nel dashboard di gestione [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Per impostazione predefinita, i dati di utilizzo vengono aggiornati dal sistema giornalmente. Il file [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Management Dashboard.xlsx, che rappresenta l'origine dati per i report amministrativi, viene aggiornato in base alla stessa pianificazione. Se il file con estensione xlsx non viene aggiornato per un determinato numero di giorni, viene attivata una regola di analisi dell'integrità che indica che il file è non aggiornato. Il valore predefinito è 5 giorni. I valori validi sono compresi tra 1 e 30.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|5|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="commonparameters"></a>\<Parametricomuni >  
 Questo cmdlet supporta i parametri comuni, ovvero Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer e OutVariable. Per altre informazioni, vedere [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Input e output  
 Il tipo di input è il tipo degli oggetti che è possibile inoltrare tramite pipe al cmdlet. Il tipo restituito è il tipo degli oggetti restituiti dal cmdlet.  
  
|||  
|-|-|  
|Input|Nessuno|  
|Output|Nessuno|  
  
## <a name="example-1"></a>Esempio 1  
  
```  
C:\PS>Set-PowerPivotServiceApplication -identity 1234567-890a-bcde-fghijklm -AllowCustomWindowsCredentials:$false -UnattendedAccount "MyTargetApp"  
```  
  
 In questo esempio si disabilita una funzionalità di aggiornamento dati con cui è possibile creare e gestire automaticamente le applicazioni di destinazione del servizio di archiviazione sicura per l'archiviazione di credenziali di Windows arbitrarie. Si imposta anche l'account di aggiornamento dati automatico [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in un'applicazione di destinazione predefinita.  
  
 Utilizzare Get-powerpivotserviceapplication per ottenere un'identità valida.  
  
## <a name="example-2"></a>Esempio 2  
  
```  
C:\PS>Set-PowerPivotServiceApplication -identity 1234567-890a-bcde-fghijklm -HealthBasedAllocation  
```  
  
 In questo esempio si specifica l'algoritmo di allocazione basato sull'integrità tramite cui vengono inoltrate le richieste di connessione al server in cui sono disponibili maggiori risorse.  
  
 Utilizzare Get-powerpivotserviceapplication per ottenere un'identità valida.  
  
## <a name="example-3"></a>Esempio 3  
  
```  
C:\PS>Set-PowerPivotServiceApplication -identity 1234567-890a-bcde-fghijklmn -BusinessHoursStartTime "07:15AM" -BusinessHoursEndTime "08:00PM"  
```  
  
 Questo esempio illustra come impostare le ore di inizio e di fine di un giorno lavorativo, da usare come opzione per la pianificazione dell'aggiornamento dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Nelle pianificazioni può essere specificata un'opzione successiva all'orario di ufficio, per l'esecuzione dell'aggiornamento dati alla fine di un giorno lavorativo.  
  
 Utilizzare Get-powerpivotserviceapplication per ottenere un'identità valida.  
  
  
