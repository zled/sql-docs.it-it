---
title: Modificare proprietà SQL Server Service avanzate utilizzando VBScript | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- VBScript [WMI]
- modifying SQL Server Service properties
- WMI Provider for Configuration Management, VBScript
ms.assetid: f3c5d981-eaa3-4d34-9b91-37e42636aa81
caps.latest.revision: 17
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: a49cc34f92a2dd35d5f85a6013a738184d913810
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="access-wmi-provider-for-configuration-management-using-vbscript"></a>Accedere al Provider WMI per Gestione configurazione utilizzando VBScript
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  In questa sezione viene descritto come creare un programma VBScript che elenca la versione delle istanze installate di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in esecuzione in un computer.  
  
 Nell'esempio di codice vengono elencate le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in esecuzione nel computer e la relativa versione.  
  
### <a name="listing-name-and-version-of-installed-instances-of-sql-server"></a>Elenco del nome e della versione delle istanze installate di SQL Server  
  
1.  Aprire un nuovo documento in un editor di testo, ad esempio Blocco note di [!INCLUDE[msCoName](../../includes/msconame-md.md)]. Copiare il codice riportato dopo questa procedura e salvare il file con estensione vbs, ad esempio test.vbs.  
  
2.  Connettersi a un'istanza del provider WMI per Gestione computer con la funzione VBScript `GetObject`. In questo esempio viene effettuata la connessione a un computer remoto denominato mpc. Omettere il nome del computer per connettersi al computer locale: winmgmts:root\Microsoft\SqlServer\ComputerManagement. Per ulteriori informazioni sulla funzione `GetObject`, vedere l'argomento di riferimento per VBScript.  
  
3.  Utilizzare il metodo `InstancesOf` per enumerare un elenco dei servizi. È inoltre possibile enumerare i servizi mediante una query WQL semplice e il metodo `ExecQuery` anziché utilizzare il metodo `InstancesOf`.  
  
4.  Utilizzare il metodo `ExecQuery` e una query WQL per recuperare il nome e la versione delle istanze installate di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
5.  Salvare il file.  
  
6.  Eseguire lo script digitando **cscript test.vbs** al prompt dei comandi.  
  
## <a name="example"></a>Esempio  
  
```  
set wmi = GetObject("WINMGMTS:\\.\root\Microsoft\SqlServer\ComputerManagement12")  
for each prop in wmi.ExecQuery("select * from SqlServiceAdvancedProperty where SQLServiceType = 1 AND PropertyName = 'VERSION'")  
WScript.Echo prop.ServiceName & " " & prop.PropertyName & ": " & prop.PropertyStrValue  
next  
```  
  
  
