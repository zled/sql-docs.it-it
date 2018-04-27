---
title: Supporto di Azure Active Directory in SQL Server Data Tools (SSDT) | Microsoft Docs
ms.custom: ''
ms.date: 03/05/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssdt
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssdt
ms.tgt_pltfrm: ''
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 1e8f19c1dcc629ec6e97aa02cd23be1c101ad596
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="azure-active-directory-support-in-sql-server-data-tools-ssdt"></a>Supporto di Azure Active Directory in SQL Server Data Tools (SSDT)

[!INCLUDE[appliesto-xx-asdb-xxxx-xxx-md.md](../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

SQL Server Data Tools (SSDT) supporta vari metodi di autenticazione di [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-whatis).

![Finestra di dialogo di connessione di SSDT](media/azure-active-directory/interactive.png)

## <a name="active-directory-password-authentication"></a>Autenticazione della password Active Directory

L'autenticazione della password di Active Directory è un meccanismo di connessione al database SQL di Azure tramite identità in Azure Active Directory (Azure AD).  Usare questo metodo per la connessione se si è connessi a Windows con le credenziali da un dominio che non è federato con Azure o se si usa l'autenticazione di Azure AD tramite Azure AD basata sul dominio iniziale o client. Per altre informazioni, vedere [Connessione al database SQL oppure a SQL Data Warehouse con l'autenticazione di Azure Active Directory](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication).  

## <a name="active-directory-integrated-authentication"></a>Autenticazione integrata di Active Directory

L'autenticazione integrata di Active Directory è un meccanismo di connessione al database SQL di Azure tramite identità in Azure Active Directory (Azure AD). Usare questo metodo per la connessione se si è connessi a Windows con le credenziali di Azure Active Directory da un dominio federato. Per altre informazioni, vedere [Connessione al database SQL oppure a SQL Data Warehouse con l'autenticazione di Azure Active Directory](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication).

## <a name="active-directory-interactive-authentication-preview"></a>Autenticazione interattiva di Active Directory (anteprima)

SSDT offre un nuovo metodo di autenticazione per la connessione a un database SQL di Azure: l'**autenticazione interattiva di Active Directory**.


> [!NOTE]
> L'autenticazione interattiva di Active Directory è disponibile quando ci si connette con SSDT nell'[anteprima di Visual Studio 2017](https://www.visualstudio.com/vs/preview/) e richiede l'installazione dell'[anteprima di .NET 4.7.2 (KB4038188)](https://go.microsoft.com/fwlink/?linkid=867317) nel computer che esegue SSDT. Se l'anteprima di .NET 4.7.2 (KB4038188) non è installata, l'opzione di autenticazione interattiva di Active Directory non sarà disponibile.


L'autenticazione interattiva di Active Directory supporta un'autenticazione interattiva che consente di usare Multi-Factor Authentication (MFA) di Azure Active Directory (AD) per l'autenticazione con il database SQL di Azure. Questo metodo supporta utenti di Azure AD nativi e federati e utenti guest da altri account (inclusi utenti B2B, account Microsoft e account non Microsoft come @outlook.com, @hotmail.com, @live.com e @gmail.com). Se si seleziona questo metodo, è necessario specificare il **nome utente** e il campo Password verrà disabilitato. 

Quando si esegue l'autenticazione con l'*autenticazione interattiva di Active Directory* viene visualizzata una finestra un'autenticazione che richiede agli utenti di immettere manualmente una password.

![Finestra di dialogo di accesso](media/azure-active-directory/sign-in.png)

L'autenticazione a più fattori viene imposta da Azure AD tramite questa finestra popup di autenticazione a più fattori aggiuntiva durante il processo di autenticazione.

> [!NOTE]
> Dato che l'*autenticazione interattiva di Active Directory* richiede agli utenti di immettere manualmente la password (in modo interattivo), non è consigliabile per i flussi di lavoro automatizzati.


## <a name="known-issues-and-limitations"></a>Problemi noti e limitazioni

- L'*autenticazione interattiva di Active Directory* è supportata solo quando ci si connette a un database SQL di Azure. Non è supportata per SQL Server (in locale o in una macchina virtuale) o per Azure SQL Data Warehouse.
- L'*autenticazione interattiva di Active Directory* non è supportata nella finestra di dialogo di connessione in *Esplora server*. È necessario connettersi usando SSDT con *Esplora oggetti di SQL Server*.
- L'integrazione di Single Sign-On con l'account attualmente connesso in Visual Studio non è supportata per SSDT.
- La versione di SQLPackage.exe installata nella directory Extensions durante l'installazione di Visual Studio non è progettata per l'uso da tale percorso. Per usare SQLpackage.exe con AAD, visitare la pagina https://www.microsoft.com/en-us/download/details.aspx?id=55088 
- La funzionalità Confronto dati di SSDT non è supportata per l'autenticazione AAD, incluso il nuovo metodo di autenticazione.  





## <a name="see-also"></a>Vedere anche  
[Autenticazione a più fattori](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication)  
[Autenticazione di Azure Active Directory con il database SQL](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure)  
[SQL Server Data Tools in Visual Studio](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)  
[Forum MSDN di SSDT](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[Blog del Team di SSDT](http://blogs.msdn.com/b/ssdt/)  
[Riferimento all'API DACFx](https://msdn.microsoft.com/library/dn645454.aspx)  
[Scaricare SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  
