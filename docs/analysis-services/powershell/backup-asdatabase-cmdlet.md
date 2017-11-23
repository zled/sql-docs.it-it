---
title: Cmdlet backup-ASDatabase | Documenti Microsoft
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
ms.assetid: 03d58a82-021c-4e13-b265-c084f42a8bb2
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: cc648f0ad73c9ed39f49e823fe4293b57ff0d470
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="backup-asdatabase-cmdlet"></a>Cmdlet Backup-ASDatabase

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Eseguire il backup di un database multidimensionale o tabulare di Analysis Services in un file di backup di Analysis Services (con estensione abf).  

>[!NOTE] 
>In questo articolo può contenere esempi e informazioni non aggiornate. Usare il cmdlet Get-Help per la versione più recente.
  
## <a name="syntax"></a>Sintassi  
 `Backup-ASDatabase [-BackupFile] <string> [-Name] <string> [-AllowOverwrite <SwitchParameter>] [-BackupRemotePartitions <SwitchParameter>] [-ApplyCompression <SwitchParameter>] [-FilePassword <SecureString>] [-Locations <Microsoft.AnalysisServices.BackupLocation[]>] [-Server <string>] [-Credential <PSCredential>] [<CommonParameters>]`  
  
 `Backup-ASDatabase –Database <Microsoft.AnalysisServices.Database> [-AllowOverwrite <SwitchParameter>] [-BackupRemotePartitions <SwitchParameter>] [-ApplyCompression <SwitchParameter>] [-FilePassword <SecureString>] [-Locations <Microsoft.AnalysisServices.BackupLocation[]>] [-Server <string>] [-Credential <PSCredential>] [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 Consente a un amministratore di sistema di Analysis Services di eseguire il backup di un database multidimensionale o tabulare in un file di backup. Se non si specifica un percorso, viene utilizzato il percorso di backup predefinito specificato durante l'installazione.  
  
 È possibile crittografare i file di cui si esegue il backup. Utilizzare -FilePassword per crittografare il file. Quando si ripristina il file in un secondo momento, è necessario fornire la stessa password specificata per la crittografia.  
  
 Questo cmdlet supporta il parametro -Credential, che può essere utilizzato se è stata configurata l'istanza di Analysis Services per l'accesso HTTP. Il parametro -Credential accetta un oggetto PSCredential che fornisce un'identità utente di Windows. In IIS verrà quindi rappresentato questo utente durante la connessione ad Analysis Services. Per eseguire il backup, è necessario che l'identità disponga delle autorizzazioni di amministratore di sistema nell'istanza di Analysis Services.  
  
## <a name="parameters"></a>Parametri  
  
### <a name="-backupfile-string"></a>-BackupFile \<stringa >  
 Specifica il percorso e il nome del file di backup. Se si specifica solo un nome file senza un percorso, verrà utilizzato il percorso di backup predefinito. Questo parametro viene utilizzato solo con il parametro -Name.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-name-string"></a>-Nome \<stringa >  
 Specifica il database di Analysis Services di cui eseguire il backup. È possibile specificare un database utilizzando il parametro -Database o -Name se si desidera passare il nome come una stringa.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|1|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-allowoverwrite-switchparameter"></a>AllowOverwrite - \<SwitchParameter >  
 Sovrascrive un file di backup con lo stesso nome.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-backupremotepartitions-switchparameter"></a>BackupRemotePartitions - \<SwitchParameter >  
 Specifica se le partizioni remote saranno incluse nel backup.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-applycompressionswitchparameter"></a>-ApplyCompression\<SwitchParameter >  
 Specifica se comprimere il file di backup.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-filepassword-securestring"></a>-FilePassword \<SecureString >  
 Specifica una password da utilizzare con la crittografia del file di backup.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-locations-microsoftanalysisservicesbackuplocation"></a>-Percorsi \<[] Microsoft.AnalysisServices.BackupLocation >  
 Specifica il percorso in cui verrà archiviato il file di backup.  
  
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
  
### <a name="-database-microsoftanalysisservicesdatabase"></a>-Database \<[] Microsoft.AnalysisServices.Database >  
 Specifica un oggetto di database di Analysis Services di cui eseguire il backup. Un database può essere specificato utilizzando il parametro -Database o -Name. Utilizzare -Database se si desidera inoltrare tramite pipe il nome del database.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|true|  
|Accettare caratteri jolly?|false|  
  
### <a name="commonparameters"></a>\<Parametricomuni >  
 In questo cmdlet vengono supportati i parametri comuni: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable. Per altre informazioni, vedere [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Input e output  
 Il tipo di input è il tipo degli oggetti che è possibile inoltrare tramite pipe al cmdlet. Il tipo restituito è il tipo degli oggetti restituiti dal cmdlet.  
  
|||  
|-|-|  
|Input|Microsoft.AnalysisServices.Database<br /><br /> È possibile inoltrare tramite pipe più database di cui si desidera eseguire il backup, ad esempio tutti i database di un'istanza specifica.|  
|Output|Nessuno|  
  
## <a name="example-1"></a>Esempio 1  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default >backup-asdatabase awdb-20110930.abf “Adventure Works” -AllowOverwrite -ApplyCompression  
```  
  
 Questo comando esegue il backup del database Adventure Works in un file con estensione abf nel percorso di backup predefinito. Se nel percorso è presente un file con lo stesso nome, verrà sovrascritto.  
  
## <a name="example-2"></a>Esempio 2  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default >$AWDB = get-item “databases\Adventure Works”   
PS SQLSERVER:\SQLAS\Localhost\default >Backup-asdatabase –database:$AWDB –AllowOverwrite  
```  
  
 Per questo comando viene utilizzato -Database anziché -Backupfile e -Name. Utilizzare il parametro -Database se si desidera inoltrare tramite pipe il nome del database al cmdlet.  
  
## <a name="example-3"></a>Esempio 3  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default\databases >dir * | backup-asdatabase  
```  
  
 Questo comando esegue il backup di tutti i database nel server locale.  
  
## <a name="example-4"></a>Esempio 4  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default > $pwd = read-host –AsSecureString –Prompt “Password”   
PS SQLSERVER:\SQLAS\Localhost\default > $pwd -is [System.IDisposable]   
PS SQLSERVER:\SQLAS\Localhost\default > backup-asdatabase –backupfile test.abf –name contoso_retail –filepassword:$pwd server myremoteserver  
PS SQLSERVER:\SQLAS\Localhost\default >$pwd.Dispose()  
PS SQLSERVER:\SQLAS\Localhost\default >Remove-Variable –Name pwd  
```  
  
 Le righe 1 e 2 vengono utilizzate per richiedere una password che verrà utilizzata per crittografare il file.  
  
 La riga 3 esegue il backup del database di esempio Contoso_Retail presente sul server Analysis Services remoto in un file di backup di Analysis Services denominato test.abf, ugualmente sul remoto. Il file viene salvato nella cartella di backup predefinita dell'istanza predefinita.  
  
 Le righe 4 e 5 rimuovono la password.  
  
  
  
