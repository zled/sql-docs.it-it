---
title: FIPS Mode | Microsoft Docs
ms.custom: 
ms.date: 01/19/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 
author: v-nisidh
ms.author: v-nisidh
manager: andrela
ms.workload: Inactive
ms.openlocfilehash: e6e60a44f4dbe890683436ea6f6801f504396239
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2018
---
# <a name="fips-mode"></a>Modalità FIPS
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Il Driver JDBC di Microsoft per SQL Server supporta *modalità conforme a FIPS 140*. Per Oracle / JVM Sun, consultare il [modalità conforme a FIPS 140 per SunJSSE](https://docs.oracle.com/javase/7/docs/technotes/guides/security/jsse/FIPS.html) sezione fornito da Oracle per configurare FIPS abilitata JVM. 

**Prerequisiti**:
* FIPS configurato JVM
* Certificato SSL appropriato.
* File dei criteri appropriati. 
* Parametri di configurazione appropriato. 


## <a name="fips-configured-jvm"></a>FIPS configurato JVM

Per vedere i moduli approvati per la configurazione di FIPS, fare riferimento il [convalidato FIPS 140-1 e i moduli di crittografia FIPS 140-2](http://csrc.nist.gov/groups/STM/cmvp/documents/140-1/1401val2016.htm). 

I fornitori abbia alcuni passaggi aggiuntivi per configurare JVM con FIPS.

### <a name="ensure-your-jvm-is-in-fips-mode"></a>Verificare che la JVM sia in modalità FIPS
Per garantire che la JVM è FIPS abilitata, eseguire il seguente frammento: 

````
public boolean isFIPS() throws Exception {
    Provider jsse = Security.getProvider("SunJSSE");
    return jsse != null && jsse.getInfo().contains("FIPS");
}
````

## <a name="appropriate-ssl-certificate"></a>Certificato SSL appropriato
Per connettersi a SQL Server in modalità FIPS, è necessario un certificato SSL valido. Installare o importarlo nell'archivio chiavi Java nel computer client (JVM) in cui FIPS è abilitato. Se si non importare o installare il certificato appropriato, potrebbe non essere in grado di connettersi a SQL Server come non è possibile stabilire una connessione sicura.

### <a name="importing-ssl-certificate-in-java-keystore"></a>Importare il certificato SSL in Java KeyStore
Per FIPS, probabilmente è necessario importare il certificato (con estensione CERT) per entrambi PKCS o in un formato specifico del provider. Utilizzare il frammento di codice seguente per importare il certificato SSL e archiviarlo in una cartella di lavoro con il formato appropriato per archivio chiavi. _TRUST_STORE_PASSWORD_ è la password per Java KeyStore. 

````
    public void saveGenericKeyStore(String provider, String trustStoreType, String certName, String certPath) throws KeyStoreException, CertificateException, NoSuchAlgorithmException, NoSuchProviderException, IOException {
        KeyStore ks = KeyStore.getInstance(trustStoreType, provider);
        FileOutputStream os = new FileOutputStream("./MyTrustStore_" + trustStoreType);
        ks.load(null, null);
        ks.setCertificateEntry(certName, getCertificate(certPath));
        ks.store(os, TRUST_STORE_PASSWORD.toCharArray());
        os.flush();
        os.close();
    }

    private Certificate getCertificate(String pathName) throws FileNotFoundException, CertificateException {
        FileInputStream fis = new FileInputStream(pathName);
        CertificateFactory cf = CertificateFactory.getInstance("X.509");
        return cf.generateCertificate(fis);
    }

````


Nell'esempio seguente importa un certificato SSL di Azure nel formato PKCS12 con BouncyCastle Provider. Il certificato viene importato nella directory di lavoro denominata _MyTrustStore_PKCS12_ usando il frammento di codice seguente:

` saveGenericKeyStore(BCFIPS, PKCS12, "SQLAzure SSL Certificate Name", "SQLAzure.cer"); `

## <a name="appropriate-policy-files"></a>File dei criteri appropriati
Per alcuni provider FIPS, sono necessari JAR criteri senza restrizioni. In questi casi, per Sun / Oracle, il download di Java Cryptography Extension (JCE) Unlimited Strenght Jurisdiction Policy Files per [JRE 8](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html) o [JRE 7](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html). 

## <a name="appropriate-configuration-parameters"></a>Parametri di configurazione appropriato
Per eseguire il Driver JDBC in modalità conforme a FIPS, è possibile configurare le proprietà di connessione come illustrato nella tabella seguente. 

**Proprietà**: 

|Proprietà|Tipo|Valore predefinito|Description|Note|
|---|---|---|---|---|
|encrypt|valore booleano ["true / false"]|"false"|Per l'abilitazione di FIPS JVM crittografare proprietà deve essere **true**||
|TrustServerCertificate|valore booleano ["true / false"]|"false"|Per FIPS, è necessario convalidare la catena di certificati, pertanto l'utente deve usare **"false"** valore di questa proprietà. ||
|trustStore|String|null|Il percorso del file Keystore Java in cui è stato importato il certificato. Se si installa certificato nel sistema, quindi non è necessario passare un valore. Driver utilizza cacerts o jssecacerts file.||
|trustStorePassword|String|null|Password utilizzata per verificare l'integrità dei dati del file trustStore.||
|FIPS|valore booleano ["true / false"]|"false"|Per fips abilitata JVM questa proprietà deve essere **true**|Aggiunto in 6.1.4 (stabile versione 6.2.2)||
|fipsProvider|String|null|Provider FIPS configurato nella JVM. Ad esempio, BCFIPS o SunPKCS11 NSS |Aggiunto in 6.1.2 (stabile versione 6.2.2), deprecato in 6.4.0 - visualizzare i dettagli [qui](https://github.com/Microsoft/mssql-jdbc/pull/460).|
|trustStoreType|String|JKS|Per tipo di archivio attendibilità set modalità FIPS PKCS12 o tipo definito dal provider FIPS |Aggiunto in 6.1.2 (stabile versione 6.2.2)||



  
