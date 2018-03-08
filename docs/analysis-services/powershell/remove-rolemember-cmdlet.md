---
title: Il cmdlet Remove-RoleMember | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e38f56ab-facd-4bef-9502-f52f8486a6a6
caps.latest.revision: "8"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ad8117fd1b8c936914291484d7dde26702e119a1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="remove-rolemember-cmdlet"></a>Cmdlet Remove-RoleMember
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Rimuovere un membro dal ruolo specificato di un database di Analysis Services.  

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
 nessuna.  
  
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
  

  
  
