---
title: Cmdlet New-RestoreLocation | Documenti Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5ca13d8c-1c5d-4f02-869c-72e0defce6d7
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a87852e69b55ea26cb56fe6918d1d4310c339f27
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="new-restorelocation-cmdlet"></a>Cmdlet New-RestoreLocation

[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  Specifica le informazioni utilizzate per ripristinare un database.  

>[!NOTE] 
>In questo articolo può contenere esempi e informazioni non aggiornate. Usare il cmdlet Get-Help per la versione più recente.
  
## <a name="syntax"></a>Sintassi  
 `New-RestoreLocation [-File <String>] [-DataSourceId <String>] [-ConnectionString <String>] [-DataSourceType <RestoreDataSourceType>] [-Folders <RestoreFolder[]>] [-AsTemplate] [-Server <String>] [-Credential <PSCredential>] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]`  
  
 `New-RestoreLocation [-Server <String>] [-Credential <PSCredential>] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]`  
  
 Parametri comuni, ad esempio –Verbose, -Debug, parametri di errore e di avviso, -Whatif e –Confirm vengono documentati nel riferimento di Windows PowerShell. Per altre informazioni, vedere [about_CommonParameters](http://technet.microsoft.com/library/dd315352.aspx).  
  
## <a name="description"></a>Description  
 Il cmdlet New-RestoreLocation contiene informazioni utilizzate per ripristinare un database, tra cui la stringa di connessione del server e del database, le proprietà dell'origine dati, nonché i file e le cartelle associati al database ripristinato.  
  
## <a name="parameters"></a>Parametri  
  
### <a name="-file-string"></a>-File \<stringa >  
 Specifica il nome del file di backup che si ripristina.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-datasourceid-string"></a>DataSourceId - \<stringa >  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-connectionstring-string"></a>-ConnectionString \<stringa >  
 Specifica la stringa di connessione di un'istanza di Analysis Services remota.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-datasourcetype-asrestoredatasourcetype"></a>DataSourceType - \<As. RestoreDataSourceType >  
 Specifica se l'origine dati è remota o locale, in base al percorso della partizione.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-folders-asrestorefolder"></a>-Cartelle \<As. RestoreFolder >  
 Specifica le cartelle della partizione nell'istanza locale o remota.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-astemplate-switchparameter"></a>-AsTemplate \<SwitchParameter >  
 Specifica se l'oggetto deve essere creato in memoria e deve essere restituito.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-server-string"></a>-Server \<stringa >  
 Specifica l'istanza di Analysis Services a cui il cmdlet deve connettersi per l'esecuzione. Se non viene fornito alcun nome del server, la connessione verrà effettuata a localhost. Per le istanze predefinite è sufficiente specificare il nome del server, mentre per quelle denominate, utilizzare il formato nomeserver\nomeistanza. Per le connessioni HTTP, utilizzare il formato http[s]://server[:porta]/virtualdirectory/msmdpump.dll.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|localhost|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-credential-pscredential"></a>-Credential \<PSCredential >  
 Questo parametro è utilizzato per passare un nome utente e una password quando si utilizza una connessione HTTP a un'istanza di Analysis Services, se configurata per l'accesso HTTP. Per ulteriori informazioni, vedere [configura l'accesso HTTP ad Analysis Services in Internet Information Services &#40; IIS &#41; 8.0](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md) per le connessioni HTTP.  
  
 Se si specifica questo parametro, il nome utente e la password saranno utilizzati per connettersi all'istanza di Analysis Services specificata. Se non viene specificata alcuna credenziale, verrà utilizzato l'account predefinito di Windows dell'utente che sta eseguendo lo strumento.  
  
 Per usare questo parametro, creare innanzitutto un oggetto PSCredential usando Get-Credential per specificare il nome utente e la password, ad esempio, `$Cred=Get-Credential “adventure-works\bobh”`. Successivamente è possibile inoltrare tramite pipe questo oggetto al parametro -Credential `(-Credential:$Cred`.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|True (ByValue)|  
|Accettare caratteri jolly?|false|  
  
## <a name="inputs-and-outputs"></a>Input e output  
 Il tipo di input è il tipo degli oggetti che è possibile inoltrare tramite pipe al cmdlet. Il tipo restituito è il tipo degli oggetti restituiti dal cmdlet.  
  
|||  
|-|-|  
|Input|Nessuno|  
|Output|Nessuno|  
  
## <a name="examples"></a>Esempi  
  
  
