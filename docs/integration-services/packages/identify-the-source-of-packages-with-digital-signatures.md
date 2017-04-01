---
title: "Identificazione dell&#39;origine dei pacchetti con firme digitali | Microsoft Docs"
ms.custom: ""
ms.date: "08/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "firma di pacchetti [Integration Services]"
  - "certificati [Integration Services]"
  - "pacchetti [Integration Services], sicurezza"
  - "sicurezza [Integration Services], certificati"
  - "firma di criteri [Integration Services]"
ms.assetid: a433fbef-1853-4740-9d5e-8a32bc4ffbb2
caps.latest.revision: 46
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 46
---
# Identificazione dell&#39;origine dei pacchetti con firme digitali
  Un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] può essere firmato con un certificato digitale per identificarne l'origine. Dopo la firma di un pacchetto con un certificato digitale, è possibile configurare [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per controllare o verificare la firma digitale prima del caricamento del pacchetto. Per fare in modo che [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] controlli la firma, impostare un'opzione in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] o nell'utilità **dtexec** (dtexec.exe) oppure impostare un valore facoltativo del Registro di sistema.  
  
## Firma di un pacchetto con un certificato digitale  
 Prima di poter firmare un pacchetto con un certificato digitale, è necessario ottenere o creare il certificato. Dopo aver ottenuto il certificato, è possibile utilizzarlo per la firma del pacchetto. Per altre informazioni su come ottenere un certificato e usarlo per firmare un pacchetto, vedere [Firmare un pacchetto con un certificato digitale](../../integration-services/packages/sign-a-package-by-using-a-digital-certificate.md).  
  
## Impostazione di un'opzione per la verifica della firma del pacchetto  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] e l'utilità **dtexec** includono un'opzione per configurare [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per la verifica della firma digitale dei pacchetti firmati. È possibile usare [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] o l'utilità **dtexec** a seconda che si voglia controllare tutti i pacchetti o solo alcuni pacchetti specifici:  
  
-   Per controllare la firma digitale di tutti i pacchetti prima del caricamento in fase di progettazione, impostare l'opzione **Controlla firma digitale al caricamento di un pacchetto** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Questa opzione è un'impostazione globale per tutti i pacchetti di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].
  
-   Per controllare la firma digitale di un singolo pacchetto, specificare l'opzione **/VerifyS[igned]** quando si usa l'utilità **dtexec** per eseguire il pacchetto. Per altre informazioni, vedere [dtexec Utility](../../integration-services/packages/dtexec-utility.md).  
  
## Impostazione di un valore del Registro di sistema per la verifica della firma del pacchetto  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] supporta anche un valore facoltativo del Registro di sistema, **BlockedSignatureStates**, che può essere usato per gestire i criteri di un'organizzazione per il caricamento di pacchetti firmati e non firmati. Il valore del Registro di sistema consente di impedire il caricamento di pacchetti non firmati o con firme non valide o non attendibili. Per altre informazioni su come impostare questo valore del Registro di sistema, vedere [Implementare criteri per le firme tramite l'impostazione di un valore del Registro di sistema](../../integration-services/packages/implement-a-signing-policy-by-setting-a-registry-value.md).  
  
> **NOTA:** il valore facoltativo **BlockedSignatureStates** del Registro di sistema può specificare un'impostazione più restrittiva rispetto all'opzione per la firma digitale impostata in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] o nella riga di comando **dtexec**. In questo caso, l'impostazione del Registro di sistema più restrittiva ha la precedenza rispetto ad altre impostazioni.  
  
## Vedere anche  
 [Pacchetti di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-packages.md)   
 [Panoramica della sicurezza &#40;Integration Services&#41;](../../integration-services/security/security-overview-integration-services.md)  
  
  