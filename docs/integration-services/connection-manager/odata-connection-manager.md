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
ms.sourcegitcommit: 8397673c7ed9dfe8ae02871f9077ed7286e49863
ms.openlocfilehash: b23a158bff546fd6ffb4208638c039d690379ce1
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="odata-connection-manager"></a>Gestione connessione OData
  Usare una gestione connessione OData per connettersi a un'origine OData. Un componente di origine OData esegue la connessione a un'origine OData con una gestione connessione OData e utilizza i dati del servizio. Per ulteriori informazioni, vedere [OData Source](../../integration-services/data-flow/odata-source.md).  
  
## <a name="adding-an-odata-connection-manager-to-an-ssis-package"></a>Aggiunta di una gestione connessione OData a un pacchetto SSIS  
 È possibile aggiungere una nuova gestione connessione OData a un pacchetto SSIS nelle tre modalità seguenti:  
  
-   Fare clic sul pulsante **Nuovo** in **Editor origine OData**  
  
-   Fare clic con il pulsante destro del mouse sulla cartella **Gestioni connessioni** in **Esplora soluzioni**e quindi fare clic su **Nuova gestione connessione**. Selezionare **ODATA** per **Tipo gestione connessione**.  
  
-   Fare clic con il pulsante destro del mouse nel riquadro **Gestioni connessioni** nella parte inferiore della finestra di progettazione del pacchetto e quindi selezionare **Nuova connessione**. Selezionare **ODATA** per **Tipo gestione connessione**.  
  
## <a name="connection-manager-authentication"></a>Autenticazione di gestione connessione  
 Gestione connessione OData supporta cinque modalità di autenticazione.  
  
-   Autenticazione di Windows  
  
-   Autenticazione di base (con il nome utente e la password)  

-   Microsoft Dynamics AX Online (con nome utente e password)
  
-   Microsoft Dynamics CRM Online (con nome utente e password)
  
-   Microsoft Online Services (con nome utente e password)  
  
 Per l'accesso anonimo, selezionare l'opzione Autenticazione di Windows.  
  
### <a name="specifying-and-securing-credentials"></a>Specifica e protezione delle credenziali  
 Se il servizio OData richiede l'autenticazione di base, è possibile specificare un nome utente e una password in [Editor gestione connessione OData](../../integration-services/connection-manager/odata-connection-manager-editor.md). I valori immessi nell'editor sono persistenti nel pacchetto. Il valore della password è crittografato in base al livello di protezione del pacchetto.  
  
 È possibile impostare i parametri dei valori del nome utente e della password in più modalità oppure archiviarli all'esterno del pacchetto. Ad esempio, è possibile farlo usando i parametri oppure impostando le proprietà di gestione connessione direttamente quando si esegue il pacchetto con SQL Server Management Studio.  
  
## <a name="odata-connection-manager-properties"></a>Proprietà di gestione connessione OData  
 L'elenco seguente descrive le proprietà di gestione connessione OData.  
  
|||  
|-|-|  
|Proprietà|Description|  
|URL|URL del documento di servizio.|  
|UserName|Nome utente da utilizzare per l'autenticazione di base.|  
|Password|Password da utilizzare per l'autenticazione di base.|  
|ConnectionString|Riflette altre proprietà della gestione connessione.|  
  
## <a name="odata-connection-manager-editor"></a>Editor gestione connessione OData
  Utilizzare la finestra di dialogo **Editor gestione connessione OData** per aggiungere una connessione o modificare una connessione esistente a un'origine OData.  
  
### <a name="options"></a>Opzioni  
 **Nome gestione connessione**  
 Nome della gestione connessione.  
  
 **Percorso documento di servizio**  
 URL del servizio OData. Ad esempio, http://services.odata.org/V3/Northwind/Northwind.svc/.  
  
 **Autenticazione**  
 Selezionare **Autenticazione di Windows** oppure **Usa il nome utente e la password seguenti** per l' **Autenticazione di base**. Se si seleziona la seconda opzione immettere il **nome utente** e la **password**. 
 
 Esistono tre ulteriori opzioni. Selezionare **Microsoft Dynamics AX Online** per Dynamics AX Online, selezionare **Microsoft Dynamics CRM Online** per Dynamics CRM Online e selezionare **Microsoft Online Services** per Microsoft Online Services. Se si seleziona una di queste tre opzioni, immettere **nome utente** e **password**.
  
 **Test connessione**  
 Fare clic su questo pulsante per testare la connessione all'origine OData.  
  
## <a name="see-also"></a>Vedere anche  
 [Editor gestione connessione OData](../../integration-services/connection-manager/odata-connection-manager-editor.md)  
  
  
