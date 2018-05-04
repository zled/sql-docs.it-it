---
title: Classe SqlErrorLogEvent | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SqlErrorLogEvent class
- SqlErrorLogFile class
ms.assetid: bde6c467-38d0-4766-a7af-d6c9d6302b07
caps.latest.revision: 14
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 77ffaff3db702d94d5010d27627685b1d5e88473
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlerrorlogevent-class"></a>Classe SqlErrorLogEvent
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Fornisce proprietà per la visualizzazione di eventi in un file di log di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
class SQLErrorLogEvent   
{  
   stringFileName;  
   stringInstanceName;  
   datetimeLogDate;  
   stringMessage;  
   stringProcessInfo;  
};  
```  
  
## <a name="properties"></a>Proprietà  
 La classe SQLErrorLogEvent definisce le proprietà seguenti.  
  
|||  
|-|-|  
|FileName|Tipo di dati: **stringa**<br /><br /> Tipo di accesso: sola lettura<br /><br /> <br /><br /> Nome del file di log degli errori.|  
|InstanceName|Tipo di dati: **stringa**<br /><br /> Tipo di accesso: sola lettura<br /><br /> Qualificatori: chiave<br /><br /> Nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in cui si trova il file di log.|  
|LogDate|Tipo di dati: **datetime**<br /><br /> Tipo di accesso: sola lettura<br /><br /> Qualificatori: chiave<br /><br /> <br /><br /> Data e ora della registrazione dell'evento nel file di log.|  
|Message|Tipo di dati: **stringa**<br /><br /> Tipo di accesso: sola lettura<br /><br /> <br /><br /> Messaggio di evento.|  
|Classe ProcessInfo|Tipo di dati: **stringa**<br /><br /> Tipo di accesso: sola lettura<br /><br /> <br /><br /> Informazioni sull'ID del processo server di origine (SPID) per l'evento.|  
  
## <a name="remarks"></a>Osservazioni  
  
|||  
|-|-|  
|MOF|Sqlmgmproviderxpsp2up.mof|  
|DLL|Sqlmgmprovider.dll|  
|Namespace|\root\Microsoft\SqlServer\ComputerManagement10|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come recuperare valori per tutti gli eventi registrati in un file di log specificato. Per eseguire l'esempio, sostituire \< *Instance_Name*> con il nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio "Istanza1" e sostituire "File_Name" con il nome del file di log degli errori, ad esempio 'Errorlog. 1'.  
  
```  
on error resume next  
strComputer = "."  
Set objWMIService = GetObject("winmgmts:" _  
    & "{impersonationLevel=impersonate}!\\" _  
    & strComputer & "\root\MICROSOFT\SqlServer\ComputerManagement10")  
set logEvents = objWmiService.ExecQuery("SELECT * FROM SqlErrorLogEvent WHERE InstanceName = '<Instance_Name>' AND FileName = 'File_Name'")  
  
For Each logEvent in logEvents  
WScript.Echo "Instance Name: " & logEvent.InstanceName & vbNewLine _  
    & "Log Date: " & logEvent.LogDate & vbNewLine _  
    & "Log File Name: " & logEvent.FileName & vbNewLine _  
    & "Process Info: " & logEvent.ProcessInfo & vbNewLine _  
    & "Message: " & logEvent.Message & vbNewLine _  
  
Next  
```  
  
## <a name="comments"></a>Commenti  
 Quando *InstanceName* o *FileName* non disponibili nell'istruzione WQL, la query restituirà le informazioni per l'istanza predefinita e corrente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] file di log. Ad esempio, l'istruzione WQL seguente verrà restituiti tutti gli eventi di log dal file di registro corrente (ERRORLOG) nell'istanza predefinita (MSSQLSERVER).  
  
```  
"SELECT * FROM SqlErrorLogEvent"  
```  
  
## <a name="security"></a>Sicurezza  
 Per connettersi a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] file di log tramite WMI, è necessario disporre delle autorizzazioni seguenti nei computer locali e remoti:  
  
-   Accesso in lettura il **Root\Microsoft\SqlServer\ComputerManagement10** spazio dei nomi WMI. Per impostazione predefinita, chiunque dispone di accesso in lettura tramite l'autorizzazione Abilita account.  
  
-   Autorizzazione di lettura per la cartella che contiene i log degli errori. Per impostazione predefinita, l'errore registri si trovano nel percorso seguente (dove \< *unità >* rappresenta l'unità in cui è installato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e \< *InstanceName*> è il nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]):  
  
     **\<Unità >: \Programmi\Microsoft SQL Server\MSSQL13** **.\< InstanceName > \mssql\log.**  
  
 Se si sta eseguendo la connessione attraverso un firewall, assicurarsi che sia impostata un'eccezione nel firewall per WMI nei computer di destinazione remoti. Per ulteriori informazioni, vedere [la connessione a WMI con avvio remoto con Windows Vista](http://go.microsoft.com/fwlink/?LinkId=178848).  
  
## <a name="see-also"></a>Vedere anche  
 [Classe SqlErrorLogFile](../../relational-databases/wmi-provider-configuration-classes/sqlerrorlogfile-class.md)   
 [Visualizzare file di log offline](../../relational-databases/logs/view-offline-log-files.md)  
  
  
