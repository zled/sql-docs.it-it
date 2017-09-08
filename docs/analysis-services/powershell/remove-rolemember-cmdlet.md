---
title: Il cmdlet Remove-RoleMember | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e38f56ab-facd-4bef-9502-f52f8486a6a6
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c093787d86398acaaeaca8f282e1f588c3e726d7
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="remove-rolemember-cmdlet"></a>Cmdlet Remove-RoleMember

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Rimuovere un membro dal ruolo specificato di un database di Analysis Services.  

>[!NOTE] 
>In questo articolo può contenere esempi e informazioni non aggiornate. Usare il cmdlet Get-Help per la versione più recente.
  
## <a name="syntax"></a>Sintassi  
 `Remove-RoleMember [-MemberName] <System.String> [-Database] <System.String> [-RoleName] <System.String> [<CommonParameters>]`  
  
 `Remove-RoleMember [-DatabaseRole] <Microsoft.AnalysisServices.Role> [-MemberName] <System.String>  [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 Il cmdlet Remove-RoleMember rimuove un membro esistente da un ruolo di un database di Analysis Services.  
  
## <a name="parameters"></a>Parametri  
  
### <a name="-membername-string"></a>-MemberName \<stringa >  
 Specifica l'utente o il gruppo di Windows da rimuovere dal ruolo.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-database-string"></a>-Database \<stringa >  
 Specifica il database a cui appartiene il ruolo.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|1|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-rolename-string"></a>-RoleName \<stringa >  
 Specifica il ruolo da cui vengono rimossi i membri.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|2|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-databaserole-string"></a>-DatabaseRole \<stringa >  
 Specifica l'oggetto Microsoft.AnalysisServices.Role dal quale viene rimosso il membro. Utilizzare questo parametro come alternativa ai parametri –Database e –RoleName, quando si desidera fornire il ruolo del database tramite pipeline.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|true (ByPropertyName)|  
|Accettare caratteri jolly?|false|  
  
### <a name="commonparameters"></a>\<Parametricomuni >  
 In questo cmdlet vengono supportati i parametri comuni: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable. Per altre informazioni, vedere [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Input e output  
 Nessuno  
  
## <a name="example-1"></a>Esempio 1  
  
```  
PS SQLSERVER:\sqlas\localhost\default> remove-rolemember –membername “adventure-works\bobh” –database “AdventureWorks” –rolename “Reader”  
```  
  
 Questo comando rimuove un account utente di dominio Windows dal ruolo lettura, per il database AdventureWorks in esecuzione in un'istanza predefinita locale.  
  
## <a name="example-2"></a>Esempio 2  
  
```  
PS SQLSERVER:\sqlas\localhost\default> $roles= dir .\databases\AWTEST\Roles  
PS SQLSERVER:\sqlas\localhost\default> $roles  
PS SQLSERVER:\sqlas\localhost\default> remove-rolemember –membername:“adventure-works\bobh” –databaserole:$roles[0]  
```  
  
 Nella riga 1 tutti i ruoli del database AWTEST vengono aggiunti alla pipeline. Nella riga 2, dove si digita $roles al prompt, viene visualizzata la matrice di ruoli. Nella riga 3 viene rimosso l'utente di Windows "adventure-works\bobh" dal primo ruolo nella matrice.  
  
## <a name="example-3"></a>Esempio 3  
  
```  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles=dir  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles[0] | Remove-rolemember –membername “adventure-works\bobh”  
```  
  
 Questo comando rimuove un account utente di dominio Windows dal primo ruolo in una matrice, dove la matrice viene creata elencando i figli della cartella dei ruoli, nel contesto di un database specifico (AWTEST).  
  

  
  
