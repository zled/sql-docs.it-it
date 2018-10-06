---
title: Usare curl per caricare i dati in HDFS nella versione CTP 2.0 di SQL Server 2019 | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 05ce2d4d848b7c244d672f6ab43cbcf09224e63f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796591"
---
# <a name="use-curl-to-load-data-into-hdfs-on-sql-server-2019-ctp-20"></a>Usare curl per caricare i dati in HDFS in SQL Server 2019 CTP 2.0

Questo articolo illustra come usare **curl** per caricare dati in HDFS in SQL Server 2019 CTP 2.0.

## <a name="obtain-the-service-external-ip"></a>Ottenere l'IP esterno del servizio

WebHDFS viene avviato quando viene completata la distribuzione e l'accesso passa attraverso Knox. Viene esposto l'endpoint Knox attraverso un servizio Kubernetes denominato (per ora) **service-sicurezza-lb**.  Per creare l'URL WebHDFS che dovrai usare CURL per caricare e scaricare file che saranno necessari i **service-sicurezza-lb** indirizzo IP esterno e il nome del cluster del servizio. È possibile ottenere l'indirizzo IP esterno del servizio servizio-sicurezza-lb eseguendo questo comando:

```bash
kubectl get service service-security-lb -n <cluster name> -o json | jq -r .status.loadBalancer.ingress[0].ip
```

> [!NOTE]
> Il `<cluster name>` di seguito è il nome del cluster fornito quando è stato eseguito mssqlctl creare cluster `<cluster name>`.

## <a name="construct-the-url-to-access-webhdfs"></a>Creare l'URL per accedere a WebHDFS

A questo punto, è possibile costruire l'URL di accesso di WebHDFS come indicato di seguito:

`https://<service-security-lb service external IP address>:30433/gateway/default/webhdfs/v1/`

Esempio:

`https://13.66.190.205:30443/gateway/default/webhdfs/v1/`

## <a name="list-a-file"></a>Elencare un file

File di elenco sotto **hdfs: / / / airlinedata** usare il comando curl seguente:

```bash
curl -i -k -u root:root-password -X GET 'https://<service-security-lb IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/?op=liststatus'
```

## <a name="put-a-local-file-into-hdfs"></a>Inserire un file locale in HDFS

Per inserire un nuovo file **test. csv** dalla directory locale alla directory airlinedata (**Content-Type** parametro è obbligatorio) usare il comando curl seguente:

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<service-security-lb IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

## <a name="create-a-directory"></a>Creare una directory

Per creare una directory **testare** sotto `hdfs:///` usare il comando seguente:

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<service-security-lb IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sui cluster di big data di SQL Server, vedere [What ' s cluster di big data di SQL Server?](big-data-cluster-overview.md).