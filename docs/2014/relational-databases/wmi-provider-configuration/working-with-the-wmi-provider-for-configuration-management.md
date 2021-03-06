---
title: Uso del Provider WMI per Gestione configurazione | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- permissions [WMI]
- connection strings [WMI]
- security [WMI]
- WMI Provider for Configuration Management, connection strings
- WMI Provider for Configuration Management, security
- late binding [WMI]
- WMI Provider for Configuration Management, late binding
- binding [WMI]
ms.assetid: 34daa922-7074-41d0-9077-042bb18c222a
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: c2722d608b4f373de92c49f1d75b887c658417e3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48183239"
---
# <a name="working-with-the-wmi-provider-for-configuration-management"></a>Utilizzo del provider WMI per Gestione configurazione
  Prima di eseguire la programmazione con il provider WMI per Gestione computer, è necessario tenere presente quanto riportato di seguito:  
  
## <a name="binding"></a>Associazione  
 Il provider WMI per Gestione configurazione è un modello a oggetti COM che supporta l'associazione anticipata e tardiva. Con l'associazione tardiva è possibile utilizzare linguaggi di scripting, come VBScript, per modificare a livello di codice gli alias, le impostazioni di rete e i servizi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Per altre informazioni sulla programmazione di implementazioni del Provider WMI usando linguaggi di scripting, vedere la [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN [sito Web](http://go.microsoft.com/fwlink/?linkid=15426).  
  
## <a name="specifying-a-connection-string"></a>Definizione di una stringa di connessione  
 Le applicazioni indirizzano il provider WMI per Gestione configurazione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connettendosi a uno spazio dei nomi WMI definito dal provider. Il servizio Windows WMI esegue il mapping di questo spazio dei nomi alla DLL del provider e lo carica in memoria. Tutte le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono rappresentate con un solo spazio dei nomi WMI. Lo spazio dei nomi predefinito è  
  
```  
\\.\root\Microsoft\SqlServer\ComputerManagement12\instance_name  
```  
  
 dove `instance_name` corrisponde per impostazione predefinita a `MSSQLSERVER` in un'installazione predefinita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Nota:** se ci si connette tramite Windows Firewall, è necessario per assicurarsi che i computer sono configurati in modo appropriato. Vedere l'articolo "Connecting Through Windows Firewall" nella documentazione di Strumentazione gestione Windows sul [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN [sito Web](http://go.microsoft.com/fwlink/?linkid=15426).  
  
## <a name="permissions-and-server-authentication"></a>Autorizzazioni e autenticazione del server  
 Per accedere al provider WMI per Gestione configurazione, è necessario che lo script di gestione WMI del client sia in esecuzione nel contesto di un amministratore nel computer di destinazione. È necessario essere membro del gruppo locale Administrators di Windows nel computer da gestire.  
  
 L'amministratore può impostare i criteri di gruppo per controllare l'accesso utente ai provider WMI. Per ulteriori informazioni sull'impostazione dei criteri di gruppo, vedere l'argomento relativo ai criteri di gruppo e a MMC nella Guida di Gestione configurazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Lo script di gestione WMI può essere utilizzato per aggiornare l'account con cui vengono eseguiti i servizi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 I certificati di sicurezza sono supportati dal provider WMI per Gestione configurazione. Per altre informazioni sui certificati, vedere [gerarchia di crittografia](../security/encryption/encryption-hierarchy.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione configurazione SQL Server](../sql-server-configuration-manager.md)  
  
  
