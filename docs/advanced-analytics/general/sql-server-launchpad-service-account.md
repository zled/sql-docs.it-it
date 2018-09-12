---
title: Configurazione dell'account del servizio Launchpad di SQL Server | Microsoft Docs
description: Come modificare l'account del servizio Launchpad di SQL Server usata per l'esecuzione di script esterni in SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/05/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 0afdb02c578de92bc91c5f47e973148136ebd919
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892878"
---
# <a name="sql-server-launchpad-service-configuration"></a>Configurazione del servizio Launchpad di SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Un oggetto separato [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] servizio viene creato per l'istanza del motore di database a cui è stato aggiunto l'integrazione con SQL Server machine learning (R o Python).

## <a name="service-account-configuration"></a>Configurazione degli account del servizio

Per impostazione predefinita, Launchpad di SQL Server è configurato per l'esecuzione **NT Service\MSSQLLaunchpad**, che viene eseguito il provisioning con tutte le autorizzazioni necessarie per eseguire gli script esterni. Rimozione delle autorizzazioni da questo account può comportare Launchpad è Impossibile avviare o accedere all'istanza di SQL Server in cui devono essere eseguiti gli script esterni.

Autorizzazione necessaria per questo account vengono elencati di seguito. Se si modifica l'account del servizio, assicurarsi di usare la **criteri di sicurezza locali** applicazione da includere queste autorizzazioni:

+ Regolazione quote di memoria per un processo (SeIncreaseQuotaPrivilege)
+ Ignorare controllo incrociato (SeChangeNotifyPrivilege)
+ Accesso come servizio (SeServiceLogonRight)
+ Sostituzione di token a livello di processo (SeAssignPrimaryTokenPrivilege)

Per altre informazioni sulle autorizzazioni necessarie per l'esecuzione di servizi di SQL Server, vedere [Configurare account di servizio e autorizzazioni di Windows](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

<a name="bkmk_ChangingConfig"></a> 

## <a name="configuration-properties"></a>Proprietà di configurazione

1. Aprire [Gestione configurazione SQL Server](../../relational-databases/sql-server-configuration-manager.md). 

2. Fare doppio clic su Launchpad di SQL Server e selezionare **proprietà**.

    + Per modificare l'account del servizio, scegliere il **Accedi** scheda.

    + Per aumentare il numero di utenti, selezionare la **avanzate** scheda.

> [!Note]
> Nelle prime versioni di SQL Server 2016 R Services, è possibile modificare alcune proprietà del servizio modificando il [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] file di configurazione. Questo file non viene usato per la modifica delle configurazioni. Gestione configurazione SQL Server è l'approccio corretto per le modifiche alla configurazione del servizio, ad esempio l'account del servizio e il numero di utenti.

#### <a name="debug-settings"></a>Impostazioni di debug

Alcune proprietà possono essere modificate solo tramite file di configurazione della finestra di avvio, che potrebbe essere utile in alcuni casi, ad esempio il debug. Il file di configurazione viene creato durante [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di installazione e per impostazione predefinita viene salvato come file di testo normale nel percorso seguente: `<instance path>\binn\rlauncher.config`

Per poter apportare modifiche a questo file è necessario essere amministratore del computer su cui è eseguito [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Se si decide di modificare il file, si consiglia di crearne una copia di backup prima di salvare le modifiche.

La tabella seguente elenca le impostazioni avanzate per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], con i valori consentiti. 

|**Nome impostazione**|**Tipo**|**Descrizione**|
|----|----|----|
|PROCESSO\_PULIZIA\_VIA\_ESCI|Valore intero |Si tratta di un'impostazione esclusivamente interna: non modificare questo valore. </br></br>Specifica se la cartella di lavoro temporanea creata per ogni sessione runtime esterni deve essere pulita dopo il completamento della sessione. L'impostazione è utile per il debug. </br></br>I valori supportati sono **0** (disabilitato) o **1** (abilitato). </br></br>Il valore predefinito è 1, i file di log significato sono rimossi all'uscita.|
|TRACCIA\_LIVELLO|Valore intero |Consente di configurare il livello di dettaglio di traccia di MSSQLLAUNCHPAD a scopo di debug. Ciò influisce sui file di traccia nel percorso specificato dall'impostazione LOG_DIRECTORY. </br></br>I valori supportati sono: **1** (errore), **2** (prestazioni), **3** (avviso), **4** (informazioni). </br></br>Il valore predefinito è 1, vale a dire solo avvisi di output.|

Tutte le impostazioni assumono la forma di coppie chiave-valore e ogni impostazione si trova su una riga diversa. Per modificare il livello di traccia, ad esempio, si potrebbe aggiungere la riga `Default: TRACE_LEVEL=4`.

## <a name="see-also"></a>Vedere anche

[Framework di estendibilità](../concepts/extensibility-framework.md)
