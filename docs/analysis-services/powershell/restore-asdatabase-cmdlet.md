---
title: Il cmdlet Restore-ASDatabase | Documenti Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: powershell
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8ab7a2d0-679c-40e6-b9b9-042184b2dfc9
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ae57bdc2a1f385e06248ab9486b7ef5fc07f7932
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="restore-asdatabase-cmdlet"></a>Cmdlet Restore-ASDatabase

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Ripristina un database multidimensionale o tabulare da un file di backup (con estensione abf) a un'istanza di Analysis Services.  

>[!NOTE] 
>In questo articolo può contenere esempi e informazioni non aggiornate. Usare il cmdlet Get-Help per la versione più recente.
  
## <a name="syntax"></a>Sintassi  
 `Restore-ASDatabase [-RestoreFile] <string> [-Name] <string> [-AllowOverwrite <SwitchParameter>] Locations <Microsoft.AnalysisServices.RestoreLocation[]>] [-Security <Microsoft.AnalysisServices.RestoreSecurity>] [-Password <System.SecureString>] [-StorageLocation <System.string>] [-Server <string>] [-Credential <PSCredential>] [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 Consente a un amministratore di sistema di Analysis Services di ripristinare un database multidimensionale o tabulare da un file di backup (con estensione abf) a un'istanza del server locale o remota. Se il file in fase di ripristino è crittografato, utilizzare -FilePassword per fornire la password utilizzata per decrittografare il file.  
  
 Questo cmdlet supporta il parametro -Credential, che può essere utilizzato se è stata configurata l'istanza di Analysis Services per l'accesso HTTP. Il parametro -Credential accetta un oggetto PSCredential che fornisce un'identità utente di Windows. In IIS verrà quindi rappresentato questo utente durante la connessione ad Analysis Services. Per ripristinare il file, è necessario che l'identità disponga delle autorizzazioni di amministratore di sistema nell'istanza di Analysis Services.  
  
## <a name="parameters"></a>Parametri  
  
### <a name="-restorefile-string"></a>RestoreFile - \<stringa >  
 Specifica il percorso e il nome del file da ripristinare. Se si specifica solo il nome file senza un percorso, verrà utilizzato il percorso di backup predefinito.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-name-string"></a>-Nome \<stringa >  
 Specifica il database di Analysis Services da ripristinare.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|1|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-allowoverwrite-switchparameter"></a>AllowOverwrite - \<SwitchParameter >  
 Sovrascrive un database in cui vengono utilizzati lo stesso nome e percorso.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-locations-microsoftanalysisservicesrestorelocation"></a>-Percorsi \<[] Microsoft.AnalysisServices.RestoreLocation >  
 Specifica il percorso remoto delle partizioni da ripristinare.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-security-microsoftanalysisservicesrestoresecurity"></a>-Sicurezza \<Microsoft.AnalysisServices.RestoreSecurity >  
 Rappresenta le impostazioni di sicurezza utilizzate per l'operazione di ripristino. I valori validi sono CopyAll, SkipMembership, IgnoreSecurity. CopyAll ripristina ruoli e appartenenza. SkipMembership ricrea solo il ruolo. IgnoreSecurity ripristina il database, senza ruoli.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-password-securestring"></a>-Password \<SecureString >  
 Specifica una password da utilizzare per il ripristino del file di backup crittografato. È necessario specificare la password utilizzata originariamente per crittografare il file.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-storagelocation-string"></a>StorageLocation - \<stringa >  
 Specifica il percorso di archiviazione del database. Si tratta del percorso dei file di database nel file system. Impostare questo parametro se non si utilizza il percorso predefinito, cioè la cartella di backup dell'istanza di destinazione.  
  
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
 Specifica un oggetto PSCredential che fornisce un nome utente e una password di Windows. Specificare questo parametro solo se l'istanza di Analysis Services viene configurata per l'accesso HTTP, utilizzando l'autenticazione di base. Per le connessioni native in cui viene utilizzata la sicurezza integrata, questo parametro viene ignorato.  
  
 Se questo parametro è presente, le credenziali fornite vengono accodate alla stringa di connessione. In IIS verrà quindi rappresentata questa identità utente durante la connessione ad Analysis Services. Se non vengono specificate credenziali, verrà utilizzato l'account di Windows predefinito dell'utente che esegue lo strumento.  
  
 Per usare questo parametro, creare innanzitutto un oggetto PSCredential usando Get-Credential per specificare il nome utente e la password, ad esempio, `$Cred=Get-Credential “adventure-works\admin”`. Successivamente è possibile inoltrare tramite pipe questo oggetto al parametro -Credential `(-Credential:$Cred`.  
  
 Per altre informazioni sull'accesso HTTP, vedere [Configurare l'accesso HTTP ad Analysis Services in Internet Information Services &#40;IIS&#41; 8.0](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md).  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|True (ByValue)|  
|Accettare caratteri jolly?|false|  
  
### <a name="commonparameters"></a>\<Parametricomuni >  
 In questo cmdlet vengono supportati i parametri comuni: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable. Per altre informazioni, vedere [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Input e output  
 Il tipo di input è il tipo degli oggetti che è possibile inoltrare tramite pipe al cmdlet. Il tipo restituito è il tipo degli oggetti restituiti dal cmdlet.  
  
|||  
|-|-|  
|Input|System.string<br /><br /> È possibile inoltrare tramite pipe i valori stringa al cmdlet.|  
|Output|Nessuno|  
  
## <a name="example-1"></a>Esempio 1  
  
```  
PS SQLSERVER:\SQLAS\localhost\default> restore-asdatabase awtest.abf testawrestoredb –security:CopyAll  
```  
  
 Questo comando ripristina un file di backup di Analysis Services (awtest.abf) nella cartella di backup locale in un'istanza predefinita di Analysis Services locale. Non è necessario che il nome del database sia disponibile; in questo caso, questo nome viene specificato come parte dell'operazione di ripristino. Se si aggiunge –Security:CopyAll, ruoli e appartenenza al ruolo vengono popolati dal database di backup al nuovo database ripristinato.  
  
## <a name="example-2"></a>Esempio 2  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default > $pwd = read-host –AsSecureString –Prompt “Password”   
PS SQLSERVER:\SQLAS\Localhost\default > $pwd -is [System.IDisposable]   
PS SQLSERVER:\SQLAS\localhost\default> restore-asdatabase –restorefile testdb.abf –name AWTEST2 –password:$pwd  
PS SQLSERVER:\SQLAS\Localhost\default >$pwd.Dispose()  
PS SQLSERVER:\SQLAS\Localhost\default >Remove-Variable –Name pwd  
```  
  
 Le righe 1 e 2 vengono utilizzate per richiedere la password che verrà utilizzata per crittografare il file.  
  
 La riga 3 ripristina un file di backup crittografato di Analysis Services (testdb.abf) da una cartella di backup locale di un'istanza predefinita di Analysis Services.  
  
 Le righe 4 e 5 rimuovono la password.  
  
## <a name="example-3-remote-scenario"></a>Esempio 3 (scenario remoto)  
 Questo esempio mostra come ripristinare un file di backup locale da una condivisione file a un'istanza remota di Analysis Services. In questo esempio un file di backup viene ripristinato come database denominato **internetsales** in un'istanza predefinita di Analysis Services su un computer denominato **ssas-aw-srv01**.  
  
 Il file di backup si trova su una condivisione di rete con accesso pubblico in lettura. L'istanza remota di Analysis Services deve disporre dell'autorizzazione di lettura per il file. Il file deve trovarsi su una condivisione di rete, non su un'unità.  
  
 Si noti che questo esempio non è basato sul provider SQLAS. È possibile eseguire il cmdlet come comando autonomo.  
  
```  
PS SQLSERVER:\> restore-asdatabase -restorefile "\\FileServer01\DBFiles\InternetSalesTabular.abf" -name "internetsales  
" -server "SSAS-AW-SRV01"  
```  
  
## <a name="example-4"></a>Esempio 4  
  
```  
PS SQLSERVER:\SQLAS\localhost\default> restore-asdatabase –restorefile “\\myremoteserver\backups\testdb.abf” –name Contoso_Retail –server myremoteserver –storagelocation “\\myremoteserver\restoreDBFiles”  
```  
  
 Questo comando ripristina un file di backup crittografato di Analysis Services (testdb.abf) in una cartella di backup remota in un'istanza predefinita di Analysis Services remota. Il parametro –StorageLocation viene utilizzato per posizionare i file di database in un percorso non predefinito, in questo caso un file condiviso denominato restoreDBfiles.  
  
