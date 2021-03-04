# ServiceNow Plugin for Grafana

There is an official ServiceNow Plugin for Grafana, but this requires and enterprise license.

This guide is for a free alternative for ServiceNow and 

!!! note
    This effort is <b>blocked</b> due to not having direct access to ServiceNow API (Akana access only)

# Install

```
# grafana-cli --pluginUrl https://github.com/yesoreyeram/grafana-servicenow-datasource/archive/master.zip plugins install yesoreyeram-servicenow-datasource
```

Once installed, go to Grafana > Data Sources > Add data source and pick ServiceNow from the list

# Akana

The ServiceNow API for John Deere is only accessible via Akana at this time.

https://johndeere.service-now.com/kb_view.do?sysparm_article=KB0102773&sysparm_rank=1&sysparm_tsqueryId=e9396fb31bb75050cb3d2f876e4bcb9c

# Links

[Unofficial ServiceNow Plugin](https://github.com/yesoreyeram/grafana-servicenow-datasource)

[Official ServiceNow Plugin](https://grafana.com/grafana/plugins/grafana-servicenow-datasource)