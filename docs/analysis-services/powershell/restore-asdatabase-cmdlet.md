---
title: "Cmdlet Restore-ASDatabase | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 8ab7a2d0-679c-40e6-b9b9-042184b2dfc9
caps.latest.revision: 11
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 11
---
# Cmdlet Restore-ASDatabase
  Ripristina un database multidimensionale o tabulare da un file di backup (con estensione abf) a un'istanza di Analysis Services.  
  
## Sintassi  
 `Restore-ASDatabase [-RestoreFile] <string> [-Name] <string> [-AllowOverwrite <SwitchParameter>] Locations <Microsoft.AnalysisServices.RestoreLocation[]>] [-Security <Microsoft.AnalysisServices.RestoreSecurity>] [-Password <System.SecureString>] [-StorageLocation <System.string>] [-Server <string>] [-Credential <PSCredential>] [<CommonParameters>]`  
  
## Description  
 Consente a un amministratore di sistema di Analysis Services di ripristinare un database multidimensionale o tabulare da un file di backup (con estensione abf) a un'istanza del server locale o remota. Se il file in fase di ripristino è crittografato, utilizzare -FilePassword per fornire la password utilizzata per decrittografare il file.  
  
 Questo cmdlet supporta il parametro -Credential, che può essere utilizzato se è stata configurata l'istanza di Analysis Services per l'accesso HTTP. Il parametro -Credential accetta un oggetto PSCredential che fornisce un'identità utente di Windows. In IIS verrà quindi rappresentato questo utente durante la connessione ad Analysis Services. Per ripristinare il file, è necessario che l'identità disponga delle autorizzazioni di amministratore di sistema nell'istanza di Analysis Services.  
  
## Parametri  
  
### -RestoreFile \<string>  
 Specifica il percorso e il nome del file da ripristinare. Se si specifica solo il nome file senza un percorso, verrà utilizzato il percorso di backup predefinito.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -Name \<string>  
 Specifica il database di Analysis Services da ripristinare.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|1|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -AllowOverwrite \<SwitchParameter>  
 Sovrascrive un database in cui vengono utilizzati lo stesso nome e percorso.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -Locations \<Microsoft.AnalysisServices.RestoreLocation[]>  
 Specifica il percorso remoto delle partizioni da ripristinare.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -Security \<Microsoft.AnalysisServices.RestoreSecurity>  
 Rappresenta le impostazioni di sicurezza utilizzate per l'operazione di ripristino. I valori validi sono CopyAll, SkipMembership, IgnoreSecurity. CopyAll ripristina ruoli e appartenenza. SkipMembership ricrea solo il ruolo. IgnoreSecurity ripristina il database, senza ruoli.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -Password \<SecureString>  
 Specifica una password da utilizzare per il ripristino del file di backup crittografato. È necessario specificare la password utilizzata originariamente per crittografare il file.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -StorageLocation \<string>  
 Specifica il percorso di archiviazione del database. Si tratta del percorso dei file di database nel file system. Impostare questo parametro se non si utilizza il percorso predefinito, cioè la cartella di backup dell'istanza di destinazione.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -Server \<string>  
 Specifica l'istanza di Analysis Services a cui il cmdlet deve connettersi per l'esecuzione. Se non viene fornito alcun nome del server, la connessione verrà effettuata a localhost. Per le istanze predefinite è sufficiente specificare il nome del server, mentre per quelle denominate, utilizzare il formato nomeserver\nomeistanza. Per le connessioni HTTP, utilizzare il formato http[s]://server[:porta]/virtualdirectory/msmdpump.dll.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|localhost|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -Credential \<PSCredential>  
 Specifica un oggetto PSCredential che fornisce un nome utente e una password di Windows. Specificare questo parametro solo se l'istanza di Analysis Services viene configurata per l'accesso HTTP, utilizzando l'autenticazione di base. Per le connessioni native in cui viene utilizzata la sicurezza integrata, questo parametro viene ignorato.  
  
 Se questo parametro è presente, le credenziali fornite vengono accodate alla stringa di connessione. In IIS verrà quindi rappresentata questa identità utente durante la connessione ad Analysis Services. Se non vengono specificate credenziali, verrà utilizzato l'account di Windows predefinito dell'utente che esegue lo strumento.  
  
 Per usare questo parametro, creare innanzitutto un oggetto PSCredential usando Get-Credential per specificare il nome utente e la password, ad esempio `$Cred=Get-Credential “adventure-works\admin”`. Successivamente è possibile inoltrare tramite pipe questo oggetto al parametro –Credential `(-Credential:$Cred`.  
  
 Per altre informazioni sull'uso di autenticazione e credenziali, vedere [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md) (Script di PowerShell in Analysis Services). Per altre informazioni sull'accesso HTTP, vedere [Configurare l'accesso HTTP ad Analysis Services in Internet Information Services &#40;IIS&#41; 8.0](../../analysis-services/instances/configure http access to analysis services on iis 8.0.md).  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|True (ByValue)|  
|Accettare caratteri jolly?|false|  
  
### \<CommonParameters>  
 In questo cmdlet vengono supportati i parametri comuni: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable. Per altre informazioni, vedere [about_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Input e output  
 Il tipo di input è il tipo degli oggetti che è possibile inoltrare tramite pipe al cmdlet. Il tipo restituito è il tipo degli oggetti restituiti dal cmdlet.  
  
|||  
|-|-|  
|Input|System.string<br /><br /> È possibile inoltrare tramite pipe i valori stringa al cmdlet.|  
|Output|Nessuno|  
  
## Esempio 1  
  
```  
PS SQLSERVER:\SQLAS\localhost\default> restore-asdatabase awtest.abf testawrestoredb –security:CopyAll  
```  
  
 Questo comando ripristina un file di backup di Analysis Services (awtest.abf) nella cartella di backup locale in un'istanza predefinita di Analysis Services locale. Non è necessario che il nome del database sia disponibile; in questo caso, questo nome viene specificato come parte dell'operazione di ripristino. Se si aggiunge –Security:CopyAll, ruoli e appartenenza al ruolo vengono popolati dal database di backup al nuovo database ripristinato.  
  
## Esempio 2  
  
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
  
## Esempio 3 (scenario remoto)  
 Questo esempio mostra come ripristinare un file di backup locale da una condivisione file a un'istanza remota di Analysis Services. In questo esempio un file di backup viene ripristinato come database denominato **internetsales** in un'istanza predefinita di Analysis Services su un computer denominato **ssas-aw-srv01**.  
  
 Il file di backup si trova su una condivisione di rete con accesso pubblico in lettura. L'istanza remota di Analysis Services deve disporre dell'autorizzazione di lettura per il file. Il file deve trovarsi su una condivisione di rete, non su un'unità.  
  
 Si noti che questo esempio non è basato sul provider SQLAS. È possibile eseguire il cmdlet come comando autonomo.  
  
```  
PS SQLSERVER:\> restore-asdatabase -restorefile "\\FileServer01\DBFiles\InternetSalesTabular.abf" -name "internetsales  
" -server "SSAS-AW-SRV01"  
```  
  
## Esempio 4  
  
```  
PS SQLSERVER:\SQLAS\localhost\default> restore-asdatabase –restorefile “\\myremoteserver\backups\testdb.abf” –name Contoso_Retail –server myremoteserver –storagelocation “\\myremoteserver\restoreDBFiles”  
```  
  
 Questo comando ripristina un file di backup crittografato di Analysis Services (testdb.abf) in una cartella di backup remota in un'istanza predefinita di Analysis Services remota. Il parametro –StorageLocation viene utilizzato per posizionare i file di database in un percorso non predefinito, in questo caso un file condiviso denominato restoreDBfiles.  
  
## Vedere anche  
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)   
 [Post sulla gestione dei modelli tabulari tramite PowerShell](http://go.microsoft.com/fwlink/?linkID=227685)  
  
  