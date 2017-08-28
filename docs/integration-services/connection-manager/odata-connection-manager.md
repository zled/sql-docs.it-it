---
title: Gestione connessione OData | Documenti Microsoft
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3caa4372-aff3-4c0f-9ecd-97870948b8d0
caps.latest.revision: 9
f1_keywords:
- sql13.dts.designer.odatasource.connectionmanager.f1
- sql13.dts.designer.odataconnectionmanager.f1
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: f54562b59e8c61f723c17e2812ca39cb2e95f273
ms.contentlocale: it-it
ms.lasthandoff: 08/28/2017

---
# <a name="odata-connection-manager"></a>Gestione connessione OData
 Connettersi a un'origine dati OData con una gestione connessione OData. Un componente origine OData utilizza una gestione connessione OData per connettersi a un'origine dati OData e utilizzare i dati dal servizio. Per ulteriori informazioni, vedere [OData Source](../../integration-services/data-flow/odata-source.md).  
  
## <a name="adding-an-odata-connection-manager-to-an-ssis-package"></a>Aggiunta di una gestione connessione OData a un pacchetto SSIS  
 È possibile aggiungere una nuova gestione connessione OData a un pacchetto SSIS in tre modi:  
  
-   Fare clic sul pulsante **Nuovo** in **Editor origine OData**  
  
-   Fare clic con il pulsante destro del mouse sulla cartella **Gestioni connessioni** in **Esplora soluzioni**e quindi fare clic su **Nuova gestione connessione**. Selezionare **ODATA** per **Tipo gestione connessione**.  
  
-   Fare clic del mouse il **gestioni connessioni** riquadro nella parte inferiore del pacchetto della finestra di progettazione, quindi fare clic **nuova connessione**. Selezionare **ODATA** per **Tipo gestione connessione**.  
  
## <a name="connection-manager-authentication"></a>Autenticazione di gestione connessione  
 La gestione connessione OData supporta cinque modalità di autenticazione.  
  
-   Autenticazione di Windows  
  
-   Autenticazione di base (con il nome utente e la password)  

-   Microsoft Dynamics AX Online (con nome utente e password)
  
-   Microsoft Dynamics CRM Online (con nome utente e password)
  
-   Microsoft Online Services (con nome utente e password)  
  
Per l'accesso anonimo, selezionare l'opzione Autenticazione di Windows.  

Per connettersi a Microsoft Dynamics AX Online o Microsoft Dynamics CRM online, non è possibile utilizzare il **Microsoft Online Services** opzione di autenticazione. È inoltre possibile utilizzare qualsiasi opzione che è configurato per l'autenticazione a più fattori.
  
### <a name="specifying-and-securing-credentials"></a>Specifica e protezione delle credenziali  
 Se il servizio OData richiede l'autenticazione di base, è possibile specificare un nome utente e una password in [Editor gestione connessione OData](../../integration-services/connection-manager/odata-connection-manager-editor.md). I valori immessi nell'editor sono persistenti nel pacchetto. Il valore della password è crittografato in base al livello di protezione del pacchetto.  
  
 È possibile impostare i parametri dei valori del nome utente e della password in più modalità oppure archiviarli all'esterno del pacchetto. Ad esempio, utilizzare i parametri oppure impostare la proprietà di connessione manager direttamente quando si esegue il pacchetto da SQL Server Management Studio.  
  
## <a name="odata-connection-manager-properties"></a>Proprietà di gestione connessione OData  
 Nell'elenco seguente vengono descritte le proprietà della gestione connessione OData.  
  
|||  
|-|-|  
|Proprietà|Description|  
|URL|URL del documento di servizio.|  
|UserName|Nome utente da utilizzare per l'autenticazione, se necessario.|  
|Password|Password da utilizzare per l'autenticazione, se necessario.|  
|ConnectionString|Include altre proprietà della gestione connessione.|  
  
## <a name="odata-connection-manager-editor"></a>Editor gestione connessione OData
  Utilizzare il **Editor gestione connessione OData** la finestra di dialogo per aggiungere una connessione o modificare una connessione esistente a un'origine dati OData.  
  
### <a name="options"></a>Opzioni  
 **Nome gestione connessione**  
 Nome della gestione connessione.  
  
 **Percorso documento di servizio**  
 URL del servizio OData. Ad esempio, http://services.odata.org/V3/Northwind/Northwind.svc/.  
  
 **Autenticazione**  
Selezionare una delle opzioni seguenti:
-   **L'autenticazione di Windows**. Per l'accesso anonimo, selezionare questa opzione.
-   **Autenticazione di base** 
-   **Microsoft Dynamics AX Online** per Dynamics AX Online
-   **Microsoft Dynamics CRM Online** per Dynamics CRM Online
-   **Microsoft Online Services** per Microsoft Online Services

Se si seleziona un'opzione diverso dall'autenticazione di Windows, immettere il **nome utente** e **password**. 

Per connettersi a Microsoft Dynamics AX Online o Microsoft Dynamics CRM online, non è possibile utilizzare il **Microsoft Online Services** opzione di autenticazione. È inoltre possibile utilizzare qualsiasi opzione che è configurato per l'autenticazione a più fattori.

 **Test connessione**  
 Fare clic su questo pulsante per testare la connessione all'origine OData.  

