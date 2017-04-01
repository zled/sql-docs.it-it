---
title: "Cmdlet Remove-RoleMember | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: e38f56ab-facd-4bef-9502-f52f8486a6a6
caps.latest.revision: 8
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 8
---
# Cmdlet Remove-RoleMember
  Rimuovere un membro dal ruolo specificato di un database di Analysis Services.  
  
## Sintassi  
 `Remove-RoleMember [-MemberName] <System.String> [-Database] <System.String> [-RoleName] <System.String> [<CommonParameters>]`  
  
 `Remove-RoleMember [-DatabaseRole] <Microsoft.AnalysisServices.Role> [-MemberName] <System.String>  [<CommonParameters>]`  
  
## Description  
 Il cmdlet Remove-RoleMember rimuove un membro esistente da un ruolo di un database di Analysis Services.  
  
## Parametri  
  
### -MemberName \<string>  
 Specifica l'utente o il gruppo di Windows da rimuovere dal ruolo.  
  
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
 Specifica il ruolo da cui vengono rimossi i membri.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|2|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -DatabaseRole \<string>  
 Specifica l'oggetto Microsoft.AnalysisServices.Role dal quale viene rimosso il membro. Utilizzare questo parametro come alternativa ai parametri –Database e –RoleName, quando si desidera fornire il ruolo del database tramite pipeline.  
  
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
 Nessuno  
  
## Esempio 1  
  
```  
PS SQLSERVER:\sqlas\localhost\default> remove-rolemember –membername “adventure-works\bobh” –database “AdventureWorks” –rolename “Reader”  
```  
  
 Questo comando rimuove un account utente di dominio Windows dal ruolo lettura, per il database AdventureWorks in esecuzione in un'istanza predefinita locale.  
  
## Esempio 2  
  
```  
PS SQLSERVER:\sqlas\localhost\default> $roles= dir .\databases\AWTEST\Roles  
PS SQLSERVER:\sqlas\localhost\default> $roles  
PS SQLSERVER:\sqlas\localhost\default> remove-rolemember –membername:“adventure-works\bobh” –databaserole:$roles[0]  
```  
  
 Nella riga 1 tutti i ruoli del database AWTEST vengono aggiunti alla pipeline. Nella riga 2, dove si digita $roles al prompt, viene visualizzata la matrice di ruoli. Nella riga 3 viene rimosso l'utente di Windows "adventure-works\bobh" dal primo ruolo nella matrice.  
  
## Esempio 3  
  
```  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles=dir  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles[0] | Remove-rolemember –membername “adventure-works\bobh”  
```  
  
 Questo comando rimuove un account utente di dominio Windows dal primo ruolo in una matrice, dove la matrice viene creata elencando i figli della cartella dei ruoli, nel contesto di un database specifico (AWTEST).  
  
## Vedere anche  
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)   
 [Post sulla gestione dei modelli tabulari tramite PowerShell](http://go.microsoft.com/fwlink/?linkID=227685)  
  
  