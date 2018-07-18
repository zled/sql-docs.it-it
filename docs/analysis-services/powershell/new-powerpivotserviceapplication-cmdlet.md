---
title: Cmdlet New-PowerPivotServiceApplication | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5be9914dfb9361af2067cbef469f2ef6737b4fb7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="new-powerpivotserviceapplication-cmdlet"></a>Cmdlet New-PowerPivotServiceApplication
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Crea una nuova applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  

>[!NOTE] 
>In questo articolo può contenere esempi e informazioni non aggiornate. Usare il cmdlet Get-Help per la versione più recente.
  
 **Applicabile a:** SharePoint 2010 e SharePoint 2013.  
  
## <a name="syntax"></a>Sintassi  
  
```  
New-PowerPivotServiceApplication [-ServiceApplicationName] <string> [-DatabaseServerName] <string> [-DatabaseName] <string> [-AddToDefaultProxyGroup <switch>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 Con il cmdlet New-PowerPivotServiceApplication è possibile creare una nuova applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nella farm. È necessario definire almeno un'applicazione di servizio, che deve essere membro del gruppo di servizi proxy predefinito. Facoltativamente, è possibile creare applicazioni di servizio aggiuntive, se è necessario variare le impostazioni di configurazione e le proprietà. Alle applicazioni di servizio aggiuntive deve essere assegnata l'appartenenza ai gruppi di connessioni del servizio personalizzati. Solo un'applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] può essere membro del gruppo di proxy predefinito.  
  
 Viene creata una nuova applicazione di servizio utilizzando una configurazione predefinita. Per personalizzare le proprietà di configurazione, utilizzare il cmdlet Set-PowerPivotServiceApplication.  
  
## <a name="parameters"></a>Parametri  
  
### <a name="-serviceapplicationname-string"></a>-ServiceApplicationName \<string>  
 Imposta il nome visualizzato dell'applicazione di servizio.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-databaseservername-string"></a>-DatabaseServerName \<string>  
 Specifica un'istanza del motore di database relazionale di SQL Server che ospita il database dell'applicazione. Per impostazione predefinita, è possibile utilizzare il server di database della farm oppure è possibile scegliere un server di database diverso per il quale si dispone dei diritti di creazione del database.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|1|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-databasename-string"></a>-DatabaseName \<stringa >  
 Specifica il nome di un database relazionale di SQL Server in cui vengono archiviati i dati dell'applicazione. Assicurarsi di specificare un nome che corrisponda all'applicazione, in modo che sia possibile identificare più facilmente lo scopo. È possibile creare un nuovo database o specificare un database dell'applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] esistente per la nuova applicazione che si sta creando.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|2|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-addtodefaultproxygroup-switch"></a>-AddToDefaultProxyGroup \<switch>  
 Crea una connessione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nel gruppo di connessioni del servizio predefinito. Le associazioni tra applicazioni Web e applicazioni di servizio sono determinate dall'appartenenza a questo gruppo. In tutte le applicazioni Web che sottoscrivono il gruppo di connessioni del servizio predefinito è possibile usare l'applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] aggiunta al gruppo. Nonostante possano essere presenti più applicazioni del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in una farm, solo un'applicazione di servizio può essere membro del gruppo di connessioni del servizio predefinito.  
  
 Se è già presente un'applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] che è membro del gruppo di proxy predefinito, è necessario impostare AddToDefautlProxyGroup:$false per la nuova applicazione creata. Sarà necessario aggiungere la nuova applicazione di servizio a un gruppo di connessioni del servizio personalizzato.  A questo scopo, è possibile utilizzare cmdlet predefiniti di SharePoint.  Con Get-SPServiceApplicationProxyGroup viene restituito l'elenco dei gruppi di connessioni del servizio definiti nella farm.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="commonparameters"></a>\<Parametricomuni >  
 Questo cmdlet supporta i parametri comuni, ovvero Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer e OutVariable. Per altre informazioni, vedere [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Input e output  
 Il tipo di input è il tipo degli oggetti che è possibile inoltrare tramite pipe al cmdlet. Il tipo restituito è il tipo degli oggetti restituiti dal cmdlet.  
  
|||  
|-|-|  
|Input|Nessuno|  
|Output|Nessuno|  
  
## <a name="example-1"></a>Esempio 1  
  
```  
C:\PS>New-PowerPivotServiceApplication -ServiceApplicationName "PowerPivot Service Application" -DatabaseServerName "AdvWorks-SRV01\PowerPivot" -DatabaseName "PowerPivotServiceApp1" -AddtoDefaultProxyGroup:$true  
```  
  
 In questo esempio si crea una nuova applicazione di servizio. Il database dell'applicazione di servizio viene creato in un server di database denominato AdvWorks-SRV01, installato come istanza denominata di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , in base a una configurazione comune per numerose installazioni di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint. Per creare il database, è necessario disporre delle autorizzazioni dbcreator nell'istanza di SQL Server. È necessario essere membro del ruolo db_owner nel database di configurazione di SharePoint. Dal momento che si tratta della prima applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nella farm, è necessario che sia membro del gruppo di proxy predefinito.  
  
  
