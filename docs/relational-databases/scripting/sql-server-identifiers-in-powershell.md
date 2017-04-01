---
title: "Identificatori di SQL Server in PowerShell | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cmdlet [SQL Server], Encode-Sqlname"
  - "PowerShell [SQL Server], identificatori"
  - "Encode-Sqlname - cmdlet"
  - "PowerShell [SQL Server], Encode-Sqlname"
  - "Decode-Sqlname - cmdlet"
  - "PowerShell [SQL Server], Decode-Sqlname"
  - "identificatori [SQL Server], PowerShell"
  - "Cmdlet [SQL Server], Decode-Sqlname"
ms.assetid: 651099b0-33b4-453a-a864-b067f21eb8b9
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# Identificatori di SQL Server in PowerShell
  Il provider di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per Windows PowerShell usa gli identificatori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nei percorsi di Windows PowerShell. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha identificatori che possono contenere caratteri non supportati nei percorsi di Windows PowerShell. Per tali caratteri è necessario usare caratteri di escape oppure la codifica speciale quando gli identificatori vengono usati nei percorsi di Windows PowerShell.  
  
## Identificatori di SQL Server nei percorsi di Windows PowerShell  
 I provider Windows PowerShell espongono le gerarchie di dati utilizzando una struttura di percorso simile a quella del file system di Windows. Il provider [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implementa i percorsi degli oggetti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per il [!INCLUDE[ssDE](../../includes/ssde-md.md)], l'unità è impostata su SQLSERVER: la prima cartella è impostata su \SQL e agli oggetti di database viene fatto riferimento come contenitori ed elementi. Di seguito è riportato il percorso della tabella Vendor nello schema Purchasing del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] in un'istanza predefinita del [!INCLUDE[ssDE](../../includes/ssde-md.md)]:  
  
```  
SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Purchasing.Vendor  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha identificatori che sono i nomi degli oggetti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio i nomi di tabelle o colonne. Esistono due tipi di identificatori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Gli identificatori regolari sono limitati a un set di caratteri supportati anche nei percorsi di Windows PowerShell. Questi nomi possono essere utilizzati nei percorsi di Windows PowerShell senza essere modificati.  
  
-   Gli identificatori delimitati possono utilizzare caratteri non supportati nei nomi dei percorsi di Windows PowerShell. Gli identificatori delimitati sono chiamati identificatori tra parentesi se sono racchiusi tra parentesi quadre ([IdentifierName]) e identificatori tra virgolette se sono racchiusi tra virgolette doppie ("IdentifierName"). Se un identificatore delimitato utilizza caratteri non supportati nei percorsi di Windows PowerShell, i caratteri devono essere codificati o devono essere utilizzati caratteri di escape prima di utilizzare l'identificatore come nome di contenitore o di elemento. La codifica è supportata per tutti i caratteri. Per alcuni caratteri, come i due punti (:), non è possibile utilizzare caratteri di escape.  
  
## Identificatori di SQL Server nei cmdlet  
 Alcuni cmdlet di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dispongono di un parametro che accetta un identificatore come input. I valori del parametro vengono generalmente forniti come costanti di stringa tra virgolette o nelle variabili di stringa. Quando gli identificatori vengono forniti come costanti di stringa o nelle variabili, non si verifica alcun conflitto con il set dei caratteri supportati da Windows PowerShell.  
  
## Attività degli identificatori di SQL Server  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Viene descritto come specificare un nome dell'istanza, includendo il nome del computer in cui è in esecuzione l'istanza.|[Specifica di istanze nel provider SQL Server PowerShell](../../relational-databases/scripting/specify-instances-in-the-sql-server-powershell-provider.md)|  
|Viene descritto come specificare la codifica esadecimale per i caratteri negli identificatori delimitati che non sono supportati nei percorsi di Windows PowerShell. Viene inoltre descritto come decodificare i caratteri esadecimali.|[Codificare e decodificare identificatori di SLQ Server](../../relational-databases/scripting/encode-and-decode-sql-server-identifiers.md)|  
|Viene descritto come utilizzare il carattere di escape di Windows PowerShell per i caratteri non supportati nei percorsi di PowerShell.|[Identificatori di escape di SQL Server](../../relational-databases/scripting/escape-sql-server-identifiers.md)|  
  
## Vedere anche  
 [Provider PowerShell per SQL Server](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)   
 [Identificatori del database](../../relational-databases/databases/database-identifiers.md)  
  
  