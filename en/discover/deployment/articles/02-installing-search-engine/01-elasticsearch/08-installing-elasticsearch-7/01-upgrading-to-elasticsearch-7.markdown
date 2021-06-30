---
header-id: upgrading-to-elasticsearch-7
---

# Upgrading to Elasticsearch 7

[TOC levels=1-4]

Elasticsearch 7 is supported for @product-ver@. If you're upgrading @product@
and still running Elasticsearch 6, consider upgrading your Elasticsearch
servers too. If you're setting up a new system and not already running a remote
Elasticsearch 6 server, follow the 
[installation guide](/docs/7-1/deploy/-/knowledge_base/d/installing-elasticsearch-7) to install
Elasticsearch 7 and the 
[configuration guide](/docs/7-1/deploy/-/knowledge_base/d/configuring-the-liferay-elasticsearch-connector)
to configure the Elasticsearch adapter.

| **Before Proceeding,** back up your existing data before upgrading
| Elasticsearch. If something goes wrong during or after the upgrade, roll back
| to the previous version using the uncorrupted index snapshots. See
| [here](/docs/7-1/deploy/-/knowledge_base/d/backing-up-elasticsearch)
| for more information.

Here, you'll learn to upgrade an existing Elasticsearch 6 server (or cluster)
to Elasticsearch 7: 

1.  [Install and configure Elasticsearch 7](/docs/7-1/deploy/-/knowledge_base/d/installing-elasticsearch-7).

2. In @product-ver@, security is now provided out of the box. If you're using
   X-Pack security, enable it (it's disabled by default):

    ```yaml
    xpack.security.enabled: true
    ```

3.  Blacklist the bundled Liferay Connector to Elasticsearch 6.

4.  Install and configure the Liferay Connector to Elasticsearch 7.

5.  Re-index all search  and spell check indexes.

Learn about configuring Elasticsearch
[here](/docs/7-1/deploy/-/knowledge_base/d/configuring-the-liferay-elasticsearch-connector).

## Blacklisting Elasticsearch 6

To blacklist Elasticsearch 6,

1.  Create a configuration file named

    ```bash
    com.liferay.portal.bundle.blacklist.internal.BundleBlacklistConfiguration.config
    ```

2.  Give it these contents:

    ```properties
    blacklistBundleSymbolicNames=[ \
        "com.liferay.portal.search.elasticsearch6.api", \
        "com.liferay.portal.search.elasticsearch6.impl", \
        "com.liferay.portal.search.elasticsearch6.spi", \
        "com.liferay.portal.search.elasticsearch6.xpack.security.impl", \
        "Liferay Connector to X-Pack Security [Elastic Stack 6.x] - Impl", \
        "Liferay Enterprise Search Security  - Impl" \
    ]
    ```

## Re-index

Once the Elasticsearch adapter is installed and talking to the Elasticsearch
cluster, navigate to *Control Panel* &rarr; *Configuration* &rarr; *Search*,
and click *Execute* for the *Reindex all search indexes* entry.

You must also re-index the spell check indexes.

## Reverting to Elasticsearch 6

Stuff happens. If that stuff involves an unrecoverable failure during the
upgrade to Elasticsearch 7, roll back to Elasticsearch 6 and regroup.

Since your Elasticsearch 6 and 7 are currently two separate installations, this
procedure takes only a few steps:

1.  Stop the Liferay Connector to Elasticsearch 6.

2.  Stop Elasticsearch 7 and make sure that the Elasticsearch 6
    `elasticsearch.yml` and the connector app are configured to use the same
    port (9200 by default).

3.  Start the Elasticsearch server, and then restart the Liferay Connector to
    Elasticsearch 6.

