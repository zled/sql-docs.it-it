---
title: Il cmdlet Add-RoleMember | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a7da23c4c3597398be38cd4efd34f6ba21925405
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="add-rolemember-cmdlet"></a>Cmdlet Add-RoleMember
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

  Aggiungere un membro del ruolo specificato a un database multidimensionale o tabulare di Analysis Services.  

>[!NOTE] 
>In questo articolo può contenere esempi e informazioni non aggiornate. Usare il cmdlet Get-Help per la versione più recente.
  
## <a name="syntax"></a>Sintassi  
 `Add-RoleMember [-MemberName] <System.String> [-Database] <System.String> [-RoleName] <System.String> [<CommonParameters>]`  
  
 `Add-RoleMember [-MemberName] <System.String> [-DatabaseRole] <Microsoft.AnalysisServices.Role> [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 Il cmdlet Add-RoleMember aggiunge un membro valido a un ruolo del database esistente. Solo i ruoli del database sono consentiti. Non è possibile utilizzare questo cmdlet per aggiungere membri a un ruolo del server.  
  
 È possibile aggiungere solo un membro per volta, che può essere un account utente o del account.  
  
## <a name="parameters"></a>Parametri  
  
### <a name="-membername-string"></a>-MemberName \<stringa >  
 Specifica l'utente o il gruppo di Windows da aggiungere al ruolo.  
  
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
 Specifica il ruolo a cui vengono aggiunti i membri.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|2|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-databaserole-string"></a>-DatabaseRole \<stringa >  
 Specifica l'oggetto Microsoft.AnalysisServices.Role al quale deve essere aggiunto il membro. Utilizzare questo parametro come alternativa ai parametri –Database e –RoleName, quando si desidera fornire il ruolo del database tramite pipeline.  
  
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
 Il tipo di input è il tipo degli oggetti che è possibile inoltrare tramite pipe al cmdlet. Il tipo restituito è il tipo degli oggetti restituiti dal cmdlet.  
  
|||  
|-|-|  
|Input|Nessuno|  
|Output|Nessuno|  
  
## <a name="example-1"></a>Esempio 1  
  
```  
PS SQLSERVER:\sqlas\localhost\default> add-rolemember –membername “adventure-works\bobh” –database “AdventureWorks” –rolename “Reader”  
```  
  
 Questo comando aggiunge un account utente di dominio Windows al ruolo lettura, per il database AdventureWorks in esecuzione in un'istanza predefinita locale.  
  
## <a name="example-2"></a>Esempio 2  
  
```  
PS SQLSERVER:\sqlas\localhost\default> $roles= dir .\databases\AWTEST\Roles  
PS SQLSERVER:\sqlas\localhost\default> $roles  
PS SQLSERVER:\sqlas\localhost\default> add-rolemember –membername:“adventure-works\bobh” –databaserole:$roles[0]  
```  
  
 Nella riga 1 tutti i ruoli del database AWTEST vengono aggiunti alla pipeline. Nella riga 2, dove si digita $roles al prompt, viene visualizzata la matrice di ruoli. Nella riga 3 viene aggiunto l'utente di Windows adventure-works\bobh come membro del primo ruolo nella matrice.  
  
## <a name="example-3"></a>Esempio 3  
  
```  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles=dir  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles[0] | Add-rolemember –membername “adventure-works\bobh”  
```  
  
 Questo comando aggiunge un account utente di dominio Windows al primo ruolo in una matrice, dove la matrice viene creata elencando i figli della cartella dei ruoli, nel contesto di un database specifico (AWTEST).  
  

  
  
