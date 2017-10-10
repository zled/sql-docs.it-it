---
title: Gestione connessione di archivio Azure Data Lake | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: douglasl
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSCM.F1
- sql14.dts.designer.afpadlscm.f1
ms.assetid: f4c44553-0f08-4731-ac47-7534990b8c8d
caps.latest.revision: 7
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: 5acf2de3fccc2f5180358f87bd02591811c59c72
ms.contentlocale: it-it
ms.lasthandoff: 10/10/2017

---
# <a name="azure-data-lake-store-connection-manager"></a>Gestione connessioni di Azure Data Lake Store
Un pacchetto di SQL Server Integration Services (SSIS) è possibile utilizzare la gestione connessione di archivio Azure Data Lake per connettersi a un servizio di archivio Azure Data Lake con uno dei due tipi di autenticazione seguenti:
-   Identità dell'utente AD Azure
-   Identità del servizio di Azure AD 

La gestione connessione di archivio Azure Data Lake è un componente del [Feature Pack di SQL Server Integration Services (SSIS) per Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

>   [!NOTE]
> Per assicurarsi che la Gestione connessioni di Azure Data Lake Store e che i componenti che la usano, cioè l'origine e la destinazione di Azure Data Lake Store, possano connettersi ai servizi, scaricare la versione del Feature Pack di Azure più recente da [qui](https://www.microsoft.com/download/details.aspx?id=49492). 
 
## <a name="configure-the-azure-data-lake-store-connection-manager"></a>Configurare la Gestione connessioni di Azure Data Lake Store

1.  Nel **Aggiungi gestione connessione SSIS** nella finestra di dialogo **AzureDataLake**, quindi selezionare **Aggiungi**. Il **Editor gestione connessione di Azure Data Lake archivio** verrà visualizzata la finestra di dialogo.
  
2.  Nel **Editor gestione connessione di Azure Data Lake archivio** della finestra di dialogo di **ADLS Host** campo, specificare l'URL host di archivio Azure Data Lake. Ad esempio: `https://test.azuredatalakestore.net` o `test.azuredatalakestore.net`.
  
3.  Nel **autenticazione** campo, scegliere il tipo di autenticazione appropriato per accedere ai dati in archivio Azure Data Lake.

    1.  Se si seleziona il **identità dell'utente AD Azure** autenticazione opzione, eseguire le operazioni seguenti:
        1. Specificare i valori per il **nome utente** e **Password** campi. 
    
        2. Per testare la connessione, selezionare **Test connessione**. Se l'utente o dell'amministratore tenant non è stata precedentemente consenso per consentire di SSIS accedere ai dati di archivio Azure Data Lake, selezionare **Accept** quando richiesto. Per altre informazioni su questa esperienza di consenso, vedere [Integrazione di applicazioni con Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-integrating-applications#updating-an-application).
    
        >   [!NOTE] 
        > Quando si seleziona il **identità dell'utente AD Azure** opzione di autenticazione, l'autenticazione a più fattori e l'autenticazione di account Microsoft non sono supportati.
    
    2. Se si seleziona il **identità del servizio di Azure AD** autenticazione opzione, eseguire le operazioni seguenti:
        1. Creare un'applicazione Azure Active Directory (AAD) e il servizio principale per accedere ai dati di Azure Data Lake.
    
        2. Assegnare le autorizzazioni appropriate per consentire l'applicazione di AAD di accedere alle risorse di Azure Data Lake. Per altre informazioni su questa opzione di autenticazione, vedere [Use portal to create Active Directory application and service principal that can access resources](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal)(Usare il portale per creare applicazioni ed entità servizio di Active Directory che possano accedere alle risorse).
    
        3. Specificare i valori per il **Id Client**, **chiave segreta**, e **nome Tenant** campi.
    
        4. Per testare la connessione, selezionare **Test connessione**.  
  
6.  Selezionare **OK** per chiudere la **Editor gestione connessione di Azure Data Lake archivio** la finestra di dialogo.  
  
È possibile visualizzare le proprietà del componente Gestione connessione create nella finestra **Proprietà** .  
  
  
