---
title: Gestione connessione di Azure Data Lake Analytics | Microsoft Docs
ms.custom: ''
ms.date: 05/18/2018
ms.prod: sql
ms.prod_service: integration-services
ms.component: connection-manager
ms.reviewer: douglasl
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSCM.F1
- sql14.dts.designer.afpadlscm.f1
ms.assetid: f4c44553-0f08-4731-ac47-7534990b8c8d
caps.latest.revision: 7
author: yanancai
ms.author: yanacai
manager: craigg
ms.openlocfilehash: 17b63aad55cf50262d7e1e56267859b1a34cc9d3
ms.sourcegitcommit: 44e9bf62f2c75449c17753ed66bf85c43928dbd5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/05/2018
ms.locfileid: "37854413"
---
# <a name="azure-data-lake-analytics-connection-manager"></a>Gestione connessione di Azure Data Lake Analytics

Un pacchetto di SQL Server Integration Services (SSIS) è in grado di usare Gestione connessione di Azure Data Lake Analytics per connettersi a un servizio di Azure Data Lake Analytics con uno dei due tipi di autenticazione seguenti:
-   Identità utente Azure AD
-   Identità del servizio di Azure AD 

Gestione connessione di Azure Data Lake Analytics è un componente del [Feature Pack di SQL Server Integration Services (SSIS) per Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
 
## <a name="configure-the-azure-data-lake-analytics-connection-manager"></a>Configurare la gestione connessione di Azure Data Lake Analytics

1.  Nella finestra di dialogo **Aggiungi gestione connessione SSIS** selezionare **AzureDataLakeAnalytics**e quindi **Aggiungi**. Viene visualizzata la finestra di dialogo dell'**editor di Gestione connessione di Azure Data Lake Analytics**.
  
2.  Nella finestra di dialogo dell'**editor di Gestione connessione di Azure Data Lake Analytics** specificare il nome dell'account di Data Lake Analytics nel campo **ADLA Account Name** (Nome account ADLA). Ad esempio: nomeaccountadla.
  
3.  Nel campo **Autenticazione** scegliere il tipo di autenticazione appropriato per accedere ai dati in Azure Data Lake Analytics.

    1.  Se si seleziona l'opzione di autenticazione **Identità utente Azure AD**, eseguire le operazioni seguenti:
        1. Specificare i valori per i campi **Nome utente** e **Password**. 
    
        2. Fare clic su **Test connessione** per testare la connessione. Se l'utente o l'amministratore del tenant non ha precedentemente autorizzato SSIS ad accedere all'account di Azure Data Lake Analytics, selezionare **Accetto** quando richiesto. Per altre informazioni su questa esperienza di consenso, vedere [Integrazione di applicazioni con Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-integrating-applications#updating-an-application).
    
        >   [!NOTE] 
        > Quando si seleziona l'autenticazione dell'**identità del servizio di Azure AD** l'autenticazione a più fattori e l'autenticazione dell'account Microsoft non sono supportate.
    
    2. Se si seleziona l'autenticazione dell'**identità del servizio di Azure AD**, eseguire le operazioni seguenti:
        1. Creare un'applicazione Azure Active Directory (AAD) e l'entità servizio per accedere all'account di Azure Data Lake Analytics. Per altre informazioni su questa opzione di autenticazione, vedere [Use portal to create Active Directory application and service principal that can access resources](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal) (Usare il portale per creare applicazioni ed entità servizio di Active Directory che possano accedere alle risorse).
    
        2. Assegnare le autorizzazioni appropriate per consentire all'applicazione AAD di accedere all'account di Azure Data Analytics. Informazioni su come concedere autorizzazioni all'account di Azure Data Lake Analytics [usando l'Aggiunta guidata utente](https://docs.microsoft.com/azure/data-lake-analytics/data-lake-analytics-manage-use-portal#add-a-new-user). 
    
        3. Specificare i valori per i campi **ID applicazione**, **Chiave di autenticazione** e **ID Tenant**.
    
        4. Fare clic su **Test connessione** per testare la connessione.  

4.  Selezionare **OK** per chiudere la finestra di dialogo dell'**editor di Gestione connessione di Azure Data Lake Analytics**.  

## <a name="view-the-properties-of-the-connection-manager"></a>Visualizzare le proprietà della gestione connessione
È possibile visualizzare le proprietà del componente Gestione connessione create nella finestra **Proprietà** .  
  
  
