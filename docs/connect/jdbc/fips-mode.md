---
title: La modalità FIPS | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: v-nisidh
ms.author: v-nisidh
manager: andrela
ms.openlocfilehash: cc13455e6f56950d6988909b53aa7664c7fd77f3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47723829"
---
# <a name="fips-mode"></a>Modalità FIPS
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Microsoft JDBC Driver per SQL Server supporta *modalità conforme a FIPS 140*. Per Oracle / JVM Sun, vedere la [modalità conforme a FIPS 140 per SunJSSE](https://docs.oracle.com/javase/7/docs/technotes/guides/security/jsse/FIPS.html) sezione fornito da Oracle per configurare FIPS per JVM abilitato. 

**Prerequisiti**:
* FIPS configurato JVM
* Certificato SSL appropriato.
* File dei criteri appropriate. 
* Parametri di configurazione appropriato. 


## <a name="fips-configured-jvm"></a>FIPS configurato JVM

Per visualizzare i moduli approvati per la configurazione di FIPS, vedere la [convalidati tramite FIPS 140-1 e moduli di crittografia FIPS 140-2](http://csrc.nist.gov/groups/STM/cmvp/documents/140-1/1401val2016.htm). 

I fornitori possono avere alcuni passaggi aggiuntivi per configurare JVM a FIPS.

### <a name="ensure-your-jvm-is-in-fips-mode"></a>Verificare che il JVM è in modalità FIPS
Per garantire la JVM abilitato FIPS, eseguire il frammento di codice seguente: 

```java
public boolean isFIPS() throws Exception {
    Provider jsse = Security.getProvider("SunJSSE");
    return jsse != null && jsse.getInfo().contains("FIPS");
}
```

## <a name="appropriate-ssl-certificate"></a>Certificato SSL appropriato
Per connettersi a SQL Server in modalità FIPS, è necessario un certificato SSL valido. Installare o importarlo in Java Key Store nel computer client (JVM) in cui è abilitato FIPS.

### <a name="importing-ssl-certificate-in-java-keystore"></a>Importare il certificato SSL nell'archivio chiavi Java
Per FIPS, molto probabilmente è necessario importare il certificato (con estensione CERT) per entrambi PKCS o in un formato specifico del provider. Usare il frammento di codice seguente per importare il certificato SSL e archiviarlo in una directory di lavoro con il formato dell'archivio chiavi appropriata. _TRUST_STORE_PASSWORD_ è la password per archivio chiavi Java. 

```java
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

```


Nell'esempio seguente importa un certificato SSL di Azure nel formato PKCS12 BouncyCastle provider. Il certificato viene importato nella directory di lavoro denominata _MyTrustStore_PKCS12_ usando il frammento seguente:

` saveGenericKeyStore(BCFIPS, PKCS12, "SQLAzure SSL Certificate Name", "SQLAzure.cer"); `

## <a name="appropriate-policy-files"></a>File dei criteri appropriati
Per alcuni provider di FIPS, sono necessari file JAR di criteri senza restrizioni. In questi casi, per Sun / Oracle, scaricare il Java Cryptography Extension (JCE) senza limiti Strenght Jurisdiction Policy Files per [JRE 8](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html) oppure [JRE 7](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html). 

## <a name="appropriate-configuration-parameters"></a>Parametri di configurazione appropriato
Per eseguire il Driver JDBC in modalità FIPS compatibile, configurare le proprietà di connessione come illustrato nella tabella seguente. 

**Proprietà**: 

|Proprietà|Tipo|Default|Descrizione|Note|
|---|---|---|---|---|
|encrypt|booleano ["true/false"]|"false"|Per FIPS abilitata JVM crittografa la proprietà deve essere **true**||
|TrustServerCertificate|booleano ["true/false"]|"false"|Per FIPS, l'utente deve convalidare la catena di certificati in modo che l'utente deve usare **"false"** valore per questa proprietà. ||
|trustStore|String|null|Il percorso del file dell'archivio chiavi Java in cui è stato importato il certificato. Se si installa certificato nel sistema, quindi non è necessario passare un valore. Driver utilizza file cacerts o jssecacerts.||
|trustStorePassword|String|null|Password utilizzata per verificare l'integrità dei dati del file trustStore.||
|fips|booleano ["true/false"]|"false"|Per JVM abilitato FIPS questa proprietà deve essere **true**|Aggiunto in 6.1.4 (stabile versione 6.2.2)||
|fipsProvider|String|null|Provider FIPS configurato nella JVM. Ad esempio, BCFIPS o SunPKCS11 NSS |Aggiunto in 6.1.2 (stabile versione 6.2.2), deprecato in 6.4.0 - visualizzare i dettagli [qui](https://github.com/Microsoft/mssql-jdbc/pull/460).|
|trustStoreType|String|JKS|Per tipo di archivio trust set modalità FIPS PKCS12 o tipo definito dal provider FIPS |Aggiunto in 6.1.2 (stabile versione 6.2.2)||



  
