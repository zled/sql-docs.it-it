---
title: "Cmdlet Add-RoleMember | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 827c8bbc-d48f-4e49-9ea5-abb1380f7623
caps.latest.revision: 14
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 14
---
# Cmdlet Add-RoleMember
  Aggiungere un membro del ruolo specificato a un database multidimensionale o tabulare di Analysis Services.  
  
## Sintassi  
 `Add-RoleMember [-MemberName] <System.String> [-Database] <System.String> [-RoleName] <System.String> [<CommonParameters>]`  
  
 `Add-RoleMember [-MemberName] <System.String> [-DatabaseRole] <Microsoft.AnalysisServices.Role> [<CommonParameters>]`  
  
## Description  
 Il cmdlet Add-RoleMember aggiunge un membro valido a un ruolo del database esistente. Solo i ruoli del database sono consentiti. Non è possibile utilizzare questo cmdlet per aggiungere membri a un ruolo del server.  
  
 È possibile aggiungere solo un membro per volta, che può essere un account utente o del account.  
  
## Parametri  
  
### -MemberName \<string>  
 Specifica l'utente o il gruppo di Windows da aggiungere al ruolo.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -Database \<string>  
 Specifica il database a cui appartiene il ruolo.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|1|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -RoleName \<string>  
 Specifica il ruolo a cui vengono aggiunti i membri.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|2|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -DatabaseRole \<string>  
 Specifica l'oggetto Microsoft.AnalysisServices.Role al quale deve essere aggiunto il membro. Utilizzare questo parametro come alternativa ai parametri –Database e –RoleName, quando si desidera fornire il ruolo del database tramite pipeline.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|true (ByPropertyName)|  
|Accettare caratteri jolly?|false|  
  
### \<CommonParameters>  
 In questo cmdlet vengono supportati i parametri comuni: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable. Per altre informazioni, vedere [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Input e output  
 Il tipo di input è il tipo degli oggetti che è possibile inoltrare tramite pipe al cmdlet. Il tipo restituito è il tipo degli oggetti restituiti dal cmdlet.  
  
|||  
|-|-|  
|Input|Nessuno|  
|Output|Nessuno|  
  
## Esempio 1  
  
```  
PS SQLSERVER:\sqlas\localhost\default> add-rolemember –membername “adventure-works\bobh” –database “AdventureWorks” –rolename “Reader”  
```  
  
 Questo comando aggiunge un account utente di dominio Windows al ruolo lettura, per il database AdventureWorks in esecuzione in un'istanza predefinita locale.  
  
## Esempio 2  
  
```  
PS SQLSERVER:\sqlas\localhost\default> $roles= dir .\databases\AWTEST\Roles  
PS SQLSERVER:\sqlas\localhost\default> $roles  
PS SQLSERVER:\sqlas\localhost\default> add-rolemember –membername:“adventure-works\bobh” –databaserole:$roles[0]  
```  
  
 Nella riga 1 tutti i ruoli del database AWTEST vengono aggiunti alla pipeline. Nella riga 2, dove si digita $roles al prompt, viene visualizzata la matrice di ruoli. Nella riga 3 viene aggiunto l'utente di Windows adventure-works\bobh come membro del primo ruolo nella matrice.  
  
## Esempio 3  
  
```  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles=dir  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles[0] | Add-rolemember –membername “adventure-works\bobh”  
```  
  
 Questo comando aggiunge un account utente di dominio Windows al primo ruolo in una matrice, dove la matrice viene creata elencando i figli della cartella dei ruoli, nel contesto di un database specifico (AWTEST).  
  
## Vedere anche  
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)   
 [Post sulla gestione dei modelli tabulari tramite PowerShell](http://go.microsoft.com/fwlink/?linkID=227685)  
  
  