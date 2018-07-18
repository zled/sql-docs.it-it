---
title: Connettersi a SQL Server (AccessToSQL) | Documenti Microsoft
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: ceb77a97-d6d5-4a92-90a6-342e97d12b54
caps.latest.revision: 3
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 50649ffad9b862fa914178400a3c68d5e398c6cb
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34773527"
---
# <a name="connect-to-sql-server-accesstosql"></a>Connettersi a SQL Server (AccessToSQL)
Utilizzare il **Connetti al Server SQL** la finestra di dialogo per connettersi all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] che si desidera eseguire la migrazione a. Per accedere al **Connetti al Server SQL** della finestra di dialogo il **File** menu, fare clic su **Connetti a SQL Server**.  
  
## <a name="options"></a>Opzioni  
**Nome server**  
Immettere o selezionare l'istanza di SQL Server a cui connettersi. Per impostazione predefinita, viene visualizzata l'istanza che si è connessi a più di recente.  
  
-   Se ci si connette all'istanza predefinita nel computer locale, è possibile immettere **localhost** o un punto (**.**).  
  
-   Se ci si connette all'istanza predefinita in un altro computer, immettere il nome del computer.  
  
-   Se ci si connette a un'istanza denominata in un altro computer, immettere il nome del computer, una barra rovesciata e il nome dell'istanza, ad esempio *MyServer*\\*MyInstance*.  
  
**Porta server**  
Se l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] non è configurato per accettare le connessioni sul valore predefinito (1433) di porta, immettere il numero di porta. In caso contrario, lasciare vuoto questo valore.  
  
**Database**  
Specificare il database per eseguire la migrazione di oggetti e dati. Questa opzione non è disponibile durante la riconnessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
**Autenticazione**  
Selezionare il metodo di autenticazione utilizzato per connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Per utilizzare l'account di Windows corrente, selezionare l'autenticazione di Windows. Per specificare un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] account di accesso e password, selezionare [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] l'autenticazione.  
  
**Nome utente**  
Se si utilizza [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] l'autenticazione, immettere l'account di accesso per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Se si utilizza l'autenticazione di Windows, questa opzione non è disponibile.  
  
**Password**  
Se si utilizza [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] l'autenticazione, immettere la password per l'account di accesso nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Se si utilizza l'autenticazione di Windows, questa opzione non è disponibile.  
  
**Encrypt Connection**  
Se si desidera connettersi in modo sicuro a SQL Server, utilizzare Crittografa connessione controllando il **Crittografa connessione** casella di controllo.  
  
**TrustServerCertificate**  
Se si desidera utilizzare questa opzione, selezionare il **considera attendibile certificato Server** casella di controllo.  
  
> [!NOTE]  
> Per abilitare **considera attendibile certificato Server**, "Encrypt" deve essere impostato su **True**.  
  
