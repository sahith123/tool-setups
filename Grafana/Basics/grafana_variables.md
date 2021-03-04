# Grafana Variables

You can declare variables in Grafana to be used in queries and to add dropdowns to Dashboards.

![Grafana Graph](../img/grafana-variables1.png)
![Grafana Graph](../img/grafana-variables2.png)

When creating a variable, think of it as a query statement you would make to get a list of things, like a list of AWS accounts or S3 bucket names:

![Grafana Graph](../img/grafana-variables3.png)

Once these variables are defined, they can be used to create new visualizations:

![Grafana Graph](../img/grafana-variables4.png)

From here, you can use a WHERE statement just like you would in a SQL query to limit results from the dropdown to the selected variable:

![Grafana Graph](../img/grafana-variables5.png)

!!! note
    It's very important to wrap your variable in single quotes or you may get errors.

At this point, when using the Dashboard, you can drop down to select the variables to only display information for a specific account or bucket:

![Grafana Graph](../img/grafana-variables6.png)

# Drop Down Menu Inheritance - ElasticSearch

Say for example, you want to select one menu, which the next drop down menu so you can really dial down into something.

For example: Organization > AWS Account > Component

![Grafana Graph](../img/grafana-variables7.png)

This is an ElasticSearch example, so to create these variables, you would use the "query" filter with the previous variable to drill down:

![Grafana Graph](../img/grafana-variables8.png)

The organization is just a list of all Organization keywords:

![Grafana Graph](../img/grafana-variables9.png)

Next is get the AWS Account ID and filter by Organization:

![Grafana Graph](../img/grafana-variables10.png)

Next is to get all Components and filter by AWS Account ID:

![Grafana Graph](../img/grafana-variables11.png)

# Drop Down Menu Inheritance - SQL

This works the same way, but with SQL statements:

![Grafana Graph](../img/grafana-variables12.png)

First create a list using a standard SQL statement:

![Grafana Graph](../img/grafana-variables13.png)

Next, use a SQL statement with a WHERE clause to filter by AWS Account:

![Grafana Graph](../img/grafana-variables14.png)

The end result is that when you pick and AWS Account Name, it will then show all the S3 Buckets for that AWS Account:

![Grafana Graph](../img/grafana-variables15.png)

# Saving dropdown variables as default values for the dashboard

Some dashboards you create or download may default to the first variable in the dropdown list and this may not be the correct desired result.  If you want a different variable to be the default value in the dashboard, then select the default variable, then save the dashboard and select "save current variables" before saving.

![Grafana Graph](../img/grafana-variables16.png)

![Grafana Graph](../img/grafana-variables17.png)